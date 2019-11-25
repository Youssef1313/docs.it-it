---
title: Elemento <clear> per <listeners> per <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 049b8e7ed17633c0f34b062915afaf719927dad6
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088921"
---
# <a name="clear-element-for-listeners-for-trace"></a><span data-ttu-id="1ce74-102">\<elemento clear > per \<listeners > per \<Trace ></span><span class="sxs-lookup"><span data-stu-id="1ce74-102">\<clear> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="1ce74-103">Cancella la raccolta `Listeners` per una traccia.</span><span class="sxs-lookup"><span data-stu-id="1ce74-103">Clears the `Listeners` collection for trace.</span></span>  

<span data-ttu-id="1ce74-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1ce74-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1ce74-105">&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="1ce74-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="1ce74-106">&nbsp;&nbsp;&nbsp;&nbsp;\<[**Trace**](trace-element.md) ></span><span class="sxs-lookup"><span data-stu-id="1ce74-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\</span></span>
<span data-ttu-id="1ce74-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**listener**](listeners-element-for-trace.md)\<</span><span class="sxs-lookup"><span data-stu-id="1ce74-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\</span></span>
<span data-ttu-id="1ce74-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**deselezionare >**</span><span class="sxs-lookup"><span data-stu-id="1ce74-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="1ce74-109">Sintassi</span><span class="sxs-lookup"><span data-stu-id="1ce74-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1ce74-110">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="1ce74-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1ce74-111">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="1ce74-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1ce74-112">Attributi</span><span class="sxs-lookup"><span data-stu-id="1ce74-112">Attributes</span></span>  
 <span data-ttu-id="1ce74-113">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="1ce74-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1ce74-114">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="1ce74-114">Child Elements</span></span>  
 <span data-ttu-id="1ce74-115">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="1ce74-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1ce74-116">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="1ce74-116">Parent Elements</span></span>  
  
|<span data-ttu-id="1ce74-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="1ce74-117">Element</span></span>|<span data-ttu-id="1ce74-118">Descrizione</span><span class="sxs-lookup"><span data-stu-id="1ce74-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1ce74-119">Elemento radice in ciascun file di configurazione usato in Common Language Runtime e nelle applicazioni .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1ce74-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="1ce74-120">Specifica i listener di traccia per raccogliere, archiviare e indirizzare i messaggi, oltre al livello di impostazione di un'opzione di traccia.</span><span class="sxs-lookup"><span data-stu-id="1ce74-120">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="1ce74-121">Contiene i listener che raccolgono, archiviano e indirizzano i messaggi di traccia.</span><span class="sxs-lookup"><span data-stu-id="1ce74-121">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="1ce74-122">Contiene i listener che raccolgono, archiviano e indirizzano i messaggi.</span><span class="sxs-lookup"><span data-stu-id="1ce74-122">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="1ce74-123">I listener indirizzano l'output di traccia a una destinazione appropriata.</span><span class="sxs-lookup"><span data-stu-id="1ce74-123">Listeners direct the tracing output to an appropriate target.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ce74-124">Note</span><span class="sxs-lookup"><span data-stu-id="1ce74-124">Remarks</span></span>  
 <span data-ttu-id="1ce74-125">L'elemento `<clear>` rimuove tutti i listener dalla raccolta `Listeners` per Trace.</span><span class="sxs-lookup"><span data-stu-id="1ce74-125">The `<clear>` element removes all listeners from the `Listeners` collection for trace.</span></span> <span data-ttu-id="1ce74-126">È possibile utilizzare l'elemento `<clear>` prima di utilizzare l'elemento `<add>` per verificare che non siano presenti altri listener attivi nella raccolta.</span><span class="sxs-lookup"><span data-stu-id="1ce74-126">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
 <span data-ttu-id="1ce74-127">È possibile cancellare il `Listeners` raccolta a livello di codice chiamando il metodo <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> sulla proprietà <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> (`System.Diagnostics.Trace.Listeners.Clear()`).</span><span class="sxs-lookup"><span data-stu-id="1ce74-127">You can clear the `Listeners` collection programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> method on the <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> property (`System.Diagnostics.Trace.Listeners.Clear()`).</span></span>  
  
 <span data-ttu-id="1ce74-128">Questo elemento può essere utilizzato nel file di configurazione del computer (Machine. config) e nel file di configurazione dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="1ce74-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1ce74-129">L'elemento `<clear>` rimuove la <xref:System.Diagnostics.DefaultTraceListener> dalla raccolta `Listeners`, modificando il comportamento dei metodi <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>e <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1ce74-129">The `<clear>` element removes the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection, altering the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="1ce74-130">La chiamata di un metodo di `Assert` o `Fail` comporta in genere la visualizzazione di una finestra di messaggio.</span><span class="sxs-lookup"><span data-stu-id="1ce74-130">Calling an `Assert` or `Fail` method normally results in the display of a message box.</span></span> <span data-ttu-id="1ce74-131">Tuttavia, la finestra di messaggio non viene visualizzata se la <xref:System.Diagnostics.DefaultTraceListener> non è presente nella raccolta `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="1ce74-131">However, the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ce74-132">Esempio</span><span class="sxs-lookup"><span data-stu-id="1ce74-132">Example</span></span>  
 <span data-ttu-id="1ce74-133">Nell'esempio seguente viene illustrato come utilizzare l'elemento `<clear>` prima di utilizzare l'elemento `<add>` per aggiungere il listener `console` alla raccolta `Listeners` per Trace.</span><span class="sxs-lookup"><span data-stu-id="1ce74-133">The following example shows how to use the `<clear>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for trace.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <clear/>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a><span data-ttu-id="1ce74-134">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1ce74-134">See also</span></span>

- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="1ce74-135">Schema delle impostazioni di traccia e debug</span><span class="sxs-lookup"><span data-stu-id="1ce74-135">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="1ce74-136">\<remove></span><span class="sxs-lookup"><span data-stu-id="1ce74-136">\<remove></span></span>](remove-element-for-listeners-for-trace.md)
- [<span data-ttu-id="1ce74-137">Listener di traccia</span><span class="sxs-lookup"><span data-stu-id="1ce74-137">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
