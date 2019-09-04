---
title: Funzioni di sistema
ms.date: 03/30/2017
ms.assetid: b7c71b58-09e6-44ce-a3e5-a0fdb892fb86
ms.openlocfilehash: 552f374bc1824a16fb323cd19abe79c1914295a7
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248233"
---
# <a name="system-functions"></a>Funzioni di sistema
Il provider di dati .NET Framework per SQL Server (SqlClient) fornisce le funzioni di sistema seguenti:  
  
|Funzione|Descrizione|  
|--------------|-----------------|  
|`CHECKSUM (` `value`, [`value`, [`value`]]`)`|Restituisce il valore checksum. `CHECKSUM` viene usata per la compilazione di indici hash.<br /><br /> **Argomenti**<br /><br /> `value`: `Boolean` ,`Byte` ,,`Int64` ,,`String`,,,,, O.`Binary` `DateTime` `Decimal` `Single` `Int32` `Int16` `Double` `Guid` È possibile specificare uno, due o tre valori.<br /><br /> **Valore restituito**<br /><br /> Valore assoluto dell'espressione specificata.<br /><br /> **Esempio**<br /><br /> `SqlServer.CHECKSUM(10,100,1000.0)`|  
|`CURRENT_TIMESTAMP ()`|Produce la data e l'ora correnti nel formato interno di SQL Server per i valori `DateTime` con precisione pari a 7 e a 3 rispettivamente in SQL Server 2008 e SQL Server 2005.<br /><br /> **Valore restituito**<br /><br /> Data e ora di sistema correnti come valore `DateTime`.<br /><br /> **Esempio**<br /><br /> `SqlServer.CURRENT_TIMESTAMP()`|  
|`CURRENT_ USER` `()`|Restituisce il nome dell'utente corrente.<br /><br /> **Valore restituito**<br /><br /> Tipo `String` ASCII.<br /><br /> **Esempio**<br /><br /> `SqlServer.CURRENT_USER()`|  
|`DATALENGTH` `(` `expression` `)`|Restituisce il numero di byte usato per rappresentare qualsiasi espressione.<br /><br /> **Argomenti**<br /><br /> `expression`: `Boolean` ,`Byte` ,,`Single` ,`String`,, ,`DateTime`,, ,`DateTimeOffset`,, O`Binary` `Int64` `Int32` `Decimal` `Int16` `Double` `Time` `Guid`.<br /><br /> **Valore restituito**<br /><br /> Dimensione delle proprietà, come valore `Int32`.<br /><br /> **Esempio**<br /><br /> `SELECT VALUE SqlServer.DATALENGTH(P.Name)FROM`<br /><br /> `AdventureWorksEntities.Product AS P`|  
|`HOST_NAME()`|Restituisce il nome della workstation.<br /><br /> **Valore restituito**<br /><br /> Tipo `String` Unicode.<br /><br /> **Esempio**<br /><br /> `SqlServer.HOST_NAME()`|  
|`ISDATE(` `expression` `)`|Determina se un'espressione di input è una data valida.<br /><br /> **Argomenti**<br /><br /> `expression`: `Boolean` ,`Byte` ,,`Single` ,`String`,, ,`DateTime`,, ,`DateTimeOffset`,, O`Binary` `Int64` `Int32` `Decimal` `Int16` `Double` `Time` `Guid`.<br /><br /> **Valore restituito**<br /><br /> Oggetto `Int32`. Uno (1) se l'espressione di input è una data valida; in caso contrario, zero (0).<br /><br /> **Esempio**<br /><br /> `SqlServer.ISDATE('1/1/2006')`|  
|`ISNUMERIC(` `expression` `)`|Determina se un'espressione restituisce un tipo numerico valido.<br /><br /> **Argomenti**<br /><br /> `expression`: `Boolean` ,`Byte` ,,`Single` ,`String`,, ,`DateTime`,, ,`DateTimeOffset`,, O`Binary` `Int64` `Int32` `Decimal` `Int16` `Double` `Time` `Guid`.<br /><br /> **Valore restituito**<br /><br /> Oggetto `Int32`. Uno (1) se l'espressione di input è una data valida; in caso contrario, zero (0).<br /><br /> **Esempio**<br /><br /> `SqlServer.ISNUMERIC('21')`|  
|`NEWID()`|Crea un valore univoco di tipo Guid.<br /><br /> **Valore restituito**<br /><br /> Oggetto `Guid`.<br /><br /> **Esempio**<br /><br /> `SqlServer.NEWID()`|  
|`USER_NAME(` `id` `)`|Restituisce un nome utente del database corrispondente al numero di identificazione specificato.<br /><br /> **Argomenti**<br /><br /> `expression`: Numero di identificazione `Int32` associato a un utente del database.<br /><br /> **Valore restituito**<br /><br /> Tipo `String` Unicode.<br /><br /> **Esempio**<br /><br /> `SqlServer.USER_NAME(0)`|  
  
 Per altre informazioni sulle funzioni String supportate da SqlClient, vedere la documentazione relativa alla versione di SQL Server specificata nel file manifesto del provider SqlClient:  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[Funzioni di sistema (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115918)|[Funzioni di sistema (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115917)|[Funzioni di sistema (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=115919)|  
  
## <a name="see-also"></a>Vedere anche

- [Linguaggio Entity SQL](./language-reference/entity-sql-language.md)
- [SqlClient per funzioni Entity Framework](sqlclient-for-ef-functions.md)
