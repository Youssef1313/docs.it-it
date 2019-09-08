---
title: 'Procedura: Esportare informazioni WSDL personalizzate'
ms.date: 03/30/2017
ms.assetid: 5c1e4b58-b76b-472b-9635-2f80d42a0734
ms.openlocfilehash: 723121798fee3a3c0b49a7f15995bb26444836e8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797013"
---
# <a name="how-to-export-custom-wsdl"></a>Procedura: Esportare informazioni WSDL personalizzate

In questo argomento viene illustrato come esportare informazioni WSDL personalizzate. A tale scopo è necessario definire un nuovo attributo di codice denominato `WsdlDocumentationAttribute` che consente di aggiungere informazioni personalizzate nel codice WSDL generato dal servizio.

## <a name="to-export-custom-wsdl-information"></a>Per esportare informazioni WSDL personalizzate

1. Implementare l'interfaccia <xref:System.ServiceModel.Description.IWsdlExportExtension>. Questa interfaccia può essere implementata in una classe che implementa una delle interfacce seguenti: <xref:System.ServiceModel.Description.IOperationBehavior>, <xref:System.ServiceModel.Description.IContractBehavior> o <xref:System.ServiceModel.Description.IEndpointBehavior>. Può inoltre essere implementata in una classe derivata della classe <xref:System.ServiceModel.Channels.BindingElement>. In questo esempio l'interfaccia <xref:System.ServiceModel.Description.IWsdlExportExtension> viene implementata in una classe di attributo che implementa l'interfaccia <xref:System.ServiceModel.Description.IContractBehavior>.

2. L'interfaccia <xref:System.ServiceModel.Description.IWsdlExportExtension> definisce due metodi: <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> e <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29>. Questi metodi consentono di modificare e/o aggiungere informazioni aggiuntive nel contesto <xref:System.ServiceModel.Description.WsdlContractConversionContext>. In questo esempio il metodo <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> viene utilizzato per recuperare una raccolta di oggetti <xref:System.ServiceModel.Description.OperationDescription>. All'interno di questa raccolta viene quindi eseguita una ricerca per verificare la presenza di un attributo `WsdlDocumentationAttribute`. Se la ricerca ha esito positivo, il sistema estrae il testo associato all'attributo trovato, genera un elemento riassuntivo e quindi aggiunge tale elemento all'elemento `DocumentationElement` dell'operazione.

    ```csharp
    public void ExportContract(WsdlExporter exporter, WsdlContractConversionContext context)
    {
        Console.WriteLine("Inside ExportContract");
        if (context.Contract != null)
        {
            // Set the document element; if this is not done first, there is no XmlElement in the
            // DocumentElement property.
            context.WsdlPortType.Documentation = string.Empty;
            // Contract comments.
            XmlDocument owner = context.WsdlPortType.DocumentationElement.OwnerDocument;
            XmlElement summaryElement = Formatter.CreateSummaryElement(owner, this.Text);
            context.WsdlPortType.DocumentationElement.AppendChild(summaryElement);

            foreach (OperationDescription op in context.Contract.Operations)
            {
                Operation operation = context.GetOperation(op);
                object[] opAttrs = op.SyncMethod.GetCustomAttributes(typeof(WsdlDocumentationAttribute), false);
                if (opAttrs.Length == 1)
                {
                    string opComment = ((WsdlDocumentationAttribute)opAttrs[0]).Text;

                    // This.Text returns the string for the operation-level attributes.
                    // Set the doc element; if this is not done first, there is no XmlElement in the
                    // DocumentElement property.
                    operation.Documentation = String.Empty;

                    XmlDocument opOwner = operation.DocumentationElement.OwnerDocument;
                    XmlElement newSummaryElement = Formatter.CreateSummaryElement(opOwner, opComment);
                    operation.DocumentationElement.AppendChild(newSummaryElement);
                }
            }
        }
    }
    ```

## <a name="example"></a>Esempio

Nell'esempio di codice seguente viene illustrata l'implementazione completa della classe `WsdlDocumentationAttribute`.

