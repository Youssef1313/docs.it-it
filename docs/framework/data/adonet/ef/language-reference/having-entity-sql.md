---
title: HAVING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
ms.openlocfilehash: fe8a177b83932c1c7607f8444c05292c0ee29684
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250841"
---
# <a name="having-entity-sql"></a>HAVING (Entity SQL)
Specifica una condizione di ricerca per un gruppo o un'aggregazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
[ HAVING search_condition ]  
```  
  
## <a name="arguments"></a>Argomenti  
 `search_condition`  
 Specifica la condizione di ricerca che il gruppo o l'aggregazione deve soddisfare. Se viene usata assieme alla clausola GROUP BY ALL, la clausola HAVING è prioritaria rispetto a ALL.  
  
## <a name="remarks"></a>Note  
 La clausola HAVING viene usata per specificare una condizione di filtro aggiuntiva sul risultato di un raggruppamento. Se non viene specificata alcuna clausola GROUP BY nell'espressione di query, viene presupposto un gruppo con singolo set implicito.  
  
> [!NOTE]
> HAVING può essere utilizzato solo con l'istruzione [Select](select-entity-sql.md) . Se non si usa [Group by](group-by-entity-sql.md) , la clausola HAVING si comporta come una clausola WHERE.  
  
 La clausola HAVING funziona come la clausola WHERE eccetto per il fatto che viene applicata dopo l'operazione GROUP BY. Questo significa che la clausola HAVING può fare riferimento solo alle aggregazioni e agli alias di raggruppamento, come illustrato nell'esempio seguente.  
  
```  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 L'esempio precedente consente di limitare i gruppi esclusivamente a quelli che includono più di un prodotto.  
  
## <a name="example"></a>Esempio  
 Nella query Entity SQL seguente vengono usati gli operatori HAVING e GROUP BY per specificare una condizione di ricerca per un gruppo o un'aggregazione. La query è basata sul modello Sales di AdventureWorks. Per compilare ed eseguire questa query, effettuare le operazioni seguenti:  
  
1. Attenersi alla procedura descritta [in procedura: Eseguire una query che restituisce i risultati](../how-to-execute-a-query-that-returns-primitivetype-results.md)di PrimitiveType.  
  
2. Passare la query seguente come argomento al metodo `ExecutePrimitiveTypeQuery` :  
  
 [!code-csharp[DP EntityServices Concepts 2#HAVING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#having)]  
  
## <a name="see-also"></a>Vedere anche

- [Riferimento a Entity SQL](entity-sql-reference.md)
- [Espressioni di query](query-expressions-entity-sql.md)
