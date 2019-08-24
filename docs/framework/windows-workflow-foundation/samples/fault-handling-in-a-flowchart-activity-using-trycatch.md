---
title: Gestione errori in un'attività Flowchart utilizzando TryCatch
ms.date: 03/30/2017
ms.assetid: 50922964-bfe0-4ba8-9422-0e7220d514fd
ms.openlocfilehash: 42eb660aff01c7e29227c28a6ad0d47d4370eb91
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2019
ms.locfileid: "70016024"
---
# <a name="fault-handling-in-a-flowchart-activity-using-trycatch"></a><span data-ttu-id="058f3-102">Gestione errori in un'attività Flowchart utilizzando TryCatch</span><span class="sxs-lookup"><span data-stu-id="058f3-102">Fault Handling in a Flowchart Activity Using TryCatch</span></span>

<span data-ttu-id="058f3-103">In questo esempio viene illustrato come è possibile usare l'attività <xref:System.Activities.Statements.TryCatch> all'interno di un'attività del flusso di controllo complessa.</span><span class="sxs-lookup"><span data-stu-id="058f3-103">This sample shows how the <xref:System.Activities.Statements.TryCatch> activity can be used within a complex control flow activity.</span></span>

<span data-ttu-id="058f3-104">In questo esempio vengono passati un codice promozione e un numero di elementi figlio come variabili a un'attività <xref:System.Activities.Statements.Flowchart> che calcola un sconto in base a formule che corrispondono al codice di promozione.</span><span class="sxs-lookup"><span data-stu-id="058f3-104">In this sample, a promotion code and number of children are passed as variables to a <xref:System.Activities.Statements.Flowchart> activity that calculates a discount based on formulae that correspond to the promotion code.</span></span> <span data-ttu-id="058f3-105">Nell'esempio è incluso codice imperativo e versioni della finestra di progettazione del flusso di lavoro dell'esempio.</span><span class="sxs-lookup"><span data-stu-id="058f3-105">The sample includes imperative code and workflow designer versions of the sample.</span></span>

<span data-ttu-id="058f3-106">Nella tabella seguente sono indicate in dettaglio le variabili dell'attività `CreateFlowchartWithFaults`.</span><span class="sxs-lookup"><span data-stu-id="058f3-106">The following table details the variables for the `CreateFlowchartWithFaults` activity.</span></span>

|<span data-ttu-id="058f3-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="058f3-107">Parameters</span></span>|<span data-ttu-id="058f3-108">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="058f3-108">Description</span></span>|
|----------------|-----------------|
|<span data-ttu-id="058f3-109">promoCode</span><span class="sxs-lookup"><span data-stu-id="058f3-109">promoCode</span></span>|<span data-ttu-id="058f3-110">Codice promozione.</span><span class="sxs-lookup"><span data-stu-id="058f3-110">The promotion code.</span></span> <span data-ttu-id="058f3-111">Digitare:  String</span><span class="sxs-lookup"><span data-stu-id="058f3-111">Type: String</span></span><br /><br /> <span data-ttu-id="058f3-112">I valori possibili con descrizione tra parentesi:</span><span class="sxs-lookup"><span data-stu-id="058f3-112">The possible values with description in parentheses:</span></span><br /><br /> <span data-ttu-id="058f3-113">-Singolo (singolo)</span><span class="sxs-lookup"><span data-stu-id="058f3-113">-   Single (Single)</span></span><br /><span data-ttu-id="058f3-114">-MNK (sposato senza figli).</span><span class="sxs-lookup"><span data-stu-id="058f3-114">-   MNK (Married with no kids.)</span></span><br /><span data-ttu-id="058f3-115">-MWK (sposato con Kids.)</span><span class="sxs-lookup"><span data-stu-id="058f3-115">-   MWK (Married with kids.)</span></span>|
|<span data-ttu-id="058f3-116">numKids</span><span class="sxs-lookup"><span data-stu-id="058f3-116">numKids</span></span>|<span data-ttu-id="058f3-117">Numero di bambini.</span><span class="sxs-lookup"><span data-stu-id="058f3-117">The number of children.</span></span> <span data-ttu-id="058f3-118">Tipo: int</span><span class="sxs-lookup"><span data-stu-id="058f3-118">Type: int</span></span>|

