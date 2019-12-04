---
title: Estendibilità della griglia delle proprietà-esempio WF
ms.date: 03/30/2017
ms.assetid: 3530c3a3-756d-4712-9f10-fb2897414d3a
ms.openlocfilehash: 130d8702795bccf0d5f28b5c0940bd7c25be3556
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715597"
---
# <a name="property-grid-extensibility"></a><span data-ttu-id="ccb86-102">Estendibilità della griglia delle proprietà</span><span class="sxs-lookup"><span data-stu-id="ccb86-102">Property grid extensibility</span></span>

<span data-ttu-id="ccb86-103">Uno sviluppatore può personalizzare la griglia delle proprietà visualizzata quando un'attività specificata viene selezionata all'interno della finestra di progettazione.</span><span class="sxs-lookup"><span data-stu-id="ccb86-103">A developer can customize the property grid that is displayed when a given activity is selected within the designer.</span></span> <span data-ttu-id="ccb86-104">Questa operazione può essere eseguita per creare un'esperienza di modifica dettagliata.</span><span class="sxs-lookup"><span data-stu-id="ccb86-104">This can be done to create a rich editing experience.</span></span> <span data-ttu-id="ccb86-105">In questo esempio viene illustrato come procedere.</span><span class="sxs-lookup"><span data-stu-id="ccb86-105">This sample shows how this can be done.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="ccb86-106">Dimostrazione</span><span class="sxs-lookup"><span data-stu-id="ccb86-106">Demonstrates</span></span>

<span data-ttu-id="ccb86-107">Estensibilità della griglia delle proprietà della finestra di progettazione flussi di lavoro.</span><span class="sxs-lookup"><span data-stu-id="ccb86-107">Workflow designer property grid extensibility.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ccb86-108">È possibile che gli esempi siano già installati nel computer.</span><span class="sxs-lookup"><span data-stu-id="ccb86-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ccb86-109">Verificare la directory seguente (impostazione predefinita) prima di continuare.</span><span class="sxs-lookup"><span data-stu-id="ccb86-109">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="ccb86-110">Se questa directory non esiste, passare a [Windows Communication Foundation (WCF) ed esempi di Windows Workflow Foundation (WF) per .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) per scaricare tutti i Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] esempi.</span><span class="sxs-lookup"><span data-stu-id="ccb86-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ccb86-111">Questo esempio si trova nella directory seguente.</span><span class="sxs-lookup"><span data-stu-id="ccb86-111">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`

## <a name="discussion"></a><span data-ttu-id="ccb86-112">Discussione</span><span class="sxs-lookup"><span data-stu-id="ccb86-112">Discussion</span></span>

<span data-ttu-id="ccb86-113">Per estendere la griglia delle proprietà, uno sviluppatore dispone di opzioni per personalizzare l'aspetto inline di un editor della griglia delle proprietà o fornire una finestra di dialogo che viene visualizzata per un'area di modifica più avanzata.</span><span class="sxs-lookup"><span data-stu-id="ccb86-113">To extend the property grid, a developer has options to customize the inline appearance of a property grid editor or provide a dialog that appears for a more advanced editing surface.</span></span> <span data-ttu-id="ccb86-114">In questo esempio vengono illustrati due editor diversi, ovvero un editor inline e un editor della finestra di dialogo.</span><span class="sxs-lookup"><span data-stu-id="ccb86-114">There are two different editors demonstrated in this sample; an inline editor and a dialog editor.</span></span>

## <a name="inline-editor"></a><span data-ttu-id="ccb86-115">Editor inline</span><span class="sxs-lookup"><span data-stu-id="ccb86-115">Inline editor</span></span>

<span data-ttu-id="ccb86-116">Nell'esempio di editor inline viene illustrato quanto segue:</span><span class="sxs-lookup"><span data-stu-id="ccb86-116">The inline editor sample demonstrates the following:</span></span>

- <span data-ttu-id="ccb86-117">Viene creato un tipo che deriva da <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor>.</span><span class="sxs-lookup"><span data-stu-id="ccb86-117">Creates a type that derives from <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor>.</span></span>

- <span data-ttu-id="ccb86-118">Nel costruttore, il valore <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> è impostato con un modello di dati Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="ccb86-118">In the constructor, the <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> value is set with a Windows Presentation Foundation (WPF) data template.</span></span> <span data-ttu-id="ccb86-119">È possibile associarlo a un modello XAML, ma in questo esempio il codice viene usato per inizializzare l'associazione dati.</span><span class="sxs-lookup"><span data-stu-id="ccb86-119">This can be bound to a XAML template, but in this sample, code is used to initialize data binding.</span></span>

