---
title: 'Procedura: scrivere dati oggetto in un file XML'
ms.date: 07/20/2015
ms.assetid: f7966480-5ed2-43ac-9894-33427436de2a
ms.openlocfilehash: b2181a74c83782cf4737b2a94fc5fb08fee28a10
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345461"
---
# <a name="how-to-write-object-data-to-an-xml-file-visual-basic"></a>How to: Write Object Data to an XML File (Visual Basic)
Questo esempio scrive l'oggetto da una classe in un file XML usando la classe <xref:System.Xml.Serialization.XmlSerializer>.  
  
## <a name="example"></a>Esempio  
  
```vb  
Public Module XMLWrite  
  
    Sub Main()  
        WriteXML()  
    End Sub  
  
    Public Class Book  
        Public Title As String  
    End Class  
  
    Public Sub WriteXML()  
        Dim overview As New Book  
        overview.Title = "Serialization Overview"  
        Dim writer As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
        Dim file As New System.IO.StreamWriter(  
            "c:\temp\SerializationOverview.xml")  
        writer.Serialize(file, overview)  
        file.Close()  
    End Sub  
End Module  
```  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 La classe deve avere un costruttore public senza parametri.  
  
## <a name="robust-programming"></a>Programmazione efficiente  
 Le seguenti condizioni possono generare un'eccezione:  
  
- La classe da serializzare non ha un costruttore pubblico senza parametri.  
  
- Il file esiste ed è di sola lettura (<xref:System.IO.IOException>).  
  
- Percorso del file troppo lungo (<xref:System.IO.PathTooLongException>).  
  
- Il disco è pieno (<xref:System.IO.IOException>).  
  
## <a name="net-framework-security"></a>Sicurezza di .NET Framework  
 Questo esempio crea un nuovo file, se il file non esiste. Se un'applicazione deve creare un file, deve avere accesso `Create` alla cartella. Se il file esiste già, per l'applicazione è sufficiente l'accesso `Write`, un privilegio di livello inferiore. Se possibile, è più sicuro creare il file durante la distribuzione e concedere l'accesso `Read` a un unico file, anziché l'accesso `Create` a una cartella.  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.IO.StreamWriter>
- [Procedura: Leggere dati oggetto in un file XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [Serializzazione (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
