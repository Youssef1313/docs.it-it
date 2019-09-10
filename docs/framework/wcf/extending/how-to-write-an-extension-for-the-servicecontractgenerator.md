---
title: "Procedura: Scrivere un'estensione per ServiceContractGenerator"
ms.date: 03/30/2017
ms.assetid: 876ca823-bd16-4bdf-9e0f-02092df90e51
ms.openlocfilehash: af23babd9255c45b9fa89b5c167de6960f0f690e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855718"
---
# <a name="how-to-write-an-extension-for-the-servicecontractgenerator"></a>Procedura: Scrivere un'estensione per ServiceContractGenerator
In questo argomento viene illustrato come scrivere un'estensione per la classe <xref:System.ServiceModel.Description.ServiceContractGenerator>. A tal fine è necessario implementare l'interfaccia <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> su un comportamento di operazione oppure l'interfaccia <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> su un comportamento di contratto. In questo argomento viene illustrato come implementare l'interfaccia <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> in un comportamento di contratto.  
  
 <xref:System.ServiceModel.Description.ServiceContractGenerator> genera contratti di servizio, tipi di client e configurazioni client da istanze <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription> e <xref:System.ServiceModel.Channels.Binding>. In genere, si importano istanze <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription> e <xref:System.ServiceModel.Channels.Binding> da metadati del servizio e si utilizzano quindi tali istanze per generare il codice necessario per chiamare il servizio. In questo esempio viene utilizzata un'implementazione <xref:System.ServiceModel.Description.IWsdlImportExtension> per elaborare annotazioni WSDL e aggiungere estensioni di generazione del codice ai contratti importati al fine di generare commenti sul codice generato.  
  
### <a name="to-write-an-extension-for-the-servicecontractgenerator"></a>Scrivere un'estensione per ServiceContractGenerator  
  
1. Implementare <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>. Per modificare il contratto di servizio generato, utilizzare l'istanza <xref:System.ServiceModel.Description.ServiceContractGenerationContext> passata nel metodo <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29>.  
  
    ```csharp
    public void GenerateContract(ServiceContractGenerationContext context)  
    {  
        Console.WriteLine("In generate contract.");  
    context.ContractType.Comments.AddRange(Formatter.FormatComments(commentText));  
    }  
    ```  
  
2. Implementare <xref:System.ServiceModel.Description.IWsdlImportExtension> nella stessa classe. Il metodo <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> consente di elaborare un'estensione WSDL specifica (annotazioni WSDL in questo caso) mediante l'aggiunta di un'estensione di generazione del codice all'istanza <xref:System.ServiceModel.Description.ContractDescription> importata.  
  
    ```csharp
    public void ImportContract(WsdlImporter importer, WsdlContractConversionContext context)  
       {  
                // Contract documentation  
             if (context.WsdlPortType.Documentation != null)  
             {  
                    context.Contract.Behaviors.Add(new WsdlDocumentationImporter(context.WsdlPortType.Documentation));  
             }  
             // Operation documentation  
             foreach (Operation operation in context.WsdlPortType.Operations)  
             {  
                if (operation.Documentation != null)  
                {  
                   OperationDescription operationDescription = context.Contract.Operations.Find(operation.Name);  
                   if (operationDescription != null)  
                   {  
                            operationDescription.Behaviors.Add(new WsdlDocumentationImporter(operation.Documentation));  
                   }  
                }  
             }  
          }  
          public void BeforeImport(ServiceDescriptionCollection wsdlDocuments, XmlSchemaSet xmlSchemas, ICollection<XmlElement> policy)   
            {  
                Console.WriteLine("BeforeImport called.");  
            }  
  
          public void ImportEndpoint(WsdlImporter importer, WsdlEndpointConversionContext context)   
            {  
                Console.WriteLine("ImportEndpoint called.");  
            }  
    ```  
  
3. Aggiungere l'unità di importazione WSDL alla configurazione del client.  
  
    ```xml  
    <metadata>  
      <wsdlImporters>  
        <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
      </wsdlImporters>  
    </metadata>  
    ```  
  
4. Nel codice client creare `MetadataExchangeClient` e chiamare `GetMetadata`.  
  
    ```csharp  
    MetadataExchangeClient mexClient = new MetadataExchangeClient(metadataAddress);  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet metaDocs = mexClient.GetMetadata();  
    ```  
  
5. Creare un `WsdlImporter` e chiamare `ImportAllContracts`.  
  
    ```csharp  
    WsdlImporter importer = new WsdlImporter(metaDocs);            System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
6. Creare `ServiceContractGenerator` e chiamare `GenerateServiceContractType` per ogni contratto.  
  
    ```csharp  
    ServiceContractGenerator generator = new ServiceContractGenerator();  
    foreach (ContractDescription contract in contracts)  
    {  
       generator.GenerateServiceContractType(contract);  
    }  
    if (generator.Errors.Count != 0)  
       throw new Exception("There were errors during code compilation.");  
    ```  
  
7. <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> viene chiamato automaticamente per ogni comportamento del contratto in un determinato contratto che implementa <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>. Questo metodo può quindi modificare l'oggetto <xref:System.ServiceModel.Description.ServiceContractGenerationContext> passato. In questo esempio vengono aggiunti commenti.  
  
## <a name="see-also"></a>Vedere anche

- [Metadati](../feature-details/metadata.md)
- [Procedura: Importa WSDL personalizzato](how-to-import-custom-wsdl.md)
