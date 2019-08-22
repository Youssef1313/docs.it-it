---
title: Elemento <module> (impostazioni di rete)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#module
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/module
helpviewer_keywords:
- module element
- <module> element
ms.assetid: 10318725-9666-4d65-ab61-b94c64e59f13
ms.openlocfilehash: 851a63b41dfb5d3b4058e1373148f48d47d9d6ae
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664074"
---
# <a name="module-element-network-settings"></a><span data-ttu-id="cd1ef-102">\<Elemento > del modulo (impostazioni di rete)</span><span class="sxs-lookup"><span data-stu-id="cd1ef-102">\<module> Element (Network Settings)</span></span>
<span data-ttu-id="cd1ef-103">Aggiunge un nuovo modulo proxy all'applicazione.</span><span class="sxs-lookup"><span data-stu-id="cd1ef-103">Adds a new proxy module to the application.</span></span>  
  
 <span data-ttu-id="cd1ef-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="cd1ef-104">\<configuration></span></span>  
<span data-ttu-id="cd1ef-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="cd1ef-105">\<system.net></span></span>  
<span data-ttu-id="cd1ef-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="cd1ef-106">\<defaultProxy></span></span>  
<span data-ttu-id="cd1ef-107">\<> moduli</span><span class="sxs-lookup"><span data-stu-id="cd1ef-107">\<module></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd1ef-108">Sintassi</span><span class="sxs-lookup"><span data-stu-id="cd1ef-108">Syntax</span></span>  
  
```xml  
<module   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd1ef-109">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="cd1ef-109">Attributes and Elements</span></span>  
 <span data-ttu-id="cd1ef-110">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="cd1ef-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd1ef-111">Attributi</span><span class="sxs-lookup"><span data-stu-id="cd1ef-111">Attributes</span></span>  
  
|<span data-ttu-id="cd1ef-112">**Attributo**</span><span class="sxs-lookup"><span data-stu-id="cd1ef-112">**Attribute**</span></span>|<span data-ttu-id="cd1ef-113">**Descrizione**</span><span class="sxs-lookup"><span data-stu-id="cd1ef-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="cd1ef-114">Il nome completo del tipo (indicato dalla <xref:System.Type.FullName%2A> proprietà) e il nome dell'assembly (indicato <xref:System.Reflection.Assembly.FullName%2A> dalla proprietà), separati da una virgola, che implementa il proxy.</span><span class="sxs-lookup"><span data-stu-id="cd1ef-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cd1ef-115">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="cd1ef-115">Child Elements</span></span>  
 <span data-ttu-id="cd1ef-116">Nessuno.</span><span class="sxs-lookup"><span data-stu-id="cd1ef-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cd1ef-117">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="cd1ef-117">Parent Elements</span></span>  
  
|<span data-ttu-id="cd1ef-118">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="cd1ef-118">**Element**</span></span>|<span data-ttu-id="cd1ef-119">**Descrizione**</span><span class="sxs-lookup"><span data-stu-id="cd1ef-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="cd1ef-120">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="cd1ef-120">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="cd1ef-121">Configura il server proxy Hypertext Transfer Protocol (HTTP).</span><span class="sxs-lookup"><span data-stu-id="cd1ef-121">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd1ef-122">Note</span><span class="sxs-lookup"><span data-stu-id="cd1ef-122">Remarks</span></span>  
 <span data-ttu-id="cd1ef-123">L' `module` elemento registra le classi proxy che implementano l' <xref:System.Net.IWebProxy> interfaccia.</span><span class="sxs-lookup"><span data-stu-id="cd1ef-123">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="cd1ef-124">Dopo la registrazione della classe proxy, `module` può essere utilizzato per richiedere informazioni mediante il proxy supportato.</span><span class="sxs-lookup"><span data-stu-id="cd1ef-124">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="cd1ef-125">Il valore `type` dell'attributo deve corrispondere al nome della classe del modulo e al nome della corrispondente libreria di collegamento dinamico (dll).</span><span class="sxs-lookup"><span data-stu-id="cd1ef-125">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="cd1ef-126">File di configurazione</span><span class="sxs-lookup"><span data-stu-id="cd1ef-126">Configuration Files</span></span>  
 <span data-ttu-id="cd1ef-127">Questo elemento può essere usato nel file di configurazione dell'applicazione o nel file di configurazione del computer (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="cd1ef-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd1ef-128">Esempio</span><span class="sxs-lookup"><span data-stu-id="cd1ef-128">Example</span></span>  
 <span data-ttu-id="cd1ef-129">Nell'esempio seguente viene registrata una classe proxy personalizzata.</span><span class="sxs-lookup"><span data-stu-id="cd1ef-129">The following example registers a custom proxy class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <module  
        type="Test.CustomWebProxy, TestProxy, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b23a5c561934e385"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cd1ef-130">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="cd1ef-130">See also</span></span>

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="cd1ef-131">Schema delle impostazioni di rete</span><span class="sxs-lookup"><span data-stu-id="cd1ef-131">Network Settings Schema</span></span>](index.md)