<span data-ttu-id="058f3-119">L'attività `CreateFlowchartWithFaults` usa un'attività <xref:System.Activities.Statements.FlowSwitch%601> che passa l'argomento `promoCode` e calcola lo sconto usando la formula seguente.</span><span class="sxs-lookup"><span data-stu-id="058f3-119">The `CreateFlowchartWithFaults` activity uses a <xref:System.Activities.Statements.FlowSwitch%601> activity that switches on the `promoCode` argument and calculates the discount using the following formula.</span></span>

|<span data-ttu-id="058f3-120">Valore di `promoCode`</span><span class="sxs-lookup"><span data-stu-id="058f3-120">Value of `promoCode`</span></span>|<span data-ttu-id="058f3-121">Sconto (%)</span><span class="sxs-lookup"><span data-stu-id="058f3-121">Discount (%)</span></span>|
|--------------------------|--------------------|
|<span data-ttu-id="058f3-122">Single</span><span class="sxs-lookup"><span data-stu-id="058f3-122">Single</span></span>|<span data-ttu-id="058f3-123">10</span><span class="sxs-lookup"><span data-stu-id="058f3-123">10</span></span>|
|<span data-ttu-id="058f3-124">MNK</span><span class="sxs-lookup"><span data-stu-id="058f3-124">MNK</span></span>|<span data-ttu-id="058f3-125">15</span><span class="sxs-lookup"><span data-stu-id="058f3-125">15</span></span>|
|<span data-ttu-id="058f3-126">MWK</span><span class="sxs-lookup"><span data-stu-id="058f3-126">MWK</span></span>|<span data-ttu-id="058f3-127">15 + (1-1/`numberOfKids`)\*10 **Nota:**  Potenzialmente, questo calcolo può generare <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="058f3-127">15 + (1 – 1/`numberOfKids`)\*10 **Note:**  Potentially, this calculation can throw a <xref:System.DivideByZeroException>.</span></span> <span data-ttu-id="058f3-128">Viene quindi eseguito il wrapping del calcolo dello sconto in un'attività <xref:System.Activities.Statements.TryCatch> che rileva l'eccezione <xref:System.DivideByZeroException> e imposta lo sconto su zero.</span><span class="sxs-lookup"><span data-stu-id="058f3-128">So, the discount calculation is wrapped in a <xref:System.Activities.Statements.TryCatch> activity that catches the <xref:System.DivideByZeroException> exception and sets the discount to zero.</span></span>|

#### <a name="to-use-this-sample"></a><span data-ttu-id="058f3-129">Per usare questo esempio</span><span class="sxs-lookup"><span data-stu-id="058f3-129">To use this sample</span></span>

1. <span data-ttu-id="058f3-130">Con Visual Studio 2010 aprire il file della soluzione FlowchartWithFaultHandling. sln.</span><span class="sxs-lookup"><span data-stu-id="058f3-130">Using Visual Studio 2010, open the FlowchartWithFaultHandling.sln solution file.</span></span>

2. <span data-ttu-id="058f3-131">Per compilare la soluzione, premere CTRL+MAIUSC+B.</span><span class="sxs-lookup"><span data-stu-id="058f3-131">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="058f3-132">Per eseguire la soluzione, premere F5.</span><span class="sxs-lookup"><span data-stu-id="058f3-132">To run the solution, press F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="058f3-133">È possibile che gli esempi siano già installati nel computer.</span><span class="sxs-lookup"><span data-stu-id="058f3-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="058f3-134">Verificare la directory seguente (impostazione predefinita) prima di continuare.</span><span class="sxs-lookup"><span data-stu-id="058f3-134">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="058f3-135">Se questa directory non esiste, passare a [Windows Communication Foundation (WCF) ed esempi di Windows Workflow Foundation (WF) per .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) per scaricare tutti i Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ed esempi.</span><span class="sxs-lookup"><span data-stu-id="058f3-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="058f3-136">Questo esempio si trova nella directory seguente.</span><span class="sxs-lookup"><span data-stu-id="058f3-136">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\FlowChartWithFaultHandling`

## <a name="see-also"></a><span data-ttu-id="058f3-137">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="058f3-137">See also</span></span>

- [<span data-ttu-id="058f3-138">Flussi di lavoro del diagramma di flusso</span><span class="sxs-lookup"><span data-stu-id="058f3-138">Flowchart Workflows</span></span>](../flowchart-workflows.md)
- [<span data-ttu-id="058f3-139">Eccezioni</span><span class="sxs-lookup"><span data-stu-id="058f3-139">Exceptions</span></span>](../exceptions.md)
