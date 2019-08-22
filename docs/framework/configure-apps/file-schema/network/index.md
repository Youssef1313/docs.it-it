---
title: Schema delle impostazioni di rete
ms.date: 03/30/2017
helpviewer_keywords:
- elements [.NET Framework], network configuration elements
- sending data, network configuration elements
- receiving data, network configuration elements
- configuration settings [.NET Framework], networks
- Internet, network configuration elements
- network configuration elements
- network settings
- connections [.NET Framework], network configuration elements
- network resources, network configuration elements
ms.assetid: f1de5a0f-76c5-4833-819f-5222b8146340
ms.openlocfilehash: 0f5d762a2b688bebcb7c027be6c639b6d64c069d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664113"
---
# <a name="network-settings-schema"></a><span data-ttu-id="7b6ff-102">Schema delle impostazioni di rete</span><span class="sxs-lookup"><span data-stu-id="7b6ff-102">Network Settings Schema</span></span>
<span data-ttu-id="7b6ff-103">Tramite le impostazioni di rete viene specificata la modalità di connessione a Internet di .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7b6ff-103">Network settings specify how the .NET Framework connects to the Internet.</span></span> <span data-ttu-id="7b6ff-104">La tabella seguente descrive la funzione di ogni elemento di configurazione figlio dell'[elemento \<system.Net> (impostazioni di rete)](system-net-element-network-settings.md).</span><span class="sxs-lookup"><span data-stu-id="7b6ff-104">The following table describes the function of each child configuration element under the [\<system.Net> Element (Network Settings)](system-net-element-network-settings.md).</span></span>  
  
|<span data-ttu-id="7b6ff-105">Elemento</span><span class="sxs-lookup"><span data-stu-id="7b6ff-105">Element</span></span>|<span data-ttu-id="7b6ff-106">Descrizione</span><span class="sxs-lookup"><span data-stu-id="7b6ff-106">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7b6ff-107">Elemento \<authenticationModules> (impostazioni di rete)</span><span class="sxs-lookup"><span data-stu-id="7b6ff-107">\<authenticationModules> Element (Network Settings)</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="7b6ff-108">Specifica i moduli usati per autenticare le richieste Internet.</span><span class="sxs-lookup"><span data-stu-id="7b6ff-108">Specifies the modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="7b6ff-109">Elemento \<connectionManagement> (impostazioni di rete)</span><span class="sxs-lookup"><span data-stu-id="7b6ff-109">\<connectionManagement> Element (Network Settings)</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="7b6ff-110">Specifica il numero massimo di connessioni a host Internet.</span><span class="sxs-lookup"><span data-stu-id="7b6ff-110">Specifies the maximum number of connections to Internet hosts.</span></span>|  
|[<span data-ttu-id="7b6ff-111">Elemento \<defaultProxy> (impostazioni di rete)</span><span class="sxs-lookup"><span data-stu-id="7b6ff-111">\<defaultProxy> Element (Network Settings)</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="7b6ff-112">Specifica il server proxy usato per le richieste HTTP indirizzate a Internet.</span><span class="sxs-lookup"><span data-stu-id="7b6ff-112">Specifies the proxy server used for HTTP requests to the Internet.</span></span>|  
|[<span data-ttu-id="7b6ff-113">Elemento \<mailSettings> (impostazioni di rete)</span><span class="sxs-lookup"><span data-stu-id="7b6ff-113">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="7b6ff-114">Contiene le impostazioni per le opzioni di invio della posta elettronica.</span><span class="sxs-lookup"><span data-stu-id="7b6ff-114">Contains settings for mail sending options.</span></span>|  
|[<span data-ttu-id="7b6ff-115">Elemento \<requestCaching> (impostazioni di rete)</span><span class="sxs-lookup"><span data-stu-id="7b6ff-115">\<requestCaching> Element (Network Settings)</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="7b6ff-116">Controlla il meccanismo di memorizzazione nella cache per le richieste di rete.</span><span class="sxs-lookup"><span data-stu-id="7b6ff-116">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="7b6ff-117">Elemento \<webRequestModules> (impostazioni di rete)</span><span class="sxs-lookup"><span data-stu-id="7b6ff-117">\<webRequestModules> Element (Network Settings)</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="7b6ff-118">Specifica i moduli usati per richiedere informazioni da host Internet.</span><span class="sxs-lookup"><span data-stu-id="7b6ff-118">Specifies the modules used to request information from Internet hosts.</span></span>|  
  
 <span data-ttu-id="7b6ff-119">Tramite le impostazioni URI viene specificata la modalità di gestione da parte di .NET Framework degli indirizzi Web espressi tramite Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="7b6ff-119">Uri settings specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span> <span data-ttu-id="7b6ff-120">La tabella seguente descrive la funzione di ogni elemento di configurazione figlio dell'[elemento \<Uri> (impostazioni URI)](uri-element-uri-settings.md).</span><span class="sxs-lookup"><span data-stu-id="7b6ff-120">The following table describes the function of each child configuration element under the [\<Uri> Element (Uri Settings)](uri-element-uri-settings.md).</span></span>  
  
|<span data-ttu-id="7b6ff-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="7b6ff-121">Element</span></span>|<span data-ttu-id="7b6ff-122">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="7b6ff-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7b6ff-123">Elemento \<idn> (impostazioni URI)</span><span class="sxs-lookup"><span data-stu-id="7b6ff-123">\<idn> Element (Uri Settings)</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="7b6ff-124">Specifica se l'analisi IDN (Internationalized Domain Name) viene applicata ai nomi di dominio.</span><span class="sxs-lookup"><span data-stu-id="7b6ff-124">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="7b6ff-125">Elemento \<iriParsing> (impostazioni URI)</span><span class="sxs-lookup"><span data-stu-id="7b6ff-125">\<iriParsing> Element (Uri Settings)</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="7b6ff-126">Specifica se l'analisi IRI (International Resource Identifier) viene applicata a un <xref:System.Uri> e se devono essere applicate le regole di analisi IRI.</span><span class="sxs-lookup"><span data-stu-id="7b6ff-126">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="7b6ff-127">Elemento \<schemeSettings> (impostazioni URI)</span><span class="sxs-lookup"><span data-stu-id="7b6ff-127">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="7b6ff-128">Specifica come verrà analizzato un <xref:System.Uri> per schemi specifici.</span><span class="sxs-lookup"><span data-stu-id="7b6ff-128">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7b6ff-129">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7b6ff-129">See also</span></span>

- [<span data-ttu-id="7b6ff-130">Configurazione di applicazioni Internet</span><span class="sxs-lookup"><span data-stu-id="7b6ff-130">Configuring Internet Applications</span></span>](../../../network-programming/configuring-internet-applications.md)
- [<span data-ttu-id="7b6ff-131">Schema dei file di configurazione</span><span class="sxs-lookup"><span data-stu-id="7b6ff-131">Configuration File Schema</span></span>](../index.md)
