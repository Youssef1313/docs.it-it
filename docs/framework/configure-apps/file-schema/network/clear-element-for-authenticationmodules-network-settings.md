---
title: Elemento <clear> per authenticationModules (impostazioni di rete)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, authenticationModules
- <authenticationModules>, clear element
- <clear> element, authenticationModules
- authenticationModules, clear element
ms.assetid: dc522c45-4a80-4831-8955-f7b68a47edfd
ms.openlocfilehash: 12ac146926103b40073d34f48895b0645c8a8ed2
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659472"
---
# <a name="clear-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="5385f-102">\<Cancella > elemento per authenticationModules (impostazioni di rete)</span><span class="sxs-lookup"><span data-stu-id="5385f-102">\<clear> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="5385f-103">Cancella tutti i moduli di autenticazione dall'applicazione.</span><span class="sxs-lookup"><span data-stu-id="5385f-103">Clears all authentication modules from the application.</span></span>  
  
 <span data-ttu-id="5385f-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="5385f-104">\<configuration></span></span>  
<span data-ttu-id="5385f-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="5385f-105">\<system.net></span></span>  
<span data-ttu-id="5385f-106">\<authenticationModules></span><span class="sxs-lookup"><span data-stu-id="5385f-106">\<authenticationModules></span></span>  
<span data-ttu-id="5385f-107">\<Cancella ></span><span class="sxs-lookup"><span data-stu-id="5385f-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5385f-108">Sintassi</span><span class="sxs-lookup"><span data-stu-id="5385f-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5385f-109">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="5385f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5385f-110">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="5385f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5385f-111">Attributi</span><span class="sxs-lookup"><span data-stu-id="5385f-111">Attributes</span></span>  
 <span data-ttu-id="5385f-112">Nessuno.</span><span class="sxs-lookup"><span data-stu-id="5385f-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5385f-113">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="5385f-113">Child Elements</span></span>  
 <span data-ttu-id="5385f-114">Nessuno.</span><span class="sxs-lookup"><span data-stu-id="5385f-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5385f-115">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="5385f-115">Parent Elements</span></span>  
  
|<span data-ttu-id="5385f-116">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="5385f-116">**Element**</span></span>|<span data-ttu-id="5385f-117">**Descrizione**</span><span class="sxs-lookup"><span data-stu-id="5385f-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5385f-118">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="5385f-118">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="5385f-119">Specifica i moduli usati per autenticare le richieste di rete.</span><span class="sxs-lookup"><span data-stu-id="5385f-119">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5385f-120">Note</span><span class="sxs-lookup"><span data-stu-id="5385f-120">Remarks</span></span>  
 <span data-ttu-id="5385f-121">L' `clear` elemento rimuove tutti i moduli di autenticazione definiti in precedenza nel file di configurazione o a un livello superiore nella gerarchia di configurazione.</span><span class="sxs-lookup"><span data-stu-id="5385f-121">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="5385f-122">File di configurazione</span><span class="sxs-lookup"><span data-stu-id="5385f-122">Configuration Files</span></span>  
 <span data-ttu-id="5385f-123">Questo elemento può essere usato nel file di configurazione dell'applicazione o nel file di configurazione del computer (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="5385f-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5385f-124">Esempio</span><span class="sxs-lookup"><span data-stu-id="5385f-124">Example</span></span>  
 <span data-ttu-id="5385f-125">Nell'esempio seguente vengono rimossi tutti i moduli di autenticazione configurati.</span><span class="sxs-lookup"><span data-stu-id="5385f-125">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5385f-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5385f-126">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="5385f-127">Schema delle impostazioni di rete</span><span class="sxs-lookup"><span data-stu-id="5385f-127">Network Settings Schema</span></span>](index.md)
