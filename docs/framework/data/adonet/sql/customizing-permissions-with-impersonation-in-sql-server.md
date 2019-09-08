---
title: Personalizzazione delle autorizzazioni con rappresentazione in SQL Server
ms.date: 03/30/2017
ms.assetid: dc733d09-1d6d-4af0-9c4b-8d24504860f1
ms.openlocfilehash: b5dcef80afffa7bb3722a09020c5445dbc47f16a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782480"
---
# <a name="customizing-permissions-with-impersonation-in-sql-server"></a>Personalizzazione delle autorizzazioni con rappresentazione in SQL Server
In molte applicazioni vengono usate le stored procedure per accedere ai dati, basandosi sul concatenamento delle proprietà per restringere l'accesso alle tabelle di base. È possibile concedere autorizzazioni EXECUTE sulle stored procedure, revocando o negando le autorizzazioni sulle tabelle di base. SQL Server non verifica le autorizzazioni del chiamante se il proprietario della stored procedure coincide con quello delle tabelle. Il concatenamento delle proprietà non funziona se i proprietari degli oggetti sono diversi oppure se si usano istruzioni SQL dinamiche.  
  
 È possibile usare la clausola EXECUTE AS in una stored procedure quando il chiamante non dispone delle autorizzazioni sugli oggetti di database cui viene fatto riferimento. Per effetto della clausola EXECUTE AS il contesto di esecuzione viene passato all'utente proxy. Tutto il codice, nonché qualsiasi chiamata a stored procedure o trigger annidati, viene eseguito nel contesto di sicurezza dell'utente proxy. Viene ripristinato il contesto di esecuzione del chiamante originale solo dopo l'esecuzione della stored procedure o quando viene eseguita un'istruzione REVERT.  
  
## <a name="context-switching-with-the-execute-as-statement"></a>Cambio del contesto con l'istruzione EXECUTE AS  
 L'istruzione EXECUTE AS Transact-SQL consente di cambiare il contesto di esecuzione di un'istruzione mediante la rappresentazione di un altro account di accesso o utente del database. Si tratta di una tecnica utile per testare query e stored procedure usando le credenziali di un altro utente.  
  
```  
EXECUTE AS LOGIN = 'loginName';  
EXECUTE AS USER = 'userName';  
```  
  
 È necessario disporre delle autorizzazioni IMPERSONATE per l'account di accesso o l'utente che si intende rappresentare. Questa autorizzazione è implica per `sysadmin` su tutti i database e per i membri del ruolo `db_owner` sui database di cui sono proprietari.  
  
## <a name="granting-permissions-with-the-execute-as-clause"></a>Concessione delle autorizzazioni con la clausola EXECUTE AS  
 È possibile usare la clausola EXECUTE AS nell'intestazione della definizione di una stored procedure, un trigger o una funzione definita dall'utente, ad eccezione delle funzioni inline valutate a livello di tabella. La stored procedure viene quindi eseguita nel contesto del nome utente o della parola chiave specificata nella clausola EXECUTE AS. È possibile creare un utente proxy nel database di cui non è stato eseguito il mapping a un account di accesso, concedendo solo le autorizzazioni necessarie sugli oggetti cui la stored procedure ha accesso. Solo l'utente proxy specificato nella clausola EXECUTE AS deve disporre delle autorizzazioni su tutti gli oggetti cui il modulo ha accesso.  
  
> [!NOTE]
> Per alcune azioni, ad esempio TRUNCATE TABLE, non sono disponibili autorizzazioni da concedere. Incorporando l'istruzione all'interno di una stored procedure e specificando un utente proxy che dispone delle autorizzazioni ALTER TABLE, è possibile estendere le autorizzazioni necessarie per troncare la tabella ai chiamanti che dispongono solo delle autorizzazioni EXECUTE per la stored procedure.  
  
 Il contesto specificato nella clausola EXECUTE AS è valido per la durata della stored procedura, incluse stored procedure e trigger annidati. Il contesto ritorna al chiamante al termine dell'esecuzione o quando viene eseguita l'istruzione REVERT.  
  
 L'uso di una clausola EXECUTE AS in una stored procedure implica tre passaggi:  
  
