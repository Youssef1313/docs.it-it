---
title: SELECT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 9a33bd0d-ded1-41e7-ba3c-305502755e3b
ms.openlocfilehash: 3d3564c37d8971d3261cb47acb774bd1b9f92192
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249207"
---
# <a name="select-entity-sql"></a>SELECT (Entity SQL)
Specifica gli elementi restituiti da una query.  
  
## <a name="syntax"></a>Sintassi  
  
```  
SELECT [ ALL | DISTINCT ] [ topSubclause ] aliasedExpr   
      [{ , aliasedExpr }] FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause ]  
or  
SELECT VALUE [ ALL | DISTINCT ] [ topSubclause ] expr FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause  
```  
  
## <a name="arguments"></a>Argomenti  
 ALL  
 Specifica che nel set di risultati possono essere inclusi duplicati. ALL è l'argomento predefinito.  
  
 DISTINCT  
 Specifica che nel set di risultati possono essere inclusi solo risultati univoci.  
  
 VALUE  
 Consente di specificare un solo elemento e non aggiunge un wrapper di riga.  
  
 `topSubclause`  
 Qualsiasi espressione valida che indica il numero dei primi risultati che devono essere restituiti dalla query, nel formato `top(expr)`.  
  
 Il parametro LIMIT dell'operatore [Order by](order-by-entity-sql.md) consente inoltre di selezionare i primi n elementi del set di risultati.  
  
 `aliasedExpr`  
 Espressione nel formato seguente:  
  
 `expr`come `identifier` &#124;`expr`  
  
 `expr`  
 Valore letterale o espressione.  
  
## <a name="remarks"></a>Note  
 La clausola SELECT viene valutata in seguito alla valutazione delle clausole [from](from-entity-sql.md), [Group by](group-by-entity-sql.md)e [having](having-entity-sql.md) . La clausola SELECT può fare riferimento solo agli elementi attualmente inclusi nell'ambito (dalla clausola FROM o da ambiti esterni). Se è stata specificata una clausola GROUP BY, la clausola SELECT può fare riferimento solo agli alias per le chiavi GROUP BY. Il riferimento agli elementi della clausola FROM è consentito solo nelle funzioni di aggregazione.  
  
 L'elenco di una o più espressioni di query che seguono la parola chiave SELECT è noto come elenco di selezione o, più formalmente, come proiezione. La forma più generale di proiezione è una singola espressione di query. Se si seleziona un membro `member1` da una raccolta `collection1`, verrà creata una nuova raccolta di tutti i valori di `member1` per ogni oggetto di `collection1`, come illustrato nell'esempio seguente.  
  
```  
SELECT collection1.member1 FROM collection1  
```  
  
 Se, ad esempio, `customers` è una raccolta di tipo `Customer` con una proprietà `Name` di tipo `string`, se si seleziona `Name` da `customers` verrà creata una raccolta di stringhe, come illustrato nell'esempio seguente.  
  
```  
SELECT customers.Name FROM customers AS c  
```  
  
 È anche possibile usare la sintassi JOIN (FULL, INNER, LEFT, OUTER, ON e RIGHT). ON è obbligatorio per gli inner join e non è consentito per i cross join.  
  
## <a name="row-and-value-select-clauses"></a>Clausole SELECT per la selezione di righe e di valori  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] supporta due varianti della clausola SELECT. La prima variante, per la selezione di righe, è identificata dalla parola chiave SELECT e può essere usata per specificare uno o più valori da proiettare. Poiché ai valori restituiti viene aggiunto in modo implicito un wrapper di riga, il risultato dell'espressione di query è sempre un multiset di righe.  
  
 In ogni espressione di query in una clausola per la selezione di righe deve essere specificato un alias. Se non viene specificato alcun alias, in[!INCLUDE[esql](../../../../../../includes/esql-md.md)] viene eseguito un tentativo di generare un alias usando le regole di generazione di alias.  
  
 L'altra variante della clausola SELECT, per la selezione di valori, è identificata dalla parola chiave SELECT VALUE. Questo tipo di clausola consente di specificare un solo valore e non aggiunge un wrapper di riga.  
  
 Una clausola per la selezione di righe può essere sempre espressa in termini di VALUE SELECT, come illustrato nell'esempio seguente.  
  
```  
SELECT 1 AS a, "abc" AS b FROM C  
SELECT VALUE ROW(1 AS a, "abc" AS b) FROM C   
```  
  
## <a name="all-and-distinct-modifiers"></a>Modificatori ALL e DISTINCT  
 Entrambe le varianti della clausola SELECT in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] consentono di specificare un modificatore ALL o DISTINCT. Se viene specificato il modificatore DISTINCT, i duplicati vengono eliminati dalla raccolta prodotta dall'espressione di query, fino alla clausola SELECT inclusa. Se viene specificato il modificatore ALL, non viene eseguita alcuna eliminazione dei duplicati. ALL rappresenta l'impostazione predefinita.  
  
## <a name="differences-from-transact-sql"></a>Differenze rispetto a Transact-SQL  
 A differenza di Transact-SQL, in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] non è supportato l'uso dell'argomento * nella clausola SELECT.  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] consente invece alle query di proiettare interi record facendo riferimento agli alias della raccolta dalla clausola FROM, come illustrato nell'esempio seguente.  
  
```  
SELECT * FROM T1, T2  
```  
  
 L'espressione di query Transact-SQL precedente viene espressa [!INCLUDE[esql](../../../../../../includes/esql-md.md)] in nel modo seguente.  
  
```  
SELECT a1, a2 FROM T1 AS a1, T2 AS a2  
```  
  
## <a name="example"></a>Esempio  
 Nella query Entity SQL seguente viene usato l'operatore SELECT per specificare gli elementi che devono essere restituiti da una query. La query è basata sul modello Sales di AdventureWorks. Per compilare ed eseguire questa query, effettuare le operazioni seguenti:  
  
1. Attenersi alla procedura descritta [in procedura: Eseguire una query che restituisce i risultati](../how-to-execute-a-query-that-returns-structuraltype-results.md)di StructuralType.  
  
2. Passare la query seguente come argomento al metodo `ExecuteStructuralTypeQuery` :  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## <a name="see-also"></a>Vedere anche

- [Espressioni di query](query-expressions-entity-sql.md)
- [Riferimento a Entity SQL](entity-sql-reference.md)
- [TOP](top-entity-sql.md)
