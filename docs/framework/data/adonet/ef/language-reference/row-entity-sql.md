---
title: ROW (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 06da96e8-55d7-486c-991a-4e514d837ff9
ms.openlocfilehash: dfd0031f49cbdf41797cecf21c149fafde4d7a8c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249245"
---
# <a name="row-entity-sql"></a>ROW (Entity SQL)
Consente di costruire record anonimi strutturalmente tipizzati da uno o più valori.  
  
## <a name="syntax"></a>Sintassi  
  
```  
ROW ( expression [ AS alias ] [,...] )  
```  
  
## <a name="arguments"></a>Argomenti  
 `expression`  
 Qualsiasi espressione di query valida che restituisce un valore da costruire in un tipo di riga.  
  
 `alias`  
 Specifica un alias per il valore specificato in un tipo di riga. Se non viene fornito un alias, in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] viene eseguito un tentativo di generare un alias usando le regole di generazione di alias [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .  
  
## <a name="return-value"></a>Valore restituito  
 Tipo di riga.  
  
## <a name="remarks"></a>Note  
 Si usano costruttori ROW in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] per costruire record anonimi strutturalmente tipizzati da uno o più valori. Il tipo di risultato di un costruttore ROW è un tipo di riga i cui tipi di campo corrispondono ai tipi dei valori usati per costruire la riga. L'espressione seguente consente ad esempio di costruire un valore di tipo `Record(a int, b string, c int)`.  
  
```  
ROW(1 AS a, "abc" AS b, a+34 AS c)  
```  
  
 Se non si fornisce un alias per un'espressione in un costruttore di riga, in Entity Framework viene eseguito un tentativo di generarne uno. Per altre informazioni, vedere la sezione "Regole relative all'utilizzo degli alias" dell'argomento [Identificatori](identifiers-entity-sql.md) .  
  
 Le regole seguenti riguardano l'uso di alias nelle espressioni in un costruttore di riga:  
  
- Le espressioni in un costruttore ROW non possono fare riferimento ad altri alias nello stesso costruttore.  
  
- Due espressioni nello stesso costruttore di riga non possono avere lo stesso alias.  
  
 Per ulteriori informazioni sui costruttori di query, vedere [costruzione di tipi](constructing-types-entity-sql.md).  
  
## <a name="example"></a>Esempio  
 Nella query Entity SQL seguente viene usato l'operatore ROW per costruire record anonimi strutturalmente tipizzati. La query è basata sul modello Sales di AdventureWorks. Per compilare ed eseguire questa query, effettuare le operazioni seguenti:  
  
1. Attenersi alla procedura descritta [in procedura: Eseguire una query che restituisce i risultati](../how-to-execute-a-query-that-returns-structuraltype-results.md)di StructuralType.  
  
2. Passare la query seguente come argomento al metodo `ExecuteStructuralTypeQuery` :  
  
 [!code-csharp[DP EntityServices Concepts 2#ROW](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#row)]  
  
## <a name="see-also"></a>Vedere anche

- [Costruzione di tipi](constructing-types-entity-sql.md)
- [Riferimento a Entity SQL](entity-sql-reference.md)
- [Definizioni di tipo](type-definitions-entity-sql.md)
