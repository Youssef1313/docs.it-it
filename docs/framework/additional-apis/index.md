---
title: Librerie di classi e API aggiuntive
ms.date: 01/29/2018
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
author: mairaw
ms.author: mairaw
ms.topic: conceptual
ms.openlocfilehash: 0aed6f32bbd3ffdc9446e9d17be2d90c62444ee1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053248"
---
# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="36ede-102">Librerie di classi e API aggiuntive</span><span class="sxs-lookup"><span data-stu-id="36ede-102">Additional class libraries and APIs</span></span>

<span data-ttu-id="36ede-103">Il .NET Framework è in continua evoluzione.</span><span class="sxs-lookup"><span data-stu-id="36ede-103">The .NET Framework is constantly evolving.</span></span> <span data-ttu-id="36ede-104">Per migliorare lo sviluppo multipiattaforma e introdurre nuove funzionalità in anticipo, le nuove funzionalità vengono rilasciate fuori banda (OOB).</span><span class="sxs-lookup"><span data-stu-id="36ede-104">To improve cross-platform development and introduce new functionality early, new features are released out of band (OOB).</span></span> <span data-ttu-id="36ede-105">Questo argomento elenca i progetti fuori banda (OOB) per i quali viene fornita la documentazione.</span><span class="sxs-lookup"><span data-stu-id="36ede-105">This topic lists the OOB projects that we provide documentation for.</span></span>  
  
<span data-ttu-id="36ede-106">Inoltre, alcune librerie sono destinate a piattaforme o implementazioni specifiche di .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="36ede-106">In addition, some libraries target specific platforms or implementations of the .NET Framework.</span></span> <span data-ttu-id="36ede-107">Ad esempio, la <xref:System.Text.CodePagesEncodingProvider> classe rende disponibili le codifiche della tabella codici per le app UWP sviluppate usando il .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="36ede-107">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using the .NET Framework.</span></span> <span data-ttu-id="36ede-108">Questo argomento include anche un elenco di queste librerie.</span><span class="sxs-lookup"><span data-stu-id="36ede-108">This topic lists these libraries as well.</span></span>  
  
## <a name="oob-projects"></a><span data-ttu-id="36ede-109">Progetti OOB</span><span class="sxs-lookup"><span data-stu-id="36ede-109">OOB projects</span></span>
  
| <span data-ttu-id="36ede-110">Progetto</span><span class="sxs-lookup"><span data-stu-id="36ede-110">Project</span></span> | <span data-ttu-id="36ede-111">Descrizione</span><span class="sxs-lookup"><span data-stu-id="36ede-111">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | <span data-ttu-id="36ede-112">Fornisce raccolte thread-safe e che non modificano mai il contenuto.</span><span class="sxs-lookup"><span data-stu-id="36ede-112">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <xref:System.Net.Http.WinHttpHandler> | <span data-ttu-id="36ede-113">Fornisce un gestore di messaggi per <xref:System.Net.Http.HttpClient> basato sull'interfaccia WinHTTP di Windows.</span><span class="sxs-lookup"><span data-stu-id="36ede-113">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| <xref:System.Numerics> | <span data-ttu-id="36ede-114">Fornisce una libreria di tipi di vettori in grado di sfruttare l'accelerazione basata su hardware SIMD.</span><span class="sxs-lookup"><span data-stu-id="36ede-114">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>| 
| <xref:System.Threading.Tasks.Dataflow> | <span data-ttu-id="36ede-115">La libreria del flusso di dati TPL fornisce i componenti del flusso di dati per aumentare l'affidabilità delle applicazioni abilitate per la concorrenza.</span><span class="sxs-lookup"><span data-stu-id="36ede-115">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |  

## <a name="platform-specific-libraries"></a><span data-ttu-id="36ede-116">Librerie specifiche della piattaforma</span><span class="sxs-lookup"><span data-stu-id="36ede-116">Platform-specific libraries</span></span>
  
| <span data-ttu-id="36ede-117">Progetto</span><span class="sxs-lookup"><span data-stu-id="36ede-117">Project</span></span> | <span data-ttu-id="36ede-118">Descrizione</span><span class="sxs-lookup"><span data-stu-id="36ede-118">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <span data-ttu-id="36ede-119">Estende la <xref:System.Text.EncodingProvider> classe per rendere disponibili le codifiche della tabella codici alle app destinate al piattaforma UWP (Universal Windows Platform).</span><span class="sxs-lookup"><span data-stu-id="36ede-119">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |  
  
## <a name="private-apis"></a><span data-ttu-id="36ede-120">API private</span><span class="sxs-lookup"><span data-stu-id="36ede-120">Private APIs</span></span>  

<span data-ttu-id="36ede-121">Queste API supportano l'infrastruttura del prodotto e non sono progettate/supportate per l'uso direttamente dal codice.</span><span class="sxs-lookup"><span data-stu-id="36ede-121">These APIs support the product infrastructure and are not intended/supported to be used directly from your code.</span></span>  
  
