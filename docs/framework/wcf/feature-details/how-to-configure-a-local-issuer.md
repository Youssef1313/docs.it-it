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
# <a name="how-to-configure-a-local-issuer"></a><span data-ttu-id="fc94c-102">Procedura: Configurare un emittente locale</span><span class="sxs-lookup"><span data-stu-id="fc94c-102">How to: Configure a Local Issuer</span></span>

<span data-ttu-id="fc94c-103">In questo argomento viene illustrato come configurare un client per utilizzare un emittente locale per i token emessi.</span><span class="sxs-lookup"><span data-stu-id="fc94c-103">This topic describes how to configure a client to use a local issuer for issued tokens.</span></span>

<span data-ttu-id="fc94c-104">Spesso, quando un client comunica con un servizio federato, il servizio specifica l'indirizzo del servizio token di sicurezza previsto per l'emissione del token che il client utilizzerà per autenticarsi presso il servizio federato.</span><span class="sxs-lookup"><span data-stu-id="fc94c-104">Often, when a client communicates with a federated service, the service specifies the address of the security token service that is expected to issue the token the client will use to authenticate itself to the federated service.</span></span> <span data-ttu-id="fc94c-105">In alcune situazioni, il client può essere configurato per l'uso di un' *autorità emittente locale*.</span><span class="sxs-lookup"><span data-stu-id="fc94c-105">In certain situations, the client may be configured to use a *local issuer*.</span></span>

