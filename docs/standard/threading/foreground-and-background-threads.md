---
title: Thread in primo piano e in background
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], foreground
- threading [.NET Framework], background
- foreground threads
- background threads
ms.assetid: cfe0d632-dd35-47e0-91ad-f742a444005e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8dbad5da42f5ed4e03751534a3a183615a9757cc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960031"
---
# <a name="foreground-and-background-threads"></a><span data-ttu-id="c7d3c-102">Thread in primo piano e in background</span><span class="sxs-lookup"><span data-stu-id="c7d3c-102">Foreground and Background Threads</span></span>
<span data-ttu-id="c7d3c-103">Un thread gestito è un thread in background o un thread in primo piano.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-103">A managed thread is either a background thread or a foreground thread.</span></span> <span data-ttu-id="c7d3c-104">I thread in background sono identici ai thread in primo piano con un'unica eccezione: un thread in background non mantiene in esecuzione l'ambiente di esecuzione gestito.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-104">Background threads are identical to foreground threads with one exception: a background thread does not keep the managed execution environment running.</span></span> <span data-ttu-id="c7d3c-105">Dopo che tutti i thread in primo piano sono stati arrestati in un processo gestito (in cui il file EXE è un assembly gestito), il sistema arresta tutti i thread in background e si arresta.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-105">Once all foreground threads have been stopped in a managed process (where the .exe file is a managed assembly), the system stops all background threads and shuts down.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c7d3c-106">Quando il runtime arresta un thread in background perché è in corso l'arresto del processo, non vengono generate eccezioni nel thread.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-106">When the runtime stops a background thread because the process is shutting down, no exception is thrown in the thread.</span></span> <span data-ttu-id="c7d3c-107">Quando tuttavia i thread vengono arrestati perché il metodo <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> scarica il dominio dell'applicazione, viene generata un'eccezione <xref:System.Threading.ThreadAbortException> nei thread in primo piano e in background.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-107">However, when threads are stopped because the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method unloads the application domain, a <xref:System.Threading.ThreadAbortException> is thrown in both foreground and background threads.</span></span>  
  
 <span data-ttu-id="c7d3c-108">Usare la proprietà <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> per determinare se un thread è un thread in background o in primo piano oppure per modificarne lo stato.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-108">Use the <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> property to determine whether a thread is a background or a foreground thread, or to change its status.</span></span> <span data-ttu-id="c7d3c-109">Un thread può essere sostituito con un thread in background in qualsiasi momento impostandone la proprietà <xref:System.Threading.Thread.IsBackground%2A> su `true`.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-109">A thread can be changed to a background thread at any time by setting its <xref:System.Threading.Thread.IsBackground%2A> property to `true`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c7d3c-110">Lo stato di primo piano o di background di un thread non interessa l'esito di un'eccezione non gestita nel thread.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-110">The foreground or background status of a thread does not affect the outcome of an unhandled exception in the thread.</span></span> <span data-ttu-id="c7d3c-111">In .NET Framework versione 2.0 un'eccezione non gestita nei thread in primo piano o in background comporta la terminazione dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-111">In the .NET Framework version 2.0, an unhandled exception in either foreground or background threads results in termination of the application.</span></span> <span data-ttu-id="c7d3c-112">Vedere [Eccezioni in thread gestiti](../../../docs/standard/threading/exceptions-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="c7d3c-112">See [Exceptions in Managed Threads](../../../docs/standard/threading/exceptions-in-managed-threads.md).</span></span>  
  
 <span data-ttu-id="c7d3c-113">I thread che appartengono al pool di thread gestiti (ovvero, i thread la cui proprietà <xref:System.Threading.Thread.IsThreadPoolThread%2A> è `true`) sono thread in background.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-113">Threads that belong to the managed thread pool (that is, threads whose <xref:System.Threading.Thread.IsThreadPoolThread%2A> property is `true`) are background threads.</span></span> <span data-ttu-id="c7d3c-114">Tutti i thread che accedono all'ambiente di esecuzione gestito dal codice non gestito sono contrassegnati come thread in background.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-114">All threads that enter the managed execution environment from unmanaged code are marked as background threads.</span></span> <span data-ttu-id="c7d3c-115">Tutti i thread generati creando e avviando un nuovo oggetto <xref:System.Threading.Thread> sono thread in primo piano per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-115">All threads generated by creating and starting a new <xref:System.Threading.Thread> object are by default foreground threads.</span></span>  
  
 <span data-ttu-id="c7d3c-116">Se si usa un thread per monitorare un'attività, ad esempio una connessione socket, impostarne la proprietà <xref:System.Threading.Thread.IsBackground%2A> su `true` in modo che il thread non impedisca la terminazione del processo.</span><span class="sxs-lookup"><span data-stu-id="c7d3c-116">If you use a thread to monitor an activity, such as a socket connection, set its <xref:System.Threading.Thread.IsBackground%2A> property to `true` so that the thread does not prevent your process from terminating.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7d3c-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c7d3c-117">See also</span></span>

- <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>
- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadAbortException>