| <span data-ttu-id="36ede-122">Nome dell'API</span><span class="sxs-lookup"><span data-stu-id="36ede-122">API Name</span></span> |
| -------- |
| [<span data-ttu-id="36ede-123">Classe System .NET. Connection</span><span class="sxs-lookup"><span data-stu-id="36ede-123">System.Net.Connection Class</span></span>](connection.md) |
| [<span data-ttu-id="36ede-124">Campo di writeback di System .NET\_. Connection. m</span><span class="sxs-lookup"><span data-stu-id="36ede-124">System.Net.Connection.m\_WriteList Field</span></span>](m_writelist.md) |
| [<span data-ttu-id="36ede-125">Classe System .NET. ConnectionGroup</span><span class="sxs-lookup"><span data-stu-id="36ede-125">System.Net.ConnectionGroup Class</span></span>](connectiongroup.md) |
| [<span data-ttu-id="36ede-126">System.Net.ConnectionGroup.m\_ConnectionList Field</span><span class="sxs-lookup"><span data-stu-id="36ede-126">System.Net.ConnectionGroup.m\_ConnectionList Field</span></span>](m_connectionlist.md) |
| [<span data-ttu-id="36ede-127">Classe System .NET. CoreResponseData</span><span class="sxs-lookup"><span data-stu-id="36ede-127">System.Net.CoreResponseData Class</span></span>](coreresponsedata.md) |
| [<span data-ttu-id="36ede-128">System.Net.CoreResponseData.m\_ResponseHeaders Field</span><span class="sxs-lookup"><span data-stu-id="36ede-128">System.Net.CoreResponseData.m\_ResponseHeaders Field</span></span>](coreresponsedata_m_responseheaders.md) |
| [<span data-ttu-id="36ede-129">System.Net.CoreResponseData.m\_StatusCode Field</span><span class="sxs-lookup"><span data-stu-id="36ede-129">System.Net.CoreResponseData.m\_StatusCode Field</span></span>](coreresponsedata_m_statuscode.md) |
| [<span data-ttu-id="36ede-130">System .NET. HttpWebRequest. \_Campo autodirects</span><span class="sxs-lookup"><span data-stu-id="36ede-130">System.Net.HttpWebRequest.\_AutoRedirects Field</span></span>](_autoredirects.md) |
| [<span data-ttu-id="36ede-131">System .NET. HttpWebRequest. \_Campo CoreResponse</span><span class="sxs-lookup"><span data-stu-id="36ede-131">System.Net.HttpWebRequest.\_CoreResponse Field</span></span>](httpwebrequest__coreresponse.md) |
| [<span data-ttu-id="36ede-132">System .NET. HttpWebRequest. \_Campo HttpResponse</span><span class="sxs-lookup"><span data-stu-id="36ede-132">System.Net.HttpWebRequest.\_HttpResponse Field</span></span>](_httpresponse.md) |
| [<span data-ttu-id="36ede-133">System.Net.ServicePoint.m\_ConnectionGroupList Field</span><span class="sxs-lookup"><span data-stu-id="36ede-133">System.Net.ServicePoint.m\_ConnectionGroupList Field</span></span>](m_connectiongrouplist.md) |
| [<span data-ttu-id="36ede-134">System.Net.ServicePointManager.s\_ServicePointTable Field</span><span class="sxs-lookup"><span data-stu-id="36ede-134">System.Net.ServicePointManager.s\_ServicePointTable Field</span></span>](s_servicepointtable.md) |
| [<span data-ttu-id="36ede-135">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span><span class="sxs-lookup"><span data-stu-id="36ede-135">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span></span>](s-isdebuggercheckdisabledfortestpurposes-field.md) |
| [<span data-ttu-id="36ede-136">Classe System. Windows. Forms. Design. DataMemberFieldEditor</span><span class="sxs-lookup"><span data-stu-id="36ede-136">System.Windows.Forms.Design.DataMemberFieldEditor Class</span></span>](datamemberfieldeditor-class.md) |
| [<span data-ttu-id="36ede-137">Classe System. Windows. Forms. Design. DataMemberListEditor</span><span class="sxs-lookup"><span data-stu-id="36ede-137">System.Windows.Forms.Design.DataMemberListEditor Class</span></span>](datamemberlisteditor-class.md) |
  
## <a name="see-also"></a><span data-ttu-id="36ede-138">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="36ede-138">See also</span></span>

- [<span data-ttu-id="36ede-139">.NET Framework e rilascio fuori programma</span><span class="sxs-lookup"><span data-stu-id="36ede-139">The .NET Framework and Out-of-Band Releases</span></span>](../get-started/the-net-framework-and-out-of-band-releases.md)