<span data-ttu-id="fc94c-106">Windows Communication Foundation (WCF) usa un'autorità emittente locale nei casi in cui l'indirizzo dell'emittente di un'associazione federata `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` è `null`o.</span><span class="sxs-lookup"><span data-stu-id="fc94c-106">Windows Communication Foundation (WCF) uses a local issuer in cases where the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`.</span></span> <span data-ttu-id="fc94c-107">In tali casi, è necessario configurare la classe <xref:System.ServiceModel.Description.ClientCredentials> con l'indirizzo dell'emittente locale e con l'associazione da utilizzare per comunicare con tale emittente.</span><span class="sxs-lookup"><span data-stu-id="fc94c-107">In such cases, you must configure the <xref:System.ServiceModel.Description.ClientCredentials> with the address of the local issuer and the binding to use to communicate with that issuer.</span></span>

> [!NOTE]
> <span data-ttu-id="fc94c-108">Se la <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> `ClientCredentials` proprietà della classe è impostata su `true`, non viene specificato un indirizzo dell'emittente locale [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) e l'indirizzo dell'autorità emittente specificato dalla > WSFederationHttpBinding o da un'altra associazione federata è `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self` ,`http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous`o è`null`, viene usato l'emittente di Windows CardSpace.</span><span class="sxs-lookup"><span data-stu-id="fc94c-108">If the <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> property of the `ClientCredentials` class is set to `true`, a local issuer address is not specified, and the issuer address specified by the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) or other federated binding is `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self`, `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous`, or is `null`, then the Windows CardSpace issuer is used.</span></span>

## <a name="to-configure-the-local-issuer-in-code"></a><span data-ttu-id="fc94c-109">Per configurare l'emittente locale nel codice</span><span class="sxs-lookup"><span data-stu-id="fc94c-109">To configure the local issuer in code</span></span>

1. <span data-ttu-id="fc94c-110">Creare una variabile di tipo <xref:System.ServiceModel.Security.IssuedTokenClientCredential>.</span><span class="sxs-lookup"><span data-stu-id="fc94c-110">Create a variable of type <xref:System.ServiceModel.Security.IssuedTokenClientCredential></span></span>

2. <span data-ttu-id="fc94c-111">Impostare la variabile sull'istanza restituita dalla proprietà <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> della classe `ClientCredentials`.</span><span class="sxs-lookup"><span data-stu-id="fc94c-111">Set the variable to the instance returned from the <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> property of the `ClientCredentials` class.</span></span> <span data-ttu-id="fc94c-112">L'istanza viene restituita dalla proprietà <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> del client (ereditata da <xref:System.ServiceModel.ClientBase%601>) o dalla proprietà <xref:System.ServiceModel.ChannelFactory.Credentials%2A> della classe <xref:System.ServiceModel.ChannelFactory>:</span><span class="sxs-lookup"><span data-stu-id="fc94c-112">That instance is returned by the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the client (inherited from <xref:System.ServiceModel.ClientBase%601>) or the <xref:System.ServiceModel.ChannelFactory.Credentials%2A> property of the <xref:System.ServiceModel.ChannelFactory>:</span></span>

     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]

3. <span data-ttu-id="fc94c-113">Impostare la proprietà <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> su una nuova istanza di <xref:System.ServiceModel.EndpointAddress>, con l'indirizzo dell'emittente locale come argomento per il costruttore.</span><span class="sxs-lookup"><span data-stu-id="fc94c-113">Set the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> property to a new instance of the <xref:System.ServiceModel.EndpointAddress>, with the address of the local issuer as an argument to the constructor.</span></span>

     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]

     <span data-ttu-id="fc94c-114">In alternativa, creare una nuova istanza <xref:System.Uri> come argomento per il costruttore.</span><span class="sxs-lookup"><span data-stu-id="fc94c-114">Alternatively, create a new <xref:System.Uri> instance as an argument to the constructor.</span></span>

     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]

     <span data-ttu-id="fc94c-115">Il `addressHeaders` parametro è una matrice di <xref:System.ServiceModel.Channels.AddressHeader> istanze, come illustrato.</span><span class="sxs-lookup"><span data-stu-id="fc94c-115">The `addressHeaders` parameter is an array of <xref:System.ServiceModel.Channels.AddressHeader> instances, as shown.</span></span>

     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]

4. <span data-ttu-id="fc94c-116">Impostare l'associazione per l'emittente locale utilizzando la <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> proprietà.</span><span class="sxs-lookup"><span data-stu-id="fc94c-116">Set the binding for the local issuer using the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> property.</span></span>

     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]

5. <span data-ttu-id="fc94c-117">facoltativo.</span><span class="sxs-lookup"><span data-stu-id="fc94c-117">Optional.</span></span> <span data-ttu-id="fc94c-118">Aggiungere i comportamenti dell'endpoint configurati per l'emittente locale aggiungendo tali comportamenti alla raccolta restituita dalla proprietà <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A>.</span><span class="sxs-lookup"><span data-stu-id="fc94c-118">Add configured endpoint behaviors for the local issuer by adding such behaviors to the collection returned by the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> property.</span></span>

     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]

## <a name="to-configure-the-local-issuer-in-configuration"></a><span data-ttu-id="fc94c-119">Per configurare l'emittente locale nella configurazione</span><span class="sxs-lookup"><span data-stu-id="fc94c-119">To configure the local issuer in configuration</span></span>

1. <span data-ttu-id="fc94c-120">Creare un [ \<elemento > LocalIssuer](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md) come figlio dell' [ \<elemento > IssuedToken](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) che è figlio dell' [ \<elemento ClientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) in un comportamento dell'endpoint.</span><span class="sxs-lookup"><span data-stu-id="fc94c-120">Create a [\<localIssuer>](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md) element as a child of the [\<issuedToken>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) element that is itself a child of the [\<clientCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element in an endpoint behavior.</span></span>

2. <span data-ttu-id="fc94c-121">Impostare l'attributo `address` sull'indirizzo dell'emittente locale che accetterà richieste del token.</span><span class="sxs-lookup"><span data-stu-id="fc94c-121">Set the `address` attribute to the address of the local issuer that will accept token requests.</span></span>

3. <span data-ttu-id="fc94c-122">Impostare gli attributi `binding` e `bindingConfiguration` su valori che fanno riferimento all'associazione appropriata da utilizzare durante la comunicazione con l'endpoint dell'emittente locale.</span><span class="sxs-lookup"><span data-stu-id="fc94c-122">Set the `binding` and `bindingConfiguration` attributes to values that reference the appropriate binding to use when communicating with the local issuer endpoint.</span></span>

4. <span data-ttu-id="fc94c-123">facoltativo.</span><span class="sxs-lookup"><span data-stu-id="fc94c-123">Optional.</span></span> <span data-ttu-id="fc94c-124">Impostare l' [ \<elemento Identity >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) come figlio dell'elemento <`localIssuer`> e specificare le informazioni sull'identità per l'emittente locale.</span><span class="sxs-lookup"><span data-stu-id="fc94c-124">Set the [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) element as a child of the <`localIssuer`> element and specify identity information for the local issuer.</span></span>

5. <span data-ttu-id="fc94c-125">facoltativo.</span><span class="sxs-lookup"><span data-stu-id="fc94c-125">Optional.</span></span> <span data-ttu-id="fc94c-126">Impostare le [ \<intestazioni >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) elemento come figlio dell'elemento <`localIssuer`> e specificare intestazioni aggiuntive necessarie per indirizzare correttamente l'emittente locale.</span><span class="sxs-lookup"><span data-stu-id="fc94c-126">Set the [\<headers>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) element as a child of the <`localIssuer`> element and specify additional headers that are required in order to correctly address the local issuer.</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="fc94c-127">Sicurezza di .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fc94c-127">.NET Framework Security</span></span>

<span data-ttu-id="fc94c-128">Si noti che, se per una determinata associazione vengono specificati l'indirizzo dell'emittente e l'associazione, l'emittente locale non verrà utilizzato per gli endpoint che utilizzano tale associazione.</span><span class="sxs-lookup"><span data-stu-id="fc94c-128">Note that if an issuer address and binding are specified for a given binding, the local issuer is not used for endpoints that use that binding.</span></span> <span data-ttu-id="fc94c-129">Per i client che prevedono di utilizzare sempre l'emittente locale, è necessario accertarsi di non utilizzare tale associazione o di modificare l'associazione in modo che l'indirizzo dell'emittente sia `null`.</span><span class="sxs-lookup"><span data-stu-id="fc94c-129">Clients who expect to always use the local issuer should ensure that they do not use such a binding or that they modify the binding so that the issuer address is `null`.</span></span>

## <a name="see-also"></a><span data-ttu-id="fc94c-130">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="fc94c-130">See also</span></span>

- [<span data-ttu-id="fc94c-131">Procedura: Configurare le credenziali in un Servizio federativo</span><span class="sxs-lookup"><span data-stu-id="fc94c-131">How to: Configure Credentials on a Federation Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="fc94c-132">Procedura: Creazione di un client federato</span><span class="sxs-lookup"><span data-stu-id="fc94c-132">How to: Create a Federated Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="fc94c-133">Procedura: Creare un'associazione WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="fc94c-133">How to: Create a WSFederationHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
