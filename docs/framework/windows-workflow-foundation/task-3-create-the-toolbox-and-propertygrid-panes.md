---
title: 'Attività 3: creare i riquadri Casella degli strumenti e PropertyGrid'
ms.date: 03/30/2017
ms.assetid: 72c1546a-eed5-4f0f-a616-719a163414f4
ms.openlocfilehash: 29e50b24135cd3d6a02052d846e1781b0d9fa325
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716224"
---
# <a name="task-3-create-the-toolbox-and-propertygrid-panes"></a><span data-ttu-id="384e9-102">Attività 3: creare i riquadri Casella degli strumenti e PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="384e9-102">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>

<span data-ttu-id="384e9-103">In questa attività verranno creati i riquadri **casella degli strumenti** e **PropertyGrid** e aggiunti al progettazione flussi di lavoro Windows riallocato.</span><span class="sxs-lookup"><span data-stu-id="384e9-103">In this task, you will create the **Toolbox** and **PropertyGrid** panes and add them to the rehosted Windows Workflow Designer.</span></span>

<span data-ttu-id="384e9-104">Per riferimento, al termine di questo argomento viene fornito il codice che deve trovarsi nel file MainWindow.xaml.cs dopo aver completato le tre attività riportate nella sezione relativa alla [riallocazione della progettazione flussi di lavoro](rehosting-the-workflow-designer.md) serie di argomenti.</span><span class="sxs-lookup"><span data-stu-id="384e9-104">For reference, the code that should be in the MainWindow.xaml.cs file after completing the three tasks in the [Rehosting the Workflow Designer](rehosting-the-workflow-designer.md) series of topics is provided at the end of this topic.</span></span>

## <a name="to-create-the-toolbox-and-add-it-to-the-grid"></a><span data-ttu-id="384e9-105">Per creare la casella degli strumenti e aggiungerla alla griglia</span><span class="sxs-lookup"><span data-stu-id="384e9-105">To create the Toolbox and add it to the grid</span></span>

1. <span data-ttu-id="384e9-106">Aprire il progetto HostingApplication ottenuto seguendo la procedura descritta in [attività 2: ospitare il progettazione flussi di lavoro](task-2-host-the-workflow-designer.md).</span><span class="sxs-lookup"><span data-stu-id="384e9-106">Open the HostingApplication project you obtained by following the procedure described in [Task 2: Host the Workflow Designer](task-2-host-the-workflow-designer.md).</span></span>

2. <span data-ttu-id="384e9-107">Nel riquadro **Esplora soluzioni** fare clic con il pulsante destro del mouse sul file *MainWindow. XAML* e selezionare **Visualizza codice**.</span><span class="sxs-lookup"><span data-stu-id="384e9-107">In the **Solution Explorer** pane, right-click the *MainWindow.xaml* file and select **View Code**.</span></span>

3. <span data-ttu-id="384e9-108">Aggiungere un metodo di `GetToolboxControl` alla classe `MainWindow` che crea una <xref:System.Activities.Presentation.Toolbox.ToolboxControl>, aggiunge una nuova categoria della **casella degli strumenti** alla **casella degli strumenti**e assegna i tipi di attività <xref:System.Activities.Statements.Assign> e <xref:System.Activities.Statements.Sequence> a tale categoria.</span><span class="sxs-lookup"><span data-stu-id="384e9-108">Add a `GetToolboxControl` method to the `MainWindow` class that creates a <xref:System.Activities.Presentation.Toolbox.ToolboxControl>, adds a new **Toolbox** category to the **Toolbox**, and assigns the <xref:System.Activities.Statements.Assign> and <xref:System.Activities.Statements.Sequence> activity types to that category.</span></span>

    ```csharp
    private ToolboxControl GetToolboxControl()
    {
        // Create the ToolBoxControl.
        var ctrl = new ToolboxControl();

        // Create a category.
        var category = new ToolboxCategory("category1");

        // Create Toolbox items.
        var tool1 =
            new ToolboxItemWrapper("System.Activities.Statements.Assign",
            typeof(Assign).Assembly.FullName, null, "Assign");

        var tool2 = new ToolboxItemWrapper("System.Activities.Statements.Sequence",
            typeof(Sequence).Assembly.FullName, null, "Sequence");

        // Add the Toolbox items to the category.
        category.Add(tool1);
        category.Add(tool2);

        // Add the category to the ToolBox control.
        ctrl.Categories.Add(category);
        return ctrl;
    }
    ```

