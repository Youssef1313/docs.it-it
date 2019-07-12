---
title: 'Procedura dettagliata: Hosting di un controllo ActiveX in WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ActiveX controls [WPF interoperability]
- hosting ActiveX controls [WPF]
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
ms.openlocfilehash: 0181093de1c40889110ab7eae75a3847a17845a9
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859945"
---
# <a name="walkthrough-hosting-an-activex-control-in-wpf"></a><span data-ttu-id="6ce06-102">Procedura dettagliata: Hosting di un controllo ActiveX in WPF</span><span class="sxs-lookup"><span data-stu-id="6ce06-102">Walkthrough: Hosting an ActiveX Control in WPF</span></span>
<span data-ttu-id="6ce06-103">Per consentire di migliorare l'interazione con i browser, è possibile usare controlli Microsoft ActiveX nel [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-applicazione basata su.</span><span class="sxs-lookup"><span data-stu-id="6ce06-103">To enable improved interaction with browsers, you can use Microsoft ActiveX controls in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span> <span data-ttu-id="6ce06-104">Questa procedura dettagliata illustra come è possibile ospitare le [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] come un controllo in un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pagina.</span><span class="sxs-lookup"><span data-stu-id="6ce06-104">This walkthrough demonstrates how you can host the [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] as a control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page.</span></span>

 <span data-ttu-id="6ce06-105">Le attività illustrate nella procedura dettagliata sono le seguenti:</span><span class="sxs-lookup"><span data-stu-id="6ce06-105">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="6ce06-106">Creazione del progetto.</span><span class="sxs-lookup"><span data-stu-id="6ce06-106">Creating the project.</span></span>

- <span data-ttu-id="6ce06-107">Creazione del controllo ActiveX.</span><span class="sxs-lookup"><span data-stu-id="6ce06-107">Creating the ActiveX control.</span></span>

