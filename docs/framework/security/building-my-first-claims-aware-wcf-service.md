---
title: Creazione del primo servizio WCF che può riconoscere attestazioni
ms.date: 03/30/2017
ms.assetid: e0e6d091-9a97-4888-8f2c-cbcee42d90ee
author: BrucePerlerMS
ms.openlocfilehash: 330d785721cb434f74ec746310a71bfd39fefd0b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045547"
---
# <a name="building-my-first-claims-aware-wcf-service"></a>Creazione del primo servizio WCF che può riconoscere attestazioni
## <a name="applies-to"></a>Si applica a  
  
- Windows Identity Foundation (WIF)  
  
- Windows Communication Foundation (WCF)  
  
## <a name="overview"></a>Panoramica  
 In questo argomento viene illustrato lo scenario di compilazione di servizi WCF in grado di riconoscere attestazioni mediante WIF. Uno scenario di servizio Web in grado di riconoscere attestazioni è in genere caratterizzato da tre partecipanti: il servizio Web stesso, l'utente finale e il servizio token di sicurezza. come illustrato nella figura seguente:  
  
 ![Diagramma che mostra i componenti del servizio WCF in grado di riconoscere attestazioni di base.](./media/building-my-first-claims-aware-wcf-service/windows-identify-foundation-basic-claims-aware-windows-communication-foundation-service.gif)  
  
1. Tramite il client del servizio WCF (talvolta definito agente) viene utilizzato WIF per inviare le credenziali al servizio token di sicurezza e alla riuscita dell'autenticazione, tramite l'agente viene emesso un token dal servizio token di sicurezza.  
  
2. L'agente invia questo token emesso dal servizio token di sicurezza al servizio WCF.  
  
3. Il servizio WCF in grado di riconoscere attestazioni viene configurato per considerare attendibili il servizio token di sicurezza e i token da quest'ultimo emessi. Tramite il servizio WCF in grado di riconoscere attestazioni viene utilizzato WIF per convalidare il token e analizzarlo. Gli sviluppatori usano tipi e API WIF appropriati, ad esempio **ClaimsPrincipal**, per esigenze dell'applicazione come l'implementazione della relativa autorizzazione.  
  
 A partire da .NET 4.5, WIF fa parte del pacchetto .NET Framework. La disponibilità delle classi di WIF direttamente nel framework consente una maggiore integrazione dell'identità basata sulle attestazioni nella piattaforma .NET, semplificando l'utilizzo delle attestazioni. Con WIF 4.5 non è necessario installare altri componenti fuori banda per avviare lo sviluppo di applicazioni Web in grado di riconoscere attestazioni. Le classi di WIF vengono ora estese tra diversi assembly, i principali dei quali sono System.Security.Claims, System.IdentityModel e System.IdentityModel.Services.  
  
 Il servizio token di sicurezza è un servizio tramite cui vengono rilasciati dei token alla riuscita dell'autenticazione. Microsoft offre due servizi token di sicurezza standard del settore:  
  
- [Active Directory Federation Services (AD FS) 2,0](https://go.microsoft.com/fwlink/?LinkID=247516)
  
- [Servizio di controllo di accesso di Microsoft Azure (ACS)](https://docs.microsoft.com/previous-versions/azure/azure-services/hh147631(v=azure.100))
  
 AD FS 2.0 fa parte di Windows Server R2 e può essere utilizzato come servizio token di sicurezza in scenari locali. Azure Active Directory Access Control (detto anche Servizio di controllo di accesso o ACS) è un servizio cloud, fornito come parte di Microsoft Azure. Per fini di test e didattici, è inoltre possibile utilizzare altri servizi token di sicurezza per compilare applicazioni in grado di riconoscere attestazioni. Ad esempio, è possibile usare il servizio STS di sviluppo locale che fa parte di [Identity and Access Tool per Visual Studio](https://go.microsoft.com/fwlink/?LinkID=245849) , disponibile gratuitamente online.  
  
 Per compilare il primo servizio WCF in grado di riconoscere attestazioni usando [WIF, vedere Procedura: Abilitare WIF per un'applicazione](how-to-enable-wif-for-a-wcf-web-service-application.md)del servizio Web WCF.
  
## <a name="see-also"></a>Vedere anche

- [Guida introduttiva a WIF](getting-started-with-wif.md)
