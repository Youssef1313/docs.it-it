---
title: Elemento <remove> per schemeSettings (impostazioni URI)
ms.date: 03/30/2017
ms.assetid: 4095ba51-de20-4f87-b562-018abe422c91
ms.openlocfilehash: 4a891eb8a2fd2d66b6435e2ae774ecd4a157c0f9
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659228"
---
# <a name="remove-element-for-schemesettings-uri-settings"></a><span data-ttu-id="ef4f2-102">\<rimuovere > elemento per schemeSettings (impostazioni URI)</span><span class="sxs-lookup"><span data-stu-id="ef4f2-102">\<remove> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="ef4f2-103">Rimuove un'impostazione dello schema per un nome di schema.</span><span class="sxs-lookup"><span data-stu-id="ef4f2-103">Removes a scheme setting for a scheme name.</span></span>  
  
 <span data-ttu-id="ef4f2-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="ef4f2-104">\<configuration></span></span>  
<span data-ttu-id="ef4f2-105">\<uri></span><span class="sxs-lookup"><span data-stu-id="ef4f2-105">\<uri></span></span>  
<span data-ttu-id="ef4f2-106">\<schemeSettings></span><span class="sxs-lookup"><span data-stu-id="ef4f2-106">\<schemeSettings></span></span>  
<span data-ttu-id="ef4f2-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="ef4f2-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef4f2-108">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ef4f2-108">Syntax</span></span>  
  
```xml  
<remove
  name="http|https"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ef4f2-109">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="ef4f2-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ef4f2-110">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="ef4f2-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ef4f2-111">Attributi</span><span class="sxs-lookup"><span data-stu-id="ef4f2-111">Attributes</span></span>  
  
|<span data-ttu-id="ef4f2-112">Attributo</span><span class="sxs-lookup"><span data-stu-id="ef4f2-112">Attribute</span></span>|<span data-ttu-id="ef4f2-113">Descrizione</span><span class="sxs-lookup"><span data-stu-id="ef4f2-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ef4f2-114">name</span><span class="sxs-lookup"><span data-stu-id="ef4f2-114">name</span></span>|<span data-ttu-id="ef4f2-115">Nome dello schema a cui si applica questa impostazione.</span><span class="sxs-lookup"><span data-stu-id="ef4f2-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="ef4f2-116">Gli unici valori supportati sono Name = "http" e Name = "https".</span><span class="sxs-lookup"><span data-stu-id="ef4f2-116">The only supported values are name="http" and name="https".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ef4f2-117">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="ef4f2-117">Child Elements</span></span>  
 <span data-ttu-id="ef4f2-118">Nessuno.</span><span class="sxs-lookup"><span data-stu-id="ef4f2-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ef4f2-119">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="ef4f2-119">Parent Elements</span></span>  
  
|<span data-ttu-id="ef4f2-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="ef4f2-120">Element</span></span>|<span data-ttu-id="ef4f2-121">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="ef4f2-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ef4f2-122">Elemento \<schemeSettings> (impostazioni URI)</span><span class="sxs-lookup"><span data-stu-id="ef4f2-122">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="ef4f2-123">Specifica come verrà analizzato un <xref:System.Uri> per schemi specifici.</span><span class="sxs-lookup"><span data-stu-id="ef4f2-123">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef4f2-124">Note</span><span class="sxs-lookup"><span data-stu-id="ef4f2-124">Remarks</span></span>  
 <span data-ttu-id="ef4f2-125">Per impostazione predefinita, <xref:System.Uri?displayProperty=nameWithType> la classe Annulla l'escape per la percentuale di delimitatori di percorso codificati prima di eseguire la compressione del percorso.</span><span class="sxs-lookup"><span data-stu-id="ef4f2-125">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="ef4f2-126">Questa operazione è stata implementata come meccanismo di sicurezza da attacchi come i seguenti:</span><span class="sxs-lookup"><span data-stu-id="ef4f2-126">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="ef4f2-127">Se questo URI viene passato a moduli che non gestiscono correttamente la percentuale di caratteri codificati, potrebbe verificarsi il seguente comando eseguito dal server:</span><span class="sxs-lookup"><span data-stu-id="ef4f2-127">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="ef4f2-128">Per questo motivo, <xref:System.Uri?displayProperty=nameWithType> First Class Annulla l'escape dei delimitatori di percorso e quindi applica la compressione del percorso.</span><span class="sxs-lookup"><span data-stu-id="ef4f2-128">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="ef4f2-129">Il risultato del passaggio dell'URL dannoso precedente <xref:System.Uri?displayProperty=nameWithType> al costruttore della classe comporta l'URI seguente:</span><span class="sxs-lookup"><span data-stu-id="ef4f2-129">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="ef4f2-130">Questo comportamento predefinito può essere modificato in modo da non delimitatore di percorso codificato con percentuale di escape utilizzando l'opzione di configurazione schemeSettings per uno schema specifico.</span><span class="sxs-lookup"><span data-stu-id="ef4f2-130">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="ef4f2-131">File di configurazione</span><span class="sxs-lookup"><span data-stu-id="ef4f2-131">Configuration Files</span></span>  
 <span data-ttu-id="ef4f2-132">Questo elemento può essere usato nel file di configurazione dell'applicazione o nel file di configurazione del computer (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="ef4f2-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef4f2-133">Esempio</span><span class="sxs-lookup"><span data-stu-id="ef4f2-133">Example</span></span>  
 <span data-ttu-id="ef4f2-134">Nell'esempio seguente viene illustrata una configurazione utilizzata <xref:System.Uri> dalla classe che rimuove qualsiasi impostazione dello schema per lo schema http.</span><span class="sxs-lookup"><span data-stu-id="ef4f2-134">The following example shows a configuration used by the <xref:System.Uri> class that removes any scheme settings for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <remove name="http"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ef4f2-135">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ef4f2-135">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="ef4f2-136">Schema delle impostazioni di rete</span><span class="sxs-lookup"><span data-stu-id="ef4f2-136">Network Settings Schema</span></span>](index.md)
