---
title: Tabella decisioni. Framework .NET da usare per Docker
description: Architettura di microservizi .NET per applicazioni .NET in contenitori | Tabella decisioni, framework .NET da usare per Docker
ms.date: 09/11/2018
ms.openlocfilehash: 96b2750e52d64b06444b7f87dea624879f37d3d7
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2019
ms.locfileid: "68675818"
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a><span data-ttu-id="72007-104">Tabella decisioni: framework .NET da usare per Docker</span><span class="sxs-lookup"><span data-stu-id="72007-104">Decision table: .NET frameworks to use for Docker</span></span>

<span data-ttu-id="72007-105">La tabella decisioni seguente indica se usare .NET Framework o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="72007-105">The following decision table summarizes whether to use .NET Framework or .NET Core.</span></span> <span data-ttu-id="72007-106">Tenere presente che per i contenitori Linux sono necessari host Docker (macchine virtuali o server) basati su Linux e che per i contenitori Windows sono necessari host Docker (macchine virtuali o server) basati su Windows Server.</span><span class="sxs-lookup"><span data-stu-id="72007-106">Remember that for Linux containers, you need Linux-based Docker hosts (VMs or servers) and that for Windows Containers you need Windows Server based Docker hosts (VMs or servers).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="72007-107">I computer di sviluppo eseguiranno un host Docker, Linux o Windows.</span><span class="sxs-lookup"><span data-stu-id="72007-107">Your development machines will run one Docker host, either Linux or Windows.</span></span> <span data-ttu-id="72007-108">I servizi correlati da eseguire e testare insieme in un'unica soluzione dovranno essere eseguiti sulla stessa piattaforma di contenitori.</span><span class="sxs-lookup"><span data-stu-id="72007-108">Related microservices that you want to run and test together in one solution will all need to run on the same container platform.</span></span>

