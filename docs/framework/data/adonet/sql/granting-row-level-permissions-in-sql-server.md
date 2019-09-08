---
title: Concessione di autorizzazioni a livello di riga in SQL Server
ms.date: 03/30/2017
ms.assetid: a55aaa12-34ab-41cd-9dec-fd255b29258c
ms.openlocfilehash: df5fcb4a6c73e12bec2ab17501fdfb02cf672324
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782360"
---
# <a name="granting-row-level-permissions-in-sql-server"></a>Concessione di autorizzazioni a livello di riga in SQL Server

In alcuni scenari è necessario controllare l'accesso a un livello caratterizzato da una maggior granularità rispetto a quanto consentito dalla semplice concessione, revoca o negazione delle autorizzazioni sui dati. Ad esempio, in un'applicazione di database usata in un ospedale potrebbe essere necessario consentire ai medici di visualizzare solo le informazioni correlate ai propri pazienti. Scenari simili sono presenti in molti ambienti, tra cui quelli delle applicazioni destinate al settore finanziario, legale, statale e militare. Per contribuire a gestire questi scenari, SQL Server 2016 fornisce una funzionalità di [sicurezza a livello di riga](/sql/relational-databases/security/row-level-security) che semplifica e centralizza la logica di accesso a livello di riga in un criterio di sicurezza. Per le versioni precedenti di SQL Server, una funzionalità simile può essere ottenuta usando le visualizzazioni per applicare filtri a livello di riga.

## <a name="implementing-row-level-filtering"></a>Implementazione di applicazione di filtri a livello di riga

L'applicazione di filtri a livello di riga viene usata per applicazioni che archiviano informazioni in un'unica tabella, come nell'esempio dell'ospedale. Per applicare i filtri a livello di riga, ogni riga include una colonna che definisce un parametro discriminante, ad esempio un nome utente, un'etichetta o un altro identificatore. È possibile creare un criterio di sicurezza o una visualizzazione nella tabella, che consente di filtrare le righe a cui l'utente può accedere. È possibile quindi creare stored procedure con parametri, che controllano i tipi di query, che l'utente può eseguire.

L'esempio seguente descrive come configurare l'applicazione di filtri a livello di riga basati su un nome utente o un nome di accesso:

- Creare la tabella, aggiungendo una colonna per l'archiviazione del nome.

- Abilitare l'applicazione di filtri a livello di riga:

  - Se si usa SQL Server 2016 o versioni successive oppure il [database SQL di Azure](https://docs.microsoft.com/azure/sql-database/), creare un criterio di sicurezza che aggiunga un predicato nella tabella per limitare le righe restituite a quelle che corrispondono all'utente del database corrente (usando la funzione predefinita CURRENT_USER()) o il nome di accesso corrente (usando la funzione predefinita SUSER_SNAME()):

      ```sql
      CREATE SCHEMA Security
      GO

      CREATE FUNCTION Security.userAccessPredicate(@UserName sysname)
          RETURNS TABLE
          WITH SCHEMABINDING
      AS
          RETURN SELECT 1 AS accessResult
          WHERE @UserName = SUSER_SNAME()
      GO

      CREATE SECURITY POLICY Security.userAccessPolicy
          ADD FILTER PREDICATE Security.userAccessPredicate(UserName) ON dbo.MyTable,
          ADD BLOCK PREDICATE Security.userAccessPredicate(UserName) ON dbo.MyTable
      GO
      ```

  - Se si usa una versione di SQL Server precedente alla 2016, è possibile ottenere funzionalità simili usando una visualizzazione:

      ```sql
      CREATE VIEW vw_MyTable
      AS
          RETURN SELECT * FROM MyTable
          WHERE UserName = SUSER_SNAME()
      GO
      ```

- Creare stored procedure per selezionare, inserire, aggiornare ed eliminare i dati. Se il filtro viene applicato dai criteri di sicurezza, le stored procedure devono eseguire queste operazioni direttamente nella tabella di base. In caso contrario, se il filtro viene applicato da una visualizzazione, le stored procedure devono invece operare sulla visualizzazione. Il criterio di sicurezza o la visualizzazione filtrerà automaticamente le righe restituite o modificate dalle query utente e la stored procedure fornirà un limite di sicurezza più rigoroso per impedire che gli utenti con accesso diretto alle query eseguano query che possono dedurre l'esistenza di dati filtrati.

- Per le stored procedure che inseriscono dati, acquisire il nome utente usando la stessa funzione specificata nel criterio di sicurezza o nella visualizzazione e inserire tale valore nella colonna UserName.

- Negare al ruolo `public` tutte le autorizzazioni sulle tabelle (e sulle visualizzazioni, se pertinente). Gli utenti non potranno ereditare autorizzazioni da altri ruoli del database perché il predicato del filtro è basato su nomi utenti o di accesso e non su ruoli.

- Concedere ai ruoli del database l'autorizzazione EXECUTE sulle stored procedure. Gli utenti potranno accedere ai dati solo tramite le stored procedure specificate.

## <a name="see-also"></a>Vedere anche

- [Sicurezza a livello di riga](/sql/relational-databases/security/row-level-security)
- [Protezione delle applicazioni ADO.NET](../securing-ado-net-applications.md)
- [Cenni preliminari sulla sicurezza in SQL Server](overview-of-sql-server-security.md)
- [Scenari di sicurezza delle applicazioni in SQL Server](application-security-scenarios-in-sql-server.md)
- [Gestione delle autorizzazioni con stored procedure in SQL Server](managing-permissions-with-stored-procedures-in-sql-server.md)
- [Scrittura dinamica sicura in SQL Server](writing-secure-dynamic-sql-in-sql-server.md)
- [Panoramica di ADO.NET](../ado-net-overview.md)
