---
title: 'Procedura: Eseguire la convalida tramite XSD (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 6a7f83a9-2d74-4c2b-8417-0a8595879516
ms.openlocfilehash: 0e35e12efa9530fd5bbcf7a21e86ed03c1325bc4
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253246"
---
# <a name="how-to-validate-using-xsd-linq-to-xml-c"></a>Procedura: Eseguire la convalida tramite XSD (LINQ to XML) (C#)
Lo spazio dei nomi <xref:System.Xml.Schema> contiene metodi di estensione che semplificano la convalida di un albero XML rispetto a un file XSD (Schema Definition Language). Per altre informazioni, vedere la documentazione del metodo <xref:System.Xml.Schema.Extensions.Validate%2A>.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene creato un oggetto <xref:System.Xml.Schema.XmlSchemaSet>, quindi vengono convalidati due oggetti <xref:System.Xml.Linq.XDocument> rispetto al set di schemi. Uno dei documenti è valido, l'altro non lo è.  
  
```csharp  
string xsdMarkup =  
    @"<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'>  
       <xsd:element name='Root'>  
        <xsd:complexType>  
         <xsd:sequence>  
          <xsd:element name='Child1' minOccurs='1' maxOccurs='1'/>  
          <xsd:element name='Child2' minOccurs='1' maxOccurs='1'/>  
         </xsd:sequence>  
        </xsd:complexType>  
       </xsd:element>  
      </xsd:schema>";  
XmlSchemaSet schemas = new XmlSchemaSet();  
schemas.Add("", XmlReader.Create(new StringReader(xsdMarkup)));  
  
XDocument doc1 = new XDocument(  
    new XElement("Root",  
        new XElement("Child1", "content1"),  
        new XElement("Child2", "content1")  
    )  
);  
  
XDocument doc2 = new XDocument(  
    new XElement("Root",  
        new XElement("Child1", "content1"),  
        new XElement("Child3", "content1")  
    )  
);  
  
Console.WriteLine("Validating doc1");  
bool errors = false;  
doc1.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("doc1 {0}", errors ? "did not validate" : "validated");  
  
Console.WriteLine();  
Console.WriteLine("Validating doc2");  
errors = false;  
doc2.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("doc2 {0}", errors ? "did not validate" : "validated");  
```  
  
 Questo esempio produce il seguente output:  
  
```output  
Validating doc1  
doc1 validated  
  
Validating doc2  
The element 'Root' has invalid child element 'Child3'. List of possible elements expected: 'Child2'.  
doc2 did not validate  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene verificato che il documento XML del [File XML di esempio: Customers e Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) sia valido per lo schema del [File XSD di esempio: Customers e Orders](./sample-xsd-file-customers-and-orders1.md). Viene quindi modificato il documento XML di origine. Viene cambiato l'attributo `CustomerID` sul primo cliente. Dopo la modifica, gli ordini faranno riferimento a un cliente che non esiste, quindi il documento XML non verrà più convalidato.  
  
 Nell'esempio viene usato il documento XML seguente: [File XML di esempio: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
 L'esempio usa lo schema XSD seguente: [File XSD di esempio: Customers e Orders](./sample-xsd-file-customers-and-orders1.md).  
  
```csharp  
XmlSchemaSet schemas = new XmlSchemaSet();  
schemas.Add("", "CustomersOrders.xsd");  
  
Console.WriteLine("Attempting to validate");  
XDocument custOrdDoc = XDocument.Load("CustomersOrders.xml");  
bool errors = false;  
custOrdDoc.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");  
  
Console.WriteLine();  
// Modify the source document so that it will not validate.  
custOrdDoc.Root.Element("Orders").Element("Order").Element("CustomerID").Value = "AAAAA";  
Console.WriteLine("Attempting to validate after modification");  
errors = false;  
custOrdDoc.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");  
```  
  
 Questo esempio produce il seguente output:  
  
```output  
Attempting to validate  
custOrdDoc validated  
  
Attempting to validate after modification  
The key sequence 'AAAAA' in Keyref fails to refer to some key.  
custOrdDoc did not validate  
```  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.Xml.Schema.Extensions.Validate%2A>
- [Creazione di alberi XML (C#)](creating-xml-trees-linq-to-xml-2.md)