- <span data-ttu-id="ccb86-120">Il modello di dati dispone di un contesto dei dati di <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> dell'elemento di cui è stato eseguito il rendering nella griglia delle proprietà.</span><span class="sxs-lookup"><span data-stu-id="ccb86-120">The data template has a data context of the <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> of the item rendered in the property grid.</span></span> <span data-ttu-id="ccb86-121">Notare nel codice seguente (da CustomInlineEditor.cs) che questo contesto viene quindi associato alla proprietà `Value`.</span><span class="sxs-lookup"><span data-stu-id="ccb86-121">Note in the following code (from CustomInlineEditor.cs) that this context then binds to the `Value` property.</span></span>

    ```csharp
    FrameworkElementFactory stack = new FrameworkElementFactory(typeof(StackPanel));
    FrameworkElementFactory slider = new FrameworkElementFactory(typeof(Slider));
    Binding sliderBinding = new Binding("Value");
    sliderBinding.Mode = BindingMode.TwoWay;
    slider.SetValue(Slider.MinimumProperty, 0.0);
    slider.SetValue(Slider.MaximumProperty, 100.0);
    slider.SetValue(Slider.ValueProperty, sliderBinding);
    stack.AppendChild(slider);
    ```

- <span data-ttu-id="ccb86-122">Poiché l'attività e la finestra di progettazione sono nello stesso assembly, la registrazione degli attributi di ActivityDesigner viene completata nel costruttore statico dell'attività stessa, come illustrato nell'esempio seguente da SimpleCodeActivity.cs.</span><span class="sxs-lookup"><span data-stu-id="ccb86-122">Because the activity and the designer are in the same assembly, registration of the activity designer attributes are accomplished in the static constructor of the activity itself, as shown in the following example from SimpleCodeActivity.cs.</span></span>

    ```csharp
    static SimpleCodeActivity()
    {
        AttributeTableBuilder builder = new AttributeTableBuilder();
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));
        MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

## <a name="dialog-editor"></a><span data-ttu-id="ccb86-123">editor finestre</span><span class="sxs-lookup"><span data-stu-id="ccb86-123">Dialog editor</span></span>

<span data-ttu-id="ccb86-124">Nell'esempio di editor finestre viene illustrato quanto segue:</span><span class="sxs-lookup"><span data-stu-id="ccb86-124">The dialog editor sample demonstrates the following:</span></span>

1. <span data-ttu-id="ccb86-125">Viene creato un tipo che deriva da <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor>.</span><span class="sxs-lookup"><span data-stu-id="ccb86-125">Creates a type that derives from <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor>.</span></span>

2. <span data-ttu-id="ccb86-126">Imposta il valore <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> nel costruttore con un modello di dati WPF.</span><span class="sxs-lookup"><span data-stu-id="ccb86-126">Sets the <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> value in the constructor with a WPF data template.</span></span> <span data-ttu-id="ccb86-127">Può essere creato in XAML, ma in questo esempio viene creato nel codice.</span><span class="sxs-lookup"><span data-stu-id="ccb86-127">This can be created in XAML, but in this sample, this is created in code.</span></span>

3. <span data-ttu-id="ccb86-128">Il modello di dati dispone di un contesto dei dati di <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> dell'elemento di cui è stato eseguito il rendering nella griglia delle proprietà.</span><span class="sxs-lookup"><span data-stu-id="ccb86-128">The data template has a data context of the <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> of the item rendered in the property grid.</span></span> <span data-ttu-id="ccb86-129">Nel codice seguente viene quindi eseguita l'associazione alla proprietà `Value`.</span><span class="sxs-lookup"><span data-stu-id="ccb86-129">In the following code, this then binds to the `Value` property.</span></span> <span data-ttu-id="ccb86-130">È importante includere inoltre un oggetto <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> per fornire il pulsante che genera la finestra di dialogo in FilePickerEditor.cs.</span><span class="sxs-lookup"><span data-stu-id="ccb86-130">It is critical to also include an <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> to provide the button that raises the dialog in FilePickerEditor.cs.</span></span>

    ```csharp
    this.InlineEditorTemplate = new DataTemplate();

    FrameworkElementFactory stack = new FrameworkElementFactory(typeof(StackPanel));
    stack.SetValue(StackPanel.OrientationProperty, Orientation.Horizontal);
    FrameworkElementFactory label = new FrameworkElementFactory(typeof(Label));
    Binding labelBinding = new Binding("Value");
    label.SetValue(Label.ContentProperty, labelBinding);
    label.SetValue(Label.MaxWidthProperty, 90.0);

    stack.AppendChild(label);

    FrameworkElementFactory editModeSwitch = new FrameworkElementFactory(typeof(EditModeSwitchButton));

    editModeSwitch.SetValue(EditModeSwitchButton.TargetEditModeProperty, PropertyContainerEditMode.Dialog);

    stack.AppendChild(editModeSwitch);

    this.InlineEditorTemplate.VisualTree = stack;
    ```

4. <span data-ttu-id="ccb86-131">Viene eseguito l'override del metodo <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor.ShowDialog%2A> nel tipo di finestra di progettazione per gestire la visualizzazione della finestra di dialogo.</span><span class="sxs-lookup"><span data-stu-id="ccb86-131">Overrides the <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor.ShowDialog%2A> method in the designer type to handle the display of the dialog.</span></span> <span data-ttu-id="ccb86-132">In questo esempio viene illustrato un oggetto <xref:System.Windows.Forms.FileDialog> di base.</span><span class="sxs-lookup"><span data-stu-id="ccb86-132">In this sample, a basic <xref:System.Windows.Forms.FileDialog> is shown.</span></span>

    ```csharp
    public override void ShowDialog(PropertyValue propertyValue, IInputElement commandSource)
    {
        Microsoft.Win32.OpenFileDialog ofd = new Microsoft.Win32.OpenFileDialog();
        if (ofd.ShowDialog() == true)
        {
            propertyValue.Value = ofd.FileName;
        }
    }
    ```

5. <span data-ttu-id="ccb86-133">Poiché l'attività e la finestra di progettazione sono nello stesso assembly, la registrazione degli attributi di ActivityDesigner viene completata nel costruttore statico dell'attività stessa, come illustrato nell'esempio seguente da SimpleCodeActivity.cs.</span><span class="sxs-lookup"><span data-stu-id="ccb86-133">Because the activity and the designer are in the same assembly, registration of the activity designer attributes are accomplished in the static constructor of the activity itself, as shown in the following example from SimpleCodeActivity.cs.</span></span>

    ```csharp
    static SimpleCodeActivity()
    {
        AttributeTableBuilder builder = new AttributeTableBuilder();
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));
        MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ccb86-134">Per impostare, compilare ed eseguire l'esempio</span><span class="sxs-lookup"><span data-stu-id="ccb86-134">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="ccb86-135">Compilare la soluzione, quindi aprire il file Workflow1.xaml.</span><span class="sxs-lookup"><span data-stu-id="ccb86-135">Build the solution, and then open Workflow1.xaml.</span></span>

