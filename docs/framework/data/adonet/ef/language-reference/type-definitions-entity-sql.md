---
title: Definizioni dei tipi (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 306b204a-ade5-47ef-95b5-c785d2da4a7e
ms.openlocfilehash: 471964266c290d5eba95804dbe1c2bc5225e3f83
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248956"
---
# <a name="type-definitions-entity-sql"></a>Definizioni dei tipi (Entity SQL)
Una definizione del tipo viene usata nell'istruzione per la dichiarazione di una funzione inline [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  
  
## <a name="remarks"></a>Note  
 L'istruzione di dichiarazione per una funzione inline è costituita dalla parola chiave [Function](function-entity-sql.md) seguita dall'identificatore che rappresenta il nome della funzione (ad esempio, "myavg") seguito da un elenco di definizioni dei parametri racchiuso tra parentesi (ad esempio, "quote Collection ( Decimal) ").  
  
 L'elenco di definizioni dei parametri è costituito da zero o più definizioni di parametri. Ogni definizione di parametro consiste di un identificatore (il nome del parametro alla funzione, ad esempio, "dues") seguito da una definizione del tipo (ad esempio, "Collection(Decimal)").  
  
 Le definizioni del tipo possono essere:  
  
- Il tipo dell'identificatore (ad esempio, "Int32" o "AdventureWorks.Order").  
  
- La parola chiave `COLLECTION` seguita da un'altra definizione del tipo tra parentesi (ad esempio "Collection(AdventureWorks.Order)").  
  
- La parola chiave ROW seguita da un elenco di definizioni di proprietà tra parentesi (ad esempio "Row(x AdventureWorks.Order)"). Le definizioni di proprietà hanno un formato come`identifier type_definition`" `identifier type_definition`,,...".  
  
- La parola chiave REF seguita dal tipo dell'identificatore tra parentesi (ad esempio "Ref(AdventureWorks.Order)"). L'operatore della definizione del tipo Ref richiede un tipo di entità come argomento. Non è possibile specificare un tipo primitivo come argomento.  
  
 È inoltre possibile annidare definizioni del tipo (ad esempio "Collection(Row(x Ref(AdventureWorks.Order)))").  
  
 Le opzioni di definizione del tipo sono:  
  
- `IdentifierName supported_type`o  
  
- `IdentifierName` COLLECTION(`type_definition`) o  
  
- `IdentifierName` ROW(`property_definition`) o  
  
- `IdentifierName` REF(`supported_entity_type`)  
  
 L'opzione di definizione delle proprietà è `IdentifierName type_definition`.  
  
 I tipi supportati sono qualsiasi tipo nello spazio dei nomi corrente. Questi includono sia i tipi primitivi che i tipi di entità.  
  
 Tipi di entità supportati si riferiscono solo a tipi di entità nello spazio dei nomi corrente. Non includono i tipi primitivi.  
  
## <a name="examples"></a>Esempi  
 Di seguito è riportato un esempio di definizione del tipo semplice.  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 EDM.Decimal) AS (  
   Round(p1)  
)  
MyRound(CAST(1.7 as EDM.Decimal))  
```  
  
 Di seguito è riportato un esempio di definizione del tipo COLLECTION.  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Collection(EDM.Decimal)) AS (  
   Select Round(p1) from p1  
)  
MyRound({CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)})  
```  
  
 Di seguito è riportato un esempio di definizione del tipo ROW.  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Row(x EDM.Decimal)) AS (  
   Round(p1.x)  
)  
select MyRound(row(a as x)) from {CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)} as a  
```  
  
 Di seguito è riportato un esempio di definizione del tipo REF.  
  
```  
USING Microsoft.Samples.Entity  
Function UnReference(p1 Ref(AdventureWorks.Order)) AS (  
   Deref(p1)  
)  
select Ref(x) from AdventureWorksEntities.SalesOrderHeaders as x  
```  
  
## <a name="see-also"></a>Vedere anche

- [Panoramica di Entity SQL](entity-sql-overview.md)
- [Riferimento a Entity SQL](entity-sql-reference.md)
