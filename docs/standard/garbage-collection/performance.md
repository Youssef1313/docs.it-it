---
title: Garbage Collection e prestazioni
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, troubleshooting
- garbage collection, performance
ms.assetid: c203467b-e95c-4ccf-b30b-953eb3463134
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6409bbecdef2da03a18ed246cb90478b2a1fd7f6
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054060"
---
# <a name="garbage-collection-and-performance"></a><span data-ttu-id="bed9d-102">Garbage Collection e prestazioni</span><span class="sxs-lookup"><span data-stu-id="bed9d-102">Garbage Collection and Performance</span></span>

<a name="top"></a><span data-ttu-id="bed9d-103">Questo argomento descrive i problemi relativi a Garbage Collection e all'uso della memoria.</span><span class="sxs-lookup"><span data-stu-id="bed9d-103">This topic describes issues related to garbage collection and memory usage.</span></span> <span data-ttu-id="bed9d-104">Sono incluse informazioni per risolvere i problemi che riguardano l'heap gestito e che descrivono come ridurre al minimo l'effetto di Garbage Collection sulle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="bed9d-104">It addresses issues that pertain to the managed heap and explains how to minimize the effect of garbage collection on your applications.</span></span> <span data-ttu-id="bed9d-105">Per ogni problema sono disponibili collegamenti alle procedure che è possibile usare per approfondimenti aggiuntivi.</span><span class="sxs-lookup"><span data-stu-id="bed9d-105">Each issue has links to procedures that you can use to investigate problems.</span></span>

<span data-ttu-id="bed9d-106">Di seguito sono elencate le diverse sezioni di questo argomento:</span><span class="sxs-lookup"><span data-stu-id="bed9d-106">This topic contains the following sections:</span></span>

