---
title: Novità di Windows Identity Foundation 4.5
ms.date: 03/30/2017
ms.assetid: 3b381f04-593b-471f-bd33-0362be1aade5
author: BrucePerlerMS
ms.openlocfilehash: 93631c1171f81ec8b8d94b56a56012343f6c3220
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045271"
---
# <a name="whats-new-in-windows-identity-foundation-45"></a>Novità di Windows Identity Foundation 4.5
La prima versione di Windows Identity Foundation (WIF) è stata rilasciata come download autonomo ed è nota come WIF 3.5 perché è stata introdotta nello stesso periodo di .NET 3.5 SP1. Con .NET 4.5 WIF è diventato parte di .NET Framework. La disponibilità delle classi WIF direttamente nel framework consente una maggiore integrazione dell'identità basata sulle attestazioni in .NET, semplificando l'uso delle attestazioni. Le applicazioni scritte per WIF 3.5 devono essere modificate per sfruttare il nuovo modello. Per informazioni, vedere [Linee guida per la migrazione di un'applicazione compilata con le versioni di WIF dalla 3.5 alla 4.5](guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md).  
  
 Di seguito sono descritti alcuni elementi di rilievo delle principali modifiche.  
  
## <a name="wif-is-now-part-of-the-net-framework"></a>WIF fa ora parte di .NET Framework  
 Le classi di WIF sono ora estese tra vari assembly, i principali dei quali sono `mscorlib`, `System.IdentityModel`, `System.IdentityModel.Services` e `System.ServiceModel`. Analogamente, le classi WIF sono distribuite in diversi spazi dei nomi: <xref:System.Security.Claims?displayProperty=nameWithType>, diversi spazi dei nomi [System.IdentityModel](https://go.microsoft.com/fwlink/?LinkId=272004) e <xref:System.ServiceModel.Security?displayProperty=nameWithType>. Lo spazio dei nomi <xref:System.Security.Claims?displayProperty=nameWithType> contiene le nuove classi <xref:System.Security.Claims.ClaimsPrincipal> e <xref:System.Security.Claims.ClaimsIdentity> (vedere sotto). Tutte le entità in .NET ora derivano da <xref:System.Security.Claims.ClaimsPrincipal>. Per informazioni dettagliate sugli spazi dei nomi WIF e sui tipi di classi in essi contenute, vedere [Informazioni di riferimento sulle API WIF](wif-api-reference.md). Per informazioni sulla corrispondenza degli spazi dei nomi tra WIF 3.5 e WIF 4.5, vedere [Mapping dello spazio dei nomi tra WIF 3.5 e WIF 4.5](namespace-mapping-between-wif-3-5-and-wif-4-5.md).  
  
## <a name="new-claims-model-and-principal-object"></a>Nuovi modello attestazioni e oggetto entità  
 Le attestazioni sono il nucleo fondamentale di .NET Framework 4.5. Le classi attestazione di base (<xref:System.Security.Claims.Claim>, <xref:System.Security.Claims.ClaimsIdentity>, <xref:System.Security.Claims.ClaimsPrincipal>, <xref:System.Security.Claims.ClaimTypes> e <xref:System.Security.Claims.ClaimValueTypes>) risiedono tutte direttamente in `mscorlib` nello spazio dei nomi <xref:System.Security.Claims?displayProperty=nameWithType>. Non è più necessario utilizzare le interfacce per inserire le attestazioni nel sistema di identità .NET: <xref:System.Security.Principal.WindowsPrincipal>, <xref:System.Security.Principal.GenericPrincipal> e <xref:System.Web.Security.RolePrincipal> ora ereditano da <xref:System.Security.Claims.ClaimsPrincipal>; <xref:System.Security.Principal.WindowsIdentity>, <xref:System.Security.Principal.GenericIdentity> e <xref:System.Web.Security.FormsIdentity> ora ereditano da <xref:System.Security.Claims.ClaimsIdentity>. In breve, ogni classe di entità consente ora di soddisfare le attestazioni. Le interfacce e le classi di integrazione di WIF 3.5(`WindowsClaimsIdentity`, `WindowsClaimsPrincipal`, `IClaimsPrincipal`, `IClaimsIdentity`) sono state quindi rimosse. Inoltre, la classe <xref:System.Security.Claims.ClaimsIdentity> ora espone i metodi che semplificano l'esecuzione di query sulla raccolta delle attestazioni di identità.  
  
## <a name="changes-to-the-wif-45-visual-studio-experience"></a>Modifiche all'esperienza di WIF 4.5 con Visual Studio  
  
- Funzionalità **Aggiungi riferimento STS** Questa funzionalità di Visual Studio (utilità della riga di comando FedUtil) non è più disponibile. Al suo posto è possibile usare la nuova estensione di Visual Studio **Identity and Access Tool per Visual Studio 2012**. Ciò consente di attuare una federazione con un STS esistente o di utilizzare LocalSTS per eseguire i test delle soluzioni. Una volta installata l'estensione, è possibile fare clic con il pulsante destro del mouse sul progetto e cercare **Identity and Access** nel menu di scelta rapida.  
  
- I modelli ASP.NET e STS non sono più disponibili in quanto le attestazioni possono essere utilizzate direttamente nei modelli di progetto esistenti per ASP.NET, siti Web e WCF.  
  
- I controlli nello spazio dei nomi `Microsoft.IdentityModel.Web.Controls` (`SignInControl`, `FederatedPassiveSignInControl` e `FederatedPassiveSignInStatus`) non sono disponibili in WIF 4.5.  
  
## <a name="changes-to-the-wif-45-api"></a>Modifiche all'API di WIF 4.5  
  
- In generale, le classi correlate alle attestazioni si trovano nello spazio dei nomi <xref:System.Security.Claims?displayProperty=nameWithType>, le classi correlate a WCF, ovvero i contratti di servizio, i canali, le factory canale e gli host servizio usati per scenari WS-Trust, si trovano in <xref:System.ServiceModel.Security?displayProperty=nameWithType>, tutte le altre classi WIF sono distribuite tra diversi spazi dei nomi [System.IdentityModel](https://go.microsoft.com/fwlink/?LinkId=272004), inclusi, ad esempio, le classi che rappresentano artefatti WS-* e SAML, i gestori di token e le classi correlate, oltre che le classi usate negli scenari WS-Federation. Per informazioni, vedere [Mapping dello spazio dei nomi tra WIF 3.5 e WIF 4.5](namespace-mapping-between-wif-3-5-and-wif-4-5.md) e [WIF API Reference](wif-api-reference.md) (Informazioni di riferimento sulle API WIF).  
  
- La chiave del computer è stata abilitata per l'utilizzo nei cookie di sessione per gli scenari di web farm. Per altre informazioni, vedere [WIF e Web farm](wif-and-web-farms.md).  
  
- È ora possibile configurare WIF in modo dichiarativo negli elementi [\<system.identityModel>](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) e [\<system.identityModel.services>](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md). Per altre informazioni sulla configurazione di WIF, vedere [Guida di riferimento per la configurazione di WIF](wif-configuration-reference.md).  
  
## <a name="other-notable-net-changes-or-features-that-are-caused-by-the-integration-of-wif-into-net"></a>Altre modifiche o funzionalità significative di .NET determinate dall'integrazione di WIF in .NET  
  
- In .NET Framework è stata integrata la possibilità di eseguire autorizzazioni basate su attestazioni (CBAC). È possibile configurare un oggetto <xref:System.Security.Claims.ClaimsAuthorizationManager> e utilizzare le classi <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> e <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> per eseguire controlli di accesso imperativi e dichiarativi nel codice. CBAC fornisce maggiore flessibilità e maggiore granularità rispetto ai tradizionali controlli dell'accesso basato su ruoli (RBAC). Consente inoltre una maggiore separazione dei criteri di autorizzazione dalla logica di business poiché la logica di business può basare il controllo dell'accesso su un'attestazione o su un set di attestazioni specifico e i criteri di autorizzazione per tali attestazioni possono essere configurati in modo dichiarativo nell'elemento [\<claimsAuthorizationManager>](../configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md).  
  
## <a name="wcf-changes-as-a-result-of-wif-integration"></a>Modifiche a WCF come conseguenza dell'integrazione di WIF:  
  
- Il modello di identità basato sulle attestazioni di WCF è stato sostituito da WIF. Ciò significa che le classi negli spazi dei nomi <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType> e <xref:System.IdentityModel.Selectors?displayProperty=nameWithType> devono essere rilasciate a favore dell'utilizzo delle classi di WIF.  
  
- WIF viene ora abilitato in un servizio WCF specificando l'attributo `useIdentityConfiguration` nell'elemento `<system.serviceModel>`/`<behaviors>`/`<serviceBehaviors>`/`<serviceCredentials>` come nel codice XML seguente:  
  
    ```xml  
    <serviceCredentials useIdentityConfiguration="true">  
        <!--Certificate added by Identity And Access VS Package.  Subject='CN=localhost', Issuer='CN=localhost'. Make sure you have this certificate installed. The Identity and Access tool does not install this certificate.-->  
        <serviceCertificate findValue="CN=localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName" />  
    </serviceCredentials>  
    ```  
  
     Quando si usa **Identity and Access Tool per Visual Studio 2012** (vedere **Modifiche all'esperienza con Visual Studio** in precedenza), lo strumento aggiunge un elemento `<serviceCredentials>` con l'attributo `useIdentityConfiguration` impostato sul file di configurazione. Aggiunge anche un elemento [\<system.identityModel>](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) corrispondente che contiene le impostazioni di configurazione di WIF, un binding e altre impostazioni necessarie per l'outsourcing dell'autenticazione al servizio token di sicurezza scelto.  
  
## <a name="see-also"></a>Vedere anche

- [Linee guida per la migrazione di un'applicazione compilata con le versioni di WIF dalla 3.5 alla 4.5](guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md)
- [Mapping dello spazio dei nomi tra WIF 3.5 e WIF 4.5](namespace-mapping-between-wif-3-5-and-wif-4-5.md)
- [Riferimento per le API di WIF](wif-api-reference.md)
- [Guida di riferimento per la configurazione di WIF](wif-configuration-reference.md)
