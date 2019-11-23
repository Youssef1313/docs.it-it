---
title: 'Procedura: proteggere endpoint dei metadati'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9f71b6ae-737c-4382-8d89-0a7b1c7e182b
ms.openlocfilehash: ee64e53f49e15059c91982f2e64879b9f4c76d78
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834683"
---
# <a name="how-to-secure-metadata-endpoints"></a>Procedura: proteggere endpoint dei metadati

È possibile che i metadati di un servizio contengano informazioni riservate sull'applicazione che un utente malintenzionato potrebbe sfruttare. Gli utenti del servizio, inoltre, potrebbero richiedere un meccanismo protetto per ottenere metadati sul servizio. È talvolta necessario, quindi, pubblicare i metadati utilizzando un endpoint protetto.

Gli endpoint dei metadati sono generalmente protetti utilizzando i meccanismi di sicurezza standard definiti in Windows Communication Foundation (WCF) per la protezione degli endpoint dell'applicazione. Per altre informazioni, vedere [Panoramica della sicurezza](security-overview.md).

In questo argomento vengono esaminati i passaggi che consentono di creare un endpoint protetto mediante un certificato SSL (Secure Sockets Layer) o, in altri termini, un endpoint HTTPS.

### <a name="to-create-a-secure-https-get-metadata-endpoint-in-code"></a>Per creare un endpoint di metadati HTTPS GET protetto nel codice

1. Configurare una porta con un certificato X.509 appropriato. Il certificato deve provenire da un'autorità attendibile e deve presentare l'utilizzo previsto "autorizzazione del servizio". È necessario utilizzare lo strumento HttpCfg.exe per allegare il certificato alla porta. Vedere [procedura: configurare una porta con un certificato SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).

    > [!IMPORTANT]
    > Il soggetto del certificato o il DNS (Domain Name System) deve corrispondere al nome del computer. È fondamentale perché uno dei primi passaggi eseguiti dal meccanismo HTTPS consiste nel verificare che il certificato sia emesso allo stesso URI (Uniform Resource Identifier) dell'indirizzo dal quale è richiamato.

2. Creare una nuova istanza della classe <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.

3. Impostare la proprietà <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> della classe <xref:System.ServiceModel.Description.ServiceMetadataBehavior> su `true`.

4. Impostare la proprietà <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> su un URL appropriato. Se si specifica un indirizzo assoluto, l'URL deve iniziare con lo schema "https://". Se si specifica un indirizzo relativo, è necessario fornire un indirizzo di base HTTPS per l'host del servizio. Se questa proprietà non è impostata, l'indirizzo predefinito è "" o direttamente l'indirizzo di base HTTPS per il servizio.

5. Aggiungere l'istanza alla raccolta di comportamenti restituito dalla proprietà <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> della classe <xref:System.ServiceModel.Description.ServiceDescription>, come indicato nel codice seguente.

    [!code-csharp[c_HowToSecureEndpoint#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#1)]
    [!code-vb[c_HowToSecureEndpoint#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#1)]

### <a name="to-create-a-secure-https-get-metadata-endpoint-in-configuration"></a>Per creare un endpoint di metadati HTTPS GET protetto nella configurazione

1. Aggiungere un [\<comportamenti >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elemento all'elemento [\<system. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) del file di configurazione per il servizio.

2. Aggiungere un elemento [\<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) all'elemento [\<behaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) .

3. Aggiungere un [\<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elemento all'elemento `<serviceBehaviors>`.

4. Impostare l'attributo `name` dell'elemento `<behavior>` su un valore appropriato. L'attributo `name` è obbligatorio. Nell'esempio seguente viene utilizzato il valore `mySvcBehavior`.

5. Aggiungere un [\<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) all'elemento `<behavior>`.

6. Impostare l'attributo `httpsGetEnabled` dell'elemento `<serviceMetadata>` su `true`.

7. Impostare l'attributo `httpsGetUrl` dell'elemento `<serviceMetadata>` su un valore appropriato. Se si specifica un indirizzo assoluto, l'URL deve iniziare con lo schema "https://". Se si specifica un indirizzo relativo, è necessario fornire un indirizzo di base HTTPS per l'host del servizio. Se questa proprietà non è impostata, l'indirizzo predefinito è "" o direttamente l'indirizzo di base HTTPS per il servizio.

8. Per utilizzare il comportamento con un servizio, impostare l'attributo `behaviorConfiguration` dell'elemento [\<service >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) sul valore dell'attributo Name dell'elemento Behavior. Nella configurazione seguente viene illustrato un esempio completo.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
     <system.serviceModel>
      <behaviors>
       <serviceBehaviors>
        <behavior name="mySvcBehavior">
         <serviceMetadata httpsGetEnabled="true"
              httpsGetUrl="https://localhost:8036/calcMetadata" />
        </behavior>
       </serviceBehaviors>
      </behaviors>
     <services>
      <service behaviorConfiguration="mySvcBehavior"
            name="Microsoft.Security.Samples.Calculator">
       <endpoint address="http://localhost:8037/ServiceModelSamples/calculator"
       binding="wsHttpBinding" bindingConfiguration=""
       contract="Microsoft.Security.Samples.ICalculator" />
      </service>
     </services>
    </system.serviceModel>
    </configuration>
    ```

## <a name="example"></a>Esempio

Nell'esempio seguente viene creata un'istanza della classe <xref:System.ServiceModel.ServiceHost> e viene aggiunto un endpoint. Il codice crea quindi un'istanza della classe <xref:System.ServiceModel.Description.ServiceMetadataBehavior> e imposta le proprietà per creare un punto dello scambio di metadati protetto.

[!code-csharp[c_HowToSecureEndpoint#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#0)]
[!code-vb[c_HowToSecureEndpoint#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#0)]

## <a name="compiling-the-code"></a>Compilazione del codice

Nel codice di esempio vengono utilizzati gli spazi dei nomi seguenti:

- <xref:System.ServiceModel?displayProperty=nameWithType>

- <xref:System.ServiceModel.Description?displayProperty=nameWithType>

## <a name="see-also"></a>Vedere anche

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>
- [Procedura: Configurare una porta con un certificato SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [Uso di certificati](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Considerazioni sulla sicurezza con i metadati](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
- [Securing Services and Clients](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