- <span data-ttu-id="6ce06-108">Hosting del controllo ActiveX in una pagina WPF.</span><span class="sxs-lookup"><span data-stu-id="6ce06-108">Hosting the ActiveX control on a WPF Page.</span></span>

 <span data-ttu-id="6ce06-109">Dopo aver completato questa procedura dettagliata, si sarà in grado di utilizzare controlli Microsoft ActiveX di [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-applicazione basata su.</span><span class="sxs-lookup"><span data-stu-id="6ce06-109">When you have completed this walkthrough, you will understand how to use Microsoft ActiveX controls in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6ce06-110">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="6ce06-110">Prerequisites</span></span>
 <span data-ttu-id="6ce06-111">Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="6ce06-111">You need the following components to complete this walkthrough:</span></span>

- [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] <span data-ttu-id="6ce06-112">installato nel computer in cui è installato Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6ce06-112">installed on the computer where Visual Studio is installed.</span></span>

- <span data-ttu-id="6ce06-113">Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="6ce06-113">Visual Studio 2010.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="6ce06-114">Creazione del progetto</span><span class="sxs-lookup"><span data-stu-id="6ce06-114">Creating the Project</span></span>

### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="6ce06-115">Per creare e impostare il progetto</span><span class="sxs-lookup"><span data-stu-id="6ce06-115">To create and set up the project</span></span>

1. <span data-ttu-id="6ce06-116">Creare un progetto di applicazione WPF denominato `HostingAxInWpf`.</span><span class="sxs-lookup"><span data-stu-id="6ce06-116">Create a WPF Application project named `HostingAxInWpf`.</span></span>

2. <span data-ttu-id="6ce06-117">Aggiungere un progetto libreria di controlli Windows Form alla soluzione e denominare il progetto `WmpAxLib`.</span><span class="sxs-lookup"><span data-stu-id="6ce06-117">Add a Windows Forms Control Library project to the solution, and name the project `WmpAxLib`.</span></span>

3. <span data-ttu-id="6ce06-118">Nel progetto WmpAxLib, aggiungere un riferimento all'assembly di Windows Media Player, chiamata ScriptHelpers. WMP.</span><span class="sxs-lookup"><span data-stu-id="6ce06-118">In the WmpAxLib project, add a reference to the Windows Media Player assembly, which is named wmp.dll.</span></span>

4. <span data-ttu-id="6ce06-119">Aprire il **casella degli strumenti**.</span><span class="sxs-lookup"><span data-stu-id="6ce06-119">Open the **Toolbox**.</span></span>

5. <span data-ttu-id="6ce06-120">Fare doppio clic nella **casella degli strumenti**, quindi fare clic su **Scegli elementi**.</span><span class="sxs-lookup"><span data-stu-id="6ce06-120">Right-click in the **Toolbox**, and then click **Choose Items**.</span></span>

6. <span data-ttu-id="6ce06-121">Fare clic sui **i componenti COM** scheda, seleziona la **Windows Media Player** controllare e quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="6ce06-121">Click the **COM Components** tab, select the **Windows Media Player** control, and then click **OK**.</span></span>

     <span data-ttu-id="6ce06-122">Il controllo Windows Media Player viene aggiunto per il **casella degli strumenti**.</span><span class="sxs-lookup"><span data-stu-id="6ce06-122">The Windows Media Player control is added to the **Toolbox**.</span></span>

7. <span data-ttu-id="6ce06-123">In Esplora soluzioni fare doppio clic il **UserControl1** del file e quindi fare clic su **rinominare**.</span><span class="sxs-lookup"><span data-stu-id="6ce06-123">In Solution Explorer, right-click the **UserControl1** file, and then click **Rename**.</span></span>

8. <span data-ttu-id="6ce06-124">Modificare il nome in `WmpAxControl.vb` o `WmpAxControl.cs`, a seconda del linguaggio.</span><span class="sxs-lookup"><span data-stu-id="6ce06-124">Change the name to `WmpAxControl.vb` or `WmpAxControl.cs`, depending on the language.</span></span>

9. <span data-ttu-id="6ce06-125">Se viene richiesto di rinominare tutti i riferimenti, fare clic su **Sì**.</span><span class="sxs-lookup"><span data-stu-id="6ce06-125">If you are prompted to rename all references, click **Yes**.</span></span>

## <a name="creating-the-activex-control"></a><span data-ttu-id="6ce06-126">Creazione di un controllo ActiveX</span><span class="sxs-lookup"><span data-stu-id="6ce06-126">Creating the ActiveX Control</span></span>
 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] <span data-ttu-id="6ce06-127">Genera automaticamente un <xref:System.Windows.Forms.AxHost> classe wrapper per un controllo Microsoft ActiveX quando il controllo viene aggiunto all'area di progettazione.</span><span class="sxs-lookup"><span data-stu-id="6ce06-127">automatically generates an <xref:System.Windows.Forms.AxHost> wrapper class for a Microsoft ActiveX control when the control is added to a design surface.</span></span> <span data-ttu-id="6ce06-128">La procedura seguente crea un assembly gestito denominato AxInterop.WMPLib.dll.</span><span class="sxs-lookup"><span data-stu-id="6ce06-128">The following procedure creates a managed assembly named AxInterop.WMPLib.dll.</span></span>

### <a name="to-create-the-activex-control"></a><span data-ttu-id="6ce06-129">Per creare il controllo ActiveX</span><span class="sxs-lookup"><span data-stu-id="6ce06-129">To create the ActiveX control</span></span>

1. <span data-ttu-id="6ce06-130">Aprire WmpAxControl. vb o WmpAxControl.cs in Progettazione Windows Form.</span><span class="sxs-lookup"><span data-stu-id="6ce06-130">Open WmpAxControl.vb or WmpAxControl.cs in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="6ce06-131">Dal **casella degli strumenti**, aggiungere il controllo Windows Media Player all'area di progettazione.</span><span class="sxs-lookup"><span data-stu-id="6ce06-131">From the **Toolbox**, add the Windows Media Player control to the design surface.</span></span>

3. <span data-ttu-id="6ce06-132">Nella finestra Proprietà impostare il valore del controllo Windows Media Player <xref:System.Windows.Forms.Control.Dock%2A> proprietà <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="6ce06-132">In the Properties window, set the value of the Windows Media Player control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

4. <span data-ttu-id="6ce06-133">Compilare il progetto di libreria di controlli WmpAxLib.</span><span class="sxs-lookup"><span data-stu-id="6ce06-133">Build the WmpAxLib control library project.</span></span>

## <a name="hosting-the-activex-control-on-a-wpf-page"></a><span data-ttu-id="6ce06-134">Hosting del controllo ActiveX in una pagina WPF</span><span class="sxs-lookup"><span data-stu-id="6ce06-134">Hosting the ActiveX Control on a WPF Page</span></span>

