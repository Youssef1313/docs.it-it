---
title: Funzioni di aggregazione (Entity SQL)
ms.date: 03/30/2017
ms.assetid: acfd3149-f519-4c6e-8fe1-b21d243a0e58
ms.openlocfilehash: c79071e73763b56c0dde906499f3eef1d296ce0c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251342"
---
# <a name="aggregate-functions-entity-sql"></a>Funzioni di aggregazione (Entity SQL)
Un'aggregazione è un construct di linguaggio che condensa una raccolta in un scalare come parte di un'operazione di gruppo. Le aggregazioni [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sono disponibili in due formati:  
  
- [!INCLUDE[esql](../../../../../../includes/esql-md.md)]funzioni di raccolta che possono essere utilizzate in qualsiasi punto di un'espressione. È incluso l'utilizzo di funzioni di aggregazione nelle proiezioni e di predicati che agiscono sulle raccolte. Le funzioni di raccolta sono la modalità preferibile di specificare aggregazioni in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
- Aggregazioni di gruppo in espressioni di query che dispongono di una clausola GROUP BY. Come in Transact-SQL, le aggregazioni di gruppo accettano DISTINCT e ALL come modificatori nell'input di aggregazione.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]tenta innanzitutto di interpretare un'espressione come una funzione di raccolta e se l'espressione si trova nel contesto di un'espressione SELECT, interpretata come aggregazione di gruppo.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]definisce uno speciale operatore di aggregazione denominato [GROUPPARTITION](grouppartition-entity-sql.md). Questo operatore consente di ottenere un riferimento al set di input raggruppato. Questo consente di ottenere query di raggruppamento più avanzate, dove i risultati della clausola GROUP BY possono essere usati in posizioni diverse dalle funzioni di raccolta o di aggregazione di gruppo.  
  
## <a name="collection-functions"></a>Funzioni di raccolta  
 Le funzioni della Collection operano su raccolte e restituiscono un valore scalare. Ad esempio, se `orders` è una raccolta di tutti gli oggetti `orders`, è possibile calcolare la prima data di spedizione usando l'espressione seguente:  
  
 `min(select value o.ShipDate from LOB.Orders as o)`  
  
## <a name="group-aggregates"></a>Aggregazioni di gruppo  
 Le aggregazioni di gruppo vengono calcolate su un risultato di gruppo definito dalla clausola GROUP BY. La clausola GROUP BY suddivide i dati in gruppi. Per ogni gruppo nel risultato, viene applicata la funzione di aggregazione e viene calcolata un'aggregazione distinta usando gli elementi in ciascun gruppo come input nel calcolo dell'aggregazione. Quando in un'espressione SELECT viene usata una clausola GROUP BY, nella proiezione, nella clausola ORDER BY o HAVING possono essere presenti solo nomi di espressioni di raggruppamento, aggregazioni o espressioni costanti.  
  
 Nell'esempio seguente viene calcolata la quantità media ordinata per ciascun prodotto.  
  
 `select p, avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `group by ol.Product as p`  
  
 È possibile usare un'aggregazione di gruppo senza una clausola GROUP BY esplicita nell'espressione SELECT. Tutti gli elementi saranno trattati come un gruppo singolo, equivalente al caso della specifica di un raggruppamento basato su una costante.  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol group by 1`  
  
 Le espressioni usate nella clausola GROUP BY vengono valutate usando lo stesso ambito di risoluzione dei nomi che sarebbe visibile all'espressione con la clausola WHERE.  
  
## <a name="see-also"></a>Vedere anche

- [Funzioni](functions-entity-sql.md)
