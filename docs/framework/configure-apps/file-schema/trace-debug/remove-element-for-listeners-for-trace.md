---
title: <remove>Elemento per <listeners> per<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
ms.openlocfilehash: 0c5c9efb8a22d26ea5d4467f9628af5935d6dbad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920481"
---
# <a name="remove-element-for-listeners-for-trace"></a><span data-ttu-id="f1597-102">\<rimuovere > elemento per \<i listener > per \<la traccia ></span><span class="sxs-lookup"><span data-stu-id="f1597-102">\<remove> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="f1597-103">Rimuove un listener dalla raccolta **Listeners** .</span><span class="sxs-lookup"><span data-stu-id="f1597-103">Removes a listener from the **Listeners** collection.</span></span>  
  
 <span data-ttu-id="f1597-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="f1597-104">\<configuration></span></span>  
<span data-ttu-id="f1597-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="f1597-105">\<system.diagnostics></span></span>  
<span data-ttu-id="f1597-106">\<traccia ></span><span class="sxs-lookup"><span data-stu-id="f1597-106">\<trace></span></span>  
<span data-ttu-id="f1597-107">\<listener ></span><span class="sxs-lookup"><span data-stu-id="f1597-107">\<listeners></span></span>  
<span data-ttu-id="f1597-108">\<remove></span><span class="sxs-lookup"><span data-stu-id="f1597-108">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1597-109">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f1597-109">Syntax</span></span>  
  
```xml  
<remove name="listener name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f1597-110">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="f1597-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f1597-111">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="f1597-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f1597-112">Attributi</span><span class="sxs-lookup"><span data-stu-id="f1597-112">Attributes</span></span>  
  
|<span data-ttu-id="f1597-113">Attributo</span><span class="sxs-lookup"><span data-stu-id="f1597-113">Attribute</span></span>|<span data-ttu-id="f1597-114">Descrizione</span><span class="sxs-lookup"><span data-stu-id="f1597-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f1597-115">**name**</span><span class="sxs-lookup"><span data-stu-id="f1597-115">**name**</span></span>|<span data-ttu-id="f1597-116">Attributo obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="f1597-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="f1597-117">Nome del listener da rimuovere dalla raccolta Listeners .</span><span class="sxs-lookup"><span data-stu-id="f1597-117">The name of the listener to remove from the **Listeners** collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f1597-118">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="f1597-118">Child Elements</span></span>  
 <span data-ttu-id="f1597-119">Nessuno.</span><span class="sxs-lookup"><span data-stu-id="f1597-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f1597-120">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="f1597-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f1597-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="f1597-121">Element</span></span>|<span data-ttu-id="f1597-122">Descrizione</span><span class="sxs-lookup"><span data-stu-id="f1597-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f1597-123">Elemento radice in ciascun file di configurazione usato in Common Language Runtime e nelle applicazioni .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f1597-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="f1597-124">Specifica un listener che raccoglie, archivia e instrada i messaggi.</span><span class="sxs-lookup"><span data-stu-id="f1597-124">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="f1597-125">I listener indirizzano l'output di traccia a una destinazione appropriata.</span><span class="sxs-lookup"><span data-stu-id="f1597-125">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="f1597-126">Specifica i listener di traccia per raccogliere, archiviare e indirizzare i messaggi, oltre al livello di impostazione di un'opzione di traccia.</span><span class="sxs-lookup"><span data-stu-id="f1597-126">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="f1597-127">Configura il servizio di traccia ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f1597-127">Configures the ASP.NET trace service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1597-128">Note</span><span class="sxs-lookup"><span data-stu-id="f1597-128">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f1597-129"><xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> Larimozionedidalla<xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>raccoltamodificail comportamento dei metodi,, e. `Listeners` <xref:System.Diagnostics.DefaultTraceListener></span><span class="sxs-lookup"><span data-stu-id="f1597-129">Removing the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection alters the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="f1597-130">La chiamata `Assert` di `Fail` un metodo o determina in genere la visualizzazione di una finestra di messaggio, ma la finestra di messaggio non <xref:System.Diagnostics.DefaultTraceListener> viene visualizzata se `Listeners` l'oggetto non è presente nella raccolta.</span><span class="sxs-lookup"><span data-stu-id="f1597-130">Calling an `Assert` or `Fail` method normally results in the display of a message box, however the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1597-131">Esempio</span><span class="sxs-lookup"><span data-stu-id="f1597-131">Example</span></span>  
 <span data-ttu-id="f1597-132">Nell'esempio seguente viene illustrato come rimuovere il listener di traccia predefinito dalla raccolta di **listener** di traccia.</span><span class="sxs-lookup"><span data-stu-id="f1597-132">The following example shows how to remove the default trace listener from the trace **Listeners** collection.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <remove name="Default" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f1597-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f1597-133">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="f1597-134">Schema delle impostazioni di traccia e debug</span><span class="sxs-lookup"><span data-stu-id="f1597-134">Trace and Debug Settings Schema</span></span>](index.md)
