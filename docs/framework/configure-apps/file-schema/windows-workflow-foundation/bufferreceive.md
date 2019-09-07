---
title: <bufferReceive>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
ms.openlocfilehash: be5173ea43c6f7fca7180a311885a26c889b12db
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398839"
---
# <a name="bufferreceive"></a><span data-ttu-id="b037e-101">\<bufferReceive></span><span class="sxs-lookup"><span data-stu-id="b037e-101">\<bufferReceive></span></span>
<span data-ttu-id="b037e-102">Comportamento del servizio che consente a un servizio di utilizzare l'elaborazione di ricezione memorizzata nel buffer per far sì che un servizio flusso di lavoro elabori messaggi non ordinati.</span><span class="sxs-lookup"><span data-stu-id="b037e-102">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
<span data-ttu-id="b037e-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b037e-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b037e-104">&nbsp;&nbsp;[ **\<sistema. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="b037e-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="b037e-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamenti >** ](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="b037e-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="b037e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceBehaviors**](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="b037e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="b037e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamento >** ](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="b037e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="b037e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> bufferReceive**</span><span class="sxs-lookup"><span data-stu-id="b037e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bufferReceive>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b037e-109">Sintassi</span><span class="sxs-lookup"><span data-stu-id="b037e-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b037e-110">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="b037e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b037e-111">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="b037e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b037e-112">Attributi</span><span class="sxs-lookup"><span data-stu-id="b037e-112">Attributes</span></span>  
  
|<span data-ttu-id="b037e-113">Attributo</span><span class="sxs-lookup"><span data-stu-id="b037e-113">Attribute</span></span>|<span data-ttu-id="b037e-114">Descrizione</span><span class="sxs-lookup"><span data-stu-id="b037e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b037e-115">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="b037e-115">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="b037e-116">Integer che specifica il numero massimo di messaggi in sospeso consentiti per ogni canale.</span><span class="sxs-lookup"><span data-stu-id="b037e-116">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="b037e-117">Il valore predefinito è 512.</span><span class="sxs-lookup"><span data-stu-id="b037e-117">The default value is 512.</span></span> <span data-ttu-id="b037e-118">Questa proprietà limita il numero di messaggi non ordinati che possono essere ricevuti da un servizio flusso di lavoro.</span><span class="sxs-lookup"><span data-stu-id="b037e-118">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b037e-119">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="b037e-119">Child Elements</span></span>  
 <span data-ttu-id="b037e-120">Nessuno.</span><span class="sxs-lookup"><span data-stu-id="b037e-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b037e-121">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="b037e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="b037e-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="b037e-122">Element</span></span>|<span data-ttu-id="b037e-123">Descrizione</span><span class="sxs-lookup"><span data-stu-id="b037e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b037e-124">\<comportamento > di \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="b037e-124">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="b037e-125">Specifica un elemento di comportamento.</span><span class="sxs-lookup"><span data-stu-id="b037e-125">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b037e-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b037e-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.BufferedReceiveServiceBehavior>
- <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
