---
title: ANYELEMENT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
ms.openlocfilehash: 4eea3d43ef6ae9ea91432ea277326526e5e91fbc
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251325"
---
# <a name="anyelement-entity-sql"></a>ANYELEMENT (Entity SQL)
Estrae un elemento da una raccolta multivalore.  
  
## <a name="syntax"></a>Sintassi  
  
```  
ANYELEMENT ( expression )  
```  
  
## <a name="arguments"></a>Argomenti  
 `expression`  
 Qualsiasi espressione di query valida che restituisce una raccolta da cui estrarre un elemento.  
  
## <a name="return-value"></a>Valore restituito  
 Singolo elemento nella raccolta o elemento arbitrario se nella raccolta ne è presente più di uno; se la raccolta è vuota, restituisce `null`. Se `collection` è una raccolta di tipo `Collection<T>`, `ANYELEMENT(collection)` è un'espressione valida che produce un'istanza di tipo `T`.  
  
## <a name="remarks"></a>Note  
 ANYELEMENT estrae un elemento arbitrario da una raccolta multivalore. Nell'esempio seguente viene ad esempio eseguito un tentativo di estrarre un elemento singleton dal set `Customers`.  
  
```  
ANYELEMENT(Customers)  
```  
  
## <a name="example"></a>Esempio  
 Nella query [!INCLUDE[esql](../../../../../../includes/esql-md.md)] seguente viene usato l'operatore ANYELEMENT per estrarre un elemento da una raccolta multivalore. La query è basata sul modello Sales di AdventureWorks. Per compilare ed eseguire questa query, effettuare le operazioni seguenti:  
  
1. Attenersi alla procedura descritta [in procedura: Eseguire una query che restituisce i risultati](../how-to-execute-a-query-that-returns-structuraltype-results.md)di StructuralType.  
  
2. Passare la query seguente come argomento al metodo `ExecuteStructuralTypeQuery` :  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## <a name="see-also"></a>Vedere anche

- [Riferimento a Entity SQL](entity-sql-reference.md)
- [Tipi strutturati nullable](nullable-structured-types-entity-sql.md)