### <a name="to-host-the-activex-control"></a><span data-ttu-id="6ce06-135">Per ospitare il controllo ActiveX</span><span class="sxs-lookup"><span data-stu-id="6ce06-135">To host the ActiveX control</span></span>

1. <span data-ttu-id="6ce06-136">Nel progetto HostingAxInWpf, aggiungere un riferimento all'assembly di interoperabilità ActiveX generato.</span><span class="sxs-lookup"><span data-stu-id="6ce06-136">In the HostingAxInWpf project, add a reference to the generated ActiveX interoperability assembly.</span></span>

     <span data-ttu-id="6ce06-137">Questo assembly è denominato AxInterop.WMPLib.dll ed è stato aggiunto alla cartella di Debug del progetto WmpAxLib quando è stato importato il controllo Windows Media Player.</span><span class="sxs-lookup"><span data-stu-id="6ce06-137">This assembly is named AxInterop.WMPLib.dll and was added to the Debug folder of the WmpAxLib project when you imported the Windows Media Player control.</span></span>

2. <span data-ttu-id="6ce06-138">Aggiungere un riferimento all'assembly WindowsFormsIntegration, denominato WindowsFormsIntegration. dll.</span><span class="sxs-lookup"><span data-stu-id="6ce06-138">Add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

3. <span data-ttu-id="6ce06-139">Aggiungere un riferimento di [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] assembly, chiamata ScriptHelpers. Forms.</span><span class="sxs-lookup"><span data-stu-id="6ce06-139">Add a reference to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] assembly, which is named System.Windows.Forms.dll.</span></span>

4. <span data-ttu-id="6ce06-140">Aprire MainWindow. XAML in WPF Designer.</span><span class="sxs-lookup"><span data-stu-id="6ce06-140">Open MainWindow.xaml in the WPF Designer.</span></span>

5. <span data-ttu-id="6ce06-141">Nome di <xref:System.Windows.Controls.Grid> elemento `grid1`.</span><span class="sxs-lookup"><span data-stu-id="6ce06-141">Name the <xref:System.Windows.Controls.Grid> element `grid1`.</span></span>

     [!code-xaml[HostingAxInWpf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]

6. <span data-ttu-id="6ce06-142">Nella visualizzazione progettazione o XAML, selezionare il <xref:System.Windows.Window> elemento.</span><span class="sxs-lookup"><span data-stu-id="6ce06-142">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>

7. <span data-ttu-id="6ce06-143">Nella finestra Proprietà scegliere il **eventi** scheda.</span><span class="sxs-lookup"><span data-stu-id="6ce06-143">In the Properties window, click the **Events** tab.</span></span>

8. <span data-ttu-id="6ce06-144">Fare doppio clic il <xref:System.Windows.FrameworkElement.Loaded> evento.</span><span class="sxs-lookup"><span data-stu-id="6ce06-144">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

9. <span data-ttu-id="6ce06-145">Inserire il codice seguente per gestire il <xref:System.Windows.FrameworkElement.Loaded> evento.</span><span class="sxs-lookup"><span data-stu-id="6ce06-145">Insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

     <span data-ttu-id="6ce06-146">Questo codice crea un'istanza del <xref:System.Windows.Forms.Integration.WindowsFormsHost> controllano e aggiunge un'istanza del `AxWindowsMediaPlayer` controllo come relativo elemento figlio.</span><span class="sxs-lookup"><span data-stu-id="6ce06-146">This code creates an instance of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control and adds an instance of the `AxWindowsMediaPlayer` control as its child.</span></span>

     [!code-csharp[HostingAxInWpf#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. <span data-ttu-id="6ce06-147">Premere F5 per compilare ed eseguire l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="6ce06-147">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ce06-148">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6ce06-148">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="6ce06-149">Progettare XAML in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6ce06-149">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="6ce06-150">Procedura dettagliata: Hosting di controlli Windows Form compositi in WPF</span><span class="sxs-lookup"><span data-stu-id="6ce06-150">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="6ce06-151">Procedura dettagliata: Hosting di un controllo composito WPF in Windows Form</span><span class="sxs-lookup"><span data-stu-id="6ce06-151">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