4. <span data-ttu-id="384e9-109">Aggiungere un metodo di `AddToolbox` privato alla classe `MainWindow` che posiziona la **casella degli strumenti** nella colonna sinistra della griglia.</span><span class="sxs-lookup"><span data-stu-id="384e9-109">Add a private `AddToolbox` method to the `MainWindow` class that places the **Toolbox** in the left column on the grid.</span></span>

    ```csharp
    private void AddToolBox()
    {
        ToolboxControl tc = GetToolboxControl();
        Grid.SetColumn(tc, 0);
        grid1.Children.Add(tc);
    }
    ```

5. <span data-ttu-id="384e9-110">Aggiungere una chiamata al metodo `AddToolBox` nel costruttore della classe `MainWindow()`, come illustrato nel codice seguente:</span><span class="sxs-lookup"><span data-stu-id="384e9-110">Add a call to the `AddToolBox` method in the `MainWindow()` class constructor as shown in the following code:</span></span>

    ```csharp
    public MainWindow()
    {
        InitializeComponent();
        this.RegisterMetadata();
        this.AddDesigner();

        this.AddToolBox();
    }
    ```

6. <span data-ttu-id="384e9-111">Premere <kbd>F5</kbd> per compilare ed eseguire la soluzione.</span><span class="sxs-lookup"><span data-stu-id="384e9-111">Press <kbd>F5</kbd> to build and run your solution.</span></span> <span data-ttu-id="384e9-112">È necessario visualizzare la **casella degli strumenti** contenente le attività <xref:System.Activities.Statements.Assign> e <xref:System.Activities.Statements.Sequence>.</span><span class="sxs-lookup"><span data-stu-id="384e9-112">The **Toolbox** containing the <xref:System.Activities.Statements.Assign> and <xref:System.Activities.Statements.Sequence> activities should be displayed.</span></span>

## <a name="to-create-the-propertygrid"></a><span data-ttu-id="384e9-113">Per creare il riquadro PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="384e9-113">To create the PropertyGrid</span></span>

1. <span data-ttu-id="384e9-114">Nel riquadro **Esplora soluzioni** fare clic con il pulsante destro del mouse sul file *MainWindow. XAML* e selezionare **Visualizza codice**.</span><span class="sxs-lookup"><span data-stu-id="384e9-114">In the **Solution Explorer** pane, right-click the *MainWindow.xaml* file and select **View Code**.</span></span>

2. <span data-ttu-id="384e9-115">Aggiungere il metodo `AddPropertyInspector` alla classe `MainWindow` per posizionare il riquadro **PropertyGrid** nella colonna più a destra nella griglia:</span><span class="sxs-lookup"><span data-stu-id="384e9-115">Add the `AddPropertyInspector` method to the `MainWindow` class to place the **PropertyGrid** pane in the rightmost column on the grid:</span></span>

    ```csharp
    private void AddPropertyInspector()
    {
        Grid.SetColumn(wd.PropertyInspectorView, 2);
        grid1.Children.Add(wd.PropertyInspectorView);
    }
    ```

3. <span data-ttu-id="384e9-116">Aggiungere una chiamata al metodo `AddPropertyInspector` nel costruttore della classe `MainWindow()`, come illustrato nel codice seguente:</span><span class="sxs-lookup"><span data-stu-id="384e9-116">Add a call to the `AddPropertyInspector` method in the `MainWindow()` class constructor as shown in the following code:</span></span>

    ```csharp
    public MainWindow()
    {
        InitializeComponent();
        this.RegisterMetadata();
        this.AddDesigner();
        this.AddToolBox();

        this.AddPropertyInspector();
    }
    ```