<table>
<thead>
<tr class="header">
<th><span data-ttu-id="72007-109"><strong>Architettura/Tipo di app</strong></span><span class="sxs-lookup"><span data-stu-id="72007-109"><strong>Architecture / App Type</strong></span></span></th>
<th><span data-ttu-id="72007-110"><strong>Contenitori Linux</strong></span><span class="sxs-lookup"><span data-stu-id="72007-110"><strong>Linux containers</strong></span></span></th>
<th><span data-ttu-id="72007-111"><strong>Contenitori Windows</strong></span><span class="sxs-lookup"><span data-stu-id="72007-111"><strong>Windows Containers</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="72007-112">Microservizi in contenitori</span><span class="sxs-lookup"><span data-stu-id="72007-112">Microservices on containers</span></span></td>
<td><span data-ttu-id="72007-113">.NET Core</span><span class="sxs-lookup"><span data-stu-id="72007-113">.NET Core</span></span></td>
<td><span data-ttu-id="72007-114">.NET Core</span><span class="sxs-lookup"><span data-stu-id="72007-114">.NET Core</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="72007-115">App monolitica</span><span class="sxs-lookup"><span data-stu-id="72007-115">Monolithic app</span></span></td>
<td><span data-ttu-id="72007-116">.NET Core</span><span class="sxs-lookup"><span data-stu-id="72007-116">.NET Core</span></span></td>
<td><p><span data-ttu-id="72007-117">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="72007-117">.NET Framework</span></span></p>
<p><span data-ttu-id="72007-118">.NET Core</span><span class="sxs-lookup"><span data-stu-id="72007-118">.NET Core</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="72007-119">Prestazioni e scalabilità migliori del settore</span><span class="sxs-lookup"><span data-stu-id="72007-119">Best-in-class performance and scalability</span></span></td>
<td><span data-ttu-id="72007-120">.NET Core</span><span class="sxs-lookup"><span data-stu-id="72007-120">.NET Core</span></span></td>
<td><span data-ttu-id="72007-121">.NET Core</span><span class="sxs-lookup"><span data-stu-id="72007-121">.NET Core</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="72007-122">Migrazione di un'app legacy (brown field) Windows Server ai contenitori</span><span class="sxs-lookup"><span data-stu-id="72007-122">Windows Server legacy app ("brown-field") migration to containers</span></span></td>
<td>--</td>
<td><span data-ttu-id="72007-123">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="72007-123">.NET Framework</span></span></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="72007-124">Nuovo sviluppo basato su contenitori (green field)</span><span class="sxs-lookup"><span data-stu-id="72007-124">New container-based development ("green-field")</span></span></td>
<td><span data-ttu-id="72007-125">.NET Core</span><span class="sxs-lookup"><span data-stu-id="72007-125">.NET Core</span></span></td>
<td><span data-ttu-id="72007-126">.NET Core</span><span class="sxs-lookup"><span data-stu-id="72007-126">.NET Core</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="72007-127">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="72007-127">ASP.NET Core</span></span></td>
<td><span data-ttu-id="72007-128">.NET Core</span><span class="sxs-lookup"><span data-stu-id="72007-128">.NET Core</span></span></td>
<td><p><span data-ttu-id="72007-129">.NET Core (consigliato)</span><span class="sxs-lookup"><span data-stu-id="72007-129">.NET Core (recommended)</span></span></p>
<p><span data-ttu-id="72007-130">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="72007-130">.NET Framework</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="72007-131">ASP.NET 4 (MVC 5, Web API 2 e Web Form)</span><span class="sxs-lookup"><span data-stu-id="72007-131">ASP.NET 4 (MVC 5, Web API 2, and Web Forms)</span></span></td>
<td>--</td>
<td><span data-ttu-id="72007-132">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="72007-132">.NET Framework</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="72007-133">Servizi SignalR</span><span class="sxs-lookup"><span data-stu-id="72007-133">SignalR services</span></span></td>
<td><span data-ttu-id="72007-134">.NET Core 2.1 o versioni successive</span><span class="sxs-lookup"><span data-stu-id="72007-134">.NET Core 2.1 or higher version</span></span></td>
<td><p><span data-ttu-id="72007-135">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="72007-135">.NET Framework</span></span></p>
<p><span data-ttu-id="72007-136">.NET Core 2.1 o versioni successive</span><span class="sxs-lookup"><span data-stu-id="72007-136">.NET Core 2.1 or higher version</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="72007-137">WCF, WF e altri framework legacy</span><span class="sxs-lookup"><span data-stu-id="72007-137">WCF, WF, and other legacy frameworks</span></span></td>
<td><span data-ttu-id="72007-138">WCF in .NET Core (solo la libreria client WCF)</span><span class="sxs-lookup"><span data-stu-id="72007-138">WCF in .NET Core (only the WCF client library)</span></span></td>
<td><p><span data-ttu-id="72007-139">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="72007-139">.NET Framework</span></span></p>
<p><span data-ttu-id="72007-140">WCF in .NET Core (solo la libreria client WCF)</span><span class="sxs-lookup"><span data-stu-id="72007-140">WCF in .NET Core (only the WCF client library)</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="72007-141">Utilizzo di servizi di Azure</span><span class="sxs-lookup"><span data-stu-id="72007-141">Consumption of Azure services</span></span></td>
<td><p><span data-ttu-id="72007-142">.NET Core</span><span class="sxs-lookup"><span data-stu-id="72007-142">.NET Core</span></span></p>
<p><span data-ttu-id="72007-143">(prossimamente tutti i servizi di Azure forniranno SDK client per .NET Core)</span><span class="sxs-lookup"><span data-stu-id="72007-143">(eventually all Azure services will provide client SDKs for .NET Core)</span></span></p></td>
<td><p><span data-ttu-id="72007-144">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="72007-144">.NET Framework</span></span></p>
<p><span data-ttu-id="72007-145">.NET Core</span><span class="sxs-lookup"><span data-stu-id="72007-145">.NET Core</span></span></p>
<p><span data-ttu-id="72007-146">(prossimamente tutti i servizi di Azure forniranno SDK client per .NET Core)</span><span class="sxs-lookup"><span data-stu-id="72007-146">(eventually all Azure services will provide client SDKs for .NET Core)</span></span></p></td>
</tr>
</tbody>
</table>

>[!div class="step-by-step"]
><span data-ttu-id="72007-147">[Precedente](net-framework-container-scenarios.md)
>[Successivo](net-container-os-targets.md)</span><span class="sxs-lookup"><span data-stu-id="72007-147">[Previous](net-framework-container-scenarios.md)
[Next](net-container-os-targets.md)</span></span>
