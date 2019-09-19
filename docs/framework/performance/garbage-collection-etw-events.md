---
title: Eventi ETW di Garbage Collection
ms.date: 03/30/2017
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ec90d022a0c72782f413a84b6fbd2c1b8d663a73
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046499"
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="3dc3b-102">Eventi ETW di Garbage Collection</span><span class="sxs-lookup"><span data-stu-id="3dc3b-102">Garbage Collection ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="3dc3b-103">Questi eventi raccolgono informazioni relative alla Garbage Collection</span><span class="sxs-lookup"><span data-stu-id="3dc3b-103">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="3dc3b-104">ai fini della diagnostica e del debug, tra cui stabilire quante volte è stato eseguito il processo di Garbage Collection, la quantità di memoria liberata durante la procedura di Garbage Collection e così via.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-104">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>  
  
 <span data-ttu-id="3dc3b-105">Questa categoria include i seguenti eventi:</span><span class="sxs-lookup"><span data-stu-id="3dc3b-105">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="3dc3b-106">GCStart_V1 Event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-106">GCStart_V1 Event</span></span>](#gcstart_v1_event)  
  
- [<span data-ttu-id="3dc3b-107">GCEnd_V1 Event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-107">GCEnd_V1 Event</span></span>](#gcend_v1_event)  
  
- [<span data-ttu-id="3dc3b-108">GCHeapStats_V1 Event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-108">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1_event)  
  
- [<span data-ttu-id="3dc3b-109">GCCreateSegment_V1 Event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-109">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1_event)  
  
- [<span data-ttu-id="3dc3b-110">GCFreeSegment_V1 Event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-110">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1_event)  
  
- [<span data-ttu-id="3dc3b-111">GCRestartEEBegin_V1 Event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-111">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1_event)  
  
- [<span data-ttu-id="3dc3b-112">GCRestartEEEnd_V1 Event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-112">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1_event)  
  
- [<span data-ttu-id="3dc3b-113">GCSuspendEE_V1 Event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-113">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1_event)  
  
- [<span data-ttu-id="3dc3b-114">GCSuspendEEEnd_V1 Event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-114">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1_event)  
  
- [<span data-ttu-id="3dc3b-115">GCAllocationTick_V2 Event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-115">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2_event)  
  
- [<span data-ttu-id="3dc3b-116">GCFinalizersBegin_V1 Event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-116">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1_event)  
  
- [<span data-ttu-id="3dc3b-117">GCFinalizersEnd_V1 Event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-117">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1_event)  
  
- [<span data-ttu-id="3dc3b-118">GCCreateConcurrentThread_V1 Event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-118">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1_event)  
  
- [<span data-ttu-id="3dc3b-119">GCTerminateConcurrentThread_V1 Event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-119">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1_event)  
  
<a name="gcstart_v1_event"></a>   
## <a name="gcstart_v1-event"></a><span data-ttu-id="3dc3b-120">GCStart_V1 Event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-120">GCStart_V1 Event</span></span>  
 <span data-ttu-id="3dc3b-121">La tabella seguente illustra la parola chiave e il livello</span><span class="sxs-lookup"><span data-stu-id="3dc3b-121">The following table shows the keyword and level.</span></span> <span data-ttu-id="3dc3b-122">Per altre informazioni, vedere [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="3dc3b-122">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="3dc3b-123">Parola chiave per la generazione dell'evento</span><span class="sxs-lookup"><span data-stu-id="3dc3b-123">Keyword for raising the event</span></span>|<span data-ttu-id="3dc3b-124">Level</span><span class="sxs-lookup"><span data-stu-id="3dc3b-124">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="3dc3b-125">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="3dc3b-125">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="3dc3b-126">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="3dc3b-126">Informational (4)</span></span>|  
  
 <span data-ttu-id="3dc3b-127">La tabella seguente mostra le informazioni sull'evento.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-127">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="3dc3b-128">event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-128">Event</span></span>|<span data-ttu-id="3dc3b-129">ID evento</span><span class="sxs-lookup"><span data-stu-id="3dc3b-129">Event ID</span></span>|<span data-ttu-id="3dc3b-130">Generato quando</span><span class="sxs-lookup"><span data-stu-id="3dc3b-130">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCStart_V1`|<span data-ttu-id="3dc3b-131">1</span><span class="sxs-lookup"><span data-stu-id="3dc3b-131">1</span></span>|<span data-ttu-id="3dc3b-132">È stata avviata una procedura di Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-132">A garbage collection has started.</span></span>|  
  
 <span data-ttu-id="3dc3b-133">La tabella seguente mostra i dati dell'evento.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-133">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="3dc3b-134">Nome campo</span><span class="sxs-lookup"><span data-stu-id="3dc3b-134">Field name</span></span>|<span data-ttu-id="3dc3b-135">Tipo di dati</span><span class="sxs-lookup"><span data-stu-id="3dc3b-135">Data type</span></span>|<span data-ttu-id="3dc3b-136">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="3dc3b-136">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="3dc3b-137">Conteggio</span><span class="sxs-lookup"><span data-stu-id="3dc3b-137">Count</span></span>|<span data-ttu-id="3dc3b-138">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="3dc3b-138">win:UInt32</span></span>|<span data-ttu-id="3dc3b-139">L' *ennesima*Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-139">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="3dc3b-140">Profondità</span><span class="sxs-lookup"><span data-stu-id="3dc3b-140">Depth</span></span>|<span data-ttu-id="3dc3b-141">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="3dc3b-141">win:UInt32</span></span>|<span data-ttu-id="3dc3b-142">La generazione che viene raccolta.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-142">The generation that is being collected.</span></span>|  
|<span data-ttu-id="3dc3b-143">`Reason`</span><span class="sxs-lookup"><span data-stu-id="3dc3b-143">Reason</span></span>|<span data-ttu-id="3dc3b-144">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="3dc3b-144">win:UInt32</span></span>|<span data-ttu-id="3dc3b-145">Motivo per cui è stata attivata la Garbage Collection:</span><span class="sxs-lookup"><span data-stu-id="3dc3b-145">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="3dc3b-146">0x0 - Allocazione heap oggetto piccolo.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-146">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="3dc3b-147">0x1 - Indotto.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-147">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="3dc3b-148">0x2 - Memoria insufficiente.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-148">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="3dc3b-149">0x3 - Vuoto.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-149">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="3dc3b-150">0x4 - Allocazione heap oggetto grande.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-150">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="3dc3b-151">0x5 - Spazio esaurito (per heap oggetto piccolo).</span><span class="sxs-lookup"><span data-stu-id="3dc3b-151">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="3dc3b-152">0x6 - Spazio esaurito (per heap oggetto grande).</span><span class="sxs-lookup"><span data-stu-id="3dc3b-152">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="3dc3b-153">0x7 - Indotto ma non forzato come blocco.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-153">0x7 - Induced but not forced as blocking.</span></span>|  
|<span data-ttu-id="3dc3b-154">Type</span><span class="sxs-lookup"><span data-stu-id="3dc3b-154">Type</span></span>|<span data-ttu-id="3dc3b-155">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="3dc3b-155">win:UInt32</span></span>|<span data-ttu-id="3dc3b-156">0x0 - Un'operazione di Garbage Collection bloccante è stata eseguita all'esterno della procedura di Garbage Collection in background.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-156">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="3dc3b-157">0x1 - Garbage Collection in background.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-157">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="3dc3b-158">0x2 - Un'operazione di Garbage Collection bloccante è stata eseguita durante la procedura di Garbage Collection in background.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-158">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|  
|<span data-ttu-id="3dc3b-159">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="3dc3b-159">ClrInstanceID</span></span>|<span data-ttu-id="3dc3b-160">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="3dc3b-160">win:UInt16</span></span>|<span data-ttu-id="3dc3b-161">ID univoco per l'istanza di CLR o CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-161">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="3dc3b-162">Torna all'inizio</span><span class="sxs-lookup"><span data-stu-id="3dc3b-162">Back to top</span></span>](#top)  
  
<a name="gcend_v1_event"></a>   
## <a name="gcend_v1-event"></a><span data-ttu-id="3dc3b-163">GCEnd_V1 Event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-163">GCEnd_V1 Event</span></span>  
 <span data-ttu-id="3dc3b-164">La tabella seguente illustra la parola chiave e il livello</span><span class="sxs-lookup"><span data-stu-id="3dc3b-164">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="3dc3b-165">Parola chiave per la generazione dell'evento</span><span class="sxs-lookup"><span data-stu-id="3dc3b-165">Keyword for raising the event</span></span>|<span data-ttu-id="3dc3b-166">Level</span><span class="sxs-lookup"><span data-stu-id="3dc3b-166">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="3dc3b-167">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="3dc3b-167">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="3dc3b-168">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="3dc3b-168">Informational (4)</span></span>|  
  
 <span data-ttu-id="3dc3b-169">La tabella seguente mostra le informazioni sull'evento.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-169">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="3dc3b-170">event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-170">Event</span></span>|<span data-ttu-id="3dc3b-171">ID evento</span><span class="sxs-lookup"><span data-stu-id="3dc3b-171">Event ID</span></span>|<span data-ttu-id="3dc3b-172">Generato quando</span><span class="sxs-lookup"><span data-stu-id="3dc3b-172">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCEnd_V1`|<span data-ttu-id="3dc3b-173">2</span><span class="sxs-lookup"><span data-stu-id="3dc3b-173">2</span></span>|<span data-ttu-id="3dc3b-174">È stata terminata una procedura di Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-174">The garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="3dc3b-175">La tabella seguente mostra i dati dell'evento.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-175">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="3dc3b-176">Nome campo</span><span class="sxs-lookup"><span data-stu-id="3dc3b-176">Field name</span></span>|<span data-ttu-id="3dc3b-177">Tipo di dati</span><span class="sxs-lookup"><span data-stu-id="3dc3b-177">Data type</span></span>|<span data-ttu-id="3dc3b-178">Descrizione</span><span class="sxs-lookup"><span data-stu-id="3dc3b-178">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="3dc3b-179">Conteggio</span><span class="sxs-lookup"><span data-stu-id="3dc3b-179">Count</span></span>|<span data-ttu-id="3dc3b-180">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="3dc3b-180">win:UInt32</span></span>|<span data-ttu-id="3dc3b-181">L' *ennesima*Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-181">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="3dc3b-182">Profondità</span><span class="sxs-lookup"><span data-stu-id="3dc3b-182">Depth</span></span>|<span data-ttu-id="3dc3b-183">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="3dc3b-183">win:UInt32</span></span>|<span data-ttu-id="3dc3b-184">La generazione che è stata raccolta.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-184">The generation that was collected.</span></span>|  
|<span data-ttu-id="3dc3b-185">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="3dc3b-185">ClrInstanceID</span></span>|<span data-ttu-id="3dc3b-186">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="3dc3b-186">win:UInt16</span></span>|<span data-ttu-id="3dc3b-187">ID univoco per l'istanza di CLR o CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-187">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="3dc3b-188">Torna all'inizio</span><span class="sxs-lookup"><span data-stu-id="3dc3b-188">Back to top</span></span>](#top)  
  
<a name="gcheapstats_v1_event"></a>   
## <a name="gcheapstats_v1-event"></a><span data-ttu-id="3dc3b-189">GCHeapStats_V1 Event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-189">GCHeapStats_V1 Event</span></span>  
 <span data-ttu-id="3dc3b-190">La tabella seguente illustra la parola chiave e il livello</span><span class="sxs-lookup"><span data-stu-id="3dc3b-190">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="3dc3b-191">Parola chiave per la generazione dell'evento</span><span class="sxs-lookup"><span data-stu-id="3dc3b-191">Keyword for raising the event</span></span>|<span data-ttu-id="3dc3b-192">Level</span><span class="sxs-lookup"><span data-stu-id="3dc3b-192">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="3dc3b-193">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="3dc3b-193">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="3dc3b-194">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="3dc3b-194">Informational (4)</span></span>|  
  
 <span data-ttu-id="3dc3b-195">La tabella seguente mostra le informazioni sull'evento.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-195">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="3dc3b-196">event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-196">Event</span></span>|<span data-ttu-id="3dc3b-197">ID evento</span><span class="sxs-lookup"><span data-stu-id="3dc3b-197">Event ID</span></span>|<span data-ttu-id="3dc3b-198">Descrizione</span><span class="sxs-lookup"><span data-stu-id="3dc3b-198">Description</span></span>|  
|-----------|--------------|-----------------|  
|`GCHeapStats_V1`|<span data-ttu-id="3dc3b-199">4</span><span class="sxs-lookup"><span data-stu-id="3dc3b-199">4</span></span>|<span data-ttu-id="3dc3b-200">Mostra le statistiche heap alla fine di ogni Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-200">Shows the heap statistics at the end of each garbage collection.</span></span>|  
  
 <span data-ttu-id="3dc3b-201">La tabella seguente mostra i dati dell'evento.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-201">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="3dc3b-202">Nome campo</span><span class="sxs-lookup"><span data-stu-id="3dc3b-202">Field name</span></span>|<span data-ttu-id="3dc3b-203">Tipo di dati</span><span class="sxs-lookup"><span data-stu-id="3dc3b-203">Data type</span></span>|<span data-ttu-id="3dc3b-204">Descrizione</span><span class="sxs-lookup"><span data-stu-id="3dc3b-204">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="3dc3b-205">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="3dc3b-205">GenerationSize0</span></span>|<span data-ttu-id="3dc3b-206">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="3dc3b-206">win:UInt64</span></span>|<span data-ttu-id="3dc3b-207">Dimensione, in byte, della memoria della generazione 0.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-207">The size, in bytes, of generation 0 memory.</span></span>|  
|<span data-ttu-id="3dc3b-208">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="3dc3b-208">TotalPromotedSize0</span></span>|<span data-ttu-id="3dc3b-209">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="3dc3b-209">win:UInt64</span></span>|<span data-ttu-id="3dc3b-210">Numero di byte promossi dalla generazione 0 alla generazione 1.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-210">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|  
|<span data-ttu-id="3dc3b-211">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="3dc3b-211">GenerationSize1</span></span>|<span data-ttu-id="3dc3b-212">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="3dc3b-212">win:UInt64</span></span>|<span data-ttu-id="3dc3b-213">Dimensione, in byte, della memoria di generazione 1.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-213">The size, in bytes, of generation 1 memory.</span></span>|  
|<span data-ttu-id="3dc3b-214">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="3dc3b-214">TotalPromotedSize1</span></span>|<span data-ttu-id="3dc3b-215">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="3dc3b-215">win:UInt64</span></span>|<span data-ttu-id="3dc3b-216">Numero di byte promossi dalla generazione 1 alla generazione 2.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-216">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|  
|<span data-ttu-id="3dc3b-217">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="3dc3b-217">GenerationSize2</span></span>|<span data-ttu-id="3dc3b-218">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="3dc3b-218">win:UInt64</span></span>|<span data-ttu-id="3dc3b-219">Dimensione, in byte, della memoria della generazione 2.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-219">The size, in bytes, of generation 2 memory.</span></span>|  
|<span data-ttu-id="3dc3b-220">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="3dc3b-220">TotalPromotedSize2</span></span>|<span data-ttu-id="3dc3b-221">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="3dc3b-221">win:UInt64</span></span>|<span data-ttu-id="3dc3b-222">Numero di byte rimasti nella generazione 2 dopo l'ultima raccolta.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-222">The number of bytes that survived in generation 2 after the last collection.</span></span>|  
|<span data-ttu-id="3dc3b-223">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="3dc3b-223">GenerationSize3</span></span>|<span data-ttu-id="3dc3b-224">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="3dc3b-224">win:UInt64</span></span>|<span data-ttu-id="3dc3b-225">Dimensione, in byte, dell'heap oggetto grande.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-225">The size, in bytes, of the large object heap.</span></span>|  
|<span data-ttu-id="3dc3b-226">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="3dc3b-226">TotalPromotedSize3</span></span>|<span data-ttu-id="3dc3b-227">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="3dc3b-227">win:UInt64</span></span>|<span data-ttu-id="3dc3b-228">Numero di byte rimasti nell'heap oggetto grande dopo l'ultima raccolta.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-228">The number of bytes that survived in the large object heap after the last collection.</span></span>|  
|<span data-ttu-id="3dc3b-229">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="3dc3b-229">FinalizationPromotedSize</span></span>|<span data-ttu-id="3dc3b-230">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="3dc3b-230">win:UInt64</span></span>|<span data-ttu-id="3dc3b-231">Dimensione totale, in byte, degli oggetti pronti per la finalizzazione.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-231">The total size, in bytes, of the objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="3dc3b-232">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="3dc3b-232">FinalizationPromotedCount</span></span>|<span data-ttu-id="3dc3b-233">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="3dc3b-233">win:UInt64</span></span>|<span data-ttu-id="3dc3b-234">Numero di oggetti pronti per la finalizzazione.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-234">The number of objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="3dc3b-235">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="3dc3b-235">PinnedObjectCount</span></span>|<span data-ttu-id="3dc3b-236">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="3dc3b-236">win:UInt32</span></span>|<span data-ttu-id="3dc3b-237">Numero di oggetti bloccati (fissi).</span><span class="sxs-lookup"><span data-stu-id="3dc3b-237">The number of pinned (unmovable) objects.</span></span>|  
|<span data-ttu-id="3dc3b-238">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="3dc3b-238">SinkBlockCount</span></span>|<span data-ttu-id="3dc3b-239">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="3dc3b-239">win:UInt32</span></span>|<span data-ttu-id="3dc3b-240">Numero di blocchi di sincronizzazione in uso.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-240">The number of synchronization blocks in use.</span></span>|  
|<span data-ttu-id="3dc3b-241">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="3dc3b-241">GCHandleCount</span></span>|<span data-ttu-id="3dc3b-242">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="3dc3b-242">win:UInt32</span></span>|<span data-ttu-id="3dc3b-243">Numero di handle di Garbage Collection in uso.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-243">The number of garbage collection handles in use.</span></span>|  
|<span data-ttu-id="3dc3b-244">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="3dc3b-244">ClrInstanceID</span></span>|<span data-ttu-id="3dc3b-245">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="3dc3b-245">win:UInt16</span></span>|<span data-ttu-id="3dc3b-246">ID univoco per l'istanza di CLR o CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="3dc3b-247">Torna all'inizio</span><span class="sxs-lookup"><span data-stu-id="3dc3b-247">Back to top</span></span>](#top)  
  
<a name="gccreatesegment_v1_event"></a>   
## <a name="gccreatesegment_v1-event"></a><span data-ttu-id="3dc3b-248">GCCreateSegment_V1 Event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-248">GCCreateSegment_V1 Event</span></span>  
 <span data-ttu-id="3dc3b-249">La tabella seguente illustra la parola chiave e il livello</span><span class="sxs-lookup"><span data-stu-id="3dc3b-249">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="3dc3b-250">Parola chiave per la generazione dell'evento</span><span class="sxs-lookup"><span data-stu-id="3dc3b-250">Keyword for raising the event</span></span>|<span data-ttu-id="3dc3b-251">Level</span><span class="sxs-lookup"><span data-stu-id="3dc3b-251">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="3dc3b-252">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="3dc3b-252">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="3dc3b-253">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="3dc3b-253">Informational (4)</span></span>|  
  
 <span data-ttu-id="3dc3b-254">La tabella seguente mostra le informazioni sull'evento.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-254">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="3dc3b-255">event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-255">Event</span></span>|<span data-ttu-id="3dc3b-256">ID evento</span><span class="sxs-lookup"><span data-stu-id="3dc3b-256">Event ID</span></span>|<span data-ttu-id="3dc3b-257">Generato quando</span><span class="sxs-lookup"><span data-stu-id="3dc3b-257">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateSegment_V1`|<span data-ttu-id="3dc3b-258">5</span><span class="sxs-lookup"><span data-stu-id="3dc3b-258">5</span></span>|<span data-ttu-id="3dc3b-259">È stato creato un nuovo segmento di Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-259">A new garbage collection segment has been created.</span></span> <span data-ttu-id="3dc3b-260">Inoltre, quando la traccia è attivata su un processo già in esecuzione, questo evento viene generato per ogni segmento esistente.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-260">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|  
  
 <span data-ttu-id="3dc3b-261">La tabella seguente mostra i dati dell'evento.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-261">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="3dc3b-262">Nome campo</span><span class="sxs-lookup"><span data-stu-id="3dc3b-262">Field name</span></span>|<span data-ttu-id="3dc3b-263">Tipo di dati</span><span class="sxs-lookup"><span data-stu-id="3dc3b-263">Data type</span></span>|<span data-ttu-id="3dc3b-264">Descrizione</span><span class="sxs-lookup"><span data-stu-id="3dc3b-264">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="3dc3b-265">Indirizzo</span><span class="sxs-lookup"><span data-stu-id="3dc3b-265">Address</span></span>|<span data-ttu-id="3dc3b-266">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="3dc3b-266">win:UInt64</span></span>|<span data-ttu-id="3dc3b-267">Indirizzo del segmento.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-267">The address of the segment.</span></span>|  
|<span data-ttu-id="3dc3b-268">Dimensioni</span><span class="sxs-lookup"><span data-stu-id="3dc3b-268">Size</span></span>|<span data-ttu-id="3dc3b-269">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="3dc3b-269">win:UInt64</span></span>|<span data-ttu-id="3dc3b-270">Dimensione del segmento.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-270">The size of the segment.</span></span>|  
|<span data-ttu-id="3dc3b-271">Type</span><span class="sxs-lookup"><span data-stu-id="3dc3b-271">Type</span></span>|<span data-ttu-id="3dc3b-272">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="3dc3b-272">win:UInt32</span></span>|<span data-ttu-id="3dc3b-273">0x0 - Heap oggetto piccolo.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-273">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="3dc3b-274">0x1 - Heap oggetto grande.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-274">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="3dc3b-275">0x2 - Heap di sola lettura.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-275">0x2 - Read-only heap.</span></span>|  
|<span data-ttu-id="3dc3b-276">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="3dc3b-276">ClrInstanceID</span></span>|<span data-ttu-id="3dc3b-277">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="3dc3b-277">win:UInt16</span></span>|<span data-ttu-id="3dc3b-278">ID univoco per l'istanza di CLR o CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-278">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 <span data-ttu-id="3dc3b-279">Si noti che la dimensione dei segmenti allocati dal Garbage Collector è specifico dell'implementazione ed è soggetta a modifiche in qualsiasi momento, tra cui aggiornamenti periodici.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-279">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="3dc3b-280">L'applicazione non deve dare per scontata o dipendere da una particolare dimensione del segmento, né provare a configurare la quantità di memoria disponibile per le allocazioni di segmenti.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-280">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>  
  
 [<span data-ttu-id="3dc3b-281">Torna all'inizio</span><span class="sxs-lookup"><span data-stu-id="3dc3b-281">Back to top</span></span>](#top)  
  
<a name="gcfreesegment_v1_event"></a>   
## <a name="gcfreesegment_v1-event"></a><span data-ttu-id="3dc3b-282">GCFreeSegment_V1 Event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-282">GCFreeSegment_V1 Event</span></span>  
 <span data-ttu-id="3dc3b-283">La tabella seguente illustra la parola chiave e il livello</span><span class="sxs-lookup"><span data-stu-id="3dc3b-283">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="3dc3b-284">Parola chiave per la generazione dell'evento</span><span class="sxs-lookup"><span data-stu-id="3dc3b-284">Keyword for raising the event</span></span>|<span data-ttu-id="3dc3b-285">Level</span><span class="sxs-lookup"><span data-stu-id="3dc3b-285">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="3dc3b-286">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="3dc3b-286">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="3dc3b-287">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="3dc3b-287">Informational (4)</span></span>|  
  
 <span data-ttu-id="3dc3b-288">La tabella seguente mostra le informazioni sull'evento.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-288">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="3dc3b-289">event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-289">Event</span></span>|<span data-ttu-id="3dc3b-290">ID evento</span><span class="sxs-lookup"><span data-stu-id="3dc3b-290">Event ID</span></span>|<span data-ttu-id="3dc3b-291">Generato quando</span><span class="sxs-lookup"><span data-stu-id="3dc3b-291">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFreeSegment_V1`|<span data-ttu-id="3dc3b-292">6</span><span class="sxs-lookup"><span data-stu-id="3dc3b-292">6</span></span>|<span data-ttu-id="3dc3b-293">È stato rilasciato un segmento di Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-293">A garbage collection segment has been released.</span></span>|  
  
 <span data-ttu-id="3dc3b-294">La tabella seguente mostra i dati dell'evento.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-294">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="3dc3b-295">Nome campo</span><span class="sxs-lookup"><span data-stu-id="3dc3b-295">Field name</span></span>|<span data-ttu-id="3dc3b-296">Tipo di dati</span><span class="sxs-lookup"><span data-stu-id="3dc3b-296">Data type</span></span>|<span data-ttu-id="3dc3b-297">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="3dc3b-297">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="3dc3b-298">Indirizzo</span><span class="sxs-lookup"><span data-stu-id="3dc3b-298">Address</span></span>|<span data-ttu-id="3dc3b-299">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="3dc3b-299">win:UInt64</span></span>|<span data-ttu-id="3dc3b-300">Indirizzo del segmento.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-300">The address of the segment.</span></span>|  
|<span data-ttu-id="3dc3b-301">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="3dc3b-301">ClrInstanceID</span></span>|<span data-ttu-id="3dc3b-302">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="3dc3b-302">win:UInt16</span></span>|<span data-ttu-id="3dc3b-303">ID univoco per l'istanza di CLR o CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-303">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="3dc3b-304">Torna all'inizio</span><span class="sxs-lookup"><span data-stu-id="3dc3b-304">Back to top</span></span>](#top)  
  
<a name="gcrestarteebegin_v1_event"></a>   
## <a name="gcrestarteebegin_v1-event"></a><span data-ttu-id="3dc3b-305">GCRestartEEBegin_V1 Event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-305">GCRestartEEBegin_V1 Event</span></span>  
 <span data-ttu-id="3dc3b-306">La tabella seguente illustra la parola chiave e il livello</span><span class="sxs-lookup"><span data-stu-id="3dc3b-306">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="3dc3b-307">Parola chiave per la generazione dell'evento</span><span class="sxs-lookup"><span data-stu-id="3dc3b-307">Keyword for raising the event</span></span>|<span data-ttu-id="3dc3b-308">Level</span><span class="sxs-lookup"><span data-stu-id="3dc3b-308">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="3dc3b-309">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="3dc3b-309">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="3dc3b-310">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="3dc3b-310">Informational (4)</span></span>|  
  
 <span data-ttu-id="3dc3b-311">La tabella seguente mostra le informazioni sull'evento.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-311">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="3dc3b-312">event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-312">Event</span></span>|<span data-ttu-id="3dc3b-313">ID evento</span><span class="sxs-lookup"><span data-stu-id="3dc3b-313">Event ID</span></span>|<span data-ttu-id="3dc3b-314">Generato quando</span><span class="sxs-lookup"><span data-stu-id="3dc3b-314">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEBegin_V1`|<span data-ttu-id="3dc3b-315">7</span><span class="sxs-lookup"><span data-stu-id="3dc3b-315">7</span></span>|<span data-ttu-id="3dc3b-316">Il ripristino dalla sospensione di Common Language Runtime è iniziato.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-316">Resumption from common language runtime suspension has begun.</span></span>|  
  
 <span data-ttu-id="3dc3b-317">Nessun dato dell'evento.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-317">No event data.</span></span>  
  
 [<span data-ttu-id="3dc3b-318">Torna all'inizio</span><span class="sxs-lookup"><span data-stu-id="3dc3b-318">Back to top</span></span>](#top)  
  
<a name="gcrestarteeend_v1_event"></a>   
## <a name="gcrestarteeend_v1-event"></a><span data-ttu-id="3dc3b-319">GCRestartEEEnd_V1 Event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-319">GCRestartEEEnd_V1 Event</span></span>  
 <span data-ttu-id="3dc3b-320">La tabella seguente illustra la parola chiave e il livello</span><span class="sxs-lookup"><span data-stu-id="3dc3b-320">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="3dc3b-321">Parola chiave per la generazione dell'evento</span><span class="sxs-lookup"><span data-stu-id="3dc3b-321">Keyword for raising the event</span></span>|<span data-ttu-id="3dc3b-322">Level</span><span class="sxs-lookup"><span data-stu-id="3dc3b-322">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="3dc3b-323">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="3dc3b-323">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="3dc3b-324">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="3dc3b-324">Informational (4)</span></span>|  
  
 <span data-ttu-id="3dc3b-325">La tabella seguente mostra le informazioni sull'evento.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-325">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="3dc3b-326">event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-326">Event</span></span>|<span data-ttu-id="3dc3b-327">ID evento</span><span class="sxs-lookup"><span data-stu-id="3dc3b-327">Event Id</span></span>|<span data-ttu-id="3dc3b-328">Generato quando</span><span class="sxs-lookup"><span data-stu-id="3dc3b-328">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEEnd_V1`|<span data-ttu-id="3dc3b-329">3</span><span class="sxs-lookup"><span data-stu-id="3dc3b-329">3</span></span>|<span data-ttu-id="3dc3b-330">Il ripristino dalla sospensione di Common Language Runtime è terminato.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-330">Resumption from common language runtime suspension has ended.</span></span>|  
  
 <span data-ttu-id="3dc3b-331">Nessun dato dell'evento.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-331">No event data.</span></span>  
  
 [<span data-ttu-id="3dc3b-332">Torna all'inizio</span><span class="sxs-lookup"><span data-stu-id="3dc3b-332">Back to top</span></span>](#top)  
  
<a name="gcsuspendee_v1_event"></a>   
## <a name="gcsuspendee_v1-event"></a><span data-ttu-id="3dc3b-333">GCSuspendEE_V1 Event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-333">GCSuspendEE_V1 Event</span></span>  
 <span data-ttu-id="3dc3b-334">La tabella seguente illustra la parola chiave e il livello</span><span class="sxs-lookup"><span data-stu-id="3dc3b-334">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="3dc3b-335">Parola chiave per la generazione dell'evento</span><span class="sxs-lookup"><span data-stu-id="3dc3b-335">Keyword for raising the event</span></span>|<span data-ttu-id="3dc3b-336">Level</span><span class="sxs-lookup"><span data-stu-id="3dc3b-336">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="3dc3b-337">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="3dc3b-337">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="3dc3b-338">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="3dc3b-338">Informational (4)</span></span>|  
  
 <span data-ttu-id="3dc3b-339">La tabella seguente mostra le informazioni sull'evento.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-339">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="3dc3b-340">event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-340">Event</span></span>|<span data-ttu-id="3dc3b-341">ID evento</span><span class="sxs-lookup"><span data-stu-id="3dc3b-341">Event ID</span></span>|<span data-ttu-id="3dc3b-342">Generato quando</span><span class="sxs-lookup"><span data-stu-id="3dc3b-342">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEE_V1`|<span data-ttu-id="3dc3b-343">9</span><span class="sxs-lookup"><span data-stu-id="3dc3b-343">9</span></span>|<span data-ttu-id="3dc3b-344">Inizio della sospensione del motore di esecuzione di operazioni di Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-344">Start of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="3dc3b-345">La tabella seguente mostra i dati dell'evento.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-345">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="3dc3b-346">Nome campo</span><span class="sxs-lookup"><span data-stu-id="3dc3b-346">Field name</span></span>|<span data-ttu-id="3dc3b-347">Tipo di dati</span><span class="sxs-lookup"><span data-stu-id="3dc3b-347">Data type</span></span>|<span data-ttu-id="3dc3b-348">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="3dc3b-348">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="3dc3b-349">Motivo</span><span class="sxs-lookup"><span data-stu-id="3dc3b-349">Reason</span></span>|<span data-ttu-id="3dc3b-350">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="3dc3b-350">win:UInt16</span></span>|<span data-ttu-id="3dc3b-351">0x0 - Altro.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-351">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="3dc3b-352">0x1 - Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-352">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="3dc3b-353">0x2 - Arresto del dominio applicazione.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-353">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="3dc3b-354">0x3. - Lancio del codice.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-354">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="3dc3b-355">0x4 - Arresto.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-355">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="3dc3b-356">0x5 - Debugger.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-356">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="3dc3b-357">0x6 - Preparazione per l'operazione di Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-357">0x6 - Preparation for garbage collection.</span></span>|  
|<span data-ttu-id="3dc3b-358">Conteggio</span><span class="sxs-lookup"><span data-stu-id="3dc3b-358">Count</span></span>|<span data-ttu-id="3dc3b-359">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="3dc3b-359">win:UInt32</span></span>|<span data-ttu-id="3dc3b-360">Il conteggio di Garbage Collection al momento.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-360">The GC count at the time.</span></span> <span data-ttu-id="3dc3b-361">In genere, dopo di questo si assiste a un evento di avvio GC successivo. Il conteggio corrisponde al conteggio corrente + 1 quando si aumenta l'indice di GC durante un'operazione di Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-361">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|  
|<span data-ttu-id="3dc3b-362">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="3dc3b-362">ClrInstanceID</span></span>|<span data-ttu-id="3dc3b-363">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="3dc3b-363">win:UInt16</span></span>|<span data-ttu-id="3dc3b-364">ID univoco per l'istanza di CLR o CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-364">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="3dc3b-365">Torna all'inizio</span><span class="sxs-lookup"><span data-stu-id="3dc3b-365">Back to top</span></span>](#top)  
  
<a name="gcsuspendeeend_v1_event"></a>   
## <a name="gcsuspendeeend_v1-event"></a><span data-ttu-id="3dc3b-366">GCSuspendEEEnd_V1 Event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-366">GCSuspendEEEnd_V1 Event</span></span>  
 <span data-ttu-id="3dc3b-367">La tabella seguente illustra la parola chiave e il livello:</span><span class="sxs-lookup"><span data-stu-id="3dc3b-367">The following table shows the keyword and level:</span></span>  
  
|<span data-ttu-id="3dc3b-368">Parola chiave per la generazione dell'evento</span><span class="sxs-lookup"><span data-stu-id="3dc3b-368">Keyword for raising the event</span></span>|<span data-ttu-id="3dc3b-369">Level</span><span class="sxs-lookup"><span data-stu-id="3dc3b-369">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="3dc3b-370">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="3dc3b-370">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="3dc3b-371">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="3dc3b-371">Informational (4)</span></span>|  
  
 <span data-ttu-id="3dc3b-372">La tabella seguente mostra le informazioni sull'evento:</span><span class="sxs-lookup"><span data-stu-id="3dc3b-372">The following table shows the event information:</span></span>  
  
|<span data-ttu-id="3dc3b-373">event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-373">Event</span></span>|<span data-ttu-id="3dc3b-374">ID evento</span><span class="sxs-lookup"><span data-stu-id="3dc3b-374">Event ID</span></span>|<span data-ttu-id="3dc3b-375">Generato quando</span><span class="sxs-lookup"><span data-stu-id="3dc3b-375">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEEEnd_V1`|<span data-ttu-id="3dc3b-376">8</span><span class="sxs-lookup"><span data-stu-id="3dc3b-376">8</span></span>|<span data-ttu-id="3dc3b-377">Fine della sospensione del motore di esecuzione di operazioni di Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-377">End of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="3dc3b-378">Nessun dato dell'evento.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-378">No event data.</span></span>  
  
 [<span data-ttu-id="3dc3b-379">Torna all'inizio</span><span class="sxs-lookup"><span data-stu-id="3dc3b-379">Back to top</span></span>](#top)  
  
<a name="gcallocationtick_v2_event"></a>   
## <a name="gcallocationtick_v2-event"></a><span data-ttu-id="3dc3b-380">GCAllocationTick_V2 Event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-380">GCAllocationTick_V2 Event</span></span>  
 <span data-ttu-id="3dc3b-381">La tabella seguente illustra la parola chiave e il livello</span><span class="sxs-lookup"><span data-stu-id="3dc3b-381">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="3dc3b-382">Parola chiave per la generazione dell'evento</span><span class="sxs-lookup"><span data-stu-id="3dc3b-382">Keyword for raising the event</span></span>|<span data-ttu-id="3dc3b-383">Level</span><span class="sxs-lookup"><span data-stu-id="3dc3b-383">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="3dc3b-384">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="3dc3b-384">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="3dc3b-385">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="3dc3b-385">Informational (4)</span></span>|  
  
 <span data-ttu-id="3dc3b-386">La tabella seguente mostra le informazioni sull'evento.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-386">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="3dc3b-387">event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-387">Event</span></span>|<span data-ttu-id="3dc3b-388">ID evento</span><span class="sxs-lookup"><span data-stu-id="3dc3b-388">Event ID</span></span>|<span data-ttu-id="3dc3b-389">Generato quando</span><span class="sxs-lookup"><span data-stu-id="3dc3b-389">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCAllocationTick_V2`|<span data-ttu-id="3dc3b-390">10</span><span class="sxs-lookup"><span data-stu-id="3dc3b-390">10</span></span>|<span data-ttu-id="3dc3b-391">Ogni volta vengono allocati circa 100 KB.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-391">Each time approximately 100 KB is allocated.</span></span>|  
  
 <span data-ttu-id="3dc3b-392">La tabella seguente mostra i dati dell'evento.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-392">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="3dc3b-393">Nome campo</span><span class="sxs-lookup"><span data-stu-id="3dc3b-393">Field name</span></span>|<span data-ttu-id="3dc3b-394">Tipo di dati</span><span class="sxs-lookup"><span data-stu-id="3dc3b-394">Data type</span></span>|<span data-ttu-id="3dc3b-395">Descrizione</span><span class="sxs-lookup"><span data-stu-id="3dc3b-395">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="3dc3b-396">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="3dc3b-396">AllocationAmount</span></span>|<span data-ttu-id="3dc3b-397">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="3dc3b-397">win:UInt32</span></span>|<span data-ttu-id="3dc3b-398">Dimensione dell'allocazione, in byte.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-398">The allocation size, in bytes.</span></span> <span data-ttu-id="3dc3b-399">Questo valore è preciso per le allocazioni minori della lunghezza di un ULONG (4.294.967.295 byte).</span><span class="sxs-lookup"><span data-stu-id="3dc3b-399">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="3dc3b-400">Se l'allocazione è maggiore, questo campo contiene un valore troncato.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-400">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="3dc3b-401">Usare `AllocationAmount64` per le allocazioni di dimensioni molto grandi.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-401">Use `AllocationAmount64` for very large allocations.</span></span>|  
|<span data-ttu-id="3dc3b-402">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="3dc3b-402">AllocationKind</span></span>|<span data-ttu-id="3dc3b-403">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="3dc3b-403">win:UInt32</span></span>|<span data-ttu-id="3dc3b-404">0x0 - Allocazione di oggetti piccoli (l'allocazione è nell'heap oggetto piccolo).</span><span class="sxs-lookup"><span data-stu-id="3dc3b-404">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="3dc3b-405">0x1 - Allocazione di oggetti grandi (l'allocazione è nell'heap oggetto grande).</span><span class="sxs-lookup"><span data-stu-id="3dc3b-405">0x1 - Large object allocation (allocation is in large object heap).</span></span>|  
|<span data-ttu-id="3dc3b-406">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="3dc3b-406">ClrInstanceID</span></span>|<span data-ttu-id="3dc3b-407">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="3dc3b-407">win:UInt16</span></span>|<span data-ttu-id="3dc3b-408">ID univoco per l'istanza di CLR o CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-408">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
|<span data-ttu-id="3dc3b-409">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="3dc3b-409">AllocationAmount64</span></span>|<span data-ttu-id="3dc3b-410">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="3dc3b-410">win:UInt64</span></span>|<span data-ttu-id="3dc3b-411">Dimensione dell'allocazione, in byte.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-411">The allocation size, in bytes.</span></span> <span data-ttu-id="3dc3b-412">Questo valore è preciso per le allocazioni di dimensioni molto grandi.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-412">This value is accurate for very large allocations.</span></span>|  
|<span data-ttu-id="3dc3b-413">TypeId</span><span class="sxs-lookup"><span data-stu-id="3dc3b-413">TypeId</span></span>|<span data-ttu-id="3dc3b-414">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="3dc3b-414">win:Pointer</span></span>|<span data-ttu-id="3dc3b-415">Indirizzo di MethodTable.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-415">The address of the MethodTable.</span></span> <span data-ttu-id="3dc3b-416">Quando sono presenti diversi tipi di oggetti allocati durante questo evento, questo è l'indirizzo di MethodTable che corrisponde all'ultimo oggetto allocato (l'oggetto che ha causato il superamento della soglia di 100 KB).</span><span class="sxs-lookup"><span data-stu-id="3dc3b-416">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="3dc3b-417">TypeName</span><span class="sxs-lookup"><span data-stu-id="3dc3b-417">TypeName</span></span>|<span data-ttu-id="3dc3b-418">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="3dc3b-418">win:UnicodeString</span></span>|<span data-ttu-id="3dc3b-419">Nome del tipo che è stato allocato.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-419">The name of the type that was allocated.</span></span> <span data-ttu-id="3dc3b-420">Quando sono presenti diversi tipi di oggetti allocati durante questo evento, questo è il tipo dell'ultimo oggetto allocato (l'oggetto che ha causato il superamento della soglia di 100 KB).</span><span class="sxs-lookup"><span data-stu-id="3dc3b-420">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="3dc3b-421">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="3dc3b-421">HeapIndex</span></span>|<span data-ttu-id="3dc3b-422">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="3dc3b-422">win:UInt32</span></span>|<span data-ttu-id="3dc3b-423">Heap in cui l'oggetto è stato allocato.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-423">The heap where the object was allocated.</span></span> <span data-ttu-id="3dc3b-424">Questo valore è 0 (zero) durante l'esecuzione della procedura di Garbage Collection per workstation.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-424">This value is 0 (zero) when running with workstation garbage collection.</span></span>|  
  
 [<span data-ttu-id="3dc3b-425">Torna all'inizio</span><span class="sxs-lookup"><span data-stu-id="3dc3b-425">Back to top</span></span>](#top)  
  
<a name="gcfinalizersbegin_v1_event"></a>   
## <a name="gcfinalizersbegin_v1-event"></a><span data-ttu-id="3dc3b-426">GCFinalizersBegin_V1 Event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-426">GCFinalizersBegin_V1 Event</span></span>  
 <span data-ttu-id="3dc3b-427">La tabella seguente illustra la parola chiave e il livello</span><span class="sxs-lookup"><span data-stu-id="3dc3b-427">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="3dc3b-428">Parola chiave per la generazione dell'evento</span><span class="sxs-lookup"><span data-stu-id="3dc3b-428">Keyword for raising the event</span></span>|<span data-ttu-id="3dc3b-429">Level</span><span class="sxs-lookup"><span data-stu-id="3dc3b-429">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="3dc3b-430">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="3dc3b-430">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="3dc3b-431">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="3dc3b-431">Informational (4)</span></span>|  
  
 <span data-ttu-id="3dc3b-432">La tabella seguente mostra le informazioni sull'evento.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-432">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="3dc3b-433">event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-433">Event</span></span>|<span data-ttu-id="3dc3b-434">ID evento</span><span class="sxs-lookup"><span data-stu-id="3dc3b-434">Event ID</span></span>|<span data-ttu-id="3dc3b-435">Generato quando</span><span class="sxs-lookup"><span data-stu-id="3dc3b-435">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersBegin_V1`|<span data-ttu-id="3dc3b-436">14</span><span class="sxs-lookup"><span data-stu-id="3dc3b-436">14</span></span>|<span data-ttu-id="3dc3b-437">Inizio dell'esecuzione dei finalizzatori.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-437">The start of running finalizers.</span></span>|  
  
 <span data-ttu-id="3dc3b-438">Nessun dato dell'evento.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-438">No event data.</span></span>  
  
 [<span data-ttu-id="3dc3b-439">Torna all'inizio</span><span class="sxs-lookup"><span data-stu-id="3dc3b-439">Back to top</span></span>](#top)  
  
<a name="gcfinalizersend_v1_event"></a>   
## <a name="gcfinalizersend_v1-event"></a><span data-ttu-id="3dc3b-440">GCFinalizersEnd_V1 Event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-440">GCFinalizersEnd_V1 Event</span></span>  
 <span data-ttu-id="3dc3b-441">La tabella seguente illustra la parola chiave e il livello</span><span class="sxs-lookup"><span data-stu-id="3dc3b-441">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="3dc3b-442">Parola chiave per la generazione dell'evento</span><span class="sxs-lookup"><span data-stu-id="3dc3b-442">Keyword for raising the event</span></span>|<span data-ttu-id="3dc3b-443">Level</span><span class="sxs-lookup"><span data-stu-id="3dc3b-443">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="3dc3b-444">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="3dc3b-444">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="3dc3b-445">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="3dc3b-445">Informational (4)</span></span>|  
  
 <span data-ttu-id="3dc3b-446">La tabella seguente mostra le informazioni sull'evento.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-446">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="3dc3b-447">event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-447">Event</span></span>|<span data-ttu-id="3dc3b-448">ID evento</span><span class="sxs-lookup"><span data-stu-id="3dc3b-448">Event ID</span></span>|<span data-ttu-id="3dc3b-449">Generato quando</span><span class="sxs-lookup"><span data-stu-id="3dc3b-449">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersEnd_V1`|<span data-ttu-id="3dc3b-450">13</span><span class="sxs-lookup"><span data-stu-id="3dc3b-450">13</span></span>|<span data-ttu-id="3dc3b-451">Fine dell'esecuzione dei finalizzatori.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-451">The end of running finalizers.</span></span>|  
  
 <span data-ttu-id="3dc3b-452">La tabella seguente mostra i dati dell'evento.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-452">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="3dc3b-453">Nome campo</span><span class="sxs-lookup"><span data-stu-id="3dc3b-453">Field name</span></span>|<span data-ttu-id="3dc3b-454">Tipo di dati</span><span class="sxs-lookup"><span data-stu-id="3dc3b-454">Data type</span></span>|<span data-ttu-id="3dc3b-455">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="3dc3b-455">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="3dc3b-456">Conteggio</span><span class="sxs-lookup"><span data-stu-id="3dc3b-456">Count</span></span>|<span data-ttu-id="3dc3b-457">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="3dc3b-457">win:UInt32</span></span>|<span data-ttu-id="3dc3b-458">Numero di finalizzatori eseguiti.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-458">The number of finalizers that were run.</span></span>|  
|<span data-ttu-id="3dc3b-459">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="3dc3b-459">ClrInstanceID</span></span>|<span data-ttu-id="3dc3b-460">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="3dc3b-460">win:UInt16</span></span>|<span data-ttu-id="3dc3b-461">ID univoco per l'istanza di CLR o CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-461">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="3dc3b-462">Torna all'inizio</span><span class="sxs-lookup"><span data-stu-id="3dc3b-462">Back to top</span></span>](#top)  
  
<a name="gccreateconcurrentthread_v1_event"></a>   
## <a name="gccreateconcurrentthread_v1-event"></a><span data-ttu-id="3dc3b-463">GCCreateConcurrentThread_V1 Event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-463">GCCreateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="3dc3b-464">La tabella seguente illustra la parola chiave e il livello</span><span class="sxs-lookup"><span data-stu-id="3dc3b-464">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="3dc3b-465">Parola chiave per la generazione dell'evento</span><span class="sxs-lookup"><span data-stu-id="3dc3b-465">Keyword for raising the event</span></span>|<span data-ttu-id="3dc3b-466">Level</span><span class="sxs-lookup"><span data-stu-id="3dc3b-466">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="3dc3b-467">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="3dc3b-467">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="3dc3b-468">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="3dc3b-468">Informational (4)</span></span>|  
|<span data-ttu-id="3dc3b-469">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="3dc3b-469">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="3dc3b-470">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="3dc3b-470">Informational (4)</span></span>|  
  
 <span data-ttu-id="3dc3b-471">La tabella seguente mostra le informazioni sull'evento.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-471">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="3dc3b-472">event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-472">Event</span></span>|<span data-ttu-id="3dc3b-473">ID evento</span><span class="sxs-lookup"><span data-stu-id="3dc3b-473">Event ID</span></span>|<span data-ttu-id="3dc3b-474">Generato quando</span><span class="sxs-lookup"><span data-stu-id="3dc3b-474">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="3dc3b-475">11</span><span class="sxs-lookup"><span data-stu-id="3dc3b-475">11</span></span>|<span data-ttu-id="3dc3b-476">È stato creato il thread di Garbage Collection in modalità simultanea</span><span class="sxs-lookup"><span data-stu-id="3dc3b-476">Concurrent garbage collection thread was created.</span></span>|  
  
 <span data-ttu-id="3dc3b-477">Nessun dato dell'evento.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-477">No event data.</span></span>  
  
 [<span data-ttu-id="3dc3b-478">Torna all'inizio</span><span class="sxs-lookup"><span data-stu-id="3dc3b-478">Back to top</span></span>](#top)  
  
<a name="gcterminateconcurrentthread_v1_event"></a>   
## <a name="gcterminateconcurrentthread_v1-event"></a><span data-ttu-id="3dc3b-479">GCTerminateConcurrentThread_V1 Event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-479">GCTerminateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="3dc3b-480">La tabella seguente illustra la parola chiave e il livello</span><span class="sxs-lookup"><span data-stu-id="3dc3b-480">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="3dc3b-481">Parola chiave per la generazione dell'evento</span><span class="sxs-lookup"><span data-stu-id="3dc3b-481">Keyword for raising the event</span></span>|<span data-ttu-id="3dc3b-482">Level</span><span class="sxs-lookup"><span data-stu-id="3dc3b-482">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="3dc3b-483">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="3dc3b-483">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="3dc3b-484">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="3dc3b-484">Informational (4)</span></span>|  
|<span data-ttu-id="3dc3b-485">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="3dc3b-485">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="3dc3b-486">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="3dc3b-486">Informational (4)</span></span>|  
  
 <span data-ttu-id="3dc3b-487">La tabella seguente mostra le informazioni sull'evento.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-487">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="3dc3b-488">event</span><span class="sxs-lookup"><span data-stu-id="3dc3b-488">Event</span></span>|<span data-ttu-id="3dc3b-489">ID evento</span><span class="sxs-lookup"><span data-stu-id="3dc3b-489">Event ID</span></span>|<span data-ttu-id="3dc3b-490">Generato quando</span><span class="sxs-lookup"><span data-stu-id="3dc3b-490">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="3dc3b-491">12</span><span class="sxs-lookup"><span data-stu-id="3dc3b-491">12</span></span>|<span data-ttu-id="3dc3b-492">È stato terminato il thread di Garbage Collection in modalità simultanea.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-492">Concurrent garbage collection thread was terminated.</span></span>|  
  
 <span data-ttu-id="3dc3b-493">Nessun dato dell'evento.</span><span class="sxs-lookup"><span data-stu-id="3dc3b-493">No event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dc3b-494">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3dc3b-494">See also</span></span>

- [<span data-ttu-id="3dc3b-495">Eventi ETW di CLR</span><span class="sxs-lookup"><span data-stu-id="3dc3b-495">CLR ETW Events</span></span>](clr-etw-events.md)
