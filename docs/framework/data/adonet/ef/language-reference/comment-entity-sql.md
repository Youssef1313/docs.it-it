---
title: -- (commento) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5d9de735-2099-47f1-b7e7-60856f494924
ms.openlocfilehash: 43b8cdbf5dbca8822645c27711f6984b8d741ea7
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040281"
---
# <a name="---comment-entity-sql"></a>-- (commento) (Entity SQL)
Le query[!INCLUDE[esql](../../../../../../includes/esql-md.md)] possono contenere commenti. Due trattini (`--`) indicano l'inizio di una riga di commento.  
  
## <a name="syntax"></a>Sintassi  
  
```csharp  
-- text_of_comment  
```  
  
## <a name="arguments"></a>argomenti  
 `text_of_comment`  
 Stringa di caratteri contenente il testo del commento.  
  
## <a name="example"></a>Esempio  
 Nella query Entity SQL seguente viene illustrato come usare i commenti. La query è basata sul modello Sales di AdventureWorks. Per compilare ed eseguire questa query, effettuare le operazioni seguenti:  
  
1. Seguire la procedura indicata in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Passare la query seguente come argomento al metodo `ExecuteStructuralTypeQuery` :  
  
 [!code-csharp[DP EntityServices Concepts 2#COMMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#comment)]  
  
## <a name="see-also"></a>Vedere anche

- [Panoramica di Entity SQL](entity-sql-overview.md)
- [Riferimento a Entity SQL](entity-sql-reference.md)
