---
title: Risoluzione dei problemi relativi alla modifica di controlli e componenti
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- troubleshooting components
- troubleshooting controls [Windows Forms]
- controls [Windows Forms], troubleshooting
- components [Windows Forms], troubleshooting
- Windows Forms controls, debugging
ms.assetid: e9c8c099-2271-4737-882f-50f336c7a55e
ms.openlocfilehash: c05e849705f851b51a362d3a1d1d3f81a9eaf0e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923601"
---
# <a name="troubleshooting-control-and-component-authoring"></a><span data-ttu-id="58911-102">Risoluzione dei problemi relativi alla modifica di controlli e componenti</span><span class="sxs-lookup"><span data-stu-id="58911-102">Troubleshooting Control and Component Authoring</span></span>
<span data-ttu-id="58911-103">In questo argomento vengono descritti alcuni problemi comuni che si verificano durante lo sviluppo di componenti e controlli.</span><span class="sxs-lookup"><span data-stu-id="58911-103">This topic lists the following common problems that arise when developing components and controls.</span></span> <span data-ttu-id="58911-104">Per altre informazioni, vedere l'argomento relativo alla [programmazione con i componenti](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="58911-104">For more information, see [Programming with Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120)).</span></span>  
  
- <span data-ttu-id="58911-105">Impossibile aggiungere un controllo alla casella degli strumenti</span><span class="sxs-lookup"><span data-stu-id="58911-105">Cannot Add Control to Toolbox</span></span>  
  
- <span data-ttu-id="58911-106">Impossibile eseguire il debug del componente o controllo utente di Windows Forms</span><span class="sxs-lookup"><span data-stu-id="58911-106">Cannot Debug the Windows Forms User Control or Component</span></span>  
  
- <span data-ttu-id="58911-107">L'evento viene generato due volte nel componente o controllo ereditato</span><span class="sxs-lookup"><span data-stu-id="58911-107">Event Is Raised Twice in Inherited Control or Component</span></span>  
  
- <span data-ttu-id="58911-108">Errore in fase di progettazione: "Impossibile creare il componente '*nome componente*'"</span><span class="sxs-lookup"><span data-stu-id="58911-108">Design-Time Error: "Failed to Create Component '*Component Name*'"</span></span>  
  
- <span data-ttu-id="58911-109">STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="58911-109">STAThreadAttribute</span></span>  
  
- <span data-ttu-id="58911-110">L'icona del componente non appare nella casella degli strumenti</span><span class="sxs-lookup"><span data-stu-id="58911-110">Component Icon Does Not Appear in Toolbox</span></span>  
  
## <a name="cannot-add-control-to-toolbox"></a><span data-ttu-id="58911-111">Impossibile aggiungere un controllo alla casella degli strumenti</span><span class="sxs-lookup"><span data-stu-id="58911-111">Cannot Add Control to Toolbox</span></span>  
 <span data-ttu-id="58911-112">Se si vuole aggiungere un controllo personalizzato creato in un altro progetto o un controllo di terze parti alla **casella degli strumenti**, è necessario farlo manualmente.</span><span class="sxs-lookup"><span data-stu-id="58911-112">If you want to add a custom control that you created in another project or a third-party control to the **Toolbox**, you must do so manually.</span></span> <span data-ttu-id="58911-113">Se il progetto corrente include il controllo o il componente, deve automaticamente apparire nella **casella degli strumenti**.</span><span class="sxs-lookup"><span data-stu-id="58911-113">If the current project contains your control or component, it should appear in the **Toolbox** automatically.</span></span> <span data-ttu-id="58911-114">Per altre informazioni, vedere [Procedura dettagliata: Popolamento automatico della casella degli strumenti con](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)componenti personalizzati.</span><span class="sxs-lookup"><span data-stu-id="58911-114">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>  
  
#### <a name="to-add-a-control-to-the-toolbox"></a><span data-ttu-id="58911-115">Per aggiungere un controllo alla casella degli strumenti</span><span class="sxs-lookup"><span data-stu-id="58911-115">To add a control to the Toolbox</span></span>  
  
1. <span data-ttu-id="58911-116">Fare clic con il pulsante destro del mouse nella **casella degli strumenti** e selezionare **Scegli elementi** dal menu di scelta rapida.</span><span class="sxs-lookup"><span data-stu-id="58911-116">Right-click the **Toolbox** and from the shortcut menu, select **Choose Items**.</span></span>  
  
