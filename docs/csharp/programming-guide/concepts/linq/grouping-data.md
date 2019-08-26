---
title: Raggruppamento dei dati (C#)
ms.date: 07/20/2015
ms.assetid: e414e9e4-343a-4e6e-858f-4a30c5e64492
ms.openlocfilehash: 15dafdb144ee9fd4184d4c8281d041e03161a16b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594194"
---
# <a name="grouping-data-c"></a>Raggruppamento dei dati (C#)
Il raggruppamento consiste nell'inserire i dati in gruppi in modo che gli elementi in ogni gruppo condividano un attributo comune.  
  
 Nella figura seguente vengono illustrati i risultati del raggruppamento di una sequenza di caratteri. La chiave di ogni gruppo è il carattere.  
  
 ![Diagramma che illustra un'operazione di raggruppamento LINQ.](./media/grouping-data/linq-group-operation.png)  
  
 Nella sezione seguente vengono elencati i metodi degli operatori query standard che eseguono il raggruppamento degli elementi di dati.  
  
## <a name="methods"></a>Metodi  
  
|Nome metodo|DESCRIZIONE|Sintassi di espressione della query C#|Altre informazioni|  
|-----------------|-----------------|---------------------------------|----------------------|  
|GroupBy|Raggruppa gli elementi che condividono un attributo comune. Ogni gruppo è rappresentato da un oggetto <xref:System.Linq.IGrouping%602>.|`group … by`<br /><br /> -oppure-<br /><br /> `group … by … into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|ToLookup|Inserisce gli elementi in un oggetto <xref:System.Linq.Lookup%602>, un dizionario uno-a-molti, sulla base di una funzione del selettore di chiavi.|Non applicabile.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Esempio di sintassi delle espressioni di query  
 Nell'esempio di codice seguente viene illustrato come usare la clausola `group by` per raggruppare i numeri interi in un elenco a seconda che siano numeri pari o numeri dispari.  
  
```csharp  
List<int> numbers = new List<int>() { 35, 44, 200, 84, 3987, 4, 199, 329, 446, 208 };  
  
IEnumerable<IGrouping<int, int>> query = from number in numbers  
                                         group number by number % 2;  
  
foreach (var group in query)  
{  
    Console.WriteLine(group.Key == 0 ? "\nEven numbers:" : "\nOdd numbers:");  
    foreach (int i in group)  
        Console.WriteLine(i);  
}  
  
/* This code produces the following output:  
  
    Odd numbers:  
    35  
    3987  
    199  
    329  
  
    Even numbers:  
    44  
    200  
    84  
    4  
    446  
    208  
*/  
```  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.Linq>
- [Panoramica degli operatori di query standard (C#)](./standard-query-operators-overview.md)
- [Clausola group](../../../language-reference/keywords/group-clause.md)
- [Procedura: Creare un gruppo annidato](../../linq-query-expressions/how-to-create-a-nested-group.md)
- [Procedura: Raggruppare file per estensione (LINQ) (C#)](./how-to-group-files-by-extension-linq.md)
- [Procedura: Raggruppare i risultati di una query](../../linq-query-expressions/how-to-group-query-results.md)
- [Procedura: Eseguire una sottoquery su un'operazione di raggruppamento](../../linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md)
- [Procedura: Suddividere un file in molti file usando i gruppi (LINQ) (C#)](./how-to-split-a-file-into-many-files-by-using-groups-linq.md)
