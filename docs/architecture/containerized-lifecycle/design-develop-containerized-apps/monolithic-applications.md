---
title: Applicazioni monolitiche
description: Concetti di base dell'inserimento di applicazioni monolitiche in contenitori.
ms.date: 02/15/2019
ms.openlocfilehash: a67015452fb1245ef4b24a8dc50a4b33d3f9f32e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2019
ms.locfileid: "68673598"
---
# <a name="monolithic-applications"></a><span data-ttu-id="e44db-103">Applicazioni monolitiche</span><span class="sxs-lookup"><span data-stu-id="e44db-103">Monolithic applications</span></span>

<span data-ttu-id="e44db-104">In questo scenario si sta compilando un'unica applicazione o un unico servizio Web monolitico che deve essere distribuito come contenitore.</span><span class="sxs-lookup"><span data-stu-id="e44db-104">In this scenario, you're building a single and monolithic web application or service and deploying it as a container.</span></span> <span data-ttu-id="e44db-105">All'interno l'applicazione potrebbe non essere monolitica, ma includere diverse librerie, componenti o persino livelli (livello dell'applicazione, livello del dominio, livello di accesso ai dati, e così via).</span><span class="sxs-lookup"><span data-stu-id="e44db-105">Within the application, the structure might not be monolithic; it might comprise several libraries, components, or even layers (application layer, domain layer, data access layer, etc.).</span></span> <span data-ttu-id="e44db-106">Esternamente è un singolo contenitore, come un singolo processo, una singola applicazione Web o un singolo servizio.</span><span class="sxs-lookup"><span data-stu-id="e44db-106">Externally, it's a single container, like a single process, single web application, or single service.</span></span>

<span data-ttu-id="e44db-107">Per gestire questo modello, distribuire un singolo contenitore per rappresentare l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="e44db-107">To manage this model, you deploy a single container to represent the application.</span></span> <span data-ttu-id="e44db-108">Per eseguirne la scalabilità orizzontale, basta aggiungere più copie con un bilanciamento del carico davanti.</span><span class="sxs-lookup"><span data-stu-id="e44db-108">To scale it, just add a few more copies with a load balancer in front.</span></span> <span data-ttu-id="e44db-109">La semplicità deriva dalla gestione di un'unica distribuzione in un singolo contenitore o una singola macchina virtuale (VM).</span><span class="sxs-lookup"><span data-stu-id="e44db-109">The simplicity comes from managing a single deployment in a single container or virtual machine (VM).</span></span>

<span data-ttu-id="e44db-110">Tuttavia, in base al principio secondo il quale un contenitore esegue solo un'operazione e la esegue in un unico processo, lo schema monolitico potrebbe generare conflitti.</span><span class="sxs-lookup"><span data-stu-id="e44db-110">Following the principal that a container does one thing only, and does it in one process, the monolithic pattern is in conflict.</span></span> <span data-ttu-id="e44db-111">È possibile includere più componenti/librerie o livelli interni in ogni contenitore, come illustrato nella figura 4-1.</span><span class="sxs-lookup"><span data-stu-id="e44db-111">You can include multiple components/libraries or internal layers within each container, as illustrated in Figure 4-1.</span></span>

![La maggior parte delle funzionalità di un'app monolitica risiede in un unico processo o contenitore e l'app è suddivisa in componenti, librerie o livelli interni.](./media/image1.png)

<span data-ttu-id="e44db-113">**Figura 4-1.**</span><span class="sxs-lookup"><span data-stu-id="e44db-113">**Figure 4-1.**</span></span> <span data-ttu-id="e44db-114">Esempio di architettura di un'applicazione monolitica</span><span class="sxs-lookup"><span data-stu-id="e44db-114">An example of monolithic application architecture</span></span>

<span data-ttu-id="e44db-115">Lo svantaggio di questo approccio diventa evidente con l'eventuale crescita dell'applicazione, che ne richiede il ridimensionamento.</span><span class="sxs-lookup"><span data-stu-id="e44db-115">The downside to this approach comes if or when the application grows, requiring it to scale.</span></span> <span data-ttu-id="e44db-116">Se l'intera applicazione è stata ridimensionata, non ci sono problemi.</span><span class="sxs-lookup"><span data-stu-id="e44db-116">If the entire application scaled, it's not really a problem.</span></span> <span data-ttu-id="e44db-117">Tuttavia, nella maggior parte dei casi, solo alcune parti dell'applicazione rappresentano colli di bottiglia che richiedono il ridimensionamento, mentre altri componenti vengono usati di meno.</span><span class="sxs-lookup"><span data-stu-id="e44db-117">However, in most cases, a few parts of the application are the choke points that require scaling, whereas other components are used less.</span></span>

<span data-ttu-id="e44db-118">Usando il tipico esempio di e-commerce, la parte che probabilmente sarà necessario ridimensionare è il componente relativo alle informazioni sui prodotti.</span><span class="sxs-lookup"><span data-stu-id="e44db-118">Using the typical e-commerce example, what you likely need is to scale the product information component.</span></span> <span data-ttu-id="e44db-119">Il numero di clienti che visualizzano i prodotti è molto superiore al numero di quelli che li acquistano.</span><span class="sxs-lookup"><span data-stu-id="e44db-119">Many more customers browse products than purchase them.</span></span> <span data-ttu-id="e44db-120">Molti più clienti usano il carrello per poi usare la pipeline di pagamento,</span><span class="sxs-lookup"><span data-stu-id="e44db-120">More customers use their basket than use the payment pipeline.</span></span> <span data-ttu-id="e44db-121">meno clienti aggiungono commenti o visualizzano la cronologia degli acquisti.</span><span class="sxs-lookup"><span data-stu-id="e44db-121">Fewer customers add comments or view their purchase history.</span></span> <span data-ttu-id="e44db-122">E probabilmente sono pochi i dipendenti, in una singola area, che avranno bisogno di gestire i contenuti e le campagne di marketing.</span><span class="sxs-lookup"><span data-stu-id="e44db-122">And you likely have only a handful of employees, in a single region, that need to manage the content and marketing campaigns.</span></span> <span data-ttu-id="e44db-123">Con il ridimensionamento della progettazione monolitica, tutto il codice viene distribuito più volte.</span><span class="sxs-lookup"><span data-stu-id="e44db-123">By scaling the monolithic design, all of the code is deployed multiple times.</span></span>

<span data-ttu-id="e44db-124">Oltre al problema del ridimensionamento di tutti i componenti, le modifiche apportate a un singolo componente richiedono la completa riesecuzione dei test sull'intera applicazione e una ridistribuzione completa di tutte le istanze.</span><span class="sxs-lookup"><span data-stu-id="e44db-124">In addition to the "scale-everything" problem, changes to a single component require complete retesting of the entire application as well as a complete redeployment of all the instances.</span></span>

<span data-ttu-id="e44db-125">L'approccio monolitico è comune e molte organizzazioni usano questo metodo nelle loro attività di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="e44db-125">The monolithic approach is common, and many organizations are developing with this architectural method.</span></span> <span data-ttu-id="e44db-126">Molte sono soddisfatte dei risultati ottenuti, mentre altre risentono delle limitazioni insite in questo metodo.</span><span class="sxs-lookup"><span data-stu-id="e44db-126">Many enjoy good enough results, whereas others encounter limits.</span></span> <span data-ttu-id="e44db-127">Molte organizzazioni hanno progettato le proprie applicazioni usando questo modello perché gli strumenti e l'infrastruttura a loro disposizione erano troppo complesse per creare SOA e perché non ne hanno intravisto la necessità fino a quando le dimensioni dell'app non sono aumentate.</span><span class="sxs-lookup"><span data-stu-id="e44db-127">Many designed their applications in this model because the tools and infrastructure were too difficult to build SOAs, and they didn't see the need—until the app grew.</span></span>

<span data-ttu-id="e44db-128">Dal punto di vista dell'infrastruttura, ogni server può eseguire molte applicazioni all'interno dello stesso host e avere un rapporto accettabile di efficienza nell'utilizzo di risorse, come illustrato nella figura 4-2.</span><span class="sxs-lookup"><span data-stu-id="e44db-128">From an infrastructure perspective, each server can run many applications within the same host and have an acceptable ratio of efficiency in your resources usage, as shown in Figure 4-2.</span></span>

![Un singolo host può eseguire più app in contenitori separati.](./media/image2.png)

<span data-ttu-id="e44db-130">**Figura 4-2**.</span><span class="sxs-lookup"><span data-stu-id="e44db-130">**Figure 4-2.**</span></span> <span data-ttu-id="e44db-131">Host che esegue più app in contenitori separati</span><span class="sxs-lookup"><span data-stu-id="e44db-131">A host running multiple apps/containers</span></span>

<span data-ttu-id="e44db-132">Infine, dal punto di vista della disponibilità, le applicazioni monolitiche devono essere distribuite come un unico elemento. Questo significa che, in caso sia necessario eseguire un'operazione di *arresto e avvio*, questa interesserà tutte le funzionalità e tutti gli utenti durante la finestra di distribuzione.</span><span class="sxs-lookup"><span data-stu-id="e44db-132">Finally, from an availability perspective, monolithic applications must be deployed as a whole; that means that in case you must *stop and start*, all functionality and all users will be affected during the deployment window.</span></span> <span data-ttu-id="e44db-133">In alcuni casi, l'uso di Azure e di contenitori può ridurre al minimo queste situazioni e ridurre le probabilità di tempo di inattività dell'applicazione, come illustrato nella figura 4-3.</span><span class="sxs-lookup"><span data-stu-id="e44db-133">In certain situations, the use of Azure and containers can minimize these situations and reduce the probability of downtime of your application, as you can see in Figure 4-3.</span></span>

<span data-ttu-id="e44db-134">È possibile distribuire le applicazioni monolitiche in Azure usando VM dedicate per ogni istanza.</span><span class="sxs-lookup"><span data-stu-id="e44db-134">You can deploy monolithic applications in Azure by using dedicated VMs for each instance.</span></span> <span data-ttu-id="e44db-135">Con i [set di scalabilità di macchine virtuali di Azure](https://docs.microsoft.com/azure/virtual-machine-scale-sets/) è possibile ridimensionare facilmente le VM.</span><span class="sxs-lookup"><span data-stu-id="e44db-135">Using [Azure VM Scale Sets](https://docs.microsoft.com/azure/virtual-machine-scale-sets/), you can scale the VMs easily.</span></span>

<span data-ttu-id="e44db-136">È anche possibile usare i [Servizi app di Azure](https://azure.microsoft.com/services/app-service/) per eseguire le applicazioni monolitiche e ridimensionare facilmente le istanze senza la necessità di gestire le VM.</span><span class="sxs-lookup"><span data-stu-id="e44db-136">You can also use [Azure App Services](https://azure.microsoft.com/services/app-service/) to run monolithic applications and easily scale instances without having to manage the VMs.</span></span> <span data-ttu-id="e44db-137">I Servizi app di Azure possono eseguire anche singole istanze di contenitori Docker, semplificando la distribuzione.</span><span class="sxs-lookup"><span data-stu-id="e44db-137">Azure App Services can run single instances of Docker containers, as well, simplifying the deployment.</span></span>

<span data-ttu-id="e44db-138">È possibile distribuire più VM come host Docker ed eseguire un numero qualsiasi di contenitori per VM.</span><span class="sxs-lookup"><span data-stu-id="e44db-138">You can deploy multiple VMs as Docker hosts and run any number of containers per VM.</span></span> <span data-ttu-id="e44db-139">Quindi, usando Azure Load Balancer è possibile gestire la scalabilità, come illustrato nella figura 4-3.</span><span class="sxs-lookup"><span data-stu-id="e44db-139">Then, by using an Azure Load Balancer, as illustrated in the Figure 4-3, you can manage scaling.</span></span>

![È possibile eseguire la scalabilità orizzontale di un'app monolitica in diversi host che eseguono l'app in contenitori.](./media/image3.png)

<span data-ttu-id="e44db-141">**Figura 4-3**.</span><span class="sxs-lookup"><span data-stu-id="e44db-141">**Figure 4-3**.</span></span> <span data-ttu-id="e44db-142">Più host che eseguono la scalabilità orizzontale di una singola applicazione in app/contenitori Docker</span><span class="sxs-lookup"><span data-stu-id="e44db-142">Multiple hosts scaling-out a single Docker application apps/containers</span></span>

<span data-ttu-id="e44db-143">È possibile gestire la distribuzione degli stessi host tramite le tecniche di distribuzione tradizionali.</span><span class="sxs-lookup"><span data-stu-id="e44db-143">You can manage the deployment of the hosts themselves via traditional deployment techniques.</span></span>

<span data-ttu-id="e44db-144">È possibile gestire i contenitori Docker dalla riga di comando, usando comandi quali `docker run` e `docker-compose up`, ed è anche possibile automatizzarli nelle pipeline di recapito continuo e distribuirli negli host Docker da Azure DevOps Services, ad esempio.</span><span class="sxs-lookup"><span data-stu-id="e44db-144">You can manage Docker containers from the command line by using commands like `docker run` and `docker-compose up`, and you can also automate it in Continuous Delivery (CD) pipelines and deploy to Docker hosts from Azure DevOps Services, for instance.</span></span>

## <a name="monolithic-application-deployed-as-a-container"></a><span data-ttu-id="e44db-145">Applicazione monolitica distribuita come contenitore</span><span class="sxs-lookup"><span data-stu-id="e44db-145">Monolithic application deployed as a container</span></span>

<span data-ttu-id="e44db-146">Esistono vantaggi derivanti dall'uso di contenitori per gestire le distribuzioni di applicazioni monolitiche.</span><span class="sxs-lookup"><span data-stu-id="e44db-146">There are benefits to using containers to manage monolithic deployments.</span></span> <span data-ttu-id="e44db-147">Il ridimensionamento di istanze di contenitori è molto più veloce e semplice rispetto alla distribuzione di macchine virtuali aggiuntive.</span><span class="sxs-lookup"><span data-stu-id="e44db-147">Scaling the instances of containers is far faster and easier than deploying additional VMs.</span></span>

<span data-ttu-id="e44db-148">La distribuzione degli aggiornamenti come immagini Docker è molto più veloce ed efficiente per la rete.</span><span class="sxs-lookup"><span data-stu-id="e44db-148">Deploying updates as Docker images is far faster and network efficient.</span></span> <span data-ttu-id="e44db-149">L'avvio dei contenitori Docker richiede in genere pochi secondi, consentendo implementazioni più veloci.</span><span class="sxs-lookup"><span data-stu-id="e44db-149">Docker containers typically start in seconds, speeding rollouts.</span></span> <span data-ttu-id="e44db-150">Per chiudere un contenitore Docker, è sufficiente richiamare il comando `docker stop` che viene normalmente completato in meno di un secondo.</span><span class="sxs-lookup"><span data-stu-id="e44db-150">Tearing down a Docker container is as easy as invoking the `docker stop` command, typically completing in less than a second.</span></span>

<span data-ttu-id="e44db-151">Poiché i contenitori sono implicitamente non modificabili per impostazione predefinita, non è un problema se una VM viene danneggiata perché gli script di aggiornamento hanno tralasciato alcune configurazioni specifiche o alcuni file rimasti su disco.</span><span class="sxs-lookup"><span data-stu-id="e44db-151">Because containers are inherently immutable, by design, you never need to worry about corrupted VMs because an update script forgot to account for some specific configuration or file left on disk.</span></span>

<span data-ttu-id="e44db-152">Anche se le applicazioni monolitiche possano trarre vantaggio da Docker, in questo articolo i vantaggi vengono trattati solo in modo rapido.</span><span class="sxs-lookup"><span data-stu-id="e44db-152">Although monolithic apps can benefit from Docker, we're touching on only the tips of the benefits.</span></span> <span data-ttu-id="e44db-153">I vantaggi maggiori della gestione dei contenitori derivano dalla distribuzione con agenti di orchestrazione del contenitore, che gestiscono le varie istanze e il ciclo di vita di ogni istanza del contenitore.</span><span class="sxs-lookup"><span data-stu-id="e44db-153">The larger benefits of managing containers come from deploying with container orchestrators that manage the various instances and life cycle of each container instance.</span></span> <span data-ttu-id="e44db-154">La suddivisione dell'applicazione monolitica in sottosistemi scalabili, sviluppabili e distribuibili a livello individuale è il punto di ingresso al campo dei microservizi.</span><span class="sxs-lookup"><span data-stu-id="e44db-154">Breaking up the monolithic application into subsystems that can be scaled, developed, and deployed individually is your entry point into the realm of microservices.</span></span>

<span data-ttu-id="e44db-155">Per altre informazioni su come distribuire le applicazioni monolitiche con i contenitori e su come modernizzare le applicazioni, è possibile leggere questa Guida di Microsoft aggiuntiva, [Modernizzare le applicazioni .NET esistenti con il cloud di Azure e i contenitori Windows ](../../modernize-with-azure-containers/index.md), che è anche possibile scaricare in formato PDF da <https://aka.ms/LiftAndShiftWithContainersEbook>.</span><span class="sxs-lookup"><span data-stu-id="e44db-155">To learn about how to “lift and shift” monolithic applications with containers and how you can modernize your applications, you can read this additional Microsoft guide, [Modernize existing .NET applications with Azure cloud and Windows Containers](../../modernize-with-azure-containers/index.md), that you can also download as PDF from <https://aka.ms/LiftAndShiftWithContainersEbook>.</span></span>

## <a name="publish-a-single-docker-container-app-to-azure-app-service"></a><span data-ttu-id="e44db-156">Pubblicare una singola app contenitore Docker in Servizio app di Azure</span><span class="sxs-lookup"><span data-stu-id="e44db-156">Publish a single Docker container app to Azure App Service</span></span>

<span data-ttu-id="e44db-157">Servizio app di Azure è un ottimo modo per offrire servizi scalabili basati su un singolo contenitore, sia per convalidare rapidamente un contenitore distribuito in Azure, sia nel caso di un'app costituita da un singolo contenitore.</span><span class="sxs-lookup"><span data-stu-id="e44db-157">Either because you want to get a quick validation of a container deployed to Azure or because the app is simply a single-container app, Azure App Services provides a great way to provide scalable single-container services.</span></span>

<span data-ttu-id="e44db-158">Servizio app di Azure è intuitivo e consente di essere operativi in tempi rapidi perché offre un'integrazione ottimale con Git per compilare il codice in Microsoft Visual Studio e distribuirlo direttamente in Azure.</span><span class="sxs-lookup"><span data-stu-id="e44db-158">Using Azure App Service is intuitive and you can get up and running quickly because it provides great Git integration to take your code, build it in Microsoft Visual Studio, and directly deploy it to Azure.</span></span> <span data-ttu-id="e44db-159">Ma, tradizionalmente, ovvero senza Docker, se sono necessarie altre funzionalità, framework o dipendenze che non sono supportate in Servizi app, è necessario attendere fino a quando il team di Azure aggiorna tali dipendenze nel servizio app o passare ad altri servizi, come ad esempio Service Fabric, Servizi cloud o persino le normali VM, per cui si dispone di maggior controllo ed è possibile installare un componente o un framework richiesto per l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="e44db-159">But, traditionally (with no Docker), if you needed other capabilities, frameworks, or dependencies that aren't supported in App Services, you needed to wait for it until the Azure team updates those dependencies in App Service or switched to other services like Service Fabric, Cloud Services, or even plain VMs, for which you have further control and can install a required component or framework for your application.</span></span>

<span data-ttu-id="e44db-160">Ora quando si usa Visual Studio 2017, il supporto dei contenitori in Servizio app di Azure offre la possibilità di includere ciò che si vuole nell'ambiente dell'applicazione, come illustrato nella figura 4-4.</span><span class="sxs-lookup"><span data-stu-id="e44db-160">Now, as shown in Figure 4-4, when using Visual Studio 2017, container support in Azure App Service gives you the ability to include whatever you want in your app environment.</span></span> <span data-ttu-id="e44db-161">Se è stata aggiunta una dipendenza all'app perché l'app viene eseguita in un contenitore, è possibile includere tale dipendenza nel Dockerfile o nell'immagine Docker.</span><span class="sxs-lookup"><span data-stu-id="e44db-161">If you added a dependency to your app, because you're running it in a container, you get the capability of including those dependencies in your Dockerfile or Docker image.</span></span>

![Procedura guidata di Visual Studio per la pubblicazione in Servizio app di Azure, con la selezione del registro contenitori evidenziata.](./media/image4.png)

<span data-ttu-id="e44db-163">**Figura 4-4**.</span><span class="sxs-lookup"><span data-stu-id="e44db-163">**Figure 4-4**.</span></span> <span data-ttu-id="e44db-164">Pubblicazione di un contenitore in Servizio app di Azure da app/contenitori di Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e44db-164">Publishing a container to Azure App Service from Visual Studio apps/containers</span></span>

<span data-ttu-id="e44db-165">La figura 4-4 illustra anche che il flusso di pubblicazione esegue il push di un'immagine tramite un Registro Azure Container, ovvero un registro vicino alle distribuzioni in Azure e protetto dai gruppi e dagli account di Azure Active Directory, oppure in qualsiasi altro registro Docker, come Docker Hub o i registri locali.</span><span class="sxs-lookup"><span data-stu-id="e44db-165">Figure 4-4 also shows that the publish flow pushes an image through a Container Registry, which can be the Azure Container Registry (a registry near to your deployments in Azure and secured by Azure Active Directory groups and accounts) or any other Docker Registry like Docker Hub or on-premises registries.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e44db-166">[Precedente](common-container-design-principles.md)
>[Successivo](state-and-data-in-docker-applications.md)</span><span class="sxs-lookup"><span data-stu-id="e44db-166">[Previous](common-container-design-principles.md)
[Next](state-and-data-in-docker-applications.md)</span></span>