- [<span data-ttu-id="bed9d-107">Strumenti di analisi delle prestazioni</span><span class="sxs-lookup"><span data-stu-id="bed9d-107">Performance Analysis Tools</span></span>](#performance_analysis_tools)

- [<span data-ttu-id="bed9d-108">Risoluzione dei problemi di prestazioni</span><span class="sxs-lookup"><span data-stu-id="bed9d-108">Troubleshooting Performance Issues</span></span>](#troubleshooting_performance_issues)

- [<span data-ttu-id="bed9d-109">Linee guida per la risoluzione dei problemi</span><span class="sxs-lookup"><span data-stu-id="bed9d-109">Troubleshooting Guidelines</span></span>](#troubleshooting_guidelines)

- [<span data-ttu-id="bed9d-110">Procedure di controllo delle prestazioni</span><span class="sxs-lookup"><span data-stu-id="bed9d-110">Performance Check Procedures</span></span>](#performance_check_procedures)

<a name="performance_analysis_tools"></a>

## <a name="performance-analysis-tools"></a><span data-ttu-id="bed9d-111">Strumenti di analisi delle prestazioni</span><span class="sxs-lookup"><span data-stu-id="bed9d-111">Performance Analysis Tools</span></span>

<span data-ttu-id="bed9d-112">Le sezioni seguenti descrivono gli strumenti disponibili per esaminare i problemi relativi a utilizzo della memoria e Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="bed9d-112">The following sections describe the tools that are available for investigating memory usage and garbage collection issues.</span></span> <span data-ttu-id="bed9d-113">Le [procedure](#performance_check_procedures) illustrate più avanti in questo argomento fanno riferimento a questi strumenti.</span><span class="sxs-lookup"><span data-stu-id="bed9d-113">The [procedures](#performance_check_procedures) provided later in this topic refer to these tools.</span></span>

<a name="perf_counters"></a>

### <a name="memory-performance-counters"></a><span data-ttu-id="bed9d-114">Contatori delle prestazioni di memoria</span><span class="sxs-lookup"><span data-stu-id="bed9d-114">Memory Performance Counters</span></span>

<span data-ttu-id="bed9d-115">È possibile usare i contatori delle prestazioni per raccogliere dati sulle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="bed9d-115">You can use performance counters to gather performance data.</span></span> <span data-ttu-id="bed9d-116">Per istruzioni, vedere [Profilatura runtime](../../../docs/framework/debug-trace-profile/runtime-profiling.md).</span><span class="sxs-lookup"><span data-stu-id="bed9d-116">For instructions, see [Runtime Profiling](../../../docs/framework/debug-trace-profile/runtime-profiling.md).</span></span> <span data-ttu-id="bed9d-117">La categoria Memoria CLR .NET dei contatori delle prestazioni, descritta in [Contatori delle prestazioni in .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md), fornisce informazioni su Garbage Collector.</span><span class="sxs-lookup"><span data-stu-id="bed9d-117">The .NET CLR Memory category of performance counters, as described in [Performance Counters in the .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md), provides information about the garbage collector.</span></span>

<a name="sos"></a>

### <a name="debugging-with-sos"></a><span data-ttu-id="bed9d-118">Debug con SOS</span><span class="sxs-lookup"><span data-stu-id="bed9d-118">Debugging with SOS</span></span>

<span data-ttu-id="bed9d-119">È possibile usare il [debugger di Windows (WinDbg)](/windows-hardware/drivers/debugger/index) per controllare gli oggetti nell'heap gestito.</span><span class="sxs-lookup"><span data-stu-id="bed9d-119">You can use the [Windows Debugger (WinDbg)](/windows-hardware/drivers/debugger/index) to inspect objects on the managed heap.</span></span>

<span data-ttu-id="bed9d-120">Per installare WinDbg, installare gli strumenti di debug per Windows dalla [pagina di download degli strumenti di debug per Windows](/windows-hardware/drivers/debugger/debugger-download-tools).</span><span class="sxs-lookup"><span data-stu-id="bed9d-120">To install WinDbg, install Debugging Tools for Windows from the [Download Debugging Tools for Windows](/windows-hardware/drivers/debugger/debugger-download-tools) page.</span></span>

<a name="etw"></a>

### <a name="garbage-collection-etw-events"></a><span data-ttu-id="bed9d-121">Eventi ETW di Garbage Collection</span><span class="sxs-lookup"><span data-stu-id="bed9d-121">Garbage Collection ETW Events</span></span>

<span data-ttu-id="bed9d-122">Event Tracing for Windows (ETW) è un sistema di traccia che integra il supporto per profilatura e debug offerto da .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bed9d-122">Event tracing for Windows (ETW) is a tracing system that supplements the profiling and debugging support provided by the .NET Framework.</span></span> <span data-ttu-id="bed9d-123">A partire da .NET Framework 4, gli [eventi ETW di Garbage Collection](../../../docs/framework/performance/garbage-collection-etw-events.md) acquisiscono informazioni utili per l'analisi dell'heap gestito da un punto di vista statistico.</span><span class="sxs-lookup"><span data-stu-id="bed9d-123">Starting with the .NET Framework 4, [garbage collection ETW events](../../../docs/framework/performance/garbage-collection-etw-events.md) capture useful information for analyzing the managed heap from a statistical point of view.</span></span> <span data-ttu-id="bed9d-124">Ad esempio, l'evento `GCStart_V1`, generato quando sta per verificarsi un'operazione di Garbage Collection, fornisce le informazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="bed9d-124">For example, the `GCStart_V1` event, which is raised when a garbage collection is about to occur, provides the following information:</span></span>

- <span data-ttu-id="bed9d-125">Generazione di oggetti raccolta.</span><span class="sxs-lookup"><span data-stu-id="bed9d-125">Which generation of objects is being collected.</span></span>

- <span data-ttu-id="bed9d-126">Che cosa ha attivato l'operazione di Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="bed9d-126">What triggered the garbage collection.</span></span>

- <span data-ttu-id="bed9d-127">Tipo di Garbage Collection (simultanea o non simultanea).</span><span class="sxs-lookup"><span data-stu-id="bed9d-127">Type of garbage collection (concurrent or not concurrent).</span></span>

<span data-ttu-id="bed9d-128">La registrazione degli eventi ETW è efficiente e non maschera alcun problema di prestazioni associato a Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="bed9d-128">ETW event logging is efficient and will not mask any performance problems associated with garbage collection.</span></span> <span data-ttu-id="bed9d-129">Un processo può fornire i propri eventi insieme agli eventi ETW.</span><span class="sxs-lookup"><span data-stu-id="bed9d-129">A process can provide its own events in conjunction with ETW events.</span></span> <span data-ttu-id="bed9d-130">Una volta registrati, sia gli eventi dell'applicazione sia quelli di Garbage Collection possono essere correlati per determinare come e quando si verificano problemi relativi all'heap.</span><span class="sxs-lookup"><span data-stu-id="bed9d-130">When logged, both the application's events and the garbage collection events can be correlated to determine how and when heap problems occur.</span></span> <span data-ttu-id="bed9d-131">Ad esempio, un'applicazione server può fornire eventi all'inizio e alla fine di una richiesta client.</span><span class="sxs-lookup"><span data-stu-id="bed9d-131">For example, a server application could provide events at the start and end of a client request.</span></span>

<a name="profiling_api"></a>

### <a name="the-profiling-api"></a><span data-ttu-id="bed9d-132">API di profilatura</span><span class="sxs-lookup"><span data-stu-id="bed9d-132">The Profiling API</span></span>

<span data-ttu-id="bed9d-133">Le interfacce di profilatura Common Language Runtime (CLR) forniscono informazioni dettagliate sugli oggetti interessati durante l'operazione di Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="bed9d-133">The common language runtime (CLR) profiling interfaces provide detailed information about the objects that were affected during garbage collection.</span></span> <span data-ttu-id="bed9d-134">Un profiler può ricevere una notifica all'inizio o alla fine di un'operazione di Garbage Collection</span><span class="sxs-lookup"><span data-stu-id="bed9d-134">A profiler can be notified when a garbage collection starts and ends.</span></span> <span data-ttu-id="bed9d-135">e può fornire report sugli oggetti nell'heap gestito, inclusa un'identificazione degli oggetti in ogni generazione.</span><span class="sxs-lookup"><span data-stu-id="bed9d-135">It can provide reports about the objects on the managed heap, including an identification of objects in each generation.</span></span> <span data-ttu-id="bed9d-136">Per altre informazioni, vedere [Cenni preliminari sulla profilatura](../../../docs/framework/unmanaged-api/profiling/profiling-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bed9d-136">For more information, see [Profiling Overview](../../../docs/framework/unmanaged-api/profiling/profiling-overview.md).</span></span>

<span data-ttu-id="bed9d-137">I profiler possono fornire informazioni complete.</span><span class="sxs-lookup"><span data-stu-id="bed9d-137">Profilers can provide comprehensive information.</span></span> <span data-ttu-id="bed9d-138">Tuttavia, i profiler complessi possono potenzialmente modificare il comportamento di un'applicazione.</span><span class="sxs-lookup"><span data-stu-id="bed9d-138">However, complex profilers can potentially modify an application's behavior.</span></span>

### <a name="application-domain-resource-monitoring"></a><span data-ttu-id="bed9d-139">Monitoraggio delle risorse del dominio applicazione</span><span class="sxs-lookup"><span data-stu-id="bed9d-139">Application Domain Resource Monitoring</span></span>

<span data-ttu-id="bed9d-140">A partire da .NET Framework 4, il monitoraggio delle risorse del dominio dell'applicazione consente agli host di monitorare l'utilizzo di CPU e memoria da parte del dominio dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="bed9d-140">Starting with the .NET Framework 4, Application domain resource monitoring (ARM) enables hosts to monitor CPU and memory usage by application domain.</span></span> <span data-ttu-id="bed9d-141">Per altre informazioni, vedere [Monitoraggio delle risorse del dominio applicazione](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md).</span><span class="sxs-lookup"><span data-stu-id="bed9d-141">For more information, see [Application Domain Resource Monitoring](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md).</span></span>

[<span data-ttu-id="bed9d-142">Torna all'inizio</span><span class="sxs-lookup"><span data-stu-id="bed9d-142">Back to top</span></span>](#top)

<a name="troubleshooting_performance_issues"></a>

## <a name="troubleshooting-performance-issues"></a><span data-ttu-id="bed9d-143">Risoluzione dei problemi relativi alle prestazioni</span><span class="sxs-lookup"><span data-stu-id="bed9d-143">Troubleshooting Performance Issues</span></span>

<span data-ttu-id="bed9d-144">Il primo passaggio consiste nel [determinare se il problema è in realtà causato dall'operazione di Garbage Collection](#IsGC).</span><span class="sxs-lookup"><span data-stu-id="bed9d-144">The first step is to [determine whether the issue is actually garbage collection](#IsGC).</span></span> <span data-ttu-id="bed9d-145">In questo caso, selezionare una delle voci nell'elenco seguente per risolvere il problema.</span><span class="sxs-lookup"><span data-stu-id="bed9d-145">If you determine that it is, select from the following list to troubleshoot the problem.</span></span>

- [<span data-ttu-id="bed9d-146">Viene generata un'eccezione di memoria esaurita</span><span class="sxs-lookup"><span data-stu-id="bed9d-146">An out-of-memory exception is thrown</span></span>](#Issue_OOM)

- [<span data-ttu-id="bed9d-147">Il processo usa una quantità eccessiva di memoria</span><span class="sxs-lookup"><span data-stu-id="bed9d-147">The process uses too much memory</span></span>](#Issue_TooMuchMemory)

- [<span data-ttu-id="bed9d-148">Garbage Collector non recupera gli oggetti in modo abbastanza veloce</span><span class="sxs-lookup"><span data-stu-id="bed9d-148">The garbage collector does not reclaim objects fast enough</span></span>](#Issue_NotFastEnough)

- [<span data-ttu-id="bed9d-149">L'heap gestito è troppo frammentato</span><span class="sxs-lookup"><span data-stu-id="bed9d-149">The managed heap is too fragmented</span></span>](#Issue_Fragmentation)

- [<span data-ttu-id="bed9d-150">Le pause di Garbage Collection sono troppo prolungate</span><span class="sxs-lookup"><span data-stu-id="bed9d-150">Garbage collection pauses are too long</span></span>](#Issue_LongPauses)

- [<span data-ttu-id="bed9d-151">La generazione 0 è troppo grande</span><span class="sxs-lookup"><span data-stu-id="bed9d-151">Generation 0 is too big</span></span>](#Issue_Gen0)

- [<span data-ttu-id="bed9d-152">L'utilizzo della CPU durante un'operazione di Garbage Collection è eccessivo</span><span class="sxs-lookup"><span data-stu-id="bed9d-152">CPU usage during a garbage collection is too high</span></span>](#Issue_HighCPU)

<a name="Issue_OOM"></a>

### <a name="issue-an-out-of-memory-exception-is-thrown"></a><span data-ttu-id="bed9d-153">Problema: Viene generata un'eccezione di memoria esaurita</span><span class="sxs-lookup"><span data-stu-id="bed9d-153">Issue: An Out-of-Memory Exception Is Thrown</span></span>

<span data-ttu-id="bed9d-154">Esistono due casi legittimi per la generazione di un'eccezione <xref:System.OutOfMemoryException> gestita:</span><span class="sxs-lookup"><span data-stu-id="bed9d-154">There are two legitimate cases for a managed <xref:System.OutOfMemoryException> to be thrown:</span></span>

- <span data-ttu-id="bed9d-155">Esaurimento della memoria virtuale.</span><span class="sxs-lookup"><span data-stu-id="bed9d-155">Running out of virtual memory.</span></span>

  <span data-ttu-id="bed9d-156">Garbage Collector alloca memoria dal sistema in segmenti di dimensioni predeterminate.</span><span class="sxs-lookup"><span data-stu-id="bed9d-156">The garbage collector allocates memory from the system in segments of a pre-determined size.</span></span> <span data-ttu-id="bed9d-157">Se un'allocazione richiede un segmento aggiuntivo, ma non è più disponibile un blocco contiguo libero nello spazio di memoria virtuale del processo, l'allocazione per l'heap gestito non riesce.</span><span class="sxs-lookup"><span data-stu-id="bed9d-157">If an allocation requires an additional segment, but there is no contiguous free block left in the process's virtual memory space, the allocation for the managed heap will fail.</span></span>

- <span data-ttu-id="bed9d-158">Mancanza di memoria fisica sufficiente da allocare.</span><span class="sxs-lookup"><span data-stu-id="bed9d-158">Not having enough physical memory to allocate.</span></span>

|<span data-ttu-id="bed9d-159">Controlli delle prestazioni</span><span class="sxs-lookup"><span data-stu-id="bed9d-159">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="bed9d-160">Determinare se l'eccezione di memoria esaurita è gestita.</span><span class="sxs-lookup"><span data-stu-id="bed9d-160">Determine whether the out-of-memory exception is managed.</span></span>](#OOMIsManaged)<br /><br /> [<span data-ttu-id="bed9d-161">Determinare la quantità di memoria virtuale che è possibile riservare.</span><span class="sxs-lookup"><span data-stu-id="bed9d-161">Determine how much virtual memory can be reserved.</span></span>](#GetVM)<br /><br /> [<span data-ttu-id="bed9d-162">Determinare se è disponibile memoria fisica sufficiente.</span><span class="sxs-lookup"><span data-stu-id="bed9d-162">Determine whether there is enough physical memory.</span></span>](#Physical)|

<span data-ttu-id="bed9d-163">Se si determina che l'eccezione non è legittima, contattare il Supporto tecnico Microsoft avendo a portata di mano le informazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="bed9d-163">If you determine that the exception is not legitimate, contact Microsoft Customer Service and Support with the following information:</span></span>

- <span data-ttu-id="bed9d-164">Stack con l'eccezione di memoria esaurita gestita.</span><span class="sxs-lookup"><span data-stu-id="bed9d-164">The stack with the managed out-of-memory exception.</span></span>

- <span data-ttu-id="bed9d-165">Dump di memoria completo.</span><span class="sxs-lookup"><span data-stu-id="bed9d-165">Full memory dump.</span></span>

- <span data-ttu-id="bed9d-166">Dati che dimostrano che non si tratta di un'eccezione di memoria esaurita legittima, inclusi quelli che indicano che la memoria fisica o virtuale non è la causa del problema.</span><span class="sxs-lookup"><span data-stu-id="bed9d-166">Data that proves that it is not a legitimate out-of-memory exception, including data that shows that virtual or physical memory is not an issue.</span></span>

<a name="Issue_TooMuchMemory"></a>

### <a name="issue-the-process-uses-too-much-memory"></a><span data-ttu-id="bed9d-167">Problema: Il processo usa una quantità eccessiva di memoria</span><span class="sxs-lookup"><span data-stu-id="bed9d-167">Issue: The Process Uses Too Much Memory</span></span>

<span data-ttu-id="bed9d-168">Un presupposto comune è che l'uso della memoria visualizzato nella scheda **Prestazioni** di Gestione attività di Windows può indicare quando viene usata una quantità eccessiva di memoria.</span><span class="sxs-lookup"><span data-stu-id="bed9d-168">A common assumption is that the memory usage display on the **Performance** tab of Windows Task Manager can indicate when too much memory is being used.</span></span> <span data-ttu-id="bed9d-169">Tuttavia, queste informazioni visualizzate riguardano il set di lavoro e non l'utilizzo della memoria virtuale.</span><span class="sxs-lookup"><span data-stu-id="bed9d-169">However, that display pertains to the working set; it does not provide information about virtual memory usage.</span></span>

<span data-ttu-id="bed9d-170">Se si determina che il problema è causato dall'heap gestito, è necessario misurare l'heap gestito nel tempo per stabilire gli eventuali modelli.</span><span class="sxs-lookup"><span data-stu-id="bed9d-170">If you determine that the issue is caused by the managed heap, you must measure the managed heap over time to determine any patterns.</span></span>

<span data-ttu-id="bed9d-171">Se si determina che il problema non è causato dall'heap gestito, è necessario usare il debug nativo.</span><span class="sxs-lookup"><span data-stu-id="bed9d-171">If you determine that the problem is not caused by the managed heap, you must use native debugging.</span></span>

|<span data-ttu-id="bed9d-172">Controlli delle prestazioni</span><span class="sxs-lookup"><span data-stu-id="bed9d-172">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="bed9d-173">Determinare la quantità di memoria virtuale che è possibile riservare.</span><span class="sxs-lookup"><span data-stu-id="bed9d-173">Determine how much virtual memory can be reserved.</span></span>](#GetVM)<br /><br /> [<span data-ttu-id="bed9d-174">Determinare la quantità di memoria di cui l'heap gestito esegue il commit.</span><span class="sxs-lookup"><span data-stu-id="bed9d-174">Determine how much memory the managed heap is committing.</span></span>](#ManagedHeapCommit)<br /><br /> [<span data-ttu-id="bed9d-175">Determinare la quantità di memoria riservata dall'heap gestito.</span><span class="sxs-lookup"><span data-stu-id="bed9d-175">Determine how much memory the managed heap reserves.</span></span>](#ManagedHeapReserve)<br /><br /> [<span data-ttu-id="bed9d-176">Determinare gli oggetti di grandi dimensioni nella generazione 2.</span><span class="sxs-lookup"><span data-stu-id="bed9d-176">Determine large objects in generation 2.</span></span>](#ExamineGen2)<br /><br /> [<span data-ttu-id="bed9d-177">Determinare i riferimenti agli oggetti.</span><span class="sxs-lookup"><span data-stu-id="bed9d-177">Determine references to objects.</span></span>](#ObjRef)|

<a name="Issue_NotFastEnough"></a>

### <a name="issue-the-garbage-collector-does-not-reclaim-objects-fast-enough"></a><span data-ttu-id="bed9d-178">Problema: Garbage Collector non recupera gli oggetti in modo abbastanza veloce</span><span class="sxs-lookup"><span data-stu-id="bed9d-178">Issue: The Garbage Collector Does Not Reclaim Objects Fast Enough</span></span>

<span data-ttu-id="bed9d-179">Quando sembra che gli oggetti non vengano recuperati nel modo previsto per l'operazione di Garbage Collection, è necessario determinare se vi siano riferimenti sicuri a tali oggetti.</span><span class="sxs-lookup"><span data-stu-id="bed9d-179">When it appears as if objects are not being reclaimed as expected for garbage collection, you must determine if there are any strong references to those objects.</span></span>

<span data-ttu-id="bed9d-180">È possibile riscontrare questo problema anche se non è stata eseguita alcuna operazione di Garbage Collection per la generazione che contiene un oggetto inutilizzato, a indicare che il finalizzatore per tale oggetto inutilizzato non è stato eseguito.</span><span class="sxs-lookup"><span data-stu-id="bed9d-180">You may also encounter this issue if there has been no garbage collection for the generation that contains a dead object, which indicates that the finalizer for the dead object has not been run.</span></span> <span data-ttu-id="bed9d-181">Ad esempio, ciò è possibile quando si esegue un'applicazione apartment a thread singolo (STA, Single-Threaded Apartment) e il thread che gestisce la coda del finalizzatore non può eseguire chiamate al suo interno.</span><span class="sxs-lookup"><span data-stu-id="bed9d-181">For example, this is possible when you are running a single-threaded apartment (STA) application and the thread that services the finalizer queue cannot call into it.</span></span>

|<span data-ttu-id="bed9d-182">Controlli delle prestazioni</span><span class="sxs-lookup"><span data-stu-id="bed9d-182">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="bed9d-183">Controllare i riferimenti agli oggetti.</span><span class="sxs-lookup"><span data-stu-id="bed9d-183">Check references to objects.</span></span>](#ObjRef)<br /><br /> [<span data-ttu-id="bed9d-184">Determinare se è stato eseguito un finalizzatore.</span><span class="sxs-lookup"><span data-stu-id="bed9d-184">Determine whether a finalizer has been run.</span></span>](#Induce)<br /><br /> [<span data-ttu-id="bed9d-185">Determinare se sono presenti oggetti in attesa di essere finalizzati.</span><span class="sxs-lookup"><span data-stu-id="bed9d-185">Determine whether there are objects waiting to be finalized.</span></span>](#Finalize)|

<a name="Issue_Fragmentation"></a>

### <a name="issue-the-managed-heap-is-too-fragmented"></a><span data-ttu-id="bed9d-186">Problema: L'heap gestito è troppo frammentato</span><span class="sxs-lookup"><span data-stu-id="bed9d-186">Issue: The Managed Heap Is Too fragmented</span></span>

<span data-ttu-id="bed9d-187">Il livello di frammentazione viene calcolato come percentuale di spazio libero rispetto alla memoria totale allocata per la generazione.</span><span class="sxs-lookup"><span data-stu-id="bed9d-187">The fragmentation level is calculated as the ratio of free space over the total allocated memory for the generation.</span></span> <span data-ttu-id="bed9d-188">Per la generazione 2, un livello accettabile di frammentazione non è maggiore del 20%.</span><span class="sxs-lookup"><span data-stu-id="bed9d-188">For generation 2, an acceptable level of fragmentation is no more than 20%.</span></span> <span data-ttu-id="bed9d-189">Poiché la generazione 2 può assumere dimensioni molto grandi, il rapporto di frammentazione è più importante del valore assoluto.</span><span class="sxs-lookup"><span data-stu-id="bed9d-189">Because generation 2 can get very big, the ratio of fragmentation is more important than the absolute value.</span></span>

<span data-ttu-id="bed9d-190">La disponibilità di una quantità elevata di spazio libero nella generazione 0 non costituisce un problema, perché si tratta della generazione in cui vengono allocati nuovi oggetti.</span><span class="sxs-lookup"><span data-stu-id="bed9d-190">Having lots of free space in generation 0 is not a problem because this is the generation where new objects are allocated.</span></span>

<span data-ttu-id="bed9d-191">La frammentazione si verifica sempre nell'heap oggetti grandi in quanto non viene compattato.</span><span class="sxs-lookup"><span data-stu-id="bed9d-191">Fragmentation always occurs in the large object heap because it is not compacted.</span></span> <span data-ttu-id="bed9d-192">Gli oggetti liberi adiacenti vengono naturalmente compressi in un unico spazio per soddisfare le richieste di allocazione di oggetti grandi.</span><span class="sxs-lookup"><span data-stu-id="bed9d-192">Free objects that are adjacent are naturally collapsed into a single space to satisfy large object allocation requests.</span></span>

<span data-ttu-id="bed9d-193">La frammentazione può diventare un problema nella generazione 1 e nella generazione 2.</span><span class="sxs-lookup"><span data-stu-id="bed9d-193">Fragmentation can become a problem in generation 1 and generation 2.</span></span> <span data-ttu-id="bed9d-194">Se in queste generazioni è disponibile una quantità elevata di spazio libero dopo un'operazione di Garbage Collection, potrebbe essere necessario modificare l'utilizzo degli oggetti di un'applicazione e provare a eseguire una nuova valutazione della durata degli oggetti a lungo termine.</span><span class="sxs-lookup"><span data-stu-id="bed9d-194">If these generations have a large amount of free space after a garbage collection, an application's object usage may need modification, and you should consider re-evaluating the lifetime of long-term objects.</span></span>

<span data-ttu-id="bed9d-195">Il blocco eccessivo di oggetti può aumentare la frammentazione.</span><span class="sxs-lookup"><span data-stu-id="bed9d-195">Excessive pinning of objects can increase fragmentation.</span></span> <span data-ttu-id="bed9d-196">Se la frammentazione è elevata, potrebbe essere bloccato un numero eccessivo di oggetti.</span><span class="sxs-lookup"><span data-stu-id="bed9d-196">If fragmentation is high, too many objects could be pinned.</span></span>

<span data-ttu-id="bed9d-197">Se la frammentazione della memoria virtuale impedisce a Garbage Collector di aggiungere segmenti, la causa può essere una delle seguenti:</span><span class="sxs-lookup"><span data-stu-id="bed9d-197">If fragmentation of virtual memory is preventing the garbage collector from adding segments, the causes could be one of the following:</span></span>

- <span data-ttu-id="bed9d-198">Caricamento e scaricamento frequenti di molti assembly di piccole dimensioni.</span><span class="sxs-lookup"><span data-stu-id="bed9d-198">Frequent loading and unloading of many small assemblies.</span></span>

- <span data-ttu-id="bed9d-199">Presenza di troppi riferimenti a oggetti COM durante l'interoperabilità con codice non gestito.</span><span class="sxs-lookup"><span data-stu-id="bed9d-199">Holding too many references to COM objects when interoperating with unmanaged code.</span></span>

- <span data-ttu-id="bed9d-200">Creazione di oggetti temporanei di grandi dimensioni, che fa sì che l'heap grandi oggetti allochi e liberi frequentemente segmenti di heap.</span><span class="sxs-lookup"><span data-stu-id="bed9d-200">Creation of large transient objects, which causes the large object heap to allocate and free heap segments frequently.</span></span>

  <span data-ttu-id="bed9d-201">Quando si ospita CLR, un'applicazione può richiedere che Garbage Collector ne mantenga i segmenti.</span><span class="sxs-lookup"><span data-stu-id="bed9d-201">When hosting the CLR, an application can request that the garbage collector retain its segments.</span></span> <span data-ttu-id="bed9d-202">In questo modo, viene ridotta la frequenza delle allocazioni di segmenti.</span><span class="sxs-lookup"><span data-stu-id="bed9d-202">This reduces the frequency of segment allocations.</span></span> <span data-ttu-id="bed9d-203">A questo scopo, viene usato il contrassegno STARTUP_HOARD_GC_VM nell'[Enumerazione STARTUP_FLAGS](../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="bed9d-203">This is accomplished by using the STARTUP_HOARD_GC_VM flag in the [STARTUP_FLAGS Enumeration](../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span></span>

|<span data-ttu-id="bed9d-204">Controlli delle prestazioni</span><span class="sxs-lookup"><span data-stu-id="bed9d-204">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="bed9d-205">Determinare la quantità di spazio libero nell'heap gestito.</span><span class="sxs-lookup"><span data-stu-id="bed9d-205">Determine the amount of free space in the managed heap.</span></span>](#Fragmented)<br /><br /> [<span data-ttu-id="bed9d-206">Determinare il numero di oggetti bloccati.</span><span class="sxs-lookup"><span data-stu-id="bed9d-206">Determine the number of pinned objects.</span></span>](#Pinned)|

<span data-ttu-id="bed9d-207">Se si ritiene che non sussista una causa legittima per la frammentazione, contattare il Supporto tecnico Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bed9d-207">If you think that there is no legitimate cause for the fragmentation, contact Microsoft Customer Service and Support.</span></span>

<a name="Issue_LongPauses"></a>

### <a name="issue-garbage-collection-pauses-are-too-long"></a><span data-ttu-id="bed9d-208">Problema: Le pause di Garbage Collection sono troppo prolungate</span><span class="sxs-lookup"><span data-stu-id="bed9d-208">Issue: Garbage Collection Pauses Are Too Long</span></span>

<span data-ttu-id="bed9d-209">Poiché le operazioni di Garbage Collection avvengono in tempo reale "soft", un'applicazione deve essere in grado di tollerare alcune pause.</span><span class="sxs-lookup"><span data-stu-id="bed9d-209">Garbage collection operates in soft real time, so an application must be able to tolerate some pauses.</span></span> <span data-ttu-id="bed9d-210">Un criterio che determina l'esecuzione in tempo reale "soft" è che il 95% delle operazioni deve terminare in tempo.</span><span class="sxs-lookup"><span data-stu-id="bed9d-210">A criterion for soft real time is that 95% of the operations must finish on time.</span></span>

<span data-ttu-id="bed9d-211">Nelle operazioni di Garbage Collection simultanee, i thread gestiti possono essere eseguiti durante una raccolta, che significa che le pause sono minime.</span><span class="sxs-lookup"><span data-stu-id="bed9d-211">In concurrent garbage collection, managed threads are allowed to run during a collection, which means that pauses are very minimal.</span></span>

<span data-ttu-id="bed9d-212">Poiché le operazioni di Garbage Collection effimere (generazioni 0 e 1) durano solo pochi millisecondi, la riduzione delle pause non è in genere possibile.</span><span class="sxs-lookup"><span data-stu-id="bed9d-212">Ephemeral garbage collections (generations 0 and 1) last only a few milliseconds, so decreasing pauses is usually not feasible.</span></span> <span data-ttu-id="bed9d-213">Tuttavia, è possibile ridurre le pause nelle raccolte di generazione 2 modificando il modello delle richieste di allocazione da parte di un'applicazione.</span><span class="sxs-lookup"><span data-stu-id="bed9d-213">However, you can decrease the pauses in generation 2 collections by changing the pattern of allocation requests by an application.</span></span>

<span data-ttu-id="bed9d-214">Un altro metodo, più accurato, consiste nell'usare gli [eventi ETW di Garbage Collection](../../../docs/framework/performance/garbage-collection-etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="bed9d-214">Another, more accurate, method is to use [garbage collection ETW events](../../../docs/framework/performance/garbage-collection-etw-events.md).</span></span> <span data-ttu-id="bed9d-215">È possibile individuare gli intervalli di tempo per le raccolte aggiungendo le differenze dei timestamp per una sequenza di eventi.</span><span class="sxs-lookup"><span data-stu-id="bed9d-215">You can find the timings for collections by adding the time stamp differences for a sequence of events.</span></span> <span data-ttu-id="bed9d-216">L'intera sequenza di raccolta include la sospensione del motore di esecuzione, l'operazione di Garbage Collection stessa e la ripresa del motore di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="bed9d-216">The whole collection sequence includes suspension of the execution engine, the garbage collection itself, and the resumption of the execution engine.</span></span>

<span data-ttu-id="bed9d-217">È possibile usare le [notifiche di Garbage Collection](../../../docs/standard/garbage-collection/notifications.md) per determinare se in un server sta per essere eseguita una raccolta di generazione 2 e se le richieste di reindirizzamento a un altro server potrebbero risolvere eventuali problemi relativi alle pause.</span><span class="sxs-lookup"><span data-stu-id="bed9d-217">You can use [Garbage Collection Notifications](../../../docs/standard/garbage-collection/notifications.md) to determine whether a server is about to have a generation 2 collection, and whether rerouting requests to another server could ease any problems with pauses.</span></span>

|<span data-ttu-id="bed9d-218">Controlli delle prestazioni</span><span class="sxs-lookup"><span data-stu-id="bed9d-218">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="bed9d-219">Determinare la durata di un'operazione di Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="bed9d-219">Determine the length of time in a garbage collection.</span></span>](#TimeInGC)<br /><br /> [<span data-ttu-id="bed9d-220">Determinare la causa di un'operazione di Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="bed9d-220">Determine what caused a garbage collection.</span></span>](#Triggered)|

<a name="Issue_Gen0"></a>

### <a name="issue-generation-0-is-too-big"></a><span data-ttu-id="bed9d-221">Problema: La generazione 0 è troppo grande</span><span class="sxs-lookup"><span data-stu-id="bed9d-221">Issue: Generation 0 Is Too Big</span></span>

<span data-ttu-id="bed9d-222">È probabile che la generazione 0 abbia un numero maggiore di oggetti in un sistema a 64 bit, in particolare se si usa un'operazione di Garbage Collection per server invece che per workstation.</span><span class="sxs-lookup"><span data-stu-id="bed9d-222">Generation 0 is likely to have a larger number of objects on a 64-bit system, especially when you use server garbage collection instead of workstation garbage collection.</span></span> <span data-ttu-id="bed9d-223">Ciò è dovuto al fatto che la soglia per attivare un'operazione di Garbage Collection di generazione 0 è maggiore in questi ambienti e le raccolte di generazione 0 possono essere molto più grandi.</span><span class="sxs-lookup"><span data-stu-id="bed9d-223">This is because the threshold to trigger a generation 0 garbage collection is higher in these environments, and generation 0 collections can get much bigger.</span></span> <span data-ttu-id="bed9d-224">Le prestazioni sono migliori quando un'applicazione alloca molta memoria prima dell'attivazione di un'operazione di Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="bed9d-224">Performance is improved when an application allocates more memory before a garbage collection is triggered.</span></span>

<a name="Issue_HighCPU"></a>

### <a name="issue-cpu-usage-during-a-garbage-collection-is-too-high"></a><span data-ttu-id="bed9d-225">Problema: L'utilizzo della CPU durante un'operazione di Garbage Collection è eccessivo</span><span class="sxs-lookup"><span data-stu-id="bed9d-225">Issue: CPU Usage During a Garbage Collection Is Too High</span></span>

<span data-ttu-id="bed9d-226">L'utilizzo della CPU durante un'operazione di Garbage Collection è elevato.</span><span class="sxs-lookup"><span data-stu-id="bed9d-226">CPU usage will be high during a garbage collection.</span></span> <span data-ttu-id="bed9d-227">Se il periodo di tempo del processo è significativo in un'operazione di Garbage Collection, il numero di raccolte è troppo frequente oppure la raccolta dura troppo a lungo.</span><span class="sxs-lookup"><span data-stu-id="bed9d-227">If a significant amount of process time is spent in a garbage collection, the number of collections is too frequent or the collection is lasting too long.</span></span> <span data-ttu-id="bed9d-228">Una frequenza di allocazione di oggetti maggiore nell'heap gestito fa sì che le operazioni di Garbage Collection avvengano più spesso.</span><span class="sxs-lookup"><span data-stu-id="bed9d-228">An increased allocation rate of objects on the managed heap causes garbage collection to occur more frequently.</span></span> <span data-ttu-id="bed9d-229">La riduzione della frequenza di allocazione riduce anche la frequenza delle operazioni di Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="bed9d-229">Decreasing the allocation rate reduces the frequency of garbage collections.</span></span>

<span data-ttu-id="bed9d-230">È possibile monitorare le frequenze di allocazione usando il contatore delle prestazioni `Allocated Bytes/second`.</span><span class="sxs-lookup"><span data-stu-id="bed9d-230">You can monitor allocation rates by using the `Allocated Bytes/second` performance counter.</span></span> <span data-ttu-id="bed9d-231">Per altre informazioni, vedere [Contatori delle prestazioni in .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md).</span><span class="sxs-lookup"><span data-stu-id="bed9d-231">For more information, see [Performance Counters in the .NET Framework](../../../docs/framework/debug-trace-profile/performance-counters.md).</span></span>

<span data-ttu-id="bed9d-232">La durata di una raccolta è principalmente un fattore del numero di oggetti rimanenti in seguito all'allocazione.</span><span class="sxs-lookup"><span data-stu-id="bed9d-232">The duration of a collection is primarily a factor of the number of objects that survive after allocation.</span></span> <span data-ttu-id="bed9d-233">Garbage Collector deve usare una quantità elevata di memoria se restano molti oggetti da raccogliere.</span><span class="sxs-lookup"><span data-stu-id="bed9d-233">The garbage collector must go through a large amount of memory if many objects remain to be collected.</span></span> <span data-ttu-id="bed9d-234">L'attività di compattazione degli oggetti rimanenti richiede molto tempo.</span><span class="sxs-lookup"><span data-stu-id="bed9d-234">The work to compact the survivors is time-consuming.</span></span> <span data-ttu-id="bed9d-235">Per determinare quanti oggetti sono stati gestiti durante una raccolta, impostare un punto di interruzione nel debugger alla fine di un'operazione di Garbage Collection per una generazione specificata.</span><span class="sxs-lookup"><span data-stu-id="bed9d-235">To determine how many objects were handled during a collection, set a breakpoint in the debugger at the end of a garbage collection for a specified generation.</span></span>

|<span data-ttu-id="bed9d-236">Controlli delle prestazioni</span><span class="sxs-lookup"><span data-stu-id="bed9d-236">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="bed9d-237">Determinare se l'utilizzo elevato della CPU è causato dall'operazione di Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="bed9d-237">Determine if high CPU usage is caused by garbage collection.</span></span>](#HighCPU)<br /><br /> [<span data-ttu-id="bed9d-238">Impostare un punto di interruzione alla fine dell'operazione di Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="bed9d-238">Set a breakpoint at the end of garbage collection.</span></span>](#GenBreak)|

[<span data-ttu-id="bed9d-239">Torna all'inizio</span><span class="sxs-lookup"><span data-stu-id="bed9d-239">Back to top</span></span>](#top)

<a name="troubleshooting_guidelines"></a>

## <a name="troubleshooting-guidelines"></a><span data-ttu-id="bed9d-240">Linee guida per la risoluzione dei problemi</span><span class="sxs-lookup"><span data-stu-id="bed9d-240">Troubleshooting Guidelines</span></span>

<span data-ttu-id="bed9d-241">Questa sezione contiene linee guida da tenere presenti quando si inizia a esaminare i problemi.</span><span class="sxs-lookup"><span data-stu-id="bed9d-241">This section describes guidelines that you should consider as you begin your investigations.</span></span>

### <a name="workstation-or-server-garbage-collection"></a><span data-ttu-id="bed9d-242">Garbage Collection per workstation o per server</span><span class="sxs-lookup"><span data-stu-id="bed9d-242">Workstation or Server Garbage Collection</span></span>

<span data-ttu-id="bed9d-243">Determinare se il tipo di Garbage Collection usato è quello corretto.</span><span class="sxs-lookup"><span data-stu-id="bed9d-243">Determine if you are using the correct type of garbage collection.</span></span> <span data-ttu-id="bed9d-244">Se l'applicazione usa più thread e istanze di oggetto, usare Garbage Collection per server anziché per workstation.</span><span class="sxs-lookup"><span data-stu-id="bed9d-244">If your application uses multiple threads and object instances, use server garbage collection instead of workstation garbage collection.</span></span> <span data-ttu-id="bed9d-245">Un'operazione di Garbage Collection per server viene eseguita su più thread, mentre una per workstation richiede l'esecuzione di più istanze di un'applicazione nei rispettivi thread di Garbage Collection e che queste competano per il tempo di CPU.</span><span class="sxs-lookup"><span data-stu-id="bed9d-245">Server garbage collection operates on multiple threads, whereas workstation garbage collection requires multiple instances of an application to run their own garbage collection threads and compete for CPU time.</span></span>

<span data-ttu-id="bed9d-246">Un'applicazione associata a un carico ridotto e che esegue raramente attività in background, ad esempio un servizio, può usare un'operazione di Garbage Collection per workstation con le operazioni di Garbage Collection simultanee disattivate.</span><span class="sxs-lookup"><span data-stu-id="bed9d-246">An application that has a low load and that performs tasks infrequently in the background, such as a service, could use workstation garbage collection with concurrent garbage collection disabled.</span></span>

### <a name="when-to-measure-the-managed-heap-size"></a><span data-ttu-id="bed9d-247">Quando misurare le dimensioni dell'heap gestito</span><span class="sxs-lookup"><span data-stu-id="bed9d-247">When to Measure the Managed Heap Size</span></span>

<span data-ttu-id="bed9d-248">Se non si usa un profiler, è necessario definire un modello di misurazione coerente per diagnosticare con efficacia i problemi di prestazioni.</span><span class="sxs-lookup"><span data-stu-id="bed9d-248">Unless you are using a profiler, you will have to establish a consistent measuring pattern to effectively diagnose performance issues.</span></span> <span data-ttu-id="bed9d-249">Per definire una pianificazione, considerare i punti seguenti:</span><span class="sxs-lookup"><span data-stu-id="bed9d-249">Consider the following points to establish a schedule:</span></span>

- <span data-ttu-id="bed9d-250">Se si esegue una misurazione dopo un'operazione di Garbage Collection di generazione 2, l'intero heap gestito sarò libero da oggetti inutilizzati.</span><span class="sxs-lookup"><span data-stu-id="bed9d-250">If you measure after a generation 2 garbage collection, the entire managed heap will be free of garbage (dead objects).</span></span>

- <span data-ttu-id="bed9d-251">Se si esegue una misurazione immediatamente dopo un'operazione di Garbage Collection di generazione 0, gli oggetti nelle generazioni 1 e 2 non verranno ancora raccolti.</span><span class="sxs-lookup"><span data-stu-id="bed9d-251">If you measure immediately after a generation 0 garbage collection, the objects in generations 1 and 2 will not be collected yet.</span></span>

- <span data-ttu-id="bed9d-252">Se si esegue una misurazione immediatamente prima di un'operazione di Garbage Collection, è necessario misurare tutta l'allocazione possibile prima dell'avvio dell'operazione di Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="bed9d-252">If you measure immediately before a garbage collection, you will measure as much allocation as possible before the garbage collection starts.</span></span>

- <span data-ttu-id="bed9d-253">La misurazione durante un'operazione di Garbage Collection è problematica, perché le strutture di dati di Garbage Collector non sono in uno stato valido per l'attraversamento e potrebbero non essere in grado di fornire i risultati completi.</span><span class="sxs-lookup"><span data-stu-id="bed9d-253">Measuring during a garbage collection is problematic, because the garbage collector data structures are not in a valid state for traversal and may not be able to give you the complete results.</span></span> <span data-ttu-id="bed9d-254">Si tratta di un comportamento correlato alla progettazione.</span><span class="sxs-lookup"><span data-stu-id="bed9d-254">This is by design.</span></span>

- <span data-ttu-id="bed9d-255">Quando si usa un'operazione di Garbage Collection per workstation con un'operazione di Garbage Collection simultanea, gli oggetti recuperati non vengono compattati e di conseguenza le dimensioni dell'heap possono essere uguali o maggiori (la frammentazione può farle apparire maggiori).</span><span class="sxs-lookup"><span data-stu-id="bed9d-255">When you are using workstation garbage collection with concurrent garbage collection, the reclaimed objects are not compacted, so the heap size can be the same or larger (fragmentation can make it appear to be larger).</span></span>

- <span data-ttu-id="bed9d-256">Un'operazione di Garbage Collection simultanea nella generazione 2 viene ritardata quando il carico di memoria fisica è troppo elevato.</span><span class="sxs-lookup"><span data-stu-id="bed9d-256">Concurrent garbage collection on generation 2 is delayed when the physical memory load is too high.</span></span>

<span data-ttu-id="bed9d-257">La procedura seguente descrive come impostare un punto di interruzione per misurare l'heap gestito.</span><span class="sxs-lookup"><span data-stu-id="bed9d-257">The following procedure describes how to set a breakpoint so that you can measure the managed heap.</span></span>

<a name="GenBreak"></a>

#### <a name="to-set-a-breakpoint-at-the-end-of-garbage-collection"></a><span data-ttu-id="bed9d-258">Per impostare un punto di interruzione alla fine dell'operazione di Garbage Collection</span><span class="sxs-lookup"><span data-stu-id="bed9d-258">To set a breakpoint at the end of garbage collection</span></span>

- <span data-ttu-id="bed9d-259">In WinDbg con l'estensione del debugger SOS caricata, digitare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="bed9d-259">In WinDbg with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="bed9d-260">**bp mscorwks!WKS::GCHeap::RestartEE "j (dwo(mscorwks!WKS::GCHeap::GcCondemnedGeneration)==2) 'kb';'g'"**</span><span class="sxs-lookup"><span data-stu-id="bed9d-260">**bp mscorwks!WKS::GCHeap::RestartEE "j (dwo(mscorwks!WKS::GCHeap::GcCondemnedGeneration)==2) 'kb';'g'"**</span></span>

  <span data-ttu-id="bed9d-261">dove **GcCondemnedGeneration** è impostato sulla generazione desiderata.</span><span class="sxs-lookup"><span data-stu-id="bed9d-261">where **GcCondemnedGeneration** is set to the desired generation.</span></span> <span data-ttu-id="bed9d-262">Questo comando richiede simboli privati.</span><span class="sxs-lookup"><span data-stu-id="bed9d-262">This command requires private symbols.</span></span>

  <span data-ttu-id="bed9d-263">Il comando forza un'interruzione se **RestartEE** viene eseguito dopo il recupero di oggetti di generazione 2 per l'operazione di Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="bed9d-263">This command forces a break if **RestartEE** is executed after generation 2 objects have been reclaimed for garbage collection.</span></span>

  <span data-ttu-id="bed9d-264">In un'operazione di Garbage Collection per server, solo un thread chiama **RestartEE**, in modo che il punto di interruzione si verifica solo una volta durante un'operazione di Garbage Collection di generazione 2.</span><span class="sxs-lookup"><span data-stu-id="bed9d-264">In server garbage collection, only one thread calls **RestartEE**, so the breakpoint will occur only once during a generation 2 garbage collection.</span></span>

[<span data-ttu-id="bed9d-265">Torna all'inizio</span><span class="sxs-lookup"><span data-stu-id="bed9d-265">Back to top</span></span>](#top)

<a name="performance_check_procedures"></a>

## <a name="performance-check-procedures"></a><span data-ttu-id="bed9d-266">Procedure di controllo delle prestazioni</span><span class="sxs-lookup"><span data-stu-id="bed9d-266">Performance Check Procedures</span></span>

<span data-ttu-id="bed9d-267">Questa sezione descrive le procedure per isolare la causa del problema di prestazioni:</span><span class="sxs-lookup"><span data-stu-id="bed9d-267">This section describes the following procedures to isolate the cause of your performance issue:</span></span>

- [<span data-ttu-id="bed9d-268">Determinare se il problema è causato da Garbage Collection</span><span class="sxs-lookup"><span data-stu-id="bed9d-268">Determine whether the problem is caused by garbage collection.</span></span>](#IsGC)

- [<span data-ttu-id="bed9d-269">Determinare se l'eccezione di memoria esaurita è gestita.</span><span class="sxs-lookup"><span data-stu-id="bed9d-269">Determine whether the out-of-memory exception is managed.</span></span>](#OOMIsManaged)

- [<span data-ttu-id="bed9d-270">Determinare la quantità di memoria virtuale che è possibile riservare.</span><span class="sxs-lookup"><span data-stu-id="bed9d-270">Determine how much virtual memory can be reserved.</span></span>](#GetVM)

- [<span data-ttu-id="bed9d-271">Determinare se è disponibile memoria fisica sufficiente.</span><span class="sxs-lookup"><span data-stu-id="bed9d-271">Determine whether there is enough physical memory.</span></span>](#Physical)

- [<span data-ttu-id="bed9d-272">Determinare la quantità di memoria di cui l'heap gestito esegue il commit.</span><span class="sxs-lookup"><span data-stu-id="bed9d-272">Determine how much memory the managed heap is committing.</span></span>](#ManagedHeapCommit)

- [<span data-ttu-id="bed9d-273">Determinare la quantità di memoria riservata dall'heap gestito.</span><span class="sxs-lookup"><span data-stu-id="bed9d-273">Determine how much memory the managed heap reserves.</span></span>](#ManagedHeapReserve)

- [<span data-ttu-id="bed9d-274">Determinare gli oggetti di grandi dimensioni nella generazione 2.</span><span class="sxs-lookup"><span data-stu-id="bed9d-274">Determine large objects in generation 2.</span></span>](#ExamineGen2)

- [<span data-ttu-id="bed9d-275">Determinare i riferimenti agli oggetti.</span><span class="sxs-lookup"><span data-stu-id="bed9d-275">Determine references to objects.</span></span>](#ObjRef)

- [<span data-ttu-id="bed9d-276">Determinare se è stato eseguito un finalizzatore.</span><span class="sxs-lookup"><span data-stu-id="bed9d-276">Determine whether a finalizer has been run.</span></span>](#Induce)

- [<span data-ttu-id="bed9d-277">Determinare se sono presenti oggetti in attesa di essere finalizzati.</span><span class="sxs-lookup"><span data-stu-id="bed9d-277">Determine whether there are objects waiting to be finalized.</span></span>](#Finalize)

- [<span data-ttu-id="bed9d-278">Determinare la quantità di spazio libero nell'heap gestito.</span><span class="sxs-lookup"><span data-stu-id="bed9d-278">Determine the amount of free space in the managed heap.</span></span>](#Fragmented)

- [<span data-ttu-id="bed9d-279">Determinare il numero di oggetti bloccati.</span><span class="sxs-lookup"><span data-stu-id="bed9d-279">Determine the number of pinned objects.</span></span>](#Pinned)

- [<span data-ttu-id="bed9d-280">Determinare la durata di un'operazione di Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="bed9d-280">Determine the length of time in a garbage collection.</span></span>](#TimeInGC)

- [<span data-ttu-id="bed9d-281">Determinare che cosa ha attivato un'operazione di Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="bed9d-281">Determine what triggered a garbage collection.</span></span>](#Triggered)

- [<span data-ttu-id="bed9d-282">Determinare se l'utilizzo elevato della CPU è causato da Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="bed9d-282">Determine whether high CPU usage is caused by garbage collection.</span></span>](#HighCPU)

<a name="IsGC"></a>

### <a name="to-determine-whether-the-problem-is-caused-by-garbage-collection"></a><span data-ttu-id="bed9d-283">Per determinare se il problema è causato da Garbage Collection</span><span class="sxs-lookup"><span data-stu-id="bed9d-283">To determine whether the problem is caused by garbage collection</span></span>

- <span data-ttu-id="bed9d-284">Esaminare i due contatori delle prestazioni della memoria seguenti:</span><span class="sxs-lookup"><span data-stu-id="bed9d-284">Examine the following two memory performance counters:</span></span>

  - <span data-ttu-id="bed9d-285">**Percentuale tempo in GC**.</span><span class="sxs-lookup"><span data-stu-id="bed9d-285">**% Time in GC**.</span></span> <span data-ttu-id="bed9d-286">Visualizza la percentuale di tempo trascorso, impiegato per l'esecuzione di un'operazione di Garbage Collection dopo l'ultimo ciclo di Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="bed9d-286">Displays the percentage of elapsed time that was spent performing a garbage collection after the last garbage collection cycle.</span></span> <span data-ttu-id="bed9d-287">Usare questo contatore per determinare se Garbage Collector sta impiegando troppo tempo per rendere disponibile lo spazio dell'heap gestito.</span><span class="sxs-lookup"><span data-stu-id="bed9d-287">Use this counter to determine whether the garbage collector is spending too much time to make managed heap space available.</span></span> <span data-ttu-id="bed9d-288">Se il tempo impiegato nell'operazione di Garbage Collection è relativamente ridotto, ciò può indicare un problema di risorse all'esterno dell'heap gestito.</span><span class="sxs-lookup"><span data-stu-id="bed9d-288">If the time spent in garbage collection is relatively low, that could indicate a resource problem outside the managed heap.</span></span> <span data-ttu-id="bed9d-289">Questo contatore potrebbe non essere accurato se sono interessate operazioni di Garbage Collection simultanee o in background.</span><span class="sxs-lookup"><span data-stu-id="bed9d-289">This counter may not be accurate when concurrent or background garbage collection is involved.</span></span>

  - <span data-ttu-id="bed9d-290">**N. totale di byte con commit**.</span><span class="sxs-lookup"><span data-stu-id="bed9d-290">**# Total committed Bytes**.</span></span> <span data-ttu-id="bed9d-291">Visualizza la quantità di memoria virtuale di cui Garbage Collector ha attualmente eseguito il commit.</span><span class="sxs-lookup"><span data-stu-id="bed9d-291">Displays the amount of virtual memory currently committed by the garbage collector.</span></span> <span data-ttu-id="bed9d-292">Usare questo contatore per determinare se la memoria usata da Garbage Collector è una parte eccessiva della memoria usata dall'applicazione.</span><span class="sxs-lookup"><span data-stu-id="bed9d-292">Use this counter to determine whether the memory consumed by the garbage collector is an excessive portion of the memory that your application uses.</span></span>

  <span data-ttu-id="bed9d-293">La maggior parte dei contatori delle prestazioni della memoria viene aggiornata alla fine di ogni operazione di Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="bed9d-293">Most of the memory performance counters are updated at the end of each garbage collection.</span></span> <span data-ttu-id="bed9d-294">Di conseguenza, i contatori potrebbero non riflettere le attuali condizioni su cui si vuole ottenere informazioni.</span><span class="sxs-lookup"><span data-stu-id="bed9d-294">Therefore, they may not reflect the current conditions that you want information about.</span></span>

<a name="OOMIsManaged"></a>

### <a name="to-determine-whether-the-out-of-memory-exception-is-managed"></a><span data-ttu-id="bed9d-295">Per determinare se l'eccezione di memoria esaurita è gestita</span><span class="sxs-lookup"><span data-stu-id="bed9d-295">To determine whether the out-of-memory exception is managed</span></span>

1. <span data-ttu-id="bed9d-296">Nel debugger WinDbg o di Visual Studio con l'estensione del debugger SOS caricata, digitare il comando di stampa dell'eccezione (**pe**):</span><span class="sxs-lookup"><span data-stu-id="bed9d-296">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the print exception (**pe**) command:</span></span>

    <span data-ttu-id="bed9d-297">**!pe**</span><span class="sxs-lookup"><span data-stu-id="bed9d-297">**!pe**</span></span>

    <span data-ttu-id="bed9d-298">Se l'eccezione è gestita, <xref:System.OutOfMemoryException> viene visualizzato come tipo di eccezione, come mostrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="bed9d-298">If the exception is managed, <xref:System.OutOfMemoryException> is displayed as the exception type, as shown in the following example.</span></span>

    ```
    Exception object: 39594518
    Exception type: System.OutOfMemoryException
    Message: <none>
    InnerException: <none>
    StackTrace (generated):
    ```

2. <span data-ttu-id="bed9d-299">Se l'output non specifica un'eccezione, è necessario determinare il thread da cui proviene l'eccezione di memoria esaurita.</span><span class="sxs-lookup"><span data-stu-id="bed9d-299">If the output does not specify an exception, you have to determine which thread the out-of-memory exception is from.</span></span> <span data-ttu-id="bed9d-300">Digitare il comando seguente nel debugger per mostrare tutti i thread con i rispettivi stack di chiamate:</span><span class="sxs-lookup"><span data-stu-id="bed9d-300">Type the following command in the debugger to show all the threads with their call stacks:</span></span>

    <span data-ttu-id="bed9d-301">**~\*kb**</span><span class="sxs-lookup"><span data-stu-id="bed9d-301">**~\*kb**</span></span>

    <span data-ttu-id="bed9d-302">Il thread con lo stack che include le chiamate dell'eccezione è indicato dall'argomento `RaiseTheException`.</span><span class="sxs-lookup"><span data-stu-id="bed9d-302">The thread with the stack that has exception calls is indicated by the `RaiseTheException` argument.</span></span> <span data-ttu-id="bed9d-303">Si tratta dell'oggetto eccezione gestita.</span><span class="sxs-lookup"><span data-stu-id="bed9d-303">This is the managed exception object.</span></span>

    ```
    28adfb44 7923918f 5b61f2b4 00000000 5b61f2b4 mscorwks!RaiseTheException+0xa0
    ```

3. <span data-ttu-id="bed9d-304">È possibile usare il comando seguente per eseguire il dump delle eccezioni annidate:</span><span class="sxs-lookup"><span data-stu-id="bed9d-304">You can use the following command to dump nested exceptions.</span></span>

    <span data-ttu-id="bed9d-305">**!pe -nested**</span><span class="sxs-lookup"><span data-stu-id="bed9d-305">**!pe -nested**</span></span>

    <span data-ttu-id="bed9d-306">Se non si trova alcuna eccezione, l'eccezione di memoria esaurita proviene da codice non gestito.</span><span class="sxs-lookup"><span data-stu-id="bed9d-306">If you do not find any exceptions, the out-of-memory exception originated from unmanaged code.</span></span>

<a name="GetVM"></a>

### <a name="to-determine-how-much-virtual-memory-can-be-reserved"></a><span data-ttu-id="bed9d-307">Per determinare la quantità di memoria virtuale che è possibile riservare</span><span class="sxs-lookup"><span data-stu-id="bed9d-307">To determine how much virtual memory can be reserved</span></span>

- <span data-ttu-id="bed9d-308">In WinDbg con l'estensione del debugger SOS caricata, digitare il comando seguente per ottenere l'area libera più grande:</span><span class="sxs-lookup"><span data-stu-id="bed9d-308">In WinDbg with the SOS debugger extension loaded, type the following command to get the largest free region:</span></span>

  <span data-ttu-id="bed9d-309">**!address -summary**</span><span class="sxs-lookup"><span data-stu-id="bed9d-309">**!address -summary**</span></span>

  <span data-ttu-id="bed9d-310">L'area libera più grande viene visualizzata come indicato nell'output seguente.</span><span class="sxs-lookup"><span data-stu-id="bed9d-310">The largest free region is displayed as shown in the following output.</span></span>

  ```
  Largest free region: Base 54000000 - Size 0003A980
  ```

  <span data-ttu-id="bed9d-311">In questo esempio la dimensione dell'area libera più grande è circa 24000 KB (3A980 in formato esadecimale).</span><span class="sxs-lookup"><span data-stu-id="bed9d-311">In this example, the size of the largest free region is approximately 24000 KB (3A980 in hexadecimal).</span></span> <span data-ttu-id="bed9d-312">Questa area è molto minore rispetto alle dimensioni richieste da Garbage Collector per un segmento.</span><span class="sxs-lookup"><span data-stu-id="bed9d-312">This region is much smaller than what the garbage collector needs for a segment.</span></span>

  <span data-ttu-id="bed9d-313">-oppure-</span><span class="sxs-lookup"><span data-stu-id="bed9d-313">-or-</span></span>

- <span data-ttu-id="bed9d-314">Utilizzare il comando **vmstat**:</span><span class="sxs-lookup"><span data-stu-id="bed9d-314">Use the **vmstat** command:</span></span>

  <span data-ttu-id="bed9d-315">**!vmstat**</span><span class="sxs-lookup"><span data-stu-id="bed9d-315">**!vmstat**</span></span>

  <span data-ttu-id="bed9d-316">L'area libera più grande corrisponde al valore maggiore nella colonna MAXIMUM, come indicato nell'output seguente.</span><span class="sxs-lookup"><span data-stu-id="bed9d-316">The largest free region is the largest value in the MAXIMUM column, as shown in the following output.</span></span>

  ```
  TYPE        MINIMUM   MAXIMUM     AVERAGE   BLK COUNT   TOTAL
  ~~~~        ~~~~~~~   ~~~~~~~     ~~~~~~~   ~~~~~~~~~~  ~~~~
  Free:
  Small       8K        64K         46K       36          1,671K
  Medium      80K       864K        349K      3           1,047K
  Large       1,384K    1,278,848K  151,834K  12          1,822,015K
  Summary     8K        1,278,848K  35,779K   51          1,824,735K
  ```

<a name="Physical"></a>

### <a name="to-determine-whether-there-is-enough-physical-memory"></a><span data-ttu-id="bed9d-317">Per determinare se è disponibile memoria fisica sufficiente</span><span class="sxs-lookup"><span data-stu-id="bed9d-317">To determine whether there is enough physical memory</span></span>

1. <span data-ttu-id="bed9d-318">Avviare Gestione risorse di Windows.</span><span class="sxs-lookup"><span data-stu-id="bed9d-318">Start Windows Task Manager.</span></span>

2. <span data-ttu-id="bed9d-319">Nella scheda **Prestazioni** osservare il valore di cui è stato eseguito il commit.</span><span class="sxs-lookup"><span data-stu-id="bed9d-319">On the **Performance** tab, look at the committed value.</span></span> <span data-ttu-id="bed9d-320">In Windows 7 osservare il valore di **Commit (KB)** nel **gruppo Sistema**.</span><span class="sxs-lookup"><span data-stu-id="bed9d-320">(In Windows 7, look at **Commit (KB)** in the **System group**.)</span></span>

    <span data-ttu-id="bed9d-321">Se il valore specificato in **Totale** si avvicina al valore di **Limite**, la memoria fisica è insufficiente.</span><span class="sxs-lookup"><span data-stu-id="bed9d-321">If the **Total** is close to the **Limit**, you are running low on physical memory.</span></span>

<a name="ManagedHeapCommit"></a>

### <a name="to-determine-how-much-memory-the-managed-heap-is-committing"></a><span data-ttu-id="bed9d-322">Per determinare la quantità di memoria di cui l'heap gestito esegue il commit</span><span class="sxs-lookup"><span data-stu-id="bed9d-322">To determine how much memory the managed heap is committing</span></span>

- <span data-ttu-id="bed9d-323">Usare il contatore delle prestazioni della memoria `# Total committed bytes` per ottenere il numero di byte di cui l'heap gestito sta eseguendo il commit.</span><span class="sxs-lookup"><span data-stu-id="bed9d-323">Use the `# Total committed bytes` memory performance counter to get the number of bytes that the managed heap is committing.</span></span> <span data-ttu-id="bed9d-324">Garbage Collector esegue il commit dei blocchi in un segmento nel modo necessario e non di tutti allo stesso tempo.</span><span class="sxs-lookup"><span data-stu-id="bed9d-324">The garbage collector commits chunks on a segment as needed, not all at the same time.</span></span>

  > [!NOTE]
  > <span data-ttu-id="bed9d-325">Non usare il contatore delle prestazioni `# Bytes in all Heaps`, perché non rappresenta l'effettivo utilizzo della memoria da parte dell'heap gestito.</span><span class="sxs-lookup"><span data-stu-id="bed9d-325">Do not use the `# Bytes in all Heaps` performance counter, because it does not represent actual memory usage by the managed heap.</span></span> <span data-ttu-id="bed9d-326">La dimensione di una generazione è inclusa in questo valore e corrisponde i n realtà alla dimensione della soglia, ovvero la dimensione che provoca un'operazione di Garbage Collection se la generazione include molti oggetti.</span><span class="sxs-lookup"><span data-stu-id="bed9d-326">The size of a generation is included in this value and is actually its threshold size, that is, the size that induces a garbage collection if the generation is filled with objects.</span></span> <span data-ttu-id="bed9d-327">Di conseguenza, questo valore è in genere uguale a zero.</span><span class="sxs-lookup"><span data-stu-id="bed9d-327">Therefore, this value is usually zero.</span></span>

<a name="ManagedHeapReserve"></a>

### <a name="to-determine-how-much-memory-the-managed-heap-reserves"></a><span data-ttu-id="bed9d-328">Per determinare la quantità di memoria riservata dall'heap gestito</span><span class="sxs-lookup"><span data-stu-id="bed9d-328">To determine how much memory the managed heap reserves</span></span>

- <span data-ttu-id="bed9d-329">Usare il contatore delle prestazioni della memoria `# Total reserved bytes`.</span><span class="sxs-lookup"><span data-stu-id="bed9d-329">Use the `# Total reserved bytes` memory performance counter.</span></span>

  <span data-ttu-id="bed9d-330">Garbage Collector riserva memoria in segmenti ed è possibile determinare il punto di inizio di un segmento usando il comando **eeheap**.</span><span class="sxs-lookup"><span data-stu-id="bed9d-330">The garbage collector reserves memory in segments, and you can determine where a segment starts by using the **eeheap** command.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="bed9d-331">Benché sia possibile determinare la quantità di memoria allocata da Garbage Collector per ogni segmento, le dimensioni dei segmenti sono specifiche dell'implementazione e soggette a modifiche, tra cui aggiornamenti periodici, in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="bed9d-331">Although you can determine the amount of memory the garbage collector allocates for each segment, segment size is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="bed9d-332">L'applicazione non deve dare per scontata o dipendere da una particolare dimensione del segmento, né provare a configurare la quantità di memoria disponibile per le allocazioni di segmenti.</span><span class="sxs-lookup"><span data-stu-id="bed9d-332">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

- <span data-ttu-id="bed9d-333">Nel debugger WinDbg o di Visual Studio con l'estensione del debugger SOS caricata, digitare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="bed9d-333">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="bed9d-334">**!eeheap -gc**</span><span class="sxs-lookup"><span data-stu-id="bed9d-334">**!eeheap -gc**</span></span>

  <span data-ttu-id="bed9d-335">Il risultato è il seguente.</span><span class="sxs-lookup"><span data-stu-id="bed9d-335">The result is as follows.</span></span>

  ```
  Number of GC Heaps: 2
  ------------------------------
  Heap 0 (002db550)
  generation 0 starts at 0x02abe29c
  generation 1 starts at 0x02abdd08
  generation 2 starts at 0x02ab0038
  ephemeral segment allocation context: none
    segment    begin allocated     size
  02ab0000 02ab0038  02aceff4 0x0001efbc(126908)
  Large object heap starts at 0x0aab0038
    segment    begin allocated     size
  0aab0000 0aab0038  0aab2278 0x00002240(8768)
  Heap Size   0x211fc(135676)
  ------------------------------
  Heap 1 (002dc958)
  generation 0 starts at 0x06ab1bd8
  generation 1 starts at 0x06ab1bcc
  generation 2 starts at 0x06ab0038
  ephemeral segment allocation context: none
    segment    begin allocated     size
  06ab0000 06ab0038  06ab3be4 0x00003bac(15276)
  Large object heap starts at 0x0cab0038
    segment    begin allocated     size
  0cab0000 0cab0038  0cab0048 0x00000010(16)
  Heap Size    0x3bbc(15292)
  ------------------------------
  GC Heap Size   0x24db8(150968)
  ```

  <span data-ttu-id="bed9d-336">Gli indirizzi indicati da "segment" sono gli indirizzi iniziali dei segmenti.</span><span class="sxs-lookup"><span data-stu-id="bed9d-336">The addresses indicated by "segment" are the starting addresses of the segments.</span></span>

<a name="ExamineGen2"></a>

### <a name="to-determine-large-objects-in-generation-2"></a><span data-ttu-id="bed9d-337">Per determinare gli oggetti di grandi dimensioni nella generazione 2</span><span class="sxs-lookup"><span data-stu-id="bed9d-337">To determine large objects in generation 2</span></span>

- <span data-ttu-id="bed9d-338">Nel debugger WinDbg o di Visual Studio con l'estensione del debugger SOS caricata, digitare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="bed9d-338">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="bed9d-339">**!dumpheap –stat**</span><span class="sxs-lookup"><span data-stu-id="bed9d-339">**!dumpheap –stat**</span></span>

  <span data-ttu-id="bed9d-340">Se l'heap gestito è di grandi dimensioni, il completamento di **dumpheap** può richiedere alcuni minuti.</span><span class="sxs-lookup"><span data-stu-id="bed9d-340">If the managed heap is big, **dumpheap** may take a while to finish.</span></span>

  <span data-ttu-id="bed9d-341">È possibile iniziare l'analisi dalle ultime righe dell'output, perché elencano gli oggetti che usano la maggior parte dello spazio.</span><span class="sxs-lookup"><span data-stu-id="bed9d-341">You can start analyzing from the last few lines of the output, because they list the objects that use the most space.</span></span> <span data-ttu-id="bed9d-342">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="bed9d-342">For example:</span></span>

  ```
  2c6108d4   173712     14591808 DevExpress.XtraGrid.Views.Grid.ViewInfo.GridCellInfo
  00155f80      533     15216804      Free
  7a747c78   791070     15821400 System.Collections.Specialized.ListDictionary+DictionaryNode
  7a747bac   700930     19626040 System.Collections.Specialized.ListDictionary
  2c64e36c    78644     20762016 DevExpress.XtraEditors.ViewInfo.TextEditViewInfo
  79124228   121143     29064120 System.Object[]
  035f0ee4    81626     35588936 Toolkit.TlkOrder
  00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]
  791242ec    40182     90664128 System.Collections.Hashtable+bucket[]
  790fa3e0  3154024    137881448 System.String
  Total 8454945 objects
  ```

  <span data-ttu-id="bed9d-343">L'ultimo oggetto elencato è una stringa e occupa la maggior parte dello spazio.</span><span class="sxs-lookup"><span data-stu-id="bed9d-343">The last object listed is a string and occupies the most space.</span></span> <span data-ttu-id="bed9d-344">È possibile esaminare l'applicazione per determinare come ottimizzare gli oggetti stringa.</span><span class="sxs-lookup"><span data-stu-id="bed9d-344">You can examine your application to see how your string objects can be optimized.</span></span> <span data-ttu-id="bed9d-345">Per visualizzare le stringhe comprese tra 150 e 200 byte, digitare:</span><span class="sxs-lookup"><span data-stu-id="bed9d-345">To see strings that are between 150 and 200 bytes, type the following:</span></span>

  <span data-ttu-id="bed9d-346">**!dumpheap -type System.String -min 150 -max 200**</span><span class="sxs-lookup"><span data-stu-id="bed9d-346">**!dumpheap -type System.String -min 150 -max 200**</span></span>

  <span data-ttu-id="bed9d-347">Di seguito viene riportato un esempio dei risultati.</span><span class="sxs-lookup"><span data-stu-id="bed9d-347">An example of the results is as follows.</span></span>

  ```
  Address  MT           Size  Gen
  1875d2c0 790fa3e0      152    2 System.String HighlightNullStyle_Blotter_PendingOrder-11_Blotter_PendingOrder-11
  …
  ```

  <span data-ttu-id="bed9d-348">L'uso di un numero intero invece di una stringa per un ID può rivelarsi più efficiente.</span><span class="sxs-lookup"><span data-stu-id="bed9d-348">Using an integer instead of a string for an ID can be more efficient.</span></span> <span data-ttu-id="bed9d-349">Se la stessa stringa è ripetuta migliaia di volte, provare ad applicare l'inserimento di stringhe.</span><span class="sxs-lookup"><span data-stu-id="bed9d-349">If the same string is being repeated thousands of times, consider string interning.</span></span> <span data-ttu-id="bed9d-350">Per altre informazioni sull'inserimento di stringhe, vedere l'argomento di riferimento per il metodo <xref:System.String.Intern%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bed9d-350">For more information about string interning, see the reference topic for the <xref:System.String.Intern%2A?displayProperty=nameWithType> method.</span></span>

<a name="ObjRef"></a>

### <a name="to-determine-references-to-objects"></a><span data-ttu-id="bed9d-351">Per determinare i riferimenti agli oggetti</span><span class="sxs-lookup"><span data-stu-id="bed9d-351">To determine references to objects</span></span>

- <span data-ttu-id="bed9d-352">In WinDbg con l'estensione del debugger SOS caricata, digitare il comando seguente per elencare i riferimenti agli oggetti:</span><span class="sxs-lookup"><span data-stu-id="bed9d-352">In WinDbg with the SOS debugger extension loaded, type the following command to list references to objects:</span></span>

  <span data-ttu-id="bed9d-353">**!gcroot**</span><span class="sxs-lookup"><span data-stu-id="bed9d-353">**!gcroot**</span></span>

  `-or-`

- <span data-ttu-id="bed9d-354">Per determinare i riferimenti per un oggetto specifico, includere l'indirizzo:</span><span class="sxs-lookup"><span data-stu-id="bed9d-354">To determine the references for a specific object, include the address:</span></span>

  <span data-ttu-id="bed9d-355">**!gcroot 1c37b2ac**</span><span class="sxs-lookup"><span data-stu-id="bed9d-355">**!gcroot 1c37b2ac**</span></span>

  <span data-ttu-id="bed9d-356">Le radici trovate negli stack possono essere falsi positivi.</span><span class="sxs-lookup"><span data-stu-id="bed9d-356">Roots found on stacks may be false positives.</span></span> <span data-ttu-id="bed9d-357">Per altre informazioni, usare il comando `!help gcroot`.</span><span class="sxs-lookup"><span data-stu-id="bed9d-357">For more information, use the command `!help gcroot`.</span></span>

  ```
  ebx:Root:19011c5c(System.Windows.Forms.Application+ThreadContext)->
  19010b78(DemoApp.FormDemoApp)->
  19011158(System.Windows.Forms.PropertyStore)->
  … [omitted]
  1c3745ec(System.Data.DataTable)->
  1c3747a8(System.Data.DataColumnCollection)->
  1c3747f8(System.Collections.Hashtable)->
  1c376590(System.Collections.Hashtable+bucket[])->
  1c376c98(System.Data.DataColumn)->
  1c37b270(System.Data.Common.DoubleStorage)->
  1c37b2ac(System.Double[])
  Scan Thread 0 OSTHread 99c
  Scan Thread 6 OSTHread 484
  ```

  <span data-ttu-id="bed9d-358">Il completamento del comando **gcroot** può richiedere molto tempo.</span><span class="sxs-lookup"><span data-stu-id="bed9d-358">The **gcroot** command can take a long time to finish.</span></span> <span data-ttu-id="bed9d-359">Qualsiasi oggetto non recuperato dall'operazione di Garbage Collection è un oggetto attivo.</span><span class="sxs-lookup"><span data-stu-id="bed9d-359">Any object that is not reclaimed by garbage collection is a live object.</span></span> <span data-ttu-id="bed9d-360">Questo significa che una radice mantiene direttamente o indirettamente l'oggetto, motivo per cui **gcroot** deve restituire le informazioni sul percorso dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="bed9d-360">This means that some root is directly or indirectly holding onto the object, so **gcroot** should return path information to the object.</span></span> <span data-ttu-id="bed9d-361">È consigliabile esaminare i grafici restituiti e determinare perché viene ancora fatto riferimento a questi oggetti.</span><span class="sxs-lookup"><span data-stu-id="bed9d-361">You should examine the graphs returned and see why these objects are still referenced.</span></span>

<a name="Induce"></a>

### <a name="to-determine-whether-a-finalizer-has-been-run"></a><span data-ttu-id="bed9d-362">Per determinare se è stato eseguito un finalizzatore</span><span class="sxs-lookup"><span data-stu-id="bed9d-362">To determine whether a finalizer has been run</span></span>

- <span data-ttu-id="bed9d-363">Eseguire un programma di test contenente il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="bed9d-363">Run a test program that contains the following code:</span></span>

  ```csharp
  GC.Collect();
  GC.WaitForPendingFinalizers();
  GC.Collect();
  ```

  <span data-ttu-id="bed9d-364">Se il test risolve il problema, significa che Garbage Collector non ha recuperato gli oggetti perché il finalizzatore per tali oggetti è stato sospeso.</span><span class="sxs-lookup"><span data-stu-id="bed9d-364">If the test resolves the problem, this means that the garbage collector was not reclaiming objects, because the finalizers for those objects had been suspended.</span></span> <span data-ttu-id="bed9d-365">Il metodo <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> permette ai finalizzatori di completare le rispettive attività e corregge il problema.</span><span class="sxs-lookup"><span data-stu-id="bed9d-365">The <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> method enables the finalizers to complete their tasks, and fixes the problem.</span></span>

<a name="Finalize"></a>

### <a name="to-determine-whether-there-are-objects-waiting-to-be-finalized"></a><span data-ttu-id="bed9d-366">Per determinare se sono presenti oggetti in attesa di essere finalizzati</span><span class="sxs-lookup"><span data-stu-id="bed9d-366">To determine whether there are objects waiting to be finalized</span></span>

1. <span data-ttu-id="bed9d-367">Nel debugger WinDbg o di Visual Studio con l'estensione del debugger SOS caricata, digitare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="bed9d-367">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

    <span data-ttu-id="bed9d-368">**!finalizequeue**</span><span class="sxs-lookup"><span data-stu-id="bed9d-368">**!finalizequeue**</span></span>

    <span data-ttu-id="bed9d-369">Osservare il numero di oggetti pronti per la finalizzazione.</span><span class="sxs-lookup"><span data-stu-id="bed9d-369">Look at the number of objects that are ready for finalization.</span></span> <span data-ttu-id="bed9d-370">Se il numero è elevato, è necessario esaminare il motivo per cui i finalizzatori non possono continuare del tutto o in modo abbastanza veloce.</span><span class="sxs-lookup"><span data-stu-id="bed9d-370">If the number is high, you must examine why these finalizers cannot progress at all or cannot progress fast enough.</span></span>

2. <span data-ttu-id="bed9d-371">Per ottenere un output dei thread, digitare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="bed9d-371">To get an output of threads, type the following command:</span></span>

    <span data-ttu-id="bed9d-372">**threads -special**</span><span class="sxs-lookup"><span data-stu-id="bed9d-372">**threads -special**</span></span>

    <span data-ttu-id="bed9d-373">Questo comando genera un output simile al seguente.</span><span class="sxs-lookup"><span data-stu-id="bed9d-373">This command provides output such as the following.</span></span>

    ```
       OSID     Special thread type
    2    cd0    DbgHelper
    3    c18    Finalizer
    4    df0    GC SuspendEE
    ```

    <span data-ttu-id="bed9d-374">Il thread del finalizzatore indica quale finalizzatore, se presente, è attualmente in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="bed9d-374">The finalizer thread indicates which finalizer, if any, is currently being run.</span></span> <span data-ttu-id="bed9d-375">Quando un thread del finalizzatore non esegue alcun finalizzatore, è in attesa di un evento che indichi di eseguire il lavoro.</span><span class="sxs-lookup"><span data-stu-id="bed9d-375">When a finalizer thread is not running any finalizers, it is waiting for an event to tell it to do its work.</span></span> <span data-ttu-id="bed9d-376">Nella maggior parte dei casi il thread del finalizzatore verrà visualizzato in questo stato, perché viene eseguito in THREAD_HIGHEST_PRIORITY e si suppone che completi l'esecuzione dei finalizzatori, se presenti, molto rapidamente.</span><span class="sxs-lookup"><span data-stu-id="bed9d-376">Most of the time you will see the finalizer thread in this state because it runs at THREAD_HIGHEST_PRIORITY and is supposed to finish running finalizers, if any, very quickly.</span></span>

<a name="Fragmented"></a>

### <a name="to-determine-the-amount-of-free-space-in-the-managed-heap"></a><span data-ttu-id="bed9d-377">Per determinare la quantità di spazio libero nell'heap gestito</span><span class="sxs-lookup"><span data-stu-id="bed9d-377">To determine the amount of free space in the managed heap</span></span>

- <span data-ttu-id="bed9d-378">Nel debugger WinDbg o di Visual Studio con l'estensione del debugger SOS caricata, digitare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="bed9d-378">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="bed9d-379">**!dumpheap -type Free -stat**</span><span class="sxs-lookup"><span data-stu-id="bed9d-379">**!dumpheap -type Free -stat**</span></span>

  <span data-ttu-id="bed9d-380">Questo comando visualizza le dimensioni totali di tutti gli oggetti liberi nell'heap gestito, come mostrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="bed9d-380">This command displays the total size of all the free objects on the managed heap, as shown in the following example.</span></span>

  ```
  total 230 objects
  Statistics:
        MT    Count    TotalSize Class Name
  00152b18      230     40958584      Free
  Total 230 objects
  ```

- <span data-ttu-id="bed9d-381">Per determinare lo spazio libero nella generazione 0, digitare il comando seguente per informazioni sull'utilizzo della memoria da parte della generazione:</span><span class="sxs-lookup"><span data-stu-id="bed9d-381">To determine the free space in generation 0, type the following command for memory consumption information by generation:</span></span>

  <span data-ttu-id="bed9d-382">**!eeheap -gc**</span><span class="sxs-lookup"><span data-stu-id="bed9d-382">**!eeheap -gc**</span></span>

  <span data-ttu-id="bed9d-383">Questo comando genera un output simile al seguente.</span><span class="sxs-lookup"><span data-stu-id="bed9d-383">This command displays output similar to the following.</span></span> <span data-ttu-id="bed9d-384">L'ultima riga mostra il segmento effimero.</span><span class="sxs-lookup"><span data-stu-id="bed9d-384">The last line shows the ephemeral segment.</span></span>

  ```
  Heap 0 (0015ad08)
  generation 0 starts at 0x49521f8c
  generation 1 starts at 0x494d7f64
  generation 2 starts at 0x007f0038
  ephemeral segment allocation context: none
  segment  begin     allocated  size
  00178250 7a80d84c  7a82f1cc   0x00021980(137600)
  00161918 78c50e40  78c7056c   0x0001f72c(128812)
  007f0000 007f0038  047eed28   0x03ffecf0(67103984)
  3a120000 3a120038  3a3e84f8   0x002c84c0(2917568)
  46120000 46120038  49e05d04   0x03ce5ccc(63855820)
  ```

- <span data-ttu-id="bed9d-385">Calcolare lo spazio usato dalla generazione 0:</span><span class="sxs-lookup"><span data-stu-id="bed9d-385">Calculate the space used by generation 0:</span></span>

  <span data-ttu-id="bed9d-386">**? 49e05d04-0x49521f8c**</span><span class="sxs-lookup"><span data-stu-id="bed9d-386">**? 49e05d04-0x49521f8c**</span></span>

  <span data-ttu-id="bed9d-387">Il risultato è il seguente.</span><span class="sxs-lookup"><span data-stu-id="bed9d-387">The result is as follows.</span></span> <span data-ttu-id="bed9d-388">La generazione 0 è di circa 9 MB.</span><span class="sxs-lookup"><span data-stu-id="bed9d-388">Generation 0 is approximately 9 MB.</span></span>

  ```
  Evaluate expression: 9321848 = 008e3d78
  ```

- <span data-ttu-id="bed9d-389">Il comando seguente esegue il dump dello spazio libero all'interno dell'intervallo della generazione 0:</span><span class="sxs-lookup"><span data-stu-id="bed9d-389">The following command dumps the free space within the generation 0 range:</span></span>

  <span data-ttu-id="bed9d-390">**!dumpheap -type Free -stat 0x49521f8c 49e05d04**</span><span class="sxs-lookup"><span data-stu-id="bed9d-390">**!dumpheap -type Free -stat 0x49521f8c 49e05d04**</span></span>

  <span data-ttu-id="bed9d-391">Il risultato è il seguente.</span><span class="sxs-lookup"><span data-stu-id="bed9d-391">The result is as follows.</span></span>

  ```
  ------------------------------
  Heap 0
  total 409 objects
  ------------------------------
  Heap 1
  total 0 objects
  ------------------------------
  Heap 2
  total 0 objects
  ------------------------------
  Heap 3
  total 0 objects
  ------------------------------
  total 409 objects
  Statistics:
        MT    Count TotalSize Class Name
  0015a498      409   7296540      Free
  Total 409 objects
  ```

  <span data-ttu-id="bed9d-392">Questo output mostra che la parte di generazione 0 dell'heap usa 9 MB di spazio per gli oggetti e ha 7 MB di spazio libero.</span><span class="sxs-lookup"><span data-stu-id="bed9d-392">This output shows that the generation 0 portion of the heap is using 9 MB of space for objects and has 7 MB free.</span></span> <span data-ttu-id="bed9d-393">Questa analisi mostra in quale misura la generazione 0 contribuisce alla frammentazione.</span><span class="sxs-lookup"><span data-stu-id="bed9d-393">This analysis shows the extent to which generation 0 contributes to fragmentation.</span></span> <span data-ttu-id="bed9d-394">Questa quantità di utilizzo dell'heap deve essere sottratta dalla quantità locale come causa di frammentazione da parte di oggetti a lungo termine.</span><span class="sxs-lookup"><span data-stu-id="bed9d-394">This amount of heap usage should be discounted from the total amount as the cause of fragmentation by long-term objects.</span></span>

<a name="Pinned"></a>

### <a name="to-determine-the-number-of-pinned-objects"></a><span data-ttu-id="bed9d-395">Per determinare il numero di oggetti bloccati</span><span class="sxs-lookup"><span data-stu-id="bed9d-395">To determine the number of pinned objects</span></span>

- <span data-ttu-id="bed9d-396">Nel debugger WinDbg o di Visual Studio con l'estensione del debugger SOS caricata, digitare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="bed9d-396">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="bed9d-397">**!gchandles**</span><span class="sxs-lookup"><span data-stu-id="bed9d-397">**!gchandles**</span></span>

  <span data-ttu-id="bed9d-398">Le statistiche visualizzate includono il numero di handle bloccati, come indicato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="bed9d-398">The statistics displayed includes the number of pinned handles, as the following example shows.</span></span>

  ```
  GC Handle Statistics:
  Strong Handles:      29
  Pinned Handles:      10
  ```

<a name="TimeInGC"></a>

### <a name="to-determine-the-length-of-time-in-a-garbage-collection"></a><span data-ttu-id="bed9d-399">Per determinare il periodo di tempo in un'operazione di Garbage Collection</span><span class="sxs-lookup"><span data-stu-id="bed9d-399">To determine the length of time in a garbage collection</span></span>

- <span data-ttu-id="bed9d-400">Esaminare il contatore delle prestazioni della memoria `% Time in GC`.</span><span class="sxs-lookup"><span data-stu-id="bed9d-400">Examine the `% Time in GC` memory performance counter.</span></span>

  <span data-ttu-id="bed9d-401">Il valore viene calcolato usando un intervallo di tempo di esempio.</span><span class="sxs-lookup"><span data-stu-id="bed9d-401">The value is calculated by using a sample interval time.</span></span> <span data-ttu-id="bed9d-402">Poiché i contatori vengono aggiornati alla fine di ogni operazione di Garbage Collection, l'esempio corrente avrà lo stesso valore di quello precedente se durante l'intervallo non è stata eseguita alcuna raccolta.</span><span class="sxs-lookup"><span data-stu-id="bed9d-402">Because the counters are updated at the end of each garbage collection, the current sample will have the same value as the previous sample if no collections occurred during the interval.</span></span>

  <span data-ttu-id="bed9d-403">La durata della raccolta viene ottenuta moltiplicando l'intervallo di esempio per il valore percentuale.</span><span class="sxs-lookup"><span data-stu-id="bed9d-403">Collection time is obtained by multiplying the sample interval time with the percentage value.</span></span>

  <span data-ttu-id="bed9d-404">I dati seguenti mostrano quattro intervalli di campionamento di due secondi, per uno studio di otto secondi.</span><span class="sxs-lookup"><span data-stu-id="bed9d-404">The following data shows four sampling intervals of two seconds, for an 8-second study.</span></span> <span data-ttu-id="bed9d-405">Le colonne `Gen0`, `Gen1` e `Gen2` mostrano il numero di operazioni di Garbage Collection eseguite durante l'intervallo per la generazione.</span><span class="sxs-lookup"><span data-stu-id="bed9d-405">The `Gen0`, `Gen1`, and `Gen2` columns show the number of garbage collections that occurred during that interval for that generation.</span></span>

  ```
  Interval    Gen0    Gen1    Gen2    % Time in GC
          1       9       3       1              10
          2      10       3       1               1
          3      11       3       1               3
          4      11       3       1               3
  ```

  <span data-ttu-id="bed9d-406">Queste informazioni non indicano quando è avvenuta l'operazione di Garbage Collection, ma è possibile determinare il numero di operazioni di Garbage Collection eseguite in un intervallo di tempo specifico.</span><span class="sxs-lookup"><span data-stu-id="bed9d-406">This information does not show when the garbage collection occurred, but you can determine the number of garbage collections that occurred in an interval of time.</span></span> <span data-ttu-id="bed9d-407">Presupponendo il caso peggiore, la decima operazione di Garbage Collection di generazione 0 è terminata all'inizio del secondo intervallo, mentre l'undicesima è terminata alla fine del quinto intervallo.</span><span class="sxs-lookup"><span data-stu-id="bed9d-407">Assuming the worst case, the tenth generation 0 garbage collection finished at the start of the second interval, and the eleventh generation 0 garbage collection finished at the end of the fifth interval.</span></span> <span data-ttu-id="bed9d-408">Poiché l'intervallo di tempo tra la fine della decima e la fine dell'undicesima operazione di Garbage Collection è circa 2 secondi e il contatore delle prestazioni indica 3%, la durata dell'undicesima operazione di Garbage Collection di generazione 0 è pari a (2 secondi \* 3% = 60 ms).</span><span class="sxs-lookup"><span data-stu-id="bed9d-408">The time between the end of the tenth and the end of the eleventh garbage collection is about 2 seconds, and the performance counter shows 3%, so the duration of the eleventh generation 0 garbage collection was (2 seconds \* 3% = 60ms).</span></span>

  <span data-ttu-id="bed9d-409">Questo esempio include cinque periodi.</span><span class="sxs-lookup"><span data-stu-id="bed9d-409">In this example, there are 5 periods.</span></span>

  ```
  Interval    Gen0    Gen1    Gen2     % Time in GC
          1       9       3       1                3
          2      10       3       1                1
          3      11       4       2                1
          4      11       4       2                1
          5      11       4       2               20
  ```

  <span data-ttu-id="bed9d-410">La seconda operazione di Garbage Collection di generazione 2 è iniziata durante il terzo intervallo ed è terminata durante il quinto intervallo.</span><span class="sxs-lookup"><span data-stu-id="bed9d-410">The second generation 2 garbage collection started during the third interval and finished at the fifth interval.</span></span> <span data-ttu-id="bed9d-411">Presupponendo il caso peggiore, l'ultima operazione di Garbage Collection è avvenuta per una raccolta di generazione 0 terminata all'inizio del secondo intervallo, mentre l'operazione di Garbage Collection di generazione 2 è terminata alla fine del quinto intervallo.</span><span class="sxs-lookup"><span data-stu-id="bed9d-411">Assuming the worst case, the last garbage collection was for a generation 0 collection that finished at the start of the second interval, and the generation 2 garbage collection finished at the end of the fifth interval.</span></span> <span data-ttu-id="bed9d-412">Di conseguenza, l'intervallo di tempo tra la fine dell'operazione di Garbage Collection di generazione 0 e la fine dell'operazione di Garbage Collection di generazione 2 è 4 secondi.</span><span class="sxs-lookup"><span data-stu-id="bed9d-412">Therefore, the time between the end of the generation 0 garbage collection and the end of the generation 2 garbage collection is 4 seconds.</span></span> <span data-ttu-id="bed9d-413">Poiché il contatore `% Time in GC` indica 20%, la quantità massima di tempo che l'operazione di Garbage Collection di generazione 2 avrebbe potuto impiegare è (4 secondi \* 20% = 800 ms).</span><span class="sxs-lookup"><span data-stu-id="bed9d-413">Because the `% Time in GC` counter is 20%, the maximum amount of time the generation 2 garbage collection could have taken is (4 seconds \* 20% = 800ms).</span></span>

- <span data-ttu-id="bed9d-414">In alternativa, è possibile determinare la lunghezza di un'operazione di Garbage Collection usando gli [eventi ETW di Garbage Collection](../../../docs/framework/performance/garbage-collection-etw-events.md) e analizzando le informazioni per stabilire la durata dell'operazione di Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="bed9d-414">Alternatively, you can determine the length of a garbage collection by using [garbage collection ETW events](../../../docs/framework/performance/garbage-collection-etw-events.md), and analyze the information to determine the duration of garbage collection.</span></span>

  <span data-ttu-id="bed9d-415">Ad esempio, i dati seguenti mostrano una sequenza di eventi verificatasi durante un'operazione di Garbage Collection non simultanea.</span><span class="sxs-lookup"><span data-stu-id="bed9d-415">For example, the following data shows an event sequence that occurred during a non-concurrent garbage collection.</span></span>

  ```
  Timestamp    Event name
  513052        GCSuspendEEBegin_V1
  513078        GCSuspendEEEnd
  513090        GCStart_V1
  517890        GCEnd_V1
  517894        GCHeapStats
  517897        GCRestartEEBegin
  517918        GCRestartEEEnd
  ```

  <span data-ttu-id="bed9d-416">La sospensione del thread gestito ha richiesto 26 us (`GCSuspendEEEnd` - `GCSuspendEEBegin_V1`).</span><span class="sxs-lookup"><span data-stu-id="bed9d-416">Suspending the managed thread took 26us (`GCSuspendEEEnd` – `GCSuspendEEBegin_V1`).</span></span>

  <span data-ttu-id="bed9d-417">L'effettiva operazione di Garbage Collection ha richiesto 4,8 ms (`GCEnd_V1` - `GCStart_V1`).</span><span class="sxs-lookup"><span data-stu-id="bed9d-417">The actual garbage collection took 4.8ms (`GCEnd_V1` – `GCStart_V1`).</span></span>

  <span data-ttu-id="bed9d-418">La ripresa dei thread gestiti ha richiesto 21 us (`GCRestartEEEnd` - `GCRestartEEBegin`).</span><span class="sxs-lookup"><span data-stu-id="bed9d-418">Resuming the managed threads took 21us (`GCRestartEEEnd` – `GCRestartEEBegin`).</span></span>

  <span data-ttu-id="bed9d-419">L'output seguente offre un esempio di un'operazione di Garbage Collection in background e include il processo, il thread e i campi evento.</span><span class="sxs-lookup"><span data-stu-id="bed9d-419">The following output provides an example for background garbage collection, and includes the process, thread, and event fields.</span></span> <span data-ttu-id="bed9d-420">Non tutti i dati vengono visualizzati.</span><span class="sxs-lookup"><span data-stu-id="bed9d-420">(Not all data is shown.)</span></span>

  ```
  timestamp(us)    event name            process    thread    event field
  42504385        GCSuspendEEBegin_V1    Test.exe    4372             1
  42504648        GCSuspendEEEnd         Test.exe    4372
  42504816        GCStart_V1             Test.exe    4372        102019
  42504907        GCStart_V1             Test.exe    4372        102020
  42514170        GCEnd_V1               Test.exe    4372
  42514204        GCHeapStats            Test.exe    4372        102020
  42832052        GCRestartEEBegin       Test.exe    4372
  42832136        GCRestartEEEnd         Test.exe    4372
  63685394        GCSuspendEEBegin_V1    Test.exe    4744             6
  63686347        GCSuspendEEEnd         Test.exe    4744
  63784294        GCRestartEEBegin       Test.exe    4744
  63784407        GCRestartEEEnd         Test.exe    4744
  89931423        GCEnd_V1               Test.exe    4372        102019
  89931464        GCHeapStats            Test.exe    4372
  ```

  <span data-ttu-id="bed9d-421">L'evento `GCStart_V1` in corrispondenza di 42504816 indica che si tratta di un'operazione di Garbage Collection in background, perché l'ultimo campo è `1`.</span><span class="sxs-lookup"><span data-stu-id="bed9d-421">The `GCStart_V1` event at 42504816 indicates that this is a background garbage collection, because the last field is `1`.</span></span> <span data-ttu-id="bed9d-422">Questa diventa l'operazione di Garbage Collection n.</span><span class="sxs-lookup"><span data-stu-id="bed9d-422">This becomes garbage collection No.</span></span> <span data-ttu-id="bed9d-423">102019.</span><span class="sxs-lookup"><span data-stu-id="bed9d-423">102019.</span></span>

  <span data-ttu-id="bed9d-424">L'evento `GCStart` si verifica perché è necessaria un'operazione di Garbage Collection effimera prima di avviare un'operazione di Garbage Collection in background.</span><span class="sxs-lookup"><span data-stu-id="bed9d-424">The `GCStart` event occurs because there is a need for an ephemeral garbage collection before you start a background garbage collection.</span></span> <span data-ttu-id="bed9d-425">Questa diventa l'operazione di Garbage Collection n.</span><span class="sxs-lookup"><span data-stu-id="bed9d-425">This becomes garbage collection No.</span></span> <span data-ttu-id="bed9d-426">102020.</span><span class="sxs-lookup"><span data-stu-id="bed9d-426">102020.</span></span>

  <span data-ttu-id="bed9d-427">In corrispondenza di 42514170, l'operazione di Garbage Collection n.</span><span class="sxs-lookup"><span data-stu-id="bed9d-427">At 42514170, garbage collection No.</span></span> <span data-ttu-id="bed9d-428">102020 viene completata.</span><span class="sxs-lookup"><span data-stu-id="bed9d-428">102020 finishes.</span></span> <span data-ttu-id="bed9d-429">I thread gestiti vengono riavviati a questo punto.</span><span class="sxs-lookup"><span data-stu-id="bed9d-429">The managed threads are restarted at this point.</span></span> <span data-ttu-id="bed9d-430">Questa operazione viene completata nel thread 4372, che ha attivato l'operazione di Garbage Collection in background.</span><span class="sxs-lookup"><span data-stu-id="bed9d-430">This is completed on thread 4372, which triggered this background garbage collection.</span></span>

  <span data-ttu-id="bed9d-431">Nel thread 4744 si verifica una sospensione.</span><span class="sxs-lookup"><span data-stu-id="bed9d-431">On thread 4744, a suspension occurs.</span></span> <span data-ttu-id="bed9d-432">Si tratta dell'unica volta in cui l'operazione di Garbage Collection in background deve sospendere i thread gestiti.</span><span class="sxs-lookup"><span data-stu-id="bed9d-432">This is the only time at which the background garbage collection has to suspend managed threads.</span></span> <span data-ttu-id="bed9d-433">Questa durata è di circa 99 ms ((63784407-63685394)/1000).</span><span class="sxs-lookup"><span data-stu-id="bed9d-433">This duration is approximately 99ms ((63784407-63685394)/1000).</span></span>

  <span data-ttu-id="bed9d-434">L'evento `GCEnd` per l'attività di Garbage Collection in background si trova in corrispondenza di 89931423.</span><span class="sxs-lookup"><span data-stu-id="bed9d-434">The `GCEnd` event for the background garbage collection is at 89931423.</span></span> <span data-ttu-id="bed9d-435">Di conseguenza, l'operazione di Garbage Collection è durata circa 47 secondi ((89931423-42504816)/1000).</span><span class="sxs-lookup"><span data-stu-id="bed9d-435">This means that the background garbage collection lasted for about 47seconds ((89931423-42504816)/1000).</span></span>

  <span data-ttu-id="bed9d-436">Durante l'esecuzione dei thread gestiti, è possibile visualizzare un numero qualsiasi di operazioni di Garbage Collection effimere in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="bed9d-436">While the managed threads are running, you can see any number of ephemeral garbage collections occurring.</span></span>

<a name="Triggered"></a>

### <a name="to-determine-what-triggered-a-garbage-collection"></a><span data-ttu-id="bed9d-437">Per determinare che cosa ha attivato un'operazione di Garbage Collection</span><span class="sxs-lookup"><span data-stu-id="bed9d-437">To determine what triggered a garbage collection</span></span>

- <span data-ttu-id="bed9d-438">Nel debugger WinDbg o di Visual Studio con l'estensione del debugger SOS caricata, digitare il comando seguente per mostrare tutti i thread con i rispettivi stack di chiamate:</span><span class="sxs-lookup"><span data-stu-id="bed9d-438">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command to show all the threads with their call stacks:</span></span>

  <span data-ttu-id="bed9d-439">**~\*kb**</span><span class="sxs-lookup"><span data-stu-id="bed9d-439">**~\*kb**</span></span>

  <span data-ttu-id="bed9d-440">Questo comando genera un output simile al seguente.</span><span class="sxs-lookup"><span data-stu-id="bed9d-440">This command displays output similar to the following.</span></span>

  ```
  0012f3b0 79ff0bf8 mscorwks!WKS::GCHeap::GarbageCollect
  0012f454 30002894 mscorwks!GCInterface::CollectGeneration+0xa4
  0012f490 79fa22bd fragment_ni!request.Main(System.String[])+0x48
  ```

  <span data-ttu-id="bed9d-441">Se l'operazione di Garbage Collection è stata provocata da una notifica di memoria insufficiente dal sistema operativo, lo stack di chiamate è simile, ad eccezione del fatto che il thread è il thread del finalizzatore.</span><span class="sxs-lookup"><span data-stu-id="bed9d-441">If the garbage collection was caused by a low memory notification from the operating system, the call stack is similar, except that the thread is the finalizer thread.</span></span> <span data-ttu-id="bed9d-442">Il thread del finalizzatore ottiene una notifica di memoria insufficiente asincrona e provoca l'operazione di Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="bed9d-442">The finalizer thread gets an asynchronous low memory notification and induces the garbage collection.</span></span>

  <span data-ttu-id="bed9d-443">Se l'operazione di Garbage Collection è stata causata dall'allocazione di memoria, lo stack viene visualizzato in questo modo:</span><span class="sxs-lookup"><span data-stu-id="bed9d-443">If the garbage collection was caused by memory allocation, the stack appears as follows:</span></span>

  ```
  0012f230 7a07c551 mscorwks!WKS::GCHeap::GarbageCollectGeneration
  0012f2b8 7a07cba8 mscorwks!WKS::gc_heap::try_allocate_more_space+0x1a1
  0012f2d4 7a07cefb mscorwks!WKS::gc_heap::allocate_more_space+0x18
  0012f2f4 7a02a51b mscorwks!WKS::GCHeap::Alloc+0x4b
  0012f310 7a02ae4c mscorwks!Alloc+0x60
  0012f364 7a030e46 mscorwks!FastAllocatePrimitiveArray+0xbd
  0012f424 300027f4 mscorwks!JIT_NewArr1+0x148
  000af70f 3000299f fragment_ni!request..ctor(Int32, Single)+0x20c
  0000002a 79fa22bd fragment_ni!request.Main(System.String[])+0x153
  ```

  <span data-ttu-id="bed9d-444">Un helper JIT (`JIT_New*`) chiama infine `GCHeap::GarbageCollectGeneration`.</span><span class="sxs-lookup"><span data-stu-id="bed9d-444">A just-in-time helper (`JIT_New*`) eventually calls `GCHeap::GarbageCollectGeneration`.</span></span> <span data-ttu-id="bed9d-445">Se si determina che le operazioni di Garbage Collection di generazione 2 sono causate da allocazioni, è necessario definire gli oggetti raccolti da tali operazioni e come evitarli.</span><span class="sxs-lookup"><span data-stu-id="bed9d-445">If you determine that generation 2 garbage collections are caused by allocations, you must determine which objects are collected by a generation 2 garbage collection and how to avoid them.</span></span> <span data-ttu-id="bed9d-446">Ovvero, si vuole determinare la differenza tra l'inizio e la fine di un'operazione di Garbage Collection di generazione 2, nonché gli oggetti che hanno provocato la raccolta di generazione 2.</span><span class="sxs-lookup"><span data-stu-id="bed9d-446">That is, you want to determine the difference between the start and the end of a generation 2 garbage collection, and the objects that caused the generation 2 collection.</span></span>

  <span data-ttu-id="bed9d-447">Ad esempio, digitare il comando seguente nel debugger per mostrare l'inizio di una raccolta di generazione 2:</span><span class="sxs-lookup"><span data-stu-id="bed9d-447">For example, type the following command in the debugger to show the beginning of a generation 2 collection:</span></span>

  <span data-ttu-id="bed9d-448">**!dumpheap –stat**</span><span class="sxs-lookup"><span data-stu-id="bed9d-448">**!dumpheap –stat**</span></span>

  <span data-ttu-id="bed9d-449">Output di esempio (abbreviato per mostrare gli oggetti che usano la maggior parte dello spazio):</span><span class="sxs-lookup"><span data-stu-id="bed9d-449">Example output (abridged to show the objects that use the most space):</span></span>

  ```
  79124228    31857      9862328 System.Object[]
  035f0384    25668     11601936 Toolkit.TlkPosition
  00155f80    21248     12256296      Free
  79103b6c   297003     13068132 System.Threading.ReaderWriterLock
  7a747ad4   708732     14174640 System.Collections.Specialized.HybridDictionary
  7a747c78   786498     15729960 System.Collections.Specialized.ListDictionary+DictionaryNode
  7a747bac   700298     19608344 System.Collections.Specialized.ListDictionary
  035f0ee4    89192     38887712 Toolkit.TlkOrder
  00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]
  7912c444    91616     71887080 System.Double[]
  791242ec    32451     82462728 System.Collections.Hashtable+bucket[]
  790fa3e0  2459154    112128436 System.String
  Total 6471774 objects
  ```

  <span data-ttu-id="bed9d-450">Ripetere il comando alla fine della generazione 2:</span><span class="sxs-lookup"><span data-stu-id="bed9d-450">Repeat the command at the end of generation 2:</span></span>

  <span data-ttu-id="bed9d-451">**!dumpheap –stat**</span><span class="sxs-lookup"><span data-stu-id="bed9d-451">**!dumpheap –stat**</span></span>

  <span data-ttu-id="bed9d-452">Output di esempio (abbreviato per mostrare gli oggetti che usano la maggior parte dello spazio):</span><span class="sxs-lookup"><span data-stu-id="bed9d-452">Example output (abridged to show the objects that use the most space):</span></span>

  ```
  79124228    26648      9314256 System.Object[]
  035f0384    25668     11601936 Toolkit.TlkPosition
  79103b6c   296770     13057880 System.Threading.ReaderWriterLock
  7a747ad4   708730     14174600 System.Collections.Specialized.HybridDictionary
  7a747c78   786497     15729940 System.Collections.Specialized.ListDictionary+DictionaryNode
  7a747bac   700298     19608344 System.Collections.Specialized.ListDictionary
  00155f80    13806     34007212      Free
  035f0ee4    89187     38885532 Toolkit.TlkOrder
  00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]
  791242ec    32370     82359768 System.Collections.Hashtable+bucket[]
  790fa3e0  2440020    111341808 System.String
  Total 6417525 objects
  ```

  <span data-ttu-id="bed9d-453">Gli oggetti `double[]` sono scomparsi dalla fine dell'output, a indicare che sono stati raccolti.</span><span class="sxs-lookup"><span data-stu-id="bed9d-453">The `double[]` objects disappeared from the end of the output, which means that they were collected.</span></span> <span data-ttu-id="bed9d-454">Questi oggetti corrispondono a circa 70 MB.</span><span class="sxs-lookup"><span data-stu-id="bed9d-454">These objects account for approximately 70 MB.</span></span> <span data-ttu-id="bed9d-455">Gli oggetti rimanenti non sono cambiati molto.</span><span class="sxs-lookup"><span data-stu-id="bed9d-455">The remaining objects did not change much.</span></span> <span data-ttu-id="bed9d-456">Di conseguenza, questi oggetti `double[]` sono il motivo per cui si è verificata un'operazione di Garbage Collection di generazione 2 .</span><span class="sxs-lookup"><span data-stu-id="bed9d-456">Therefore, these `double[]` objects were the reason why this generation 2 garbage collection occurred.</span></span> <span data-ttu-id="bed9d-457">Il passaggio successivo consiste nel determinare il motivo per cui gli oggetti `double[]` sono ancora presenti e perché sono diventati inutilizzati.</span><span class="sxs-lookup"><span data-stu-id="bed9d-457">Your next step is to determine why the `double[]` objects are there and why they died.</span></span> <span data-ttu-id="bed9d-458">È possibile chiedere allo sviluppatore del codice da dove provengono questi oggetti oppure è possibile usare il comando **gcroot**.</span><span class="sxs-lookup"><span data-stu-id="bed9d-458">You can ask the code developer where these objects came from, or you can use the **gcroot** command.</span></span>

<a name="HighCPU"></a>

### <a name="to-determine-whether-high-cpu-usage-is-caused-by-garbage-collection"></a><span data-ttu-id="bed9d-459">Per determinare se l'utilizzo elevato della CPU è causato da Garbage Collection</span><span class="sxs-lookup"><span data-stu-id="bed9d-459">To determine whether high CPU usage is caused by garbage collection</span></span>

- <span data-ttu-id="bed9d-460">Correlare il valore del contatore delle prestazioni della memoria `% Time in GC` alla durata del processo.</span><span class="sxs-lookup"><span data-stu-id="bed9d-460">Correlate the `% Time in GC` memory performance counter value with the process time.</span></span>

  <span data-ttu-id="bed9d-461">Se il valore `% Time in GC` mostra la presenza di picchi contemporaneamente alla durata del processo, l'operazione di Garbage Collection è la causa dell'elevato utilizzo della CPU.</span><span class="sxs-lookup"><span data-stu-id="bed9d-461">If the `% Time in GC` value spikes at the same time as process time, garbage collection is causing a high CPU usage.</span></span> <span data-ttu-id="bed9d-462">In caso contrario, profilare l'applicazione per individuare il punto in cui si verifica un utilizzo elevato.</span><span class="sxs-lookup"><span data-stu-id="bed9d-462">Otherwise, profile the application to find where the high usage is occurring.</span></span>

## <a name="see-also"></a><span data-ttu-id="bed9d-463">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="bed9d-463">See also</span></span>

- [<span data-ttu-id="bed9d-464">Garbage Collection</span><span class="sxs-lookup"><span data-stu-id="bed9d-464">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