2. <span data-ttu-id="58911-117">Nella finestra di dialogo **Scegli elementi della Casella degli strumenti** aggiungere il componente:</span><span class="sxs-lookup"><span data-stu-id="58911-117">In the **Choose Toolbox Items** dialog box, add the component:</span></span>  
  
    - <span data-ttu-id="58911-118">per aggiungere un componente o un controllo di .NET Framework, fare clic sulla scheda **Componenti di .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="58911-118">If you want to add a .NET Framework component or control, click the **.NET Framework Components** tab.</span></span>  
  
         <span data-ttu-id="58911-119">\- oppure -</span><span class="sxs-lookup"><span data-stu-id="58911-119">– or –</span></span>  
  
    - <span data-ttu-id="58911-120">per aggiungere un componente COM o un controllo ActiveX, fare clic sulla scheda **Componenti COM**.</span><span class="sxs-lookup"><span data-stu-id="58911-120">If you want to add a COM component or ActiveX control, click the **COM Components** tab.</span></span>  
  
3. <span data-ttu-id="58911-121">Se il controllo è indicato nella finestra di dialogo, verificare se è selezionato e quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="58911-121">If your control is listed in the dialog box, confirm it is selected, and then click **OK**.</span></span>  
  
     <span data-ttu-id="58911-122">Il controllo viene aggiunto alla **della casella degli strumenti**.</span><span class="sxs-lookup"><span data-stu-id="58911-122">The control is added to the **Toolbox**.</span></span>  
  
4. <span data-ttu-id="58911-123">Se il controllo non è indicato nella finestra di dialogo, eseguire queste operazioni:</span><span class="sxs-lookup"><span data-stu-id="58911-123">If your control is not listed in the dialog box, do the following:</span></span>  
  
    1. <span data-ttu-id="58911-124">Fare clic sul pulsante **Sfoglia**.</span><span class="sxs-lookup"><span data-stu-id="58911-124">Click the **Browse** button.</span></span>  
  
    2. <span data-ttu-id="58911-125">Passare alla cartella che contiene il file DLL in cui si trova il controllo.</span><span class="sxs-lookup"><span data-stu-id="58911-125">Browse to the folder that contains the .dll file that contains your control.</span></span>  
  
    3. <span data-ttu-id="58911-126">Selezionare il file DLL e fare clic su **Apri**.</span><span class="sxs-lookup"><span data-stu-id="58911-126">Select the .dll file and click **Open**.</span></span>  
  
         <span data-ttu-id="58911-127">Il controllo viene visualizzato nella finestra di dialogo.</span><span class="sxs-lookup"><span data-stu-id="58911-127">Your control appears in the dialog box.</span></span>  
  
    4. <span data-ttu-id="58911-128">Verificare se il controllo è selezionato e quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="58911-128">Confirm that your control is selected, and then click **OK**.</span></span>  
  
         <span data-ttu-id="58911-129">Il controllo viene aggiunto alla **casella degli strumenti**.</span><span class="sxs-lookup"><span data-stu-id="58911-129">Your control is added to the **Toolbox**.</span></span>  
  
## <a name="cannot-debug-the-windows-forms-user-control-or-component"></a><span data-ttu-id="58911-130">Impossibile eseguire il debug del componente o controllo utente di Windows Form</span><span class="sxs-lookup"><span data-stu-id="58911-130">Cannot Debug the Windows Forms User Control or Component</span></span>  
 <span data-ttu-id="58911-131">Se il controllo deriva dalla <xref:System.Windows.Forms.UserControl> classe, è possibile eseguire il debug del comportamento in fase di esecuzione con il contenitore di test.</span><span class="sxs-lookup"><span data-stu-id="58911-131">If your control derives from the <xref:System.Windows.Forms.UserControl> class, you can debug its run-time behavior with the test container.</span></span> <span data-ttu-id="58911-132">Per altre informazioni, vedere [Procedura: Testare il comportamento in fase di esecuzione di un](how-to-test-the-run-time-behavior-of-a-usercontrol.md)UserControl.</span><span class="sxs-lookup"><span data-stu-id="58911-132">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
 <span data-ttu-id="58911-133">Altri componenti e controlli personalizzati non sono progetti autonomi.</span><span class="sxs-lookup"><span data-stu-id="58911-133">Other custom controls and components are not stand-alone projects.</span></span> <span data-ttu-id="58911-134">Devono essere ospitati da un'applicazione, ad esempio un progetto Windows Form.</span><span class="sxs-lookup"><span data-stu-id="58911-134">They must be hosted by an application such as a Windows Forms project.</span></span> <span data-ttu-id="58911-135">Per eseguire il debug di un controllo o un componente, è necessario aggiungerlo a un progetto Windows Form.</span><span class="sxs-lookup"><span data-stu-id="58911-135">To debug a control or component, you must add it to a Windows Forms project.</span></span>  
  
