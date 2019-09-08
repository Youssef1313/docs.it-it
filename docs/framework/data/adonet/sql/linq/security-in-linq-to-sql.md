---
title: Sicurezza in LINQ to SQL
ms.date: 03/30/2017
ms.assetid: d49787f7-414e-4c71-aa33-80a5895536b1
ms.openlocfilehash: f1ebf2f72fbfe3b27b9fbfd41f0dd65c70103620
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781192"
---
# <a name="security-in-linq-to-sql"></a>Sicurezza in LINQ to SQL
Quando si esegue la connessione a un database, vi sono sempre problemi relativi alla sicurezza. Sebbene in LINQ to SQL siano disponibili alcune nuove modalità di utilizzo dei dati in SQL Server, non vengono forniti meccanismi di sicurezza aggiuntivi.  
  
## <a name="access-control-and-authentication"></a>Controllo dell'accesso e autenticazione  
 LINQ to SQL non dispone di meccanismi di autenticazione o di un modello utente. Usare le funzionalità di sicurezza di SQL Server per controllare l'accesso al database, le tabelle di database, le visualizzazioni e le stored procedure mappate al modello a oggetti. Concedere l'accesso minimo richiesto agli utenti e richiedere password complesse per l'autenticazione utente.  
  
## <a name="mapping-and-schema-information"></a>Informazioni sul mapping e sullo schema  
 Le informazioni sul mapping dei tipi SQL-CLR e sullo schema di database nel modello a oggetti o nel file di mapping esterno sono disponibili per tutti gli utenti che dispongono di accesso a tali file nel file system. Si supponga che le informazioni sullo schema siano disponibili per tutti gli utenti che possono accedere al modello a oggetti o al file di mapping esterno. Per impedire l'accesso più ampio alle informazioni dello schema, utilizzare i meccanismi di sicurezza dei file per proteggere i file di origine e i file di mapping.  
  
## <a name="connection-strings"></a>Stringhe di connessione  
 L'utilizzo di password nelle stringhe di connessione deve essere evitato, quando possibile. Una stringa di connessione non solo rappresenta un rischio per la sicurezza di per sé, ma può anche essere aggiunta come testo non crittografato al modello a oggetti o al file di mapping esterno quando si usa Progettazione relazionale oggetti o lo strumento da riga di comando SQLMetal. Chiunque disponga di accesso al modello a oggetti o al file di mapping esterno tramite il file system può vedere la password di connessione, se è inclusa nella stringa di connessione.  
  
 Per ridurre al minimo tali rischi, utilizzare la sicurezza integrata per creare una connessione trusted con SQL Server. Usando questo approccio, non è necessario archiviare una password nella stringa di connessione. Per ulteriori informazioni, vedere [SQL Server sicurezza](../sql-server-security.md).  
  
 In assenza della sicurezza integrata, nella stringa di connessione è necessaria una password non crittografata. I modi migliori per proteggere la stringa di connessione, in ordine di rischio crescente, sono i seguenti:  
  
- Usare la sicurezza integrata.  
  
- Proteggere le stringhe di connessione tramite password e ridurre al minimo i passaggi delle stringhe di connessione.  
  
- Usare una classe <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> anziché una stringa di connessione, in quanto la classe limita la durata dell'esposizione. È possibile creare un'istanza della classe <xref:System.Data.Linq.DataContext?displayProperty=nameWithType> LINQ to SQL usando un oggetto <xref:System.Data.SqlClient.SqlConnection>.  
  
- Ridurre al minimo la durata e i punti di contatto per tutte le stringhe di connessione.  
  
## <a name="see-also"></a>Vedere anche

- [Informazioni di base](background-information.md)
- [Domande frequenti](frequently-asked-questions.md)
