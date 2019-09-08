---
title: Scenari di sicurezza delle applicazioni in SQL Server
ms.date: 03/30/2017
ms.assetid: 0164f3a4-406e-4693-bec3-03c8e18b46d7
ms.openlocfilehash: bf844f35a3504af52cdb6bf745862ad5098dfc5f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782701"
---
# <a name="application-security-scenarios-in-sql-server"></a>Scenari di sicurezza delle applicazioni in SQL Server
Non esiste un singolo modo corretto per creare un'applicazione client SQL Server protetta. Ogni applicazione è univoca in termini di requisiti, ambiente di distribuzione e popolazione di utenti. Anche se un'applicazione può essere ragionevolmente protetta quando viene distribuita inizialmente, può diventare meno sicura nel corso del tempo. È impossibile prevedere con accuratezza quali minacce possano emergere nel futuro.  
  
 SQL Server, come prodotto, è stato migliorato da una versione all'altra per incorporare le più recenti funzionalità di sicurezza che consentono agli sviluppatori di creare applicazioni di database protette. Tuttavia, la sicurezza non è predefinita, ma richiede un monitoraggio e un aggiornamento costanti.  
  
## <a name="common-threats"></a>Minacce comuni  
 Gli sviluppatori devono conoscere le minacce per la sicurezza, gli strumenti disponibili per contrastarle e le misure per evitare problemi di sicurezza provocati internamente. La sicurezza può essere paragonata a una catena, in cui la rottura di uno degli anelli compromette l'efficacia dell'insieme. Nell'elenco seguente sono riportate alcune minacce comuni per la sicurezza che verranno descritte in maggior dettaglio negli argomenti di questa sezione.  
  
### <a name="sql-injection"></a>SQL injection  
 Per SQL injection si intende il processo mediante il quale un utente malintenzionato immette istruzioni Transact-SQL anziché input valido. Se l'input viene passato direttamente al server senza essere convalidato e se l'applicazione esegue inavvertitamente il codice inserito, è possibile che l'attacco danneggi o elimini definitivamente i dati. Per contrastare gli attacchi SQL Server injection, è possibile usare stored procedure e comandi con parametri, evitare le istruzioni SQL dinamiche e limitare le autorizzazioni per tutti gli utenti.  
  
### <a name="elevation-of-privilege"></a>Elevazione dei privilegi  
 Gli attacchi tramite elevazione dei privilegi si verificano quando un utente è in grado di assumere i privilegi di un account attendibile, ad esempio un proprietario o un amministratore. Usare sempre account con privilegi minimi e assegnare solo le autorizzazioni necessarie. Evitare di usare account di amministratore o di proprietario per l'esecuzione di codice. In questo modo è possibile limitare l'entità dei danni che possono verificarsi in caso di successo di un attacco. Quando si eseguono attività che richiedono autorizzazioni aggiuntive, usare la rappresentazione o la firma di stored procedure solo per la durata dell'attività. È possibile firmare le stored procedure con certificati o usare la rappresentazione per assegnare autorizzazioni temporanee.  
  
### <a name="probing-and-intelligent-observation"></a>Probe e osservazione intelligente  
 In un attacco di tipo probe è possibile che vengano usati i messaggi di errore generati da un'applicazione per ricercare vulnerabilità di sicurezza. Implementare la gestione degli errori in tutto il codice procedurale per evitare che le informazioni sugli errori di SQL Server vengano restituite all'utente finale.  
  
### <a name="authentication"></a>Authentication  
 Un attacco injection alle stringhe di connessione può verificarsi quando si usano gli account di accesso di SQL Server se in fase di esecuzione viene creata una stringa di connessione basata sull'input dell'utente. Se la stringa di connessione non viene controllata per verificare la presenza di coppie di parole chiave valide, un utente non autorizzato può inserire caratteri aggiuntivi, con la possibilità di accedere a dati sensibili o ad altre risorse del server. Se possibile, usare l'autenticazione di Windows. Se è necessario usare gli account di accesso di SQL server, usare <xref:System.Data.SqlClient.SqlConnectionStringBuilder> per creare e convalidare le stringhe di connessione in fase di esecuzione.  
  
### <a name="passwords"></a>Password  
 Gli attacchi spesso riescono perché un intruso è stato in grado di ottenere o indovinare la password di un utente con privilegi. Le password rappresentano la prima linea di difesa contro le intrusioni, quindi ai fini della sicurezza del sistema è essenziale impostare password complesse. Creare e applicare criteri password per l'autenticazione in modalità mista.  
  
 Assegnare sempre una password complessa all'account `sa`, anche quando si usa l'autenticazione di Windows.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Gestione delle autorizzazioni con stored procedure in SQL Server](managing-permissions-with-stored-procedures-in-sql-server.md)  
 Viene descritto come usare le stored procedure per gestire le autorizzazioni e controllare l'accesso ai dati. L'utilizzo di stored procedure è un sistema efficace per rispondere a molte minacce per la sicurezza.  
  
 [Scrittura dinamica sicura in SQL Server](writing-secure-dynamic-sql-in-sql-server.md)  
 Vengono descritte le tecniche per scrivere istruzioni SQL dinamiche sicure tramite le stored procedure.  
  
 [Firma di stored procedure in SQL Server](signing-stored-procedures-in-sql-server.md)  
 Viene descritto come firmare una stored procedure con un certificato per consentire agli utenti l'uso di dati cui non possono accedere direttamente. In questo modo le stored procedure possono eseguire operazioni che il chiamante non può eseguire direttamente in quanto non dispone delle autorizzazioni appropriate.  
  
 [Personalizzazione delle autorizzazioni con rappresentazione in SQL Server](customizing-permissions-with-impersonation-in-sql-server.md)  
 Viene descritto come usare la clausola EXECUTE AS per rappresentare un altro utente. Con la rappresentazione il contesto di esecuzione passa dal chiamante all'utente specificato.  
  
 [Concessione di autorizzazioni a livello di riga in SQL Server](granting-row-level-permissions-in-sql-server.md)  
 Viene descritto come implementare autorizzazioni a livello di riga per limitare l'accesso ai dati.  
  
 [Creazione di ruoli applicazione in SQL Server](creating-application-roles-in-sql-server.md)  
 Vengono descritte le funzionalità dei ruoli applicazione.  
  
 [Abilitazione dell'accesso tra database in SQL Server](enabling-cross-database-access-in-sql-server.md)  
 Viene descritto come consentire l'accesso tra database senza compromettere la sicurezza.  
  
## <a name="see-also"></a>Vedere anche

- [Sicurezza di SQL Server](sql-server-security.md)
- [Cenni preliminari sulla sicurezza in SQL Server](overview-of-sql-server-security.md)
- [Protezione delle applicazioni ADO.NET](../securing-ado-net-applications.md)
- [Panoramica di ADO.NET](../ado-net-overview.md)
