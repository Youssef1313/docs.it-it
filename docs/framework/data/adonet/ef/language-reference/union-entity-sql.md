---
title: UNION (Entity SQL)
ms.date: 03/30/2017
ms.assetid: df98a4db-b00d-4c8b-bd74-0d285f27e1df
ms.openlocfilehash: 34eac0dfd28d39ec68f084ea10dd46693f44eea3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248795"
---
# <a name="union-entity-sql"></a>UNION (Entity SQL)
Combina i risultati di due o più query in una singola raccolta.  
  
## <a name="syntax"></a>Sintassi  
  
```  
expression  
UNION [ ALL ]  
expression  
```  
  
## <a name="arguments"></a>Argomenti  
 `expression`  
 Qualsiasi espressione di query valida che restituisce una raccolta da combinare con le espressioni ALL della raccolta deve essere dello stesso tipo o di un tipo di base o derivato comune di `expression`.  
  
 UNION  
 Specifica che più raccolte devono essere combinate e restituite come singola raccolta.  
  
 ALL  
 Specifica che più raccolte devono essere combinate e restituite come singola raccolta, inclusi i duplicati. Se non viene specificato, i duplicati vengono rimossi dalla raccolta dei risultati.  
  
## <a name="return-value"></a>Valore restituito  
 Raccolta dello stesso tipo o di un tipo di base o derivato comune di `expression`.  
  
## <a name="remarks"></a>Note  
 UNION è uno degli operatori sui set di [!INCLUDE[esql](../../../../../../includes/esql-md.md)] . Tutti gli operatori sui set di [!INCLUDE[esql](../../../../../../includes/esql-md.md)] vengono valutati da sinistra a destra. Per informazioni sulla precedenza per [!INCLUDE[esql](../../../../../../includes/esql-md.md)] gli operatori sui set, vedere [except](except-entity-sql.md).  
  
## <a name="example"></a>Esempio  
 Nella query Entity SQL seguente viene usato l'operatore UNION ALL per combinare i risultati di due query in una singola raccolta. La query è basata sul modello Sales di AdventureWorks. Per compilare ed eseguire questa query, effettuare le operazioni seguenti:  
  
1. Attenersi alla procedura descritta [in procedura: Eseguire una query che restituisce i risultati](../how-to-execute-a-query-that-returns-structuraltype-results.md)di StructuralType.  
  
2. Passare la query seguente come argomento al metodo `ExecuteStructuralTypeQuery` :  
  
 [!code-csharp[DP EntityServices Concepts 2#UNION](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#union)]  
  
## <a name="see-also"></a>Vedere anche

- [Riferimento a Entity SQL](entity-sql-reference.md)
