---
title: Tipi strutturati nullable (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
ms.openlocfilehash: b155c672d8c0bef8b01fb26fb49908f094add25a
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319483"
---
# <a name="nullable-structured-types-entity-sql"></a>Tipi strutturati nullable (Entity SQL)
Un'istanza `null` di un tipo strutturato è un'istanza che non esiste ed è diversa da un'istanza esistente nella quale tutte le proprietà hanno valori `null`.  
  
 In questo argomento vengono descritti i tipi strutturati che ammettono valori Null e viene indicato quali tipi ammettono valori Null e quali modelli di codice producono istanze `null` dei tipi strutturati che ammettono valori Null.  
  
## <a name="kinds-of-nullable-structured-types"></a>Tipi strutturati che ammettono valori Null  
 Esistono tre tipi di strutture che ammettono valori Null:  
  
- Tipi di riga.  
  
- Tipi complessi.  
  
- Tipi di entità.  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a>Modelli di codice che producono istanze null di tipi strutturati  
 Negli scenari seguenti vengono prodotte istanze `null`:  
  
- Modellazione di `null` come tipo strutturato:  
  
    ```sql  
    TREAT (NULL AS StructuredType)  
    ```  
  
- Upcast di un tipo di base a un tipo derivato:  
  
    ```sql  
    TREAT (BaseType AS DerivedType)  
    ```  
  
- Outer join in una condizione false:  
  
    ```sql  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     --oppure  
  
    ```sql  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     --oppure  
  
    ```sql  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
- Dereferenziamento di riferimento `null`:  
  
    ```sql  
    DEREF(NullRef)  
    ```  
  
- Recupero di ANYELEMENT da una raccolta vuota:  
  
    ```sql  
    ANYELEMENT(EmptyCollection)  
    ```  
  
- Verifica delle istanze `null` dei tipi strutturati:  
  
    ```csharp  
    ...  
    for (int i = 0; i < reader.FieldCount; i++)  
    {  
        if (reader.IsDBNull(i))  
        {  
            Console.WriteLine("[NULL]");  
        }  
        else  
        {  
            Console.WriteLine(reader.GetValue(i).ToString());  
        }  
    }  
    ```  
  
## <a name="see-also"></a>Vedere anche

- [Panoramica di Entity SQL](entity-sql-overview.md)