1. Creazione di un utente proxy nel database non mappato a un account di accesso. Questo passaggio non è necessario ma risulta utile durante la gestione delle autorizzazioni.  
  
```  
CREATE USER proxyUser WITHOUT LOGIN  
```  
  
1. Concessione delle autorizzazioni necessarie all'utente proxy.  
  
2. Aggiunta della clausola EXECUTE AS alla stored procedure o alla funzione definita dall'utente.  
  
```  
CREATE PROCEDURE [procName] WITH EXECUTE AS 'proxyUser' AS ...  
```  
  
> [!NOTE]
> È possibile che le applicazioni che richiedono il controllo vengano interrotte perché il contesto di sicurezza originale del chiamante non viene mantenuto. Le funzioni predefinite che restituiscono l'identità dell'utente corrente, ad esempio SESSION_USER, USER, o USER_NAME, restituiscono l'utente associato alla clausola EXECUTE AS, non il chiamante originale.  
  
### <a name="using-execute-as-with-revert"></a>Uso di EXECUTE AS con REVERT  
 È possibile usare l'istruzione REVERT Transact-SQL per ripristinare il contesto di esecuzione originale.  
  
 La clausola facoltativa with no Revert cookie @variableName= consente di riportare il contesto di esecuzione al chiamante se @variableName la variabile contiene il valore corretto. Viene quindi ripristinato il contesto di esecuzione del chiamante negli ambienti in cui viene usato il pool di connessioni. Poiché il valore di @variableName è noto solo al chiamante dell'istruzione Execute As, il chiamante può garantire che il contesto di esecuzione non possa essere modificato dall'utente finale che richiama l'applicazione. Alla chiusura della connessione, il contesto viene restituito al pool. Per ulteriori informazioni sul pool di connessioni in ADO.NET, vedere [SQL Server pool di connessioni (ADO.NET)](../sql-server-connection-pooling.md).  
  
### <a name="specifying-the-execution-context"></a>Specifica del contesto di esecuzione  
 Oltre a specificare un utente, è inoltre possibile usare EXECUTE AS con le parole chiave seguenti.  
  
- CALLER. L'esecuzione come CALLER corrisponde all'impostazione predefinita. Se non vengono specificate altre opzioni, la stored procedure viene eseguita nel contesto di sicurezza del chiamante.  
  
- OWNER. Con questa parola chiave la stored procedure viene eseguita nel contesto del proprietario. Se la stored procedure viene creata in uno schema di cui è proprietario `dbo` o il proprietario del database, verrà eseguita con autorizzazioni senza restrizioni.  
  
- SELF. Con questa parola chiave la stored procedure viene eseguita nel contesto di sicurezza del creatore. Questa opzione equivale all'esecuzione come utente specificato, dove l'utente specificato è la persona che crea o modifica la stored procedure.  
  
## <a name="see-also"></a>Vedere anche

- [Protezione delle applicazioni ADO.NET](../securing-ado-net-applications.md)
- [Cenni preliminari sulla sicurezza in SQL Server](overview-of-sql-server-security.md)
- [Scenari di sicurezza delle applicazioni in SQL Server](application-security-scenarios-in-sql-server.md)
- [Gestione delle autorizzazioni con stored procedure in SQL Server](managing-permissions-with-stored-procedures-in-sql-server.md)
- [Scrittura dinamica sicura in SQL Server](writing-secure-dynamic-sql-in-sql-server.md)
- [Firma di stored procedure in SQL Server](signing-stored-procedures-in-sql-server.md)
- [Modifica di dati con stored procedure](../modifying-data-with-stored-procedures.md)
- [Panoramica di ADO.NET](../ado-net-overview.md)