#### <a name="to-debug-a-control-or-component"></a><span data-ttu-id="58911-136">Per eseguire il debug di un controllo o componente</span><span class="sxs-lookup"><span data-stu-id="58911-136">To debug a control or component</span></span>  
  
1. <span data-ttu-id="58911-137">Scegliere **Compila soluzione** dal menu **Compila** per creare il progetto.</span><span class="sxs-lookup"><span data-stu-id="58911-137">From the **Build** menu, click **Build Solution** to build your solution.</span></span>  
  
2. <span data-ttu-id="58911-138">Scegliere **Aggiungi** dal menu **File**, quindi selezionare **Nuovo progetto** per aggiungere un progetto di test all'applicazione.</span><span class="sxs-lookup"><span data-stu-id="58911-138">From the **File** menu, choose **Add**, and then **New Project** to add a test project to your application.</span></span>  
  
3. <span data-ttu-id="58911-139">Nella finestra di dialogo **Aggiungi nuovo progetto** scegliere **Applicazione Windows** come tipo di progetto.</span><span class="sxs-lookup"><span data-stu-id="58911-139">In the **Add New Project** dialog box choose **Windows Application** for the type of project.</span></span>  
  
4. <span data-ttu-id="58911-140">In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo **Riferimenti** per il nuovo progetto.</span><span class="sxs-lookup"><span data-stu-id="58911-140">In **Solution Explorer**, right-click the **References** node for the new project.</span></span> <span data-ttu-id="58911-141">Nel menu di scelta rapida fare clic su **Aggiungi riferimento** per aggiungere un riferimento al progetto contenente il controllo o il componente.</span><span class="sxs-lookup"><span data-stu-id="58911-141">On the shortcut menu, click **Add Reference** to add a reference to the project containing the control or component.</span></span>  
  