4. <span data-ttu-id="384e9-117">Premere <kbd>F5</kbd> per compilare ed eseguire la soluzione.</span><span class="sxs-lookup"><span data-stu-id="384e9-117">Press <kbd>F5</kbd> to build and run the solution.</span></span> <span data-ttu-id="384e9-118">La **casella degli strumenti**, l'area di disegno del flusso di lavoro e i riquadri **PropertyGrid** dovrebbero essere tutti visualizzati e quando si trascina un'attività <xref:System.Activities.Statements.Assign> o un'attività di <xref:System.Activities.Statements.Sequence> nell'area di disegno, la griglia delle proprietà deve essere aggiornata a seconda dell'attività evidenziata.</span><span class="sxs-lookup"><span data-stu-id="384e9-118">The **Toolbox**, workflow design canvas, and **PropertyGrid** panes should all be displayed, and when you drag an <xref:System.Activities.Statements.Assign> activity or a <xref:System.Activities.Statements.Sequence> activity onto the design canvas, the property grid should update depending on the highlighted activity.</span></span>

## <a name="example"></a><span data-ttu-id="384e9-119">Esempio</span><span class="sxs-lookup"><span data-stu-id="384e9-119">Example</span></span>

<span data-ttu-id="384e9-120">Il file *MainWindow.XAML.cs* dovrebbe ora contenere il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="384e9-120">The *MainWindow.xaml.cs* file should now contain the following code:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Documents;
using System.Windows.Input;
using System.Windows.Media;
using System.Windows.Media.Imaging;
using System.Windows.Navigation;
using System.Windows.Shapes;
// dlls added.
using System.Activities;
using System.Activities.Core.Presentation;
using System.Activities.Presentation;
using System.Activities.Presentation.Metadata;
using System.Activities.Presentation.Toolbox;
using System.Activities.Statements;
using System.ComponentModel;

namespace HostingApplication
{
    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {
        private WorkflowDesigner wd;

        public MainWindow()
        {
            InitializeComponent();
            RegisterMetadata();
            AddDesigner();
            this.AddToolBox();
            this.AddPropertyInspector();
        }

        private void AddDesigner()
        {
            // Create an instance of WorkflowDesigner class.
            this.wd = new WorkflowDesigner();

            // Place the designer canvas in the middle column of the grid.
            Grid.SetColumn(this.wd.View, 1);

            // Load a new Sequence as default.
            this.wd.Load(new Sequence());

            // Add the designer canvas to the grid.
            grid1.Children.Add(this.wd.View);
        }

        private void RegisterMetadata()
        {
            var dm = new DesignerMetadata();
            dm.Register();
        }

        private ToolboxControl GetToolboxControl()
        {
            // Create the ToolBoxControl.
            var ctrl = new ToolboxControl();

            // Create a category.
            var category = new ToolboxCategory("category1");

            // Create Toolbox items.
            var tool1 =
                new ToolboxItemWrapper("System.Activities.Statements.Assign",
                typeof(Assign).Assembly.FullName, null, "Assign");

            var tool2 = new ToolboxItemWrapper("System.Activities.Statements.Sequence",
                typeof(Sequence).Assembly.FullName, null, "Sequence");

            // Add the Toolbox items to the category.
            category.Add(tool1);
            category.Add(tool2);

            // Add the category to the ToolBox control.
            ctrl.Categories.Add(category);
            return ctrl;
        }

        private void AddToolBox()
        {
            ToolboxControl tc = GetToolboxControl();
            Grid.SetColumn(tc, 0);
            grid1.Children.Add(tc);
        }

        private void AddPropertyInspector()
        {
            Grid.SetColumn(wd.PropertyInspectorView, 2);
            grid1.Children.Add(wd.PropertyInspectorView);
        }

    }
}
```

## <a name="see-also"></a><span data-ttu-id="384e9-121">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="384e9-121">See also</span></span>

- [<span data-ttu-id="384e9-122">Riallocazione di Progettazione flussi di lavoro</span><span class="sxs-lookup"><span data-stu-id="384e9-122">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)
- [<span data-ttu-id="384e9-123">Attività 1: Creare una nuova applicazione Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="384e9-123">Task 1: Create a New Windows Presentation Foundation Application</span></span>](task-1-create-a-new-wpf-app.md)
- [<span data-ttu-id="384e9-124">Attività 2: Ospitare Progettazione flussi di lavoro</span><span class="sxs-lookup"><span data-stu-id="384e9-124">Task 2: Host the Workflow Designer</span></span>](task-2-host-the-workflow-designer.md)
