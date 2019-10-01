---
title: Resilienza nativa del cloud
description: Architettura di app .NET cloud native per Azure | Resilienza nativa del cloud
ms.date: 06/30/2019
ms.openlocfilehash: 680542abc5d8c43c577321d5ae834f0a13290da3
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184841"
---
# <a name="cloud-native-resiliency"></a><span data-ttu-id="bb176-103">Resilienza nativa del cloud</span><span class="sxs-lookup"><span data-stu-id="bb176-103">Cloud-native resiliency</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="bb176-104">La resilienza è la capacità del sistema di reagire agli errori e rimane comunque funzionante.</span><span class="sxs-lookup"><span data-stu-id="bb176-104">Resiliency is the ability of your system to react to failure and still remain functional.</span></span> <span data-ttu-id="bb176-105">Non è per evitare errori.</span><span class="sxs-lookup"><span data-stu-id="bb176-105">It isn't about avoiding failure.</span></span> <span data-ttu-id="bb176-106">Tuttavia, l'accettazione di tale errore è inevitabile nei sistemi basati sul cloud e la creazione dell'applicazione per rispondere.</span><span class="sxs-lookup"><span data-stu-id="bb176-106">But it's about accepting that failure is inevitable in cloud-based systems and building your application to respond to it.</span></span> <span data-ttu-id="bb176-107">L'obiettivo finale della resilienza consiste nel riportare l'applicazione a uno stato completamente funzionante dopo un errore.</span><span class="sxs-lookup"><span data-stu-id="bb176-107">The end-goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="bb176-108">Diversamente dalle tradizionali applicazioni monolitiche, in cui tutto viene eseguito insieme in un unico processo, i sistemi nativi del cloud adottano l'architettura distribuita, come illustrato nella figura 6-1:</span><span class="sxs-lookup"><span data-stu-id="bb176-108">Unlike traditional monolithic applications, where everything runs together in a single process, cloud-native systems embrace distributed architecture as shown in Figure 6-1:</span></span>

![Ambiente nativo cloud distribuito](./media/distributed-cloud-native-environment.png)

<span data-ttu-id="bb176-110">**Figura 6-1.**</span><span class="sxs-lookup"><span data-stu-id="bb176-110">**Figure 6-1.**</span></span> <span data-ttu-id="bb176-111">Ambiente nativo cloud distribuito</span><span class="sxs-lookup"><span data-stu-id="bb176-111">Distributed cloud-native environment</span></span>

<span data-ttu-id="bb176-112">Nella figura precedente si noti come ogni client, microservizio e [servizio di backup](https://12factor.net/backing-services) basato su cloud viene eseguito come processo separato, in esecuzione su server diversi, tutti comunicanti tramite chiamate basate su rete.</span><span class="sxs-lookup"><span data-stu-id="bb176-112">In the previous figure, note how each client, microservice, and cloud-based [backing service](https://12factor.net/backing-services) executes as a separate process, running across different servers, all communicating via network-based calls.</span></span>

<span data-ttu-id="bb176-113">Quindi, cosa potrebbe andare male?</span><span class="sxs-lookup"><span data-stu-id="bb176-113">So, what could go wrong?</span></span>

- <span data-ttu-id="bb176-114">[Latenza di rete](https://www.techopedia.com/definition/8553/network-latency)imprevista.</span><span class="sxs-lookup"><span data-stu-id="bb176-114">Unexpected [network latency](https://www.techopedia.com/definition/8553/network-latency).</span></span>
- <span data-ttu-id="bb176-115">[Errori temporanei](https://docs.microsoft.com/azure/architecture/best-practices/transient-faults) (errori di connettività di rete temporanei).</span><span class="sxs-lookup"><span data-stu-id="bb176-115">[Transient faults](https://docs.microsoft.com/azure/architecture/best-practices/transient-faults) (temporary network connectivity errors).</span></span>
- <span data-ttu-id="bb176-116">Blocco mediante un'operazione sincrona a esecuzione prolungata.</span><span class="sxs-lookup"><span data-stu-id="bb176-116">Blocking by a long-running synchronous operation.</span></span>
- <span data-ttu-id="bb176-117">Un processo host che si è arrestato in modo anomalo e verrà riavviato o spostato.</span><span class="sxs-lookup"><span data-stu-id="bb176-117">A host process that has crashed and is being restarted or moved.</span></span>
- <span data-ttu-id="bb176-118">Un microservizio di overload che non può rispondere per un breve periodo di tempo.</span><span class="sxs-lookup"><span data-stu-id="bb176-118">An overloaded microservice that can't respond for a short time.</span></span>
- <span data-ttu-id="bb176-119">Operazione DevOps in corso, ad esempio un'operazione di aggiornamento o di ridimensionamento.</span><span class="sxs-lookup"><span data-stu-id="bb176-119">An in-flight DevOps operation such as an update or scaling operation.</span></span>
- <span data-ttu-id="bb176-120">Operazione dell'agente di orchestrazione, ad esempio lo trasferimento di un servizio da un nodo a un altro.</span><span class="sxs-lookup"><span data-stu-id="bb176-120">An Orchestrator operation such as moving a service from one node to another.</span></span>
- <span data-ttu-id="bb176-121">Errori hardware dall'hardware di base.</span><span class="sxs-lookup"><span data-stu-id="bb176-121">Hardware failures from commodity hardware.</span></span>

<span data-ttu-id="bb176-122">Quando si distribuiscono servizi distribuiti nell'infrastruttura basata su cloud, i fattori dell'elenco precedente diventano molto reali ed è necessario progettare e sviluppare in modo difensivo per gestirli.</span><span class="sxs-lookup"><span data-stu-id="bb176-122">When deploying distributed services into cloud-based infrastructure, the factors from the previous list become very real and you must architect and develop defensively to deal with them.</span></span>

<span data-ttu-id="bb176-123">In un sistema distribuito su scala ridotta, l'errore sarà meno frequente, ma con l'aumentare delle prestazioni del sistema, è possibile che si verifichino più problemi a un punto in cui un errore parziale diventa il normale funzionamento.</span><span class="sxs-lookup"><span data-stu-id="bb176-123">In a small-scale distributed system, failure will be less frequent, but as a system scales up and out, you can expect to experience more of these issues to a point where partial failure becomes normal operation.</span></span>

<span data-ttu-id="bb176-124">Pertanto, l'applicazione e l'infrastruttura devono essere resilienti.</span><span class="sxs-lookup"><span data-stu-id="bb176-124">Therefore, your application and infrastructure must be resilient.</span></span> <span data-ttu-id="bb176-125">Nelle sezioni seguenti verranno illustrate le tecniche difensive che è possibile aggiungere all'applicazione e le funzionalità cloud integrate che è possibile utilizzare per consentire l'uso dell'esperienza utente da parte di Bullet.</span><span class="sxs-lookup"><span data-stu-id="bb176-125">In the following sections, we'll explore defensive techniques that you can add to your application and built-in cloud features that you can leverage to help bullet-proof your user's experience.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="bb176-126">[Precedente](azure-data-storage.md)
>[Successivo](application-resiliency-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="bb176-126">[Previous](azure-data-storage.md)
[Next](application-resiliency-patterns.md)</span></span>