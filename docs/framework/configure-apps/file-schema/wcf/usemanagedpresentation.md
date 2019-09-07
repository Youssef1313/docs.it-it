---
title: <useManagedPresentation>
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: c410967e84c9318d21ce0b3072d08b026a37b190
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399216"
---
# <a name="usemanagedpresentation"></a><span data-ttu-id="e97c2-101">\<> useManagedPresentation</span><span class="sxs-lookup"><span data-stu-id="e97c2-101">\<useManagedPresentation></span></span>
<span data-ttu-id="e97c2-102">Elemento di associazione usato per comunicare con un servizio token di sicurezza CardSpace che supporta il profilo CardSpace di WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="e97c2-102">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="e97c2-103">Questo elemento non ha attributo e è presente come un'opzione vuota.</span><span class="sxs-lookup"><span data-stu-id="e97c2-103">This element has no attribute and is present as an empty switch.</span></span>  
  
<span data-ttu-id="e97c2-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e97c2-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e97c2-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e97c2-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e97c2-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Binding >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="e97c2-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="e97c2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<CustomBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="e97c2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="e97c2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Binding >** </span><span class="sxs-lookup"><span data-stu-id="e97c2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="e97c2-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> useManagedPresentation**</span><span class="sxs-lookup"><span data-stu-id="e97c2-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useManagedPresentation>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e97c2-110">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e97c2-110">Syntax</span></span>  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e97c2-111">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="e97c2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e97c2-112">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="e97c2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e97c2-113">Attributi</span><span class="sxs-lookup"><span data-stu-id="e97c2-113">Attributes</span></span>  
 <span data-ttu-id="e97c2-114">Nessuno.</span><span class="sxs-lookup"><span data-stu-id="e97c2-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e97c2-115">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="e97c2-115">Child Elements</span></span>  
 <span data-ttu-id="e97c2-116">Nessuna</span><span class="sxs-lookup"><span data-stu-id="e97c2-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e97c2-117">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="e97c2-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e97c2-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="e97c2-118">Element</span></span>|<span data-ttu-id="e97c2-119">Descrizione</span><span class="sxs-lookup"><span data-stu-id="e97c2-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e97c2-120">\<binding></span><span class="sxs-lookup"><span data-stu-id="e97c2-120">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="e97c2-121">Definisce tutte le funzionalità di associazione dell'associazione personalizzata.</span><span class="sxs-lookup"><span data-stu-id="e97c2-121">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e97c2-122">Note</span><span class="sxs-lookup"><span data-stu-id="e97c2-122">Remarks</span></span>  
 <span data-ttu-id="e97c2-123">Questo elemento viene usato da un provider di identità per dichiarare nei relativi criteri il fatto che supporti il profilo CardSpace di WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="e97c2-123">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="e97c2-124">I provider di identità che pubblicano questo tipo di asserzione di criteri devono essere in grado di pubblicare token basati su tale profilo CardSpace.</span><span class="sxs-lookup"><span data-stu-id="e97c2-124">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e97c2-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e97c2-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="e97c2-126">Associazioni</span><span class="sxs-lookup"><span data-stu-id="e97c2-126">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e97c2-127">Estensione delle associazioni</span><span class="sxs-lookup"><span data-stu-id="e97c2-127">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="e97c2-128">Associazioni personalizzate</span><span class="sxs-lookup"><span data-stu-id="e97c2-128">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="e97c2-129">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="e97c2-129">\<customBinding></span></span>](custombinding.md)
