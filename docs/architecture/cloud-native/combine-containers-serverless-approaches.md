---
title: Combinazione di contenitori e approcci senza server
description: Combinazione di contenitori e Kubernetes con approcci senza server
ms.date: 06/30/2019
ms.openlocfilehash: 58aff43adbdd2e629370cc685f32c7b61c25f85e
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183434"
---
# <a name="combining-containers-and-serverless-approaches"></a><span data-ttu-id="35e49-103">Combinazione di contenitori e approcci senza server</span><span class="sxs-lookup"><span data-stu-id="35e49-103">Combining containers and serverless approaches</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="35e49-104">Spesso, le applicazioni basate su microservizi si basano molto sui contenitori, l'orchestrazione e il passaggio di messaggi per la comunicazione tra i nodi.</span><span class="sxs-lookup"><span data-stu-id="35e49-104">Frequently, microservices-based applications rely heavily on containers, orchestration, and message-passing for communication between nodes.</span></span> <span data-ttu-id="35e49-105">Questa messaggistica è un'attività ideale per funzioni di Azure, ma con il resto dell'applicazione configurata e distribuita con Kubernetes e gli strumenti correlati, sarebbe bello poter sfruttare le funzioni di Azure all'interno dello stesso set di strumenti.</span><span class="sxs-lookup"><span data-stu-id="35e49-105">This messaging is an ideal task for Azure Functions, but with the rest of the application configured and deployed using Kubernetes and related tools, it would be nice to be able to leverage Azure Functions within this same toolset.</span></span> <span data-ttu-id="35e49-106">Fortunatamente, è possibile eseguire il wrapping di funzioni di Azure nei contenitori Docker e distribuirle usando gli stessi processi e gli stessi strumenti del resto dell'app basata su Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="35e49-106">Fortunately, you can wrap Azure Functions in Docker containers and deploy them using the same processes and tools as the rest of your Kubernetes-based app.</span></span>

## <a name="when-does-it-make-sense-to-use-containers-with-serverless"></a><span data-ttu-id="35e49-107">Quando è consigliabile usare i contenitori senza server?</span><span class="sxs-lookup"><span data-stu-id="35e49-107">When does it make sense to use containers with serverless?</span></span>

<span data-ttu-id="35e49-108">Per impostazione predefinita, le funzioni senza server non conoscono la piattaforma in cui verranno eseguite.</span><span class="sxs-lookup"><span data-stu-id="35e49-108">By default, your serverless functions have no knowledge of the platform on which they'll run.</span></span> <span data-ttu-id="35e49-109">Tuttavia, in alcuni casi è possibile che si disponga di requisiti specifici che rendono importante personalizzare l'immagine del contenitore in cui verrà eseguito il codice.</span><span class="sxs-lookup"><span data-stu-id="35e49-109">However, in some cases you may have specific requirements that make it important for you to customize the container image in which your code will run.</span></span> <span data-ttu-id="35e49-110">Si consiglia di usare un'immagine personalizzata perché la funzione si basa su una versione specifica del linguaggio o presenta dipendenze o requisiti di configurazione che non sono supportati dall'immagine predefinita.</span><span class="sxs-lookup"><span data-stu-id="35e49-110">You may want to use a custom image because your function relies on a specific language version or has dependencies or configuration requirements that aren't supported by the default image.</span></span> <span data-ttu-id="35e49-111">In questi casi, può essere utile personalizzare il proprio contenitore e distribuire la funzione in un contenitore Docker personalizzato.</span><span class="sxs-lookup"><span data-stu-id="35e49-111">In these cases, it may make sense to customize your own container and deploy your function in a custom Docker container.</span></span>

## <a name="when-should-you-avoid-using-containers-with-azure-functions"></a><span data-ttu-id="35e49-112">Quando è consigliabile evitare di usare i contenitori con funzioni di Azure?</span><span class="sxs-lookup"><span data-stu-id="35e49-112">When should you avoid using containers with Azure Functions?</span></span>

<span data-ttu-id="35e49-113">Se si prevede di trarre vantaggio dalla fatturazione del piano a consumo per la funzione, non sarà possibile eseguire questa operazione se si usa il proprio contenitore.</span><span class="sxs-lookup"><span data-stu-id="35e49-113">If you're expecting to benefit from the consumption plan billing for your function, you won't be able to do so if you're using your own container.</span></span> <span data-ttu-id="35e49-114">Se si supera semplicemente l'uso di un contenitore Docker e si distribuiscono le funzioni nel cluster Kubernetes, non sarà più possibile trarre vantaggio dal ridimensionamento incorporato fornito da funzioni di Azure.</span><span class="sxs-lookup"><span data-stu-id="35e49-114">What's more, if you go beyond just using a Docker container and deploy your functions to your own Kubernetes cluster, you'll no longer benefit from the built-in scaling provided by Azure Functions.</span></span> <span data-ttu-id="35e49-115">È necessario usare le funzionalità di scalabilità di Kubernetes, descritte di seguito.</span><span class="sxs-lookup"><span data-stu-id="35e49-115">You'll need to use Kubernetes' scaling features, described below.</span></span>

## <a name="how-to-combine-serverless-and-docker-containers"></a><span data-ttu-id="35e49-116">Come combinare contenitori senza server e Docker</span><span class="sxs-lookup"><span data-stu-id="35e49-116">How to combine serverless and Docker containers</span></span>

