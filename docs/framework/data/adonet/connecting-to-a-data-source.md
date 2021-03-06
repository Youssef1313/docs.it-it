---
title: Connessione a un'origine dati in ADO.NET
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: 01e4048fb9c7b53b1b1907d1965f822b9a4644a4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786759"
---
# <a name="connecting-to-a-data-source-in-adonet"></a>Connessione a un'origine dati in ADO.NET
In ADO.NET si usa un oggetto **Connection** per connettersi a un'origine dati specifica fornendo le informazioni di autenticazione necessarie in una stringa di connessione. L'oggetto **connessione** utilizzato dipende dal tipo di origine dati.  
  
 Per ogni provider di dati .NET Framework incluso in .NET Framework è disponibile un oggetto <xref:System.Data.Common.DbConnection>: nel provider di dati .NET Framework per OLE DB è incluso un oggetto <xref:System.Data.OleDb.OleDbConnection>, in quello per SQL Server è incluso un oggetto <xref:System.Data.SqlClient.SqlConnection>, in quello per ODBC è incluso un oggetto <xref:System.Data.Odbc.OdbcConnection> e in quello per Oracle è incluso un oggetto <xref:System.Data.OracleClient.OracleConnection>.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Stabilire una connessione](establishing-the-connection.md)  
 Viene descritto come utilizzare un oggetto **Connection** per stabilire una connessione a un'origine dati.  
  
 [Eventi di connessione](connection-events.md)  
 Viene descritto come utilizzare un evento **InfoMessage** per recuperare messaggi informativi da un'origine dati.  
  
## <a name="see-also"></a>Vedere anche

- [Stringhe di connessione](connection-strings.md)
- [Pool di connessioni](connection-pooling.md)
- [Comandi e parametri](commands-and-parameters.md)
- [DataAdapter e DataReader](dataadapters-and-datareaders.md)
- [Transazioni e concorrenza](transactions-and-concurrency.md)
- [Panoramica di ADO.NET](ado-net-overview.md)
