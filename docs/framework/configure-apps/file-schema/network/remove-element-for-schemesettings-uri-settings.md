---
title: Elemento <remove> per schemeSettings (impostazioni URI)
ms.date: 03/30/2017
ms.assetid: 4095ba51-de20-4f87-b562-018abe422c91
ms.openlocfilehash: 0dc8c6111157ba1f23d4a0449bee8f6626027e23
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697854"
---
# <a name="remove-element-for-schemesettings-uri-settings"></a><span data-ttu-id="33dbb-102">Elemento > \<remove per schemeSettings (impostazioni URI)</span><span class="sxs-lookup"><span data-stu-id="33dbb-102">\<remove> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="33dbb-103">Rimuove un'impostazione dello schema per un nome di schema.</span><span class="sxs-lookup"><span data-stu-id="33dbb-103">Removes a scheme setting for a scheme name.</span></span>  
  
[<span data-ttu-id="33dbb-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="33dbb-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="33dbb-105">&nbsp; @ no__t-1[ **\<uri >** ](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="33dbb-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>  
<span data-ttu-id="33dbb-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<schemeSettings >** ](schemesettings-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="33dbb-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)</span></span>  
<span data-ttu-id="33dbb-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<remove >**</span><span class="sxs-lookup"><span data-stu-id="33dbb-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33dbb-108">Sintassi</span><span class="sxs-lookup"><span data-stu-id="33dbb-108">Syntax</span></span>  
  
```xml  
<remove
  name="http|https"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="33dbb-109">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="33dbb-109">Attributes and Elements</span></span>  
 <span data-ttu-id="33dbb-110">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="33dbb-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="33dbb-111">Attributi</span><span class="sxs-lookup"><span data-stu-id="33dbb-111">Attributes</span></span>  
  
|<span data-ttu-id="33dbb-112">Attributo</span><span class="sxs-lookup"><span data-stu-id="33dbb-112">Attribute</span></span>|<span data-ttu-id="33dbb-113">Descrizione</span><span class="sxs-lookup"><span data-stu-id="33dbb-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="33dbb-114">name</span><span class="sxs-lookup"><span data-stu-id="33dbb-114">name</span></span>|<span data-ttu-id="33dbb-115">Nome dello schema a cui si applica questa impostazione.</span><span class="sxs-lookup"><span data-stu-id="33dbb-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="33dbb-116">Gli unici valori supportati sono Name = "http" e Name = "https".</span><span class="sxs-lookup"><span data-stu-id="33dbb-116">The only supported values are name="http" and name="https".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="33dbb-117">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="33dbb-117">Child Elements</span></span>  
 <span data-ttu-id="33dbb-118">No.</span><span class="sxs-lookup"><span data-stu-id="33dbb-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="33dbb-119">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="33dbb-119">Parent Elements</span></span>  
  
|<span data-ttu-id="33dbb-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="33dbb-120">Element</span></span>|<span data-ttu-id="33dbb-121">Descrizione</span><span class="sxs-lookup"><span data-stu-id="33dbb-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="33dbb-122">Elemento \<schemeSettings> (impostazioni URI)</span><span class="sxs-lookup"><span data-stu-id="33dbb-122">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="33dbb-123">Specifica come verrà analizzato un <xref:System.Uri> per schemi specifici.</span><span class="sxs-lookup"><span data-stu-id="33dbb-123">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33dbb-124">Note</span><span class="sxs-lookup"><span data-stu-id="33dbb-124">Remarks</span></span>  
 <span data-ttu-id="33dbb-125">Per impostazione predefinita, la classe <xref:System.Uri?displayProperty=nameWithType> Annulla il carattere di escape per cento delimitatori di percorso codificati prima di eseguire la compressione del percorso.</span><span class="sxs-lookup"><span data-stu-id="33dbb-125">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="33dbb-126">Questa operazione è stata implementata come meccanismo di sicurezza da attacchi come i seguenti:</span><span class="sxs-lookup"><span data-stu-id="33dbb-126">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="33dbb-127">Se questo URI viene passato a moduli che non gestiscono correttamente la percentuale di caratteri codificati, potrebbe verificarsi il seguente comando eseguito dal server:</span><span class="sxs-lookup"><span data-stu-id="33dbb-127">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="33dbb-128">Per questo motivo, la classe <xref:System.Uri?displayProperty=nameWithType> First Annulla l'escape dei delimitatori di percorso e quindi applica la compressione del percorso.</span><span class="sxs-lookup"><span data-stu-id="33dbb-128">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="33dbb-129">Il risultato del passaggio dell'URL dannoso precedente al costruttore della classe <xref:System.Uri?displayProperty=nameWithType> comporta l'URI seguente:</span><span class="sxs-lookup"><span data-stu-id="33dbb-129">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="33dbb-130">Questo comportamento predefinito può essere modificato in modo da non delimitatore di percorso codificato con percentuale di escape utilizzando l'opzione di configurazione schemeSettings per uno schema specifico.</span><span class="sxs-lookup"><span data-stu-id="33dbb-130">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="33dbb-131">File di configurazione</span><span class="sxs-lookup"><span data-stu-id="33dbb-131">Configuration Files</span></span>  
 <span data-ttu-id="33dbb-132">Questo elemento può essere usato nel file di configurazione dell'applicazione o nel file di configurazione del computer (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="33dbb-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="33dbb-133">Esempio</span><span class="sxs-lookup"><span data-stu-id="33dbb-133">Example</span></span>  
 <span data-ttu-id="33dbb-134">Nell'esempio seguente viene illustrata una configurazione utilizzata dalla classe <xref:System.Uri> che rimuove qualsiasi impostazione dello schema per lo schema http.</span><span class="sxs-lookup"><span data-stu-id="33dbb-134">The following example shows a configuration used by the <xref:System.Uri> class that removes any scheme settings for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <remove name="http"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="33dbb-135">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="33dbb-135">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="33dbb-136">Schema delle impostazioni di rete</span><span class="sxs-lookup"><span data-stu-id="33dbb-136">Network Settings Schema</span></span>](index.md)