```csharp
public class WsdlDocumentationAttribute : Attribute, IContractBehavior, IWsdlExportExtension
{
string text;
       XmlElement customWsdlDocElement = null;
public WsdlDocumentationAttribute(string text)
{ this.text = text;}

       public WsdlDocumentationAttribute(XmlElement wsdlDocElement)
        { this.customWsdlDocElement = wsdlDocElement; }

        public XmlElement WsdlDocElement
        {
            get { return this.customWsdlDocElement; }
            set { this.customWsdlDocElement = value; }
        }
       public string Text
{
get { return this.text; }
set { this.text = value; }
}

     public void ExportContract(WsdlExporter exporter, WsdlContractConversionContext context)
{
          Console.WriteLine("Inside ExportContract");
if (context.Contract != null)
{
                // Set the document element; if this is not done first, there is no XmlElement in the
                // DocumentElement property.
                context.WsdlPortType.Documentation = string.Empty;
                // Contract comments.
                XmlDocument owner = context.WsdlPortType.DocumentationElement.OwnerDocument;
                XmlElement summaryElement = Formatter.CreateSummaryElement(owner, this.Text);
                context.WsdlPortType.DocumentationElement.AppendChild(summaryElement);

                foreach (OperationDescription op in context.Contract.Operations)
                {
                    Operation operation = context.GetOperation(op);
                    object[] opAttrs = op.SyncMethod.GetCustomAttributes(typeof(WsdlDocumentationAttribute), false);
                    if (opAttrs.Length == 1)
                    {
                        string opComment = ((WsdlDocumentationAttribute)opAttrs[0]).Text;

                        // This.Text returns the string for the operation-level attributes.
                        // Set the document element; if this is not done first, there is no XmlElement in the
                        // DocumentElement property.
                        operation.Documentation = String.Empty;

                        XmlDocument opOwner = operation.DocumentationElement.OwnerDocument;
                        XmlElement newSummaryElement = Formatter.CreateSummaryElement(opOwner, opComment);
                        operation.DocumentationElement.AppendChild(newSummaryElement);
                    }
                }
            }
        }

public void ExportEndpoint(WsdlExporter exporter, WsdlEndpointConversionContext context)
        {
            Console.WriteLine("ExportEndpoint called.");
        }

        public void AddBindingParameters(ContractDescription description, ServiceEndpoint endpoint, BindingParameterCollection parameters)
        { return; }

        public void ApplyClientBehavior(ContractDescription description, ServiceEndpoint endpoint, ClientRuntime client)
        { return; }

        public void ApplyDispatchBehavior(ContractDescription description, ServiceEndpoint endpoint, DispatchRuntime dispatch)
        { return; }

        public void Validate(ContractDescription description, ServiceEndpoint endpoint) { return; }
    }

  public class Formatter
  {

#region Utility Functions

    public static XmlElement CreateSummaryElement(XmlDocument owningDoc, string text)
    {
      XmlElement summaryElement = owningDoc.CreateElement("summary");
      summaryElement.InnerText = text;
      return summaryElement;
    }

public static CodeCommentStatementCollection FormatComments(string text)
{
      /*
       * Note that in Visual C# the XML comment format absorbs a
       * documentation element with a line break in the middle. This sample
       * could take an XmlElement and create code comments in which
       * the element never had a line break in it.
      */

      CodeCommentStatementCollection collection = new CodeCommentStatementCollection();
collection.Add(new CodeCommentStatement("From WsdlDocumentation:", true));
collection.Add(new CodeCommentStatement(String.Empty, true));

foreach (string line in WordWrap(text, 80))
{
collection.Add(new CodeCommentStatement(line, true));
}

collection.Add(new CodeCommentStatement(String.Empty, true));
return collection;
}

public static Collection<string> WordWrap(string text, int columnWidth)
{
Collection<string> lines = new Collection<string>();
System.Text.StringBuilder builder = new System.Text.StringBuilder();

string[] words = text.Split(' ');
foreach (string word in words)
{
if ((builder.Length > 0) && ((builder.Length + word.Length + 1) > columnWidth))
{
lines.Add(builder.ToString());
builder = new System.Text.StringBuilder();
}
builder.Append(word);
builder.Append(' ');
}
lines.Add(builder.ToString());

return lines;
}

#endregion

    public static XmlElement CreateReturnsElement(XmlDocument owner, string p)
    {
      XmlElement returnsElement = owner.CreateElement("returns");
      returnsElement.InnerText = p;
      return returnsElement;
    }
  }
```

## <a name="see-also"></a>Vedere anche

- [Metadati](../feature-details/metadata.md)