2. <span data-ttu-id="ccb86-136">Trascinare un **SimpleCodeActivity** dalla casella degli strumenti nell'area di disegno della finestra di progettazione.</span><span class="sxs-lookup"><span data-stu-id="ccb86-136">Drag a **SimpleCodeActivity** from the toolbox onto the designer canvas.</span></span>

3. <span data-ttu-id="ccb86-137">Fare clic su **SimpleCodeActivity** , quindi aprire la griglia delle proprietà in cui è presente un controllo dispositivo di scorrimento e un controllo di selezione file.</span><span class="sxs-lookup"><span data-stu-id="ccb86-137">Click the **SimpleCodeActivity** and then open the property grid where there is a slider control and a file picking control.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ccb86-138">È possibile che gli esempi siano già installati nel computer.</span><span class="sxs-lookup"><span data-stu-id="ccb86-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ccb86-139">Verificare la directory seguente (impostazione predefinita) prima di continuare.</span><span class="sxs-lookup"><span data-stu-id="ccb86-139">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="ccb86-140">Se questa directory non esiste, passare a [Windows Communication Foundation (WCF) ed esempi di Windows Workflow Foundation (WF) per .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) per scaricare tutti i Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] esempi.</span><span class="sxs-lookup"><span data-stu-id="ccb86-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ccb86-141">Questo esempio si trova nella directory seguente.</span><span class="sxs-lookup"><span data-stu-id="ccb86-141">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`
