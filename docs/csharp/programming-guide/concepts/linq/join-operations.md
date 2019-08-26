---
title: Operazioni di join (C#)
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
ms.openlocfilehash: 95661e2d0d7f4f0e75c1fa1b10e1f322923189b1
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592075"
---
# <a name="join-operations-c"></a>Operazioni di join (C#)
Un *join* di due origini dati è un'associazione di oggetti in un'origine dati con oggetti che condividono un attributo comune in un'altra origine dati.  
  
 La creazione di un join è un'operazione importante nelle query che fanno riferimento a origini dati le cui relazioni reciproche non possono essere seguite direttamente. Nella programmazione orientata a oggetti ciò potrebbe corrispondere a una correlazione non modellata tra oggetti, ad esempio la direzione inversa di una relazione unidirezionale. Un esempio di relazione unidirezionale è costituito da una classe Customer che include una proprietà di tipo City, ma la classe City non include una proprietà che sia una raccolta di oggetti Customer. Se si ha un elenco di oggetti City e si vogliono trovare tutti i clienti in ogni città, è possibile usare un'operazione join per individuarli.  
  
 I metodi di join disponibili nel framework LINQ sono <xref:System.Linq.Enumerable.Join%2A> e <xref:System.Linq.Enumerable.GroupJoin%2A>. Questi metodi eseguono equijoin, ovvero join che associano due origini dati in base all'uguaglianza delle rispettive chiavi. Per un confronto, si noti che Transact-SQL supporta operatori join diversi da 'uguale a', ad esempio l'operatore 'minore di'. In termini di database relazionale, <xref:System.Linq.Enumerable.Join%2A> implementa un inner join, ovvero un tipo di join in cui sono restituiti solo gli oggetti con una corrispondenza nell'altro set di dati. Il metodo <xref:System.Linq.Enumerable.GroupJoin%2A> non ha equivalenti diretti in termini di database relazionale, ma implementa un superset di inner join e left outer join. Un left outer join è un join che restituisce ogni elemento della prima origine dati (a sinistra), anche se non ha elementi correlati nell'altra origine dati.  
  
 L'illustrazione seguente mostra una visualizzazione concettuale dei due set e degli elementi dei set che sono inclusi in un inner join o in un left outer join.  
  
 ![Due cerchi sovrapposti che illustrano interno&#47;esterno.](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a>Metodi  
  
|Nome metodo|DESCRIZIONE|Sintassi di espressione della query C#|Altre informazioni|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Join|Unisce due sequenze in base a funzioni selector chiave ed estrae coppie di valori|`join … in … on … equals …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|Unisce due sequenze in base a funzioni selector chiave e raggruppa le corrispondenze risultanti per ogni elemento.|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.Linq>
- [Panoramica degli operatori di query standard (C#)](./standard-query-operators-overview.md)
- [Tipi anonimi](../../classes-and-structs/anonymous-types.md)
- [Formulare join e query di prodotto incrociato](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [Clausola join](../../../language-reference/keywords/join-clause.md)
- [Procedura: Creare un join usando chiavi composte](../../linq-query-expressions/how-to-join-by-using-composite-keys.md)
- [Procedura: Creare un join del contenuto da file non analoghi (LINQ) (C#)](./how-to-join-content-from-dissimilar-files-linq.md)
- [Procedura: Ordinare i risultati di una clausola join](../../linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)
- [Procedura: Eseguire operazioni di join personalizzate](../../linq-query-expressions/how-to-perform-custom-join-operations.md)
- [Procedura: Eseguire join raggruppati](../../linq-query-expressions/how-to-perform-grouped-joins.md)
- [Procedura: Eseguire inner join](../../linq-query-expressions/how-to-perform-inner-joins.md)
- [Procedura: Eseguire left outer join](../../linq-query-expressions/how-to-perform-left-outer-joins.md)
- [Procedura: Popolare le raccolte di oggetti da più origini (LINQ) (C#)](./how-to-populate-object-collections-from-multiple-sources-linq.md)
