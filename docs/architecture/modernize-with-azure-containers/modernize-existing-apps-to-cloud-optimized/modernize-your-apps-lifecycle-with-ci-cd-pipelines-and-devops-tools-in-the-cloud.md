---
title: Modernizzare il ciclo di vita dell'app con le pipeline di integrazione continua/distribuzione continua e gli strumenti DevOps nel cloud
description: Modernizzare le applicazioni .NET esistenti con il cloud di Azure e i contenitori di Windows | Modernizza il ciclo di vita dell'app con pipeline CI/CD e strumenti DevOps nel cloud
ms.date: 04/30/2018
ms.openlocfilehash: fb4bfab4a891e9c8a73867f18cb8249775f9b7b9
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2019
ms.locfileid: "69578164"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a><span data-ttu-id="5d0aa-103">Modernizzare il ciclo di vita dell'app con le pipeline di integrazione continua/distribuzione continua e gli strumenti DevOps nel cloud</span><span class="sxs-lookup"><span data-stu-id="5d0aa-103">Modernize your app's lifecycle with CI/CD pipelines and DevOps tools in the cloud</span></span>

<span data-ttu-id="5d0aa-104">Le aziende odierne devono innovare a ritmo rapido per essere competitive nel Marketplace.</span><span class="sxs-lookup"><span data-stu-id="5d0aa-104">Today’s businesses need to innovate at a rapid pace to be competitive in the marketplace.</span></span> <span data-ttu-id="5d0aa-105">La distribuzione di applicazioni moderne di alta qualità richiede strumenti e processi DevOps cruciali per implementare questo ciclo costante di innovazione.</span><span class="sxs-lookup"><span data-stu-id="5d0aa-105">Delivering high-quality, modern applications requires DevOps tools and processes that are critical to implement this constant cycle of innovation.</span></span> <span data-ttu-id="5d0aa-106">Con gli strumenti DevOps corretti, gli sviluppatori possono semplificare la distribuzione continua e ottenere applicazioni innovative in modo più rapido dagli utenti.</span><span class="sxs-lookup"><span data-stu-id="5d0aa-106">With the right DevOps tools, developers can streamline continuous deployment and get innovative applications into the hands of users more quickly.</span></span>

<span data-ttu-id="5d0aa-107">Sebbene le procedure di integrazione e distribuzione continue siano ben stabilite, l'introduzione dei contenitori introduce nuove considerazioni, soprattutto quando si lavora con applicazioni a più contenitori.</span><span class="sxs-lookup"><span data-stu-id="5d0aa-107">Although continuous integration and deployment practices are well established, the introduction of containers introduces new considerations, particularly when you are working with multi-container applications.</span></span>

<span data-ttu-id="5d0aa-108">Azure DevOps Services supporta l'integrazione e la distribuzione continue di applicazioni multicontenitore in diversi ambienti tramite le attività di distribuzione Azure DevOps Services ufficiali:</span><span class="sxs-lookup"><span data-stu-id="5d0aa-108">Azure DevOps Services supports continuous integration and deployment of multi-container applications to a variety of environments through the official Azure DevOps Services deployment tasks:</span></span>

- [<span data-ttu-id="5d0aa-109">Eseguire la distribuzione in un app Web per contenitori di Azure</span><span class="sxs-lookup"><span data-stu-id="5d0aa-109">Deploy to an Azure Web App for Containers</span></span>](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-docker-webapp?view=azure-devops)

- [<span data-ttu-id="5d0aa-110">Eseguire la distribuzione nel servizio contenitore di Azure-Kubernetes</span><span class="sxs-lookup"><span data-stu-id="5d0aa-110">Deploy to Azure Container Service – Kubernetes</span></span>](https://docs.microsoft.com/azure/devops/build-release/apps/cd/azure/deploy-container-kubernetes)

<span data-ttu-id="5d0aa-111">È anche possibile eseguire la distribuzione a [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) o DC/OS usando Azure DevOps Services attività basate su script.</span><span class="sxs-lookup"><span data-stu-id="5d0aa-111">But you also can deploy to [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) or DC/OS by using Azure DevOps Services script-based tasks.</span></span>

<span data-ttu-id="5d0aa-112">Per continuare a facilitare l'agilità della distribuzione, questi strumenti offrono ottime esperienze di distribuzione da sviluppo a test per la produzione per i carichi di lavoro dei contenitori, con una scelta di sviluppo e soluzioni di integrazione continua/distribuzione continua.</span><span class="sxs-lookup"><span data-stu-id="5d0aa-112">To continue facilitating deployment agility, these tools provide excellent dev-to-test-to-production deployment experiences for container workloads, with a choice of development and CI/CD solutions.</span></span>

<span data-ttu-id="5d0aa-113">La figura 4-12 Mostra una pipeline di distribuzione continua che distribuisce in un cluster Kubernetes nel servizio contenitore di Azure.</span><span class="sxs-lookup"><span data-stu-id="5d0aa-113">Figure 4-12 shows a continuous deployment pipeline that deploys to a Kubernetes cluster in Azure Container Service.</span></span>

![Azure DevOps Services pipeline di distribuzione continua, distribuzione in un cluster Kubernetes](./media/image12.png)

> <span data-ttu-id="5d0aa-115">**Figura 4-12.**</span><span class="sxs-lookup"><span data-stu-id="5d0aa-115">**Figure 4-12.**</span></span> <span data-ttu-id="5d0aa-116">Azure DevOps Services pipeline di distribuzione continua, distribuzione in un cluster Kubernetes</span><span class="sxs-lookup"><span data-stu-id="5d0aa-116">Azure DevOps Services continuous deployment pipeline, deploying to a Kubernetes cluster</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5d0aa-117">[Precedente](modernize-your-apps-with-monitoring-and-telemetry.md)
>[Successivo](migrate-to-hybrid-cloud-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="5d0aa-117">[Previous](modernize-your-apps-with-monitoring-and-telemetry.md)
[Next](migrate-to-hybrid-cloud-scenarios.md)</span></span>