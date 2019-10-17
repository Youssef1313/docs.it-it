---
title: Configurazione dei servizi WCF
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [WCF]
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
ms.openlocfilehash: 4fcf01c9f65f2b1bd11462a6f7d61b3551f37b86
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320656"
---
# <a name="configuring-wcf-services"></a><span data-ttu-id="18454-102">Configurazione dei servizi WCF</span><span class="sxs-lookup"><span data-stu-id="18454-102">Configuring WCF services</span></span>

<span data-ttu-id="18454-103">Dopo aver progettato e implementato il contratto di servizio, è possibile configurare il servizio.</span><span class="sxs-lookup"><span data-stu-id="18454-103">Once you have designed and implemented your service contract, you are ready to configure your service.</span></span> <span data-ttu-id="18454-104">Questa è la fase in cui si definisce e si personalizza il modo in cui il servizio viene esposto ai client, inclusa l'indicazione dell'indirizzo, del trasporto e della codifica dei messaggi usata per inviare e ricevere messaggi e del tipo di sicurezza richiesto.</span><span class="sxs-lookup"><span data-stu-id="18454-104">This is where you define and customize how your service is exposed to clients, including specifying the address where it can be found, the transport and message encoding it uses to send and receive messages, and the type of security it requires.</span></span>  
  
 <span data-ttu-id="18454-105">La configurazione specificata in questo punto include tutti i modi, imperativo nel codice o mediante un file di configurazione, in cui è possibile definire e personalizzare i vari aspetti di un servizio, ad esempio la specifica degli indirizzi dell'endpoint, dei trasporti usati e degli schemi di sicurezza.</span><span class="sxs-lookup"><span data-stu-id="18454-105">Configuration as used here includes all the ways, imperatively in code or by using a configuration file, in which you can define and customize the various aspects of a service, such as specifying its endpoint addresses, the transports used, and its security schemes.</span></span> <span data-ttu-id="18454-106">In pratica, la scrittura della configurazione è una parte essenziale della programmazione di applicazioni WCF.</span><span class="sxs-lookup"><span data-stu-id="18454-106">In practice, writing configuration is a major part of programming WCF applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="18454-107">Contenuto della sezione</span><span class="sxs-lookup"><span data-stu-id="18454-107">In This Section</span></span>  
 [<span data-ttu-id="18454-108">Configurazione semplificata</span><span class="sxs-lookup"><span data-stu-id="18454-108">Simplified Configuration</span></span>](simplified-configuration.md)  
 <span data-ttu-id="18454-109">A partire da [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], WCF viene fornita con un nuovo modello di configurazione predefinito che semplifica i requisiti di configurazione di WCF.</span><span class="sxs-lookup"><span data-stu-id="18454-109">Starting with [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], WCF comes with a new default configuration model that simplifies WCF configuration requirements.</span></span> <span data-ttu-id="18454-110">Se non si fornisce alcuna configurazione WCF per un determinato servizio, il runtime configura automaticamente il servizio con endpoint, associazioni e comportamenti predefiniti.</span><span class="sxs-lookup"><span data-stu-id="18454-110">If you do not provide any WCF configuration for a particular service, the runtime automatically configures your service with default endpoints, bindings, and behaviors.</span></span>  
  
 [<span data-ttu-id="18454-111">Configurazione dei servizi tramite file di configurazione</span><span class="sxs-lookup"><span data-stu-id="18454-111">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)  
 <span data-ttu-id="18454-112">Un servizio Windows Communication Foundation (WCF) è configurabile mediante la tecnologia di configurazione .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="18454-112">A Windows Communication Foundation (WCF) service is configurable using the .NET Framework configuration technology.</span></span> <span data-ttu-id="18454-113">In genere, gli elementi XML vengono aggiunti al file Web. config per un sito Internet Information Services (IIS) che ospita un servizio WCF.</span><span class="sxs-lookup"><span data-stu-id="18454-113">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a WCF service.</span></span> <span data-ttu-id="18454-114">Gli elementi consentono di modificare i dettagli, ad esempio gli indirizzi dell'endpoint (gli indirizzi effettivi usati per comunicare con il servizio) per i singoli computer.</span><span class="sxs-lookup"><span data-stu-id="18454-114">The elements allow you to change details, such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span>  
  
 [<span data-ttu-id="18454-115">Associazioni</span><span class="sxs-lookup"><span data-stu-id="18454-115">Bindings</span></span>](bindings.md)  
 <span data-ttu-id="18454-116">Inoltre, WCF include diverse configurazioni comuni fornite dal sistema sotto forma di binding che consentono di selezionare rapidamente le funzionalità di base per la comunicazione di un client e di un servizio, ad esempio i trasporti, la sicurezza e la codifica dei messaggi utilizzati.</span><span class="sxs-lookup"><span data-stu-id="18454-116">In addition, WCF includes several system-provided common configurations in the form of bindings that allow you to quickly select the most basic features for how a client and service communicate, such as the transports, security, and message encodings used.</span></span>  
  
 [<span data-ttu-id="18454-117">Endpoint</span><span class="sxs-lookup"><span data-stu-id="18454-117">Endpoints</span></span>](endpoints.md)  
 <span data-ttu-id="18454-118">Tutte le comunicazioni con un servizio WCF avvengono tramite gli *endpoint* del servizio.</span><span class="sxs-lookup"><span data-stu-id="18454-118">All communication with a WCF service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="18454-119">Gli endpoint contengono il contratto, le informazioni di configurazione specificate nelle associazioni e gli indirizzi che indicano dove si trova il servizio o dove ottenere informazioni sul servizio.</span><span class="sxs-lookup"><span data-stu-id="18454-119">Endpoints contain the contract, the configuration information that is specified in the bindings, and the addresses that indicate where to find the service or where to obtain information about the service.</span></span>  
  
 [<span data-ttu-id="18454-120">Protezione dei servizi</span><span class="sxs-lookup"><span data-stu-id="18454-120">Securing Services</span></span>](securing-services.md)  
 <span data-ttu-id="18454-121">Grazie a WCF e ai meccanismi di sicurezza esistenti, è possibile implementare la riservatezza, l'integrità, l'autenticazione e l'autorizzazione in qualsiasi servizio.</span><span class="sxs-lookup"><span data-stu-id="18454-121">Using WCF and existing security mechanisms, you can implement confidentiality, integrity, authentication, and authorization into any service.</span></span> <span data-ttu-id="18454-122">È inoltre possibile controllare le attività di sicurezza riuscite e non riuscite.</span><span class="sxs-lookup"><span data-stu-id="18454-122">You can also audit for security successes and failures.</span></span>  
  
 [<span data-ttu-id="18454-123">Creazione di servizi interoperativi WS-I Basic Profile 1.1</span><span class="sxs-lookup"><span data-stu-id="18454-123">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>](./creating-ws-i-basic-profile-1-1-interoperable-services.md)  
 <span data-ttu-id="18454-124">I requisiti per la distribuzione di un servizio che sia interoperativo con i servizi e i client su qualsiasi altra piattaforma o sistema operativo sono delineati nella specifica WS-I Basic Profile 1.1.</span><span class="sxs-lookup"><span data-stu-id="18454-124">The requirements for deploying a service that is interoperable with services and clients on any other platform or operating system are outlined in the WS-I Basic Profile 1.1 specification.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="18454-125">Reference</span><span class="sxs-lookup"><span data-stu-id="18454-125">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## <a name="related-sections"></a><span data-ttu-id="18454-126">Sezioni correlate</span><span class="sxs-lookup"><span data-stu-id="18454-126">Related Sections</span></span>  
 [<span data-ttu-id="18454-127">Ciclo di vita della programmazione di base</span><span class="sxs-lookup"><span data-stu-id="18454-127">Basic Programming Lifecycle</span></span>](basic-programming-lifecycle.md)  
  
 [<span data-ttu-id="18454-128">Progettazione e implementazione di servizi</span><span class="sxs-lookup"><span data-stu-id="18454-128">Designing and Implementing Services</span></span>](designing-and-implementing-services.md)  
  
 [<span data-ttu-id="18454-129">Servizi di hosting</span><span class="sxs-lookup"><span data-stu-id="18454-129">Hosting Services</span></span>](hosting-services.md)  
  
 [<span data-ttu-id="18454-130">Creazione di client</span><span class="sxs-lookup"><span data-stu-id="18454-130">Building Clients</span></span>](building-clients.md)  
  
 [<span data-ttu-id="18454-131">Introduzione all'estendibilità</span><span class="sxs-lookup"><span data-stu-id="18454-131">Introduction to Extensibility</span></span>](introduction-to-extensibility.md)  
  
 [<span data-ttu-id="18454-132">Amministrazione e diagnostica</span><span class="sxs-lookup"><span data-stu-id="18454-132">Administration and Diagnostics</span></span>](./diagnostics/index.md)  
  
## <a name="see-also"></a><span data-ttu-id="18454-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="18454-133">See also</span></span>

- [<span data-ttu-id="18454-134">Programmazione WCF di base</span><span class="sxs-lookup"><span data-stu-id="18454-134">Basic WCF Programming</span></span>](basic-wcf-programming.md)
- [<span data-ttu-id="18454-135">Panoramica dei concetti</span><span class="sxs-lookup"><span data-stu-id="18454-135">Conceptual Overview</span></span>](conceptual-overview.md)
- [<span data-ttu-id="18454-136">Dettagli delle funzionalità di WCF</span><span class="sxs-lookup"><span data-stu-id="18454-136">WCF Feature Details</span></span>](./feature-details/index.md)
