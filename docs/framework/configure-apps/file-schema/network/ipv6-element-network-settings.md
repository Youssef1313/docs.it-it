---
title: Elemento <ipv6> (impostazioni di rete)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/ipv6
- http://schemas.microsoft.com/.NetConfiguration/v2.0#ipv6
helpviewer_keywords:
- <ipv6> element
- ipv6 element
ms.assetid: 10b79aef-327b-4718-a892-e11f55e4d169
ms.openlocfilehash: d89c2e2c6943aca38f8a71092ba3121447a77574
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664104"
---
# <a name="ipv6-element-network-settings"></a><span data-ttu-id="96206-102">Elemento \<ipv6> (impostazioni di rete)</span><span class="sxs-lookup"><span data-stu-id="96206-102">\<ipv6> Element (Network Settings)</span></span>
<span data-ttu-id="96206-103">Abilita le <xref:System.Net.Dns> risposte protocollo Internet versione 6 (IPv6) dai membri obsoleti della classe.</span><span class="sxs-lookup"><span data-stu-id="96206-103">Enables Internet Protocol version 6 (IPv6) responses from obsolete members of the <xref:System.Net.Dns> class.</span></span>  
  
 <span data-ttu-id="96206-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="96206-104">\<configuration></span></span>  
<span data-ttu-id="96206-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="96206-105">\<system.net></span></span>  
<span data-ttu-id="96206-106">\<Impostazioni ></span><span class="sxs-lookup"><span data-stu-id="96206-106">\<settings></span></span>  
<span data-ttu-id="96206-107">\<ipv6></span><span class="sxs-lookup"><span data-stu-id="96206-107">\<ipv6></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96206-108">Sintassi</span><span class="sxs-lookup"><span data-stu-id="96206-108">Syntax</span></span>  
  
```xml  
<ipv6  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="96206-109">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="96206-109">Attributes and Elements</span></span>  
 <span data-ttu-id="96206-110">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="96206-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="96206-111">Attributi</span><span class="sxs-lookup"><span data-stu-id="96206-111">Attributes</span></span>  
  
|<span data-ttu-id="96206-112">**Attributo**</span><span class="sxs-lookup"><span data-stu-id="96206-112">**Attribute**</span></span>|<span data-ttu-id="96206-113">**Descrizione**</span><span class="sxs-lookup"><span data-stu-id="96206-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`enabled`|<span data-ttu-id="96206-114">Specifica se i membri della <xref:System.Net.Dns> classe restituiscono indirizzi IP versione 6 (IPv6).</span><span class="sxs-lookup"><span data-stu-id="96206-114">Specifies whether members of the <xref:System.Net.Dns> class return Internet Protocol version 6 (IPv6) addresses.</span></span> <span data-ttu-id="96206-115">Il valore predefinito è `false`.</span><span class="sxs-lookup"><span data-stu-id="96206-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="96206-116">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="96206-116">Child Elements</span></span>  
 <span data-ttu-id="96206-117">Nessuno.</span><span class="sxs-lookup"><span data-stu-id="96206-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="96206-118">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="96206-118">Parent Elements</span></span>  
  
|<span data-ttu-id="96206-119">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="96206-119">**Element**</span></span>|<span data-ttu-id="96206-120">**Descrizione**</span><span class="sxs-lookup"><span data-stu-id="96206-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="96206-121">Impostazioni</span><span class="sxs-lookup"><span data-stu-id="96206-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="96206-122">Configura le opzioni di rete di base per lo spazio dei nomi <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="96206-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96206-123">Note</span><span class="sxs-lookup"><span data-stu-id="96206-123">Remarks</span></span>  
 <span data-ttu-id="96206-124">Questa impostazione Abilita il supporto IPv6 per i membri obsoleti <xref:System.Net.Dns> della classe <xref:System.Net.Dns.BeginGetHostByName%2A>: <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, e <xref:System.Net.Dns.Resolve%2A>.</span><span class="sxs-lookup"><span data-stu-id="96206-124">This setting enables IPv6 support for the obsolete members of the <xref:System.Net.Dns> class: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, and <xref:System.Net.Dns.Resolve%2A>.</span></span> <span data-ttu-id="96206-125">Per gli altri membri dello <xref:System.Net?displayProperty=nameWithType> spazio dei nomi, è possibile che vengano restituiti indirizzi IPv6 se IPv6 è abilitato nel sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="96206-125">For other members of the <xref:System.Net?displayProperty=nameWithType> namespace, IPv6 addresses may be returned if IPv6 is enabled in the operating system.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="96206-126">File di configurazione</span><span class="sxs-lookup"><span data-stu-id="96206-126">Configuration Files</span></span>  
 <span data-ttu-id="96206-127">Questo elemento può essere usato nel file di configurazione dell'applicazione o nel file di configurazione del computer (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="96206-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="96206-128">Esempio</span><span class="sxs-lookup"><span data-stu-id="96206-128">Example</span></span>  
 <span data-ttu-id="96206-129">Nell'esempio seguente viene illustrato come abilitare il supporto IPv6 per <xref:System.Net.Dns> la classe.</span><span class="sxs-lookup"><span data-stu-id="96206-129">The following example shows how to enable IPv6 support for the <xref:System.Net.Dns> class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <ipv6 enabled="true"/>  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="96206-130">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="96206-130">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Dns?displayProperty=nameWithType>
- <xref:System.Net.Sockets.Socket.OSSupportsIPv6%2A?displayProperty=nameWithType>
- [<span data-ttu-id="96206-131">Schema delle impostazioni di rete</span><span class="sxs-lookup"><span data-stu-id="96206-131">Network Settings Schema</span></span>](index.md)
