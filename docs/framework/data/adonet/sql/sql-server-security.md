---
title: Sicurezza di SQL Server
ms.date: 03/30/2017
ms.assetid: 9053724d-a1fb-4f0f-b9dc-7f6dd893e8ff
ms.openlocfilehash: c5fd9cc82a3b1e4ffa217d65c542376fe067db06
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791627"
---
# <a name="sql-server-security"></a>Sicurezza di SQL Server
In SQL Server sono disponibili molte funzionalità che supportano la creazione di applicazioni di database protette.  
  
 Indipendentemente dalla versione di SQL Server in uso, esistono problemi di sicurezza, ad esempio furto dei dati o vandalismo, che è opportuno considerare. Anche l'integrità dei dati rientra tra i problemi di sicurezza da considerare. Se i dati non sono protetti, potrebbero diventare inutili se ne viene consentita la modifica ad hoc e vengono modificati con valori incorretti oppure eliminati, inavvertitamente o intenzionalmente. È inoltre spesso necessario garantire la conformità a requisiti di carattere legale, ad esempio la corretta archiviazione di informazioni riservate. A seconda delle leggi in vigore in una determinata giurisdizione, è infatti assolutamente vietata l'archiviazione di alcuni tipi di dati personali.  
  
 Ogni versione di SQL Server, così come ogni versione di Windows, include funzionalità di sicurezza diverse e ogni nuova versione presenta funzionalità più avanzate rispetto alle versioni precedenti. È importante comprendere che le sole funzionalità di sicurezza non bastano a garantire un'applicazione di database protetta. Ogni applicazione di database è diversa dall'altra per requisiti, ambiente di esecuzione, modello di distribuzione, posizione fisica e popolazione di utenti. Alcune applicazioni con ambito locale possono richiedere un livello minimo di sicurezza, mentre per altre applicazioni locali o distribuite tramite Internet può essere necessario adottare misure di sicurezza severe, nonché funzionalità per la valutazione e il monitoraggio continuo della sicurezza.  
  
 I requisiti di sicurezza di un'applicazione di database SQL Server devono essere considerati già in fase di progettazione e non in un secondo momento. La valutazione delle minacce nelle prime fasi del ciclo di sviluppo consente di ridurre al minimo possibili danni qualora venga rilevata una vulnerabilità.  
  
 Anche se la progettazione iniziale di un'applicazione è corretta, possono emergere nuove minacce con l'evoluzione del sistema. La creazione di più linee di difesa intorno al database consente di ridurre al minimo i danni causati da una violazione del sistema di sicurezza. La prima linea di difesa consiste nel ridurre l'area soggetta a possibili attacchi non concedendo mai un numero di autorizzazioni maggiore di quello assolutamente necessario.  
  
 Negli argomenti di questa sezione viene fornita una breve descrizione delle funzionalità di sicurezza di SQL Server pertinenti per gli sviluppatori, con collegamenti ai relativi argomenti della documentazione online di SQL Server e ad altre risorse di approfondimento.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Cenni preliminari sulla sicurezza in SQL Server](overview-of-sql-server-security.md)  
 Vengono descritte l'architettura e le funzionalità di sicurezza di SQL Server.  
  
 [Scenari di sicurezza delle applicazioni in SQL Server](application-security-scenarios-in-sql-server.md)  
 Sono contenuti argomenti che illustrano diversi scenari di sicurezza per applicazioni ADO.NET e SQL Server.  
  
 [Sicurezza in SQL Server Express](sql-server-express-security.md)  
 Descrive le considerazioni sulla sicurezza per SQL Server Express.  
  
## <a name="related-sections"></a>Sezioni correlate  
[Centro sicurezza per SQL Server motore di database e il database SQL di Azure](/sql/relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database)  
Descrive le considerazioni sulla sicurezza per SQL Server e il database SQL di Azure.

[Considerazioni sulla sicurezza per un'installazione di SQL Server](/sql/sql-server/install/security-considerations-for-a-sql-server-installation)  
Vengono descritti i problemi di sicurezza da prendere in considerazione prima di installare SQL Server.

## <a name="see-also"></a>Vedere anche

- [Protezione delle applicazioni ADO.NET](../securing-ado-net-applications.md)
- [SQL Server e ADO.NET](index.md)
