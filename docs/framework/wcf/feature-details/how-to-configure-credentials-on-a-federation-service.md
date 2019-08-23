---
title: 'Procedura: Configurare le credenziali in un servizio federativo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 149ab165-0ef3-490a-83a9-4322a07bd98a
ms.openlocfilehash: 792d2f1b113c0743bd91ccf2f7ff894d7f7d319f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912191"
---
# <a name="how-to-configure-credentials-on-a-federation-service"></a>Procedura: Configurare le credenziali in un servizio federativo
In Windows Communication Foundation (WCF) la creazione di un servizio federato è costituita dalle procedure principali seguenti:  
  
1. Configurazione di un oggetto <xref:System.ServiceModel.WSFederationHttpBinding> o di un'associazione personalizzata simile. Per ulteriori informazioni sulla creazione di un'associazione appropriata, [vedere Procedura: Creare un'associazione](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)WSFederationHttpBinding.  
  
2. Configurazione della classe <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>, che controlla come vengono autenticati i token emessi presentati al servizio.  
  
 In questo argomento vengono fornite informazioni dettagliate sul secondo passaggio. Per ulteriori informazioni sul funzionamento di un servizio federato, vedere [Federazione](../../../../docs/framework/wcf/feature-details/federation.md).  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-code"></a>Per impostare le proprietà di IssuedTokenServiceCredential nel codice  
  
1. Utilizzare la proprietà <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A> della classe <xref:System.ServiceModel.Description.ServiceCredentials> per restituire un riferimento a un'istanza di <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>. L'accesso alla proprietà viene eseguito dalla proprietà <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> della classe <xref:System.ServiceModel.ServiceHostBase>.  
  
2. Impostare la <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> proprietà su `true` se i token autocertificati, ad esempio le schede CardSpace, devono essere autenticati. Il valore predefinito è `false`.  
  
3. Popolare la raccolta restituita dalla proprietà <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> con istanze della classe <xref:System.Security.Cryptography.X509Certificates.X509Certificate2>. Ogni istanza rappresenta un emittente da cui il servizio autenticherà i token.  
  
    > [!NOTE]
    > A differenza della raccolta lato client restituita dalla proprietà <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>, la raccolta dei certificati noti non è una raccolta con chiave. Il servizio accetta i token emessi dai certificati specificati indipendentemente dall'indirizzo del client che ha inviato il messaggio contenente il token emesso (salvo gli ulteriori limiti descritti più avanti in questo argomento).  
  
4. Impostare la proprietà <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> su uno dei valori dell'enumerazione <xref:System.ServiceModel.Security.X509CertificateValidationMode>. Questa operazione può essere eseguita solo nel codice. Il valore predefinito è <xref:System.IdentityModel.Selectors.X509CertificateValidator.ChainTrust%2A>.  
  
5. Se la proprietà <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> viene impostata su <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>, assegnare un'istanza della classe <xref:System.IdentityModel.Selectors.X509CertificateValidator> personalizzata alla proprietà <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A>.  
  
6. Se la proprietà <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> viene impostata su `ChainTrust` o su `PeerOrChainTrust`, impostare la proprietà <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.RevocationMode%2A> su un valore appropriato ottenuto dall'enumerazione <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>. Si noti che la modalità di revoca non viene utilizzata nelle modalità di convalida `PeerTrust` e `Custom`.  
  
7. Se necessario, assegnare un'istanza di una classe <xref:System.IdentityModel.Tokens.SamlSerializer> personalizzata alla proprietà <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.SamlSerializer%2A>. Per l'analisi delle asserzioni SAML personalizzate, ad esempio, è necessario un serializzatore SAML (Security Assertions Markup Language).  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-configuration"></a>Per impostare le proprietà di IssuedTokenServiceCredential nella configurazione  
  
1. Creare un `<issuedTokenAuthentication>` elemento come figlio di un elemento <`serviceCredentials`>.  
  
2. Impostare l' `allowUntrustedRsaIssuers` attributo `<issuedTokenAuthentication>` dell'elemento su in `true` caso di autenticazione di un token autocertificato, ad esempio una scheda CardSpace.  
  
3. Creare un elemento `<knownCertificates>` come figlio dell'elemento `<issuedTokenAuthentication>`.  
  
4. Creare zero o più elementi `<add>`come figli dell'elemento`<knownCertificates>`e specificare come individuare il certificato utilizzando gli attributi `storeLocation`, `storeName`, `x509FindType`,, findValue`findValue`e .  
  
5. Se necessario, impostare l' `samlSerializer` attributo dell'elemento <`issuedTokenAuthentication`> sul nome del tipo della classe personalizzata <xref:System.IdentityModel.Tokens.SamlSerializer> .  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente vengono impostate le proprietà di <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> nel codice.  
  
 [!code-csharp[C_FederatedService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedservice/cs/source.cs#2)]
 [!code-vb[C_FederatedService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedservice/vb/source.vb#2)]  
  
 Affinché un servizio federativo autentichi un client, per il token emesso devono essere osservate le condizioni seguenti:  
  
- Quando la firma digitale del token emesso utilizza un identificatore della chiave di sicurezza RSA, la proprietà <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> deve essere `true`.  
  
- Quando la firma del token emesso utilizza un numero di serie dell'emittente X.509, un identificatore della chiave del soggetto X.509 o un identificatore di sicurezza dell'identificazione personale X.509, il token emesso deve essere firmato da un certificato nella raccolta restituita dalla proprietà <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> della classe <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>.  
  
- Quando il token emesso viene firmato utilizzando un certificato X.509, il certificato deve eseguire la convalida secondo la semantica specificata dal valore della proprietà <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A>, indipendentemente dal fatto che il certificato sia stato inviato al componente come <xref:System.IdentityModel.Tokens.X509RawDataKeyIdentifierClause> oppure ottenuto dalla proprietà <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>. Per ulteriori informazioni sulla convalida del certificato X. 509, vedere [utilizzo dei certificati](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 Ad esempio, impostando la proprietà <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> su <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerTrust>, verrebbe autenticato un token emesso il cui certificato di firma si trova nell'archivio certificati `TrustedPeople`. In tal caso, impostare la proprietà <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.TrustedStoreLocation%2A> su <xref:System.Security.Cryptography.X509Certificates.StoreLocation.CurrentUser> o su <xref:System.Security.Cryptography.X509Certificates.StoreLocation.LocalMachine>. È possibile selezionare altre modalità, tra cui <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>. Quando si seleziona `Custom`, è necessario assegnare un'istanza della classe <xref:System.IdentityModel.Selectors.X509CertificateValidator> alla proprietà <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CustomCertificateValidator%2A>. Con il validator personalizzato è possibile convalidare i certificati mediante qualsiasi criterio. Per altre informazioni, vedere [Procedura: Creare un servizio che usa un validator](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)del certificato personalizzato.  
  
## <a name="see-also"></a>Vedere anche

- [Federazione](../../../../docs/framework/wcf/feature-details/federation.md)
- [Federazione e attendibilità](../../../../docs/framework/wcf/feature-details/federation-and-trust.md)
- [Esempio di federazione](../../../../docs/framework/wcf/samples/federation-sample.md)
- [Procedura: Disabilitare le sessioni protette in un'associazione WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
- [Procedura: Creare un'associazione WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [Procedura: Creazione di un client federato](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [Uso di certificati](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Modalità di autenticazione di SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)
