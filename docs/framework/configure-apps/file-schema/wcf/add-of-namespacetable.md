---
title: <add> di <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 32eff2e7bfdf1aee4c7d37a0e06166afba3cb398
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566743"
---
# <a name="add-of-namespacetable"></a><span data-ttu-id="69dc7-102">\<aggiungere > di \<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="69dc7-102">\<add> of \<namespaceTable></span></span>
<span data-ttu-id="69dc7-103">Rappresenta un elemento di configurazione contenente uno spazio dei nomi da anteporre al mapping che può quindi essere usato nei filtri XPath per il routing.</span><span class="sxs-lookup"><span data-stu-id="69dc7-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
 <span data-ttu-id="69dc7-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="69dc7-104">\<system.serviceModel></span></span>  
<span data-ttu-id="69dc7-105">\<routing></span><span class="sxs-lookup"><span data-stu-id="69dc7-105">\<routing></span></span>  
<span data-ttu-id="69dc7-106">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="69dc7-106">\<namespaceTable></span></span>  
<span data-ttu-id="69dc7-107">\<add></span><span class="sxs-lookup"><span data-stu-id="69dc7-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69dc7-108">Sintassi</span><span class="sxs-lookup"><span data-stu-id="69dc7-108">Syntax</span></span>  
  
```xml  
<routing>
  <namespaceTable>
    <add namespace="String"
         prefix="String" />
  </namespaceTable>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69dc7-109">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="69dc7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="69dc7-110">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="69dc7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69dc7-111">Attributi</span><span class="sxs-lookup"><span data-stu-id="69dc7-111">Attributes</span></span>  
  
|<span data-ttu-id="69dc7-112">Attributo</span><span class="sxs-lookup"><span data-stu-id="69dc7-112">Attribute</span></span>|<span data-ttu-id="69dc7-113">Descrizione</span><span class="sxs-lookup"><span data-stu-id="69dc7-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="69dc7-114">namespace</span><span class="sxs-lookup"><span data-stu-id="69dc7-114">namespace</span></span>|<span data-ttu-id="69dc7-115">Stringa contenente lo spazio dei nomi.</span><span class="sxs-lookup"><span data-stu-id="69dc7-115">A string containing the namespace.</span></span>|  
|<span data-ttu-id="69dc7-116">prefix</span><span class="sxs-lookup"><span data-stu-id="69dc7-116">prefix</span></span>|<span data-ttu-id="69dc7-117">Stringa contenente il prefisso per questo spazio dei nomi.</span><span class="sxs-lookup"><span data-stu-id="69dc7-117">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="69dc7-118">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="69dc7-118">Child Elements</span></span>  
 <span data-ttu-id="69dc7-119">Nessuno.</span><span class="sxs-lookup"><span data-stu-id="69dc7-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="69dc7-120">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="69dc7-120">Parent Elements</span></span>  
  
|<span data-ttu-id="69dc7-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="69dc7-121">Element</span></span>|<span data-ttu-id="69dc7-122">Descrizione</span><span class="sxs-lookup"><span data-stu-id="69dc7-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="69dc7-123">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="69dc7-123">\<namespaceTable></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|<span data-ttu-id="69dc7-124">Rappresenta una sezione di configurazione per la definizione di un set di elementi contenenti lo spazio dei nomi da anteporre ai mapping che possono quindi essere usati nei filtri XPath per il routing.</span><span class="sxs-lookup"><span data-stu-id="69dc7-124">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="69dc7-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="69dc7-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