<span data-ttu-id="35e49-117">Per eseguire il wrapping di una funzione di Azure in un contenitore Docker, installare il Azure Functions Core Tools e quindi eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="35e49-117">To wrap an Azure Function in a Docker container, install the Azure Functions Core Tools and then run the following command:</span></span>

```console
func init ProjectName --docker
```

<span data-ttu-id="35e49-118">Scegliere il runtime del ruolo di lavoro desiderato dalle opzioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="35e49-118">Choose which worker runtime you want from the following options:</span></span>

- <span data-ttu-id="35e49-119">`dotnet` (C#)</span><span class="sxs-lookup"><span data-stu-id="35e49-119">`dotnet` (C#)</span></span>
- <span data-ttu-id="35e49-120">`node` (JavaScript)</span><span class="sxs-lookup"><span data-stu-id="35e49-120">`node` (JavaScript)</span></span>
- `python`

<span data-ttu-id="35e49-121">Quando viene creato il progetto, verrà incluso un Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="35e49-121">When the project is created, it will include a Dockerfile.</span></span> <span data-ttu-id="35e49-122">A questo punto, è possibile creare e testare la funzione localmente.</span><span class="sxs-lookup"><span data-stu-id="35e49-122">Now, you can create and test your function locally.</span></span> <span data-ttu-id="35e49-123">Compilare ed eseguire il comando con `docker build` i `docker run` comandi e.</span><span class="sxs-lookup"><span data-stu-id="35e49-123">Build and run it using the  `docker build` and `docker run` commands.</span></span> <span data-ttu-id="35e49-124">Per i passaggi dettagliati per iniziare a compilare funzioni di Azure con il supporto per Docker, vedere l'esercitazione [creare una funzione in Linux tramite un'immagine personalizzata](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image) .</span><span class="sxs-lookup"><span data-stu-id="35e49-124">For detailed steps to get started building Azure Functions with Docker support, see the [Create a function on Linux using a custom image](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image) tutorial.</span></span>

## <a name="how-to-combine-serverless-and-kubernetes-with-keda"></a><span data-ttu-id="35e49-125">Come combinare senza server e Kubernetes con KEDA</span><span class="sxs-lookup"><span data-stu-id="35e49-125">How to combine serverless and Kubernetes with KEDA</span></span>

<span data-ttu-id="35e49-126">Le funzioni di Azure vengono ridimensionate automaticamente per soddisfare la domanda in base alla frequenza degli eventi destinati a una determinata funzione.</span><span class="sxs-lookup"><span data-stu-id="35e49-126">Azure functions scale automatically to meet demand based on the rate of events that are targeting a given function.</span></span> <span data-ttu-id="35e49-127">Inoltre, è possibile sfruttare Kubernetes per ospitare le funzioni e usare la scalabilità automatica basata su eventi basata su Kubernetes o KEDA.</span><span class="sxs-lookup"><span data-stu-id="35e49-127">Additionally, you can leverage Kubernetes to host your functions and use Kubernetes-based Event Driven Autoscaling, or KEDA.</span></span> <span data-ttu-id="35e49-128">Quando non si verificano eventi, KEDA è in grado di ridurre le istanze di 0 e quindi, in risposta agli eventi, può aumentare il numero di contenitori per soddisfare la richiesta usando il relativo ridimensionamento automatico del Pod orizzontale.</span><span class="sxs-lookup"><span data-stu-id="35e49-128">When no events are occurring, KEDA can scale down to 0 instances, and then in response to events it can scale up the number of containers to meet the demand using its horizontal pod autoscaler.</span></span> <span data-ttu-id="35e49-129">[Altre informazioni sul ridimensionamento delle funzioni di Azure con Keda](https://docs.microsoft.com/azure/azure-functions/functions-kubernetes-keda).</span><span class="sxs-lookup"><span data-stu-id="35e49-129">[Learn more about scaling Azure functions with KEDA](https://docs.microsoft.com/azure/azure-functions/functions-kubernetes-keda).</span></span>

## <a name="references"></a><span data-ttu-id="35e49-130">Riferimenti</span><span class="sxs-lookup"><span data-stu-id="35e49-130">References</span></span>

- [<span data-ttu-id="35e49-131">Eseguire funzioni di Azure in un contenitore Docker</span><span class="sxs-lookup"><span data-stu-id="35e49-131">Run Azure Functions in a Docker Container</span></span>](https://markheath.net/post/azure-functions-docker)
- [<span data-ttu-id="35e49-132">Creare una funzione in Linux usando un'immagine personalizzata</span><span class="sxs-lookup"><span data-stu-id="35e49-132">Create a function on Linux using a custom image</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image)
- [<span data-ttu-id="35e49-133">Funzioni di Azure con scalabilità automatica basata su eventi Kubernetes</span><span class="sxs-lookup"><span data-stu-id="35e49-133">Azure Functions with Kubernetes Event Driven Autoscaling</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-kubernetes-keda)

>[!div class="step-by-step"]
><span data-ttu-id="35e49-134">[Precedente](leverage-serverless-functions.md)
>[Successivo](deploy-containers-azure.md)</span><span class="sxs-lookup"><span data-stu-id="35e49-134">[Previous](leverage-serverless-functions.md)
[Next](deploy-containers-azure.md)</span></span>