5. <span data-ttu-id="58911-142">Creare un'istanza del controllo o componente nel progetto di test.</span><span class="sxs-lookup"><span data-stu-id="58911-142">Create an instance of your control or component in the test project.</span></span> <span data-ttu-id="58911-143">Se il componente si trova nella **casella degli strumenti**, è possibile trascinarlo nell'area di progettazione oppure creare l'istanza a livello di codice, come illustrato nell'esempio di codice seguente.</span><span class="sxs-lookup"><span data-stu-id="58911-143">If your component is in the **Toolbox**, you can drag it to your designer surface, or you can create the instance programmatically, as shown in the following code example.</span></span>  
  
    ```vb  
    Dim Component1 As New MyNeatComponent()  
    ```  
  
    ```csharp  
    MyNeatComponent Component1 = new MyNeatComponent();  
    ```  
  
     <span data-ttu-id="58911-144">È ora possibile eseguire il debug del controllo o del componente come di consueto.</span><span class="sxs-lookup"><span data-stu-id="58911-144">You can now debug your control or component as usual.</span></span>  
  
 <span data-ttu-id="58911-145">Per ulteriori informazioni sul debug, vedere [debug in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio) e [procedura dettagliata: Debug di controlli di Windows Forms personalizzati in](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)fase di progettazione.</span><span class="sxs-lookup"><span data-stu-id="58911-145">For more information about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio) and [Walkthrough: Debugging Custom Windows Forms Controls at Design Time](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span></span>  
  
## <a name="event-is-raised-twice-in-inherited-control-or-component"></a><span data-ttu-id="58911-146">L'evento viene generato due volte nel componente o controllo ereditato</span><span class="sxs-lookup"><span data-stu-id="58911-146">Event Is Raised Twice in Inherited Control or Component</span></span>  
 <span data-ttu-id="58911-147">Ciò è probabilmente dovuto a una clausola `Handles` duplicata.</span><span class="sxs-lookup"><span data-stu-id="58911-147">This is likely due to a duplicated `Handles` clause.</span></span> <span data-ttu-id="58911-148">Per altre informazioni, vedere [Risoluzione dei problemi relativi ai gestori eventi ereditati in Visual Basic](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="58911-148">For more information, see [Troubleshooting Inherited Event Handlers in Visual Basic](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span></span>  
  
## <a name="design-time-error-failed-to-create-component-component-name"></a><span data-ttu-id="58911-149">Errore in fase di progettazione: "Impossibile creare il componente ' nome componente '"</span><span class="sxs-lookup"><span data-stu-id="58911-149">Design-Time Error: "Failed to Create Component 'Component Name'"</span></span>  
 <span data-ttu-id="58911-150">Il componente o il controllo deve fornire un costruttore senza parametri senza parametri.</span><span class="sxs-lookup"><span data-stu-id="58911-150">Your component or control must provide a parameterless constructor with no parameters.</span></span> <span data-ttu-id="58911-151">Quando l'ambiente di progettazione crea un'istanza del componente o controllo, non tenta di definire parametri per gli overload del costruttore che accettano tali parametri.</span><span class="sxs-lookup"><span data-stu-id="58911-151">When the design environment creates an instance of your component or control, it does not attempt to provide any parameters to constructor overloads that take parameters.</span></span>  
  
## <a name="stathreadattribute"></a><span data-ttu-id="58911-152">STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="58911-152">STAThreadAttribute</span></span>  
 <span data-ttu-id="58911-153"><xref:System.STAThreadAttribute> Informa il Common Language Runtime (CLR) che Windows Forms utilizza il modello di Apartment a thread singolo.</span><span class="sxs-lookup"><span data-stu-id="58911-153">The <xref:System.STAThreadAttribute> informs the common language runtime (CLR) that Windows Forms uses the single-threaded apartment model.</span></span> <span data-ttu-id="58911-154">È possibile riscontrare un comportamento imprevisto se non si applica questo attributo al metodo `Main` dell'applicazione Windows Form.</span><span class="sxs-lookup"><span data-stu-id="58911-154">You may notice unintended behavior if you do not apply this attribute to your Windows Forms application's `Main` method.</span></span> <span data-ttu-id="58911-155">Ad esempio, le immagini di sfondo potrebbero non essere visualizzate <xref:System.Windows.Forms.ListView>per i controlli come.</span><span class="sxs-lookup"><span data-stu-id="58911-155">For example, background images may not appear for controls like <xref:System.Windows.Forms.ListView>.</span></span> <span data-ttu-id="58911-156">Alcuni controlli possono inoltre richiedere questo attributo per il funzionamento corretto del completamento automatico e del trascinamento della selezione.</span><span class="sxs-lookup"><span data-stu-id="58911-156">Some controls may also require this attribute for correct AutoComplete and drag-and-drop behavior.</span></span>  
  
## <a name="component-icon-does-not-appear-in-toolbox"></a><span data-ttu-id="58911-157">L'icona del componente non appare nella casella degli strumenti</span><span class="sxs-lookup"><span data-stu-id="58911-157">Component Icon Does Not Appear in Toolbox</span></span>  
 <span data-ttu-id="58911-158">Quando si utilizza <xref:System.Drawing.ToolboxBitmapAttribute> per associare un'icona al componente personalizzato, la bitmap non viene visualizzata nella casella degli strumenti per i componenti generati automaticamente.</span><span class="sxs-lookup"><span data-stu-id="58911-158">When you use <xref:System.Drawing.ToolboxBitmapAttribute> to associate an icon with your custom component, the bitmap does not appear in the Toolbox for autogenerated components.</span></span> <span data-ttu-id="58911-159">Per visualizzare la bitmap, ricaricare il controllo usando la finestra di dialogo **Scegli elementi della casella degli strumenti**.</span><span class="sxs-lookup"><span data-stu-id="58911-159">To see the bitmap, reload the control by using the **Choose Toolbox Items** dialog box.</span></span> <span data-ttu-id="58911-160">Per altre informazioni, vedere [Procedura: Specificare una bitmap della casella degli strumenti](how-to-provide-a-toolbox-bitmap-for-a-control.md)per un controllo.</span><span class="sxs-lookup"><span data-stu-id="58911-160">For more information, see [How to: Provide a Toolbox Bitmap for a Control](how-to-provide-a-toolbox-bitmap-for-a-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58911-161">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="58911-161">See also</span></span>

- [<span data-ttu-id="58911-162">Sviluppo di controlli Windows Form in fase di progettazione</span><span class="sxs-lookup"><span data-stu-id="58911-162">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="58911-163">Procedura dettagliata: Popolamento automatico della casella degli strumenti con componenti personalizzati</span><span class="sxs-lookup"><span data-stu-id="58911-163">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [<span data-ttu-id="58911-164">Procedura: Testare il comportamento in fase di esecuzione di un UserControl</span><span class="sxs-lookup"><span data-stu-id="58911-164">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
- [<span data-ttu-id="58911-165">Procedura dettagliata: Debug di controlli di Windows Form personalizzati in fase di progettazione</span><span class="sxs-lookup"><span data-stu-id="58911-165">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)
- <span data-ttu-id="58911-166">[Modifica di componenti](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/5dya64wy(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="58911-166">[Component Authoring](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/5dya64wy(v=vs.120))</span></span>
- <span data-ttu-id="58911-167">[Risoluzione dei problemi di sviluppo in fase di progettazione](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="58911-167">[Troubleshooting Design-Time Development](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))</span></span>
