---
title: Assi LINQ to XML
ms.date: 07/20/2015
ms.assetid: ecd3bd00-28e5-4517-a59f-53bff39fd478
ms.openlocfilehash: 73c5325c23c4724a28a123af5c2f8c25b2fd02de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352026"
---
# <a name="linq-to-xml-axes-visual-basic"></a>Assi LINQ to XML (Visual Basic)
Dopo aver creato un albero XML o aver caricato un documento XML in un albero XML, è possibile eseguire query su di essa per cercare elementi e attributi e recuperarne i valori.  
  
 Prima di scrivere eventuali query, è necessario conoscere gli assi [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Sono disponibili due tipi di metodi per l'asse. Il primo tipo include i metodi che vengono chiamati su un unico oggetto <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XDocument> o <xref:System.Xml.Linq.XNode>. Questi metodi operano su un unico oggetto e restituiscono una raccolta di oggetti <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XAttribute> o <xref:System.Xml.Linq.XNode>. Il secondo tipo include i metodi di estensione che operano su raccolte e restituiscono raccolte. I metodi di estensione enumerano la raccolta di origine, chiamano il metodo dell'asse appropriato su ogni elemento della raccolta e concatenano i risultati.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
|Argomento|Descrizione|  
|-----------|-----------------|  
|[Cenni preliminari sugli assi di LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)|Viene fornita una definizione degli assi e ne viene illustrato l'uso nel contesto di query [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].|  
|[Procedura: recuperare una raccolta di elementi (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-elements-linq-to-xml.md)|Viene presentato il metodo <xref:System.Xml.Linq.XContainer.Elements%2A>, che consente di recuperare una raccolta degli elementi figlio di un elemento.|  
|[Procedura: recuperare il valore di un elemento (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md)|Viene spiegato come ottenere i valori di elementi.|  
|[Procedura: filtrare in nomi di elementi (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-filter-on-element-names-linq-to-xml.md)|Viene illustrato come filtrare in base a nomi di elemento quando si usano gli assi.|  
|[Procedura: concatenare le chiamate al metodo dell'asse (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-chain-axis-method-calls-linq-to-xml.md)|Viene illustrato come concatenare chiamate ai metodi degli assi.|  
|[Procedura: recuperare un singolo elemento figlio (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md)|Viene illustrato come recuperare un singolo elemento figlio di un elemento, dato il relativo nome di tag.|  
|[Procedura: recuperare una raccolta di attributi (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-attributes-linq-to-xml.md)|Viene presentato il metodo <xref:System.Xml.Linq.XElement.Attributes%2A>, che consente di recuperare gli attributi di un elemento.|  
|[Procedura: recuperare un singolo attributo (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-attribute-linq-to-xml.md)|Viene illustrato come recuperare un singolo attributo di un elemento, dato il relativo nome.|  
|[Procedura: recuperare il valore di un attributo (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-attribute-linq-to-xml.md)|Viene spiegato come ottenere i valori di attributi.|  
|[Procedura: recuperare il valore superficiale di un elemento (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-shallow-value-of-an-element.md)|Viene illustrato come recuperare il valore superficiale di un elemento|  
|[Assi integrati nel linguaggio Visual Basic (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/language-integrated-axes.md)|Riepiloga l'Visual Basic assi integrati.|  
  
## <a name="see-also"></a>Vedere anche

- [Guida per programmatori (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
