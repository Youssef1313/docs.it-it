---
title: 'Procedura: Configurare un emittente locale'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 15263371-514e-4ea6-90fb-14b4939154cd
ms.openlocfilehash: 0028a0522447588ee0fb183b5b2f93d334a7b2b2
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972072"
---
# <a name="how-to-configure-a-local-issuer"></a>Procedura: Configurare un emittente locale

In questo argomento viene illustrato come configurare un client per utilizzare un emittente locale per i token emessi.

Spesso, quando un client comunica con un servizio federato, il servizio specifica l'indirizzo del servizio token di sicurezza previsto per l'emissione del token che il client utilizzerà per autenticarsi presso il servizio federato. In alcune situazioni, il client può essere configurato per l'uso di un' *autorità emittente locale*.

Windows Communication Foundation (WCF) usa un'autorità emittente locale nei casi in cui l'indirizzo dell'emittente di un'associazione federata `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` è `null`o. In tali casi, è necessario configurare la classe <xref:System.ServiceModel.Description.ClientCredentials> con l'indirizzo dell'emittente locale e con l'associazione da utilizzare per comunicare con tale emittente.

> [!NOTE]
> Se la <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> `ClientCredentials` proprietà della classe è impostata su `true`, non viene specificato un indirizzo dell'emittente locale [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) e l'indirizzo dell'autorità emittente specificato dalla > WSFederationHttpBinding o da un'altra associazione federata è `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self` ,`http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous`o è`null`, viene usato l'emittente di Windows CardSpace.

## <a name="to-configure-the-local-issuer-in-code"></a>Per configurare l'emittente locale nel codice

1. Creare una variabile di tipo <xref:System.ServiceModel.Security.IssuedTokenClientCredential>.

2. Impostare la variabile sull'istanza restituita dalla proprietà <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> della classe `ClientCredentials`. L'istanza viene restituita dalla proprietà <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> del client (ereditata da <xref:System.ServiceModel.ClientBase%601>) o dalla proprietà <xref:System.ServiceModel.ChannelFactory.Credentials%2A> della classe <xref:System.ServiceModel.ChannelFactory>:

     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]

3. Impostare la proprietà <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> su una nuova istanza di <xref:System.ServiceModel.EndpointAddress>, con l'indirizzo dell'emittente locale come argomento per il costruttore.

     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]

     In alternativa, creare una nuova istanza <xref:System.Uri> come argomento per il costruttore.

     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]

     Il `addressHeaders` parametro è una matrice di <xref:System.ServiceModel.Channels.AddressHeader> istanze, come illustrato.

     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]

4. Impostare l'associazione per l'emittente locale utilizzando la <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> proprietà.

     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]

5. facoltativo. Aggiungere i comportamenti dell'endpoint configurati per l'emittente locale aggiungendo tali comportamenti alla raccolta restituita dalla proprietà <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A>.

     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]

## <a name="to-configure-the-local-issuer-in-configuration"></a>Per configurare l'emittente locale nella configurazione

1. Creare un [ \<elemento > LocalIssuer](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md) come figlio dell' [ \<elemento > IssuedToken](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) che è figlio dell' [ \<elemento ClientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) in un comportamento dell'endpoint.

2. Impostare l'attributo `address` sull'indirizzo dell'emittente locale che accetterà richieste del token.

3. Impostare gli attributi `binding` e `bindingConfiguration` su valori che fanno riferimento all'associazione appropriata da utilizzare durante la comunicazione con l'endpoint dell'emittente locale.

4. facoltativo. Impostare l' [ \<elemento Identity >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) come figlio dell'elemento <`localIssuer`> e specificare le informazioni sull'identità per l'emittente locale.

5. facoltativo. Impostare le [ \<intestazioni >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) elemento come figlio dell'elemento <`localIssuer`> e specificare intestazioni aggiuntive necessarie per indirizzare correttamente l'emittente locale.

## <a name="net-framework-security"></a>Sicurezza di .NET Framework

Si noti che, se per una determinata associazione vengono specificati l'indirizzo dell'emittente e l'associazione, l'emittente locale non verrà utilizzato per gli endpoint che utilizzano tale associazione. Per i client che prevedono di utilizzare sempre l'emittente locale, è necessario accertarsi di non utilizzare tale associazione o di modificare l'associazione in modo che l'indirizzo dell'emittente sia `null`.

## <a name="see-also"></a>Vedere anche

- [Procedura: Configurare le credenziali in un Servizio federativo](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [Procedura: Creazione di un client federato](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [Procedura: Creare un'associazione WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
