---
title: <certificateReference> per <identity>
ms.date: 03/30/2017
ms.assetid: ac359c65-c22d-42d2-97de-db53b77cebdb
ms.openlocfilehash: 49c731b2637c15e0b968d8c2523c51c8e138e7bf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926176"
---
# <a name="certificatereference-for-identity"></a>\<> certificateReference per \<Identity >
Specifica le impostazioni per la convalida del certificato X.509. Un client Windows Communication Foundation protetto (WCF) che si connette a un endpoint con questa identità verifica che le attestazioni presentate dal server contengano l'attestazione di identità usata per costruire l'identità.  
  
 \<identity>  
\<certificateReference>  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<certificateReference findValue="String"
                      isChainIncluded="Boolean"
                      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                      storeLocation="LocalMachine/CurrentUser"
                      X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier">
</certificateReference>
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|DESCRIZIONE|  
|---------------|-----------------|  
|findValue|Specifica il valore da cercare nell'archivio certificati X.509. Il tipo contenuto in questo attributo deve soddisfare i requisiti del valore `X509FindType` specificato. Il valore predefinito è una stringa vuota.|  
|isChainIncluded|Valore booleano che specifica se la convalida viene eseguita usando una catena di certificati.|  
|storeLocation|Specifica il percorso dell'archivio certificati che il client può usare per convalidare il certificato del server.<br /><br /> Di seguito vengono elencati i valori validi:<br /><br /> LocalMachine Archivio certificati assegnato al computer locale.<br />CurrentUser Archivio certificati assegnato all'utente corrente.<br /><br /> Il valore predefinito è LocalMachine.<br /><br /> L'attributo è di tipo <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.|  
|storeName|Specifica il nome dell'archivio certificati X.509 da aprire.<br /><br /> Di seguito vengono elencati i valori validi:<br /><br /> AddressBook Archivio certificati per altri utenti.<br />AuthRoot Archivio certificati per autorità di certificazione (CA) di terze parti.<br />CertificateAuthority Archivio certificati per autorità di certificazione intermedie.<br />Consentiti Archivio certificati per i certificati revocati.<br />My Archivio certificati per i certificati personali.<br />Radice Archivio certificati per autorità di certificazione radice attendibili.<br />TrustedPeople Archivio certificati per utenti e risorse direttamente attendibili.<br />TrustedPublisher Archivio certificati per autori direttamente attendibili.<br /><br /> Il valore predefinito è My.<br /><br /> L'attributo è di tipo <xref:System.Security.Cryptography.X509Certificates.StoreName>.|  
|X509FindType|Specifica il tipo di ricerca di certificati X.509 da eseguire. Il tipo contenuto nell'attributo `findValue` deve soddisfare i requisiti del valore X509FindType specificato.<br /><br /> Di seguito vengono elencati i valori validi:<br /><br /> -   FindByThumbPrint<br />-FindBySubjectName<br />-FindBySubjectDistinguishedName<br />-FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-   FindByTimeValid<br />-   FindByTimeNotYetValid<br />-   FindByTemplateName<br />- FindByApplicationPolicy<br />-   FindByCertificatePolicy<br />-   FindByExtension<br />-   FindByKeyUsage<br />-   FindBySubjectKeyIdentifier<br /><br /> L'impostazione predefinita è FindBySubjectDistinguishedName.<br /><br /> L'attributo è di tipo <xref:System.Security.Cryptography.X509Certificates.X509FindType>.|  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[\<identity>](identity.md)|Specifica le impostazioni che attivano l'autenticazione di un endpoint presso gli altri endpoint con cui scambia messaggi.|  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.ServiceModel.Configuration.CertificateReferenceElement>
- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
