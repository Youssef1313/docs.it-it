---
title: Mirroring del database in SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 89befaff-bb46-4290-8382-e67cdb0e3de9
ms.openlocfilehash: b18c67f5573d375fe0872d76d69a1f0aafa7e7f6
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040436"
---
# <a name="database-mirroring-in-sql-server"></a>Mirroring del database in SQL Server
Il mirroring del database in SQL Server consente di mantenere una copia, o mirror, di un database di SQL Server in un server di standby. Il mirroring assicura che siano sempre disponibili due copie separate dei dati per assicurare un'elevata disponibilità e una ridondanza completa dei dati. Il provider di dati .NET per SQL Server fornisce il supporto implicito per il mirroring del database. Pertanto, una volta configurato il provider per un database SQL Server, lo sviluppatore non dovrà eseguire alcuna operazione né scrivere codice. L'oggetto <xref:System.Data.SqlClient.SqlConnection> supporta inoltre una modalità di connessione esplicita che consente di specificare il nome di un server partner di failover in <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
 La sequenza di eventi semplificata indicata di seguito si verifica per un oggetto <xref:System.Data.SqlClient.SqlConnection> destinato a un database configurato per il mirroring:  
  
1. L'applicazione client esegue correttamente la connessione al database principale e il server restituisce il nome del server partner, che viene successivamente inserito nella cache del client.  
  
2. Se si verifica un errore nel server contenente il database principale o se viene interrotta la connettività, lo stato della connessione e lo stato della transazione andranno perduti. L'applicazione client tenta di ristabilire una connessione al database principale ma si verificherà un errore.  
  
3. A questo punto, l'applicazione client tenta di ristabilire una connessione al database mirror nel server partner in modo trasparente. Se viene eseguita correttamente, la connessione viene reindirizzata al database mirror, che diventa il nuovo database principale.  
  
## <a name="specifying-the-failover-partner-in-the-connection-string"></a>Definizione del partner di failover nella stringa di connessione  
 Se si specifica il nome di un server partner di failover nella stringa di connessione, il client tenterà una connessione al partner di failover in modo trasparente se il database principale non è disponibile quando l'applicazione client si connette per la prima volta.  
  
```csharp
";Failover Partner=PartnerServerName"  
```  
  
 Se non si specifica il nome del server partner di failover e il database principale non è disponibile quando l'applicazione client si connette per la prima volta, viene generato un oggetto <xref:System.Data.SqlClient.SqlException>.  
  
 Quando un oggetto <xref:System.Data.SqlClient.SqlConnection> viene aperto correttamente, il nome del partner di failover viene restituito dal server e sostituisce qualsiasi valore specificato nella stringa di connessione.  
  
> [!NOTE]
> Negli scenari di mirroring del database è necessario specificare in modo esplicito il nome del catalogo o del database iniziale nella stringa di connessione. Se il client riceve informazioni di failover su una connessione che non include un catalogo o un database iniziale specificato in modo esplicito, tali informazioni non vengono memorizzate nella cache e l'applicazione non tenterà di eseguire il failover se si verifica un errore nel server principale. Se una stringa di connessione include un valore per il partner di failover, ma nessun valore per il catalogo o il database iniziale, viene generato un oggetto `InvalidArgumentException`.  
  
## <a name="retrieving-the-current-server-name"></a>Recupero del nome del server corrente  
 In caso di failover, è possibile recuperare il nome del server al quale la connessione corrente è effettivamente collegata usando la proprietà <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> di un oggetto <xref:System.Data.SqlClient.SqlConnection>. Il seguente frammento di codice recupera il nome del server attivo e presuppone che la variabile della connessione faccia riferimento a un tipo <xref:System.Data.SqlClient.SqlConnection> aperto.  
  
 Quando si verifica un evento di failover e la connessione viene spostata sul server mirror, la proprietà **DataSource** viene aggiornata per riflettere il nome del mirror.  
  
```vb  
Dim activeServer As String = connection.DataSource  
```  
  
```csharp  
string activeServer = connection.DataSource;  
```  
  
## <a name="sqlclient-mirroring-behavior"></a>Comportamento del mirroring SqlClient  
 Il client tenta sempre di connettersi al server principale corrente e, in caso di errore, passa al partner di failover. Se il database mirror è già stato promosso al ruolo principale nel server partner, la connessione viene eseguita correttamente e il nuovo mapping principale-mirror viene inviato al client e memorizzato nella cache per l'intera durata della chiamata <xref:System.AppDomain>. Non è archiviato nell'archivio permanente e non è disponibile per le connessioni successive in un **AppDomain** o processo diverso. Tuttavia, è disponibile per le connessioni successive nello stesso **AppDomain**. Si noti che un altro **AppDomain** o processo in esecuzione nello stesso computer o in un computer diverso ha sempre il proprio pool di connessioni e tali connessioni non vengono reimpostate. In tal caso, se il database primario diventa inattivo, ogni processo o **AppDomain** ha esito negativo una sola volta e il pool viene cancellato automaticamente.  
  
> [!NOTE]
> Il supporto del mirroring sul server è configurato sulla base dei singoli database. Se vengono eseguite operazioni di modifica dei dati di altri database non inclusi nel set principale/mirror usando nomi in più parti o modificando il database corrente, le modifiche apportate a tali database non verranno propagate in caso di errore. Quando vengono modificati i dati di un database di cui non è stato eseguito il mirroring, non verrà generato alcun errore. Lo sviluppatore deve quindi valutare il possibile impatto di tali operazioni.  
  
## <a name="database-mirroring-resources"></a>Risorse relative al mirroring del database  
 Per la documentazione concettuale e per informazioni sulla configurazione, la distribuzione e l'amministrazione del mirroring, vedere le risorse seguenti nella documentazione di SQL Server.  
  
|Risorsa|Descrizione|  
|--------------|-----------------|  
|[Mirroring del database](/sql/database-engine/database-mirroring/database-mirroring-sql-server)|Viene descritto come impostare e configurare il mirroring in SQL Server.|  
  
## <a name="see-also"></a>Vedere anche

- [Panoramica di ADO.NET](../ado-net-overview.md)
