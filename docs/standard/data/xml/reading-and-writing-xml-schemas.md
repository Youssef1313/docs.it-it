---
title: Lettura e scrittura di schemi XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: b5757c4a-ea59-467e-ac62-be2bfe24eb77
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f80157ddf394fdd058793830bfe3052b41ad1e40
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54576486"
---
# <a name="reading-and-writing-xml-schemas"></a>Lettura e scrittura di schemi XML
È possibile usare l'API del modello SOM (Schema Object Model) per scrivere e leggere gli schemi XSD (XML Schema Definition Language) da file o altre origini e compilare schemi XML in memoria usando le classi nello spazio dei nomi <xref:System.Xml.Schema?displayProperty=nameWithType> associato alle strutture definite nella raccomandazione W3C (World Wide Web Consortium) "XML Schema".  
  
## <a name="reading-and-writing-xml-schemas"></a>Lettura e scrittura di schemi XML  
 La classe <xref:System.Xml.Schema.XmlSchema> fornisce i metodi <xref:System.Xml.Schema.XmlSchema.Read%2A> e <xref:System.Xml.Schema.XmlSchema.Write%2A> per leggere e scrivere schemi XML. Il metodo <xref:System.Xml.Schema.XmlSchema.Read%2A> restituisce un oggetto <xref:System.Xml.Schema.XmlSchema> che rappresenta lo schema XML e accetta un tipo <xref:System.Xml.Schema.ValidationEventHandler> facoltativo come parametro per gestire i messaggi di avviso e di errore della convalida dello rilevati durante la lettura di uno schema XML.  
  
 Il metodo <xref:System.Xml.Schema.XmlSchema.Write%2A> scrive schemi XML negli oggetti <xref:System.IO.Stream>, <xref:System.IO.TextWriter> e <xref:System.Xml.XmlWriter> e può accettare un oggetto <xref:System.Xml.XmlNamespaceManager> facoltativo come parametro. Un tipo <xref:System.Xml.XmlNamespaceManager> viene usato per la gestione degli spazi dei nomi rilevati in uno schema XML. Per altre informazioni sulla classe <xref:System.Xml.XmlNamespaceManager>, vedere [Gestione di spazi dei nomi in un documento XML](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md).  
  
 Nell'esempio di codice seguente vengono mostrate la lettura da un file e la scrittura in un file di schemi XML. Il codice di esempio legge il file `example.xsd` in un oggetto <xref:System.Xml.Schema.XmlSchema> mediante il metodo `static`<xref:System.Xml.Schema.XmlSchema.Read%2A>, quindi scrive il file nella console e in un nuovo file `new.xsd`. Inoltre, il codice di esempio fornisce un tipo <xref:System.Xml.Schema.ValidationEventHandler> come parametro per il metodo `static`<xref:System.Xml.Schema.XmlSchema.Read%2A>, per gestire eventuali errori o avvisi di convalida dello schema rilevati durante la generazione di XML Schema. Se il tipo <xref:System.Xml.Schema.ValidationEventHandler> non è specificato (`null`), non vengono riportati né avvisi né errori.  
  
 [!code-cpp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaReadWriteExample/CPP/XmlSchemaReadWriteExample.cpp#1)]
 [!code-csharp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaReadWriteExample/CS/XmlSchemaReadWriteExample.cs#1)]
 [!code-vb[XmlSchemaReadWriteExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaReadWriteExample/VB/XmlSchemaReadWriteExample.vb#1)]  
  
 Nell'esempio il file `example.xsd` viene considerato come input.  
  
```xml  
<?xml version="1.0"?>  
<xs:schema id="play" targetNamespace="http://tempuri.org/play.xsd" elementFormDefault="qualified" xmlns="http://tempuri.org/play.xsd" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:element name='myShoeSize'>  
        <xs:complexType>  
            <xs:simpleContent>  
                <xs:extension base='xs:decimal'>  
                    <xs:attribute name='sizing' type='xs:string' />  
                </xs:extension>  
            </xs:simpleContent>  
        </xs:complexType>  
    </xs:element>  
</xs:schema>  
```  
  
## <a name="see-also"></a>Vedere anche

- [Panoramica del modello SOM XML](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [Compilazione di schemi XML](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [Attraversamento di schemi XML](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [Modifica di schemi XML](../../../../docs/standard/data/xml/editing-xml-schemas.md)
- [Inclusione o importazione di schemi XML](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)
- [XmlSchemaSet per la compilazione di schemi](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [Post-Schema-Validation Infoset (PSVI)](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
- [Gestione di spazi dei nomi in un documento XML](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)
