---
title: Elemento <webProxyScript> (impostazioni di rete)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webProxyScript
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/webProxyScript
helpviewer_keywords:
- <webProxyScript> element
- webProxyScript element
ms.assetid: a13c26db-6218-4af3-9696-38f24b23bfac
ms.openlocfilehash: 2abab3de2965c31c11d9acaf7b78f3a668563506
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697447"
---
# <a name="webproxyscript-element-network-settings"></a><span data-ttu-id="8e339-102">Elemento > \<webProxyScript (impostazioni di rete)</span><span class="sxs-lookup"><span data-stu-id="8e339-102">\<webProxyScript> Element (Network Settings)</span></span>
<span data-ttu-id="8e339-103">Configura le caratteristiche dello script utilizzato per individuare i proxy Web.</span><span class="sxs-lookup"><span data-stu-id="8e339-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  
  
[<span data-ttu-id="8e339-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="8e339-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="8e339-105">&nbsp; @ no__t-1[ **@no__t -4system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="8e339-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="8e339-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<settings >** ](settings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="8e339-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)</span></span>  
<span data-ttu-id="8e339-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<webProxyScript >**</span><span class="sxs-lookup"><span data-stu-id="8e339-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webProxyScript>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e339-108">Sintassi</span><span class="sxs-lookup"><span data-stu-id="8e339-108">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8e339-109">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="8e339-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8e339-110">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="8e339-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8e339-111">Attributi</span><span class="sxs-lookup"><span data-stu-id="8e339-111">Attributes</span></span>  
  
|<span data-ttu-id="8e339-112">Attributo</span><span class="sxs-lookup"><span data-stu-id="8e339-112">Attribute</span></span>|<span data-ttu-id="8e339-113">Descrizione</span><span class="sxs-lookup"><span data-stu-id="8e339-113">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="8e339-114">Specifica il tempo massimo per il download dello script in ore, minuti e secondi.</span><span class="sxs-lookup"><span data-stu-id="8e339-114">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="8e339-115">Il valore predefinito è un minuto.</span><span class="sxs-lookup"><span data-stu-id="8e339-115">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8e339-116">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="8e339-116">Child Elements</span></span>  
 <span data-ttu-id="8e339-117">No.</span><span class="sxs-lookup"><span data-stu-id="8e339-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8e339-118">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="8e339-118">Parent Elements</span></span>  
  
|<span data-ttu-id="8e339-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="8e339-119">Element</span></span>|<span data-ttu-id="8e339-120">Descrizione</span><span class="sxs-lookup"><span data-stu-id="8e339-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8e339-121">Impostazioni</span><span class="sxs-lookup"><span data-stu-id="8e339-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="8e339-122">Configura le opzioni di rete di base per lo spazio dei nomi <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="8e339-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e339-123">Note</span><span class="sxs-lookup"><span data-stu-id="8e339-123">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="8e339-124">File di configurazione</span><span class="sxs-lookup"><span data-stu-id="8e339-124">Configuration Files</span></span>  
 <span data-ttu-id="8e339-125">Questo elemento può essere usato nel file di configurazione dell'applicazione o nel file di configurazione del computer (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="8e339-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e339-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8e339-126">See also</span></span>

- [<span data-ttu-id="8e339-127">Schema delle impostazioni di rete</span><span class="sxs-lookup"><span data-stu-id="8e339-127">Network Settings Schema</span></span>](index.md)
