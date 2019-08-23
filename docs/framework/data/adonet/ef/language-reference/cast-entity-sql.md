---
title: CAST (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 07b6d750-dfd4-48a9-b86c-3badcbba6f70
ms.openlocfilehash: 253dcf092deadd1049d0556af4ea0630602110d0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935820"
---
# <a name="cast-entity-sql"></a>CAST (Entity SQL)
Consente di convertire un'espressione da un tipo di dati a un altro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
CAST ( expression AS data_type )  
```  
  
## <a name="arguments"></a>Argomenti  
 `expression`  
 Qualsiasi espressione valida che è possibile convertire in `data_type`.  
  
 `data_type`  
 Tipo di dati di sistema di destinazione. Deve trattarsi di un tipo primitivo (scalare). Il tipo `data_type` usato dipende dall'ambito della query. Se una query viene eseguita con <xref:System.Data.EntityClient.EntityCommand>, il tipo di dati è un tipo definito nel modello concettuale. Per altre informazioni, vedere [CSDL Specification](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md). Se una query viene eseguita con <xref:System.Data.Objects.ObjectQuery%601>, il tipo di dati è un tipo CLR (Common Language Runtime).  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce lo stesso valore di `data_type`.  
  
## <a name="remarks"></a>Note  
 La semantica dell'espressione cast è simile a quella dell'espressione Transact-SQL CONVERT. L'espressione CAST viene usata per convertire un valore di un tipo in un valore di un altro tipo.  
  
```  
CAST( e as T )  
```  
  
 Se e è di tipo S, e S è convertibile in T, l'espressione precedente è un'espressione CAST valida. T deve essere un tipo primitivo (scalare).  
  
 Quando si esegue il cast a `Edm.Decimal`, è possibile fornire i valori dei facet di precisione e scala. Se non vengono forniti in modo esplicito, i valori predefiniti per la precisione e la scala sono 18 e 0, rispettivamente. In particolare, gli overload seguenti sono supportati per `Decimal`:  
  
- `CAST( d as Edm.Decimal );`  
  
- `CAST( d as Edm.Decimal(precision) );`  
  
- `CAST( d as Edm.Decimal(precision, scale) );`  
  
 L'utilizzo di un'espressione CAST è considerato una conversione esplicita. Le conversioni esplicite possono comportare il troncamento dei dati o la perdita di precisione.  
  
> [!NOTE]
> L'operatore CAST è supportato solo per tipi primitivi e tipi di membro di enumerazione.  
  
## <a name="example"></a>Esempio  
 Nella query [!INCLUDE[esql](../../../../../../includes/esql-md.md)] seguente viene usato l'operatore CAST per eseguire il cast di un'espressione da un tipo di dati a un altro. La query è basata sul modello Sales di AdventureWorks. Per compilare ed eseguire questa query, effettuare le operazioni seguenti:  
  
1. Attenersi alla procedura descritta [in procedura: Eseguire una query che restituisce i risultati](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)di PrimitiveType.  
  
2. Passare la query seguente come argomento al metodo `ExecutePrimitiveTypeQuery` :  
  
 [!code-csharp[DP EntityServices Concepts 2#CAST](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#cast)]  
  
## <a name="see-also"></a>Vedere anche

- [Riferimento a Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
