---
title: Creazione ed esecuzione di un'istanza del flusso di lavoro
ms.date: 03/30/2017
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
ms.openlocfilehash: fe00ebec8d81e77ff982a36419f1b0a988fcd4ab
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2019
ms.locfileid: "70016052"
---
# <a name="creating-and-running-a-workflow-instance"></a><span data-ttu-id="b6ee6-102">Creazione ed esecuzione di un'istanza del flusso di lavoro</span><span class="sxs-lookup"><span data-stu-id="b6ee6-102">Creating and Running a Workflow Instance</span></span>

<span data-ttu-id="b6ee6-103">In questo esempio viene illustrato come eseguire un'istanza del flusso di lavoro,</span><span class="sxs-lookup"><span data-stu-id="b6ee6-103">This sample shows how to run a workflow instance.</span></span> <span data-ttu-id="b6ee6-104">sia in modo sincrono che asincrono.</span><span class="sxs-lookup"><span data-stu-id="b6ee6-104">It shows how to execute it synchronously and asynchronously.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="b6ee6-105">Dimostrazione</span><span class="sxs-lookup"><span data-stu-id="b6ee6-105">Demonstrates</span></span>

<span data-ttu-id="b6ee6-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="b6ee6-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span></span>

## <a name="discussion"></a><span data-ttu-id="b6ee6-107">Discussione</span><span class="sxs-lookup"><span data-stu-id="b6ee6-107">Discussion</span></span>

<span data-ttu-id="b6ee6-108">Nella prima parte dell'esempio viene usato <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span><span class="sxs-lookup"><span data-stu-id="b6ee6-108">The first part of the sample uses <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span> <span data-ttu-id="b6ee6-109">Si tratta della modalità di base per eseguire un flusso di lavoro.</span><span class="sxs-lookup"><span data-stu-id="b6ee6-109">This is the most basic way to execute a workflow.</span></span> <span data-ttu-id="b6ee6-110">I flussi di lavoro eseguiti con <xref:System.Activities.WorkflowInvoker.Invoke%2A> possono esserlo solo in modo sincrono.</span><span class="sxs-lookup"><span data-stu-id="b6ee6-110">Workflows executed with <xref:System.Activities.WorkflowInvoker.Invoke%2A> are executed synchronously.</span></span>

<span data-ttu-id="b6ee6-111">Nella seconda parte dell'esempio viene usata la classe <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="b6ee6-111">The second part of the sample uses the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="b6ee6-112"><xref:System.Activities.WorkflowApplication> consente un maggiore controllo su ogni istanza, inclusa la possibilità di interagire con il flusso di lavoro in esecuzione ed eseguirlo in modo asincrono.</span><span class="sxs-lookup"><span data-stu-id="b6ee6-112"><xref:System.Activities.WorkflowApplication> enables you to have more control over each instance, including the ability to interact with the running workflow and to run the workflow asynchronously.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b6ee6-113">È possibile che gli esempi siano già installati nel computer.</span><span class="sxs-lookup"><span data-stu-id="b6ee6-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b6ee6-114">Verificare la directory seguente (impostazione predefinita) prima di continuare.</span><span class="sxs-lookup"><span data-stu-id="b6ee6-114">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="b6ee6-115">Se questa directory non esiste, passare a [Windows Communication Foundation (WCF) ed esempi di Windows Workflow Foundation (WF) per .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) per scaricare tutti i Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ed esempi.</span><span class="sxs-lookup"><span data-stu-id="b6ee6-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b6ee6-116">Questo esempio si trova nella directory seguente.</span><span class="sxs-lookup"><span data-stu-id="b6ee6-116">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`

## <a name="see-also"></a><span data-ttu-id="b6ee6-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b6ee6-117">See also</span></span>

- [<span data-ttu-id="b6ee6-118">Uso di WorkflowInvoker e WorkflowApplication</span><span class="sxs-lookup"><span data-stu-id="b6ee6-118">Using WorkflowInvoker and WorkflowApplication</span></span>](../using-workflowinvoker-and-workflowapplication.md)
