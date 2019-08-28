---
title: Finestre di progettazione composte personalizzate - relatore dell'elemento del flusso di lavoro
ms.date: 03/30/2017
ms.assetid: f85224cf-9e30-44a5-9a81-3bc438a34364
ms.openlocfilehash: 239f7ccd81d5bb60eed32298220df215b09e3e47
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038366"
---
# <a name="custom-composite-designers---workflow-item-presenter"></a>Finestre di progettazione composte personalizzate - relatore dell'elemento del flusso di lavoro
<xref:System.Activities.Presentation.WorkflowItemPresenter> È un tipo di chiave nel modello di programmazione di progettazione WF che consente la creazione di un'"area di rilascio" in cui è possibile posizionare un'attività arbitraria. In questo esempio viene illustrato come compilare un ActivityDesigner che emerge come "area di rilascio".

 In questo esempio viene illustrato quanto segue:

## <a name="demonstrates"></a>Dimostrazione

- Creazione di un ActivityDesigner personalizzato con un oggetto <xref:System.Activities.Presentation.WorkflowItemPresenter>.

- Registrazione della finestra di progettazione personalizzata usando l'archivio di metadati.

- Programmazione della casella degli strumenti riallocata in modo dichiarativo e imperativo.

## <a name="sample-details"></a>Dettagli dell'esempio
 Il codice per questo esempio illustra:

- L'ActivityDesigner personalizzato compilato per la classe `SimpleNativeActivity`.

- La creazione di un ActivityDesigner personalizzato con un oggetto <xref:System.Activities.Presentation.WorkflowItemPresenter>.

```xaml
<sap:ActivityDesigner x:Class="Microsoft.Samples.UsingWorkflowItemPresenter.SimpleNativeDesigner"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"
    xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">
    <sap:ActivityDesigner.Resources>
        <DataTemplate x:Key="Collapsed">
            <StackPanel>
                <TextBlock>This is the collapsed view</TextBlock>
            </StackPanel>
        </DataTemplate>
        <DataTemplate x:Key="Expanded">
            <StackPanel>
                <TextBlock>Custom Text</TextBlock>
                <sap:WorkflowItemPresenter Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"
                                        HintText="Please drop an activity here" />
            </StackPanel>
        </DataTemplate>
        <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">
            <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>
            <Style.Triggers>
                <DataTrigger Binding="{Binding Path=ShowExpanded}" Value="true">
                    <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>
                </DataTrigger>
            </Style.Triggers>
        </Style>
    </sap:ActivityDesigner.Resources>
    <Grid>
        <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}" />
    </Grid>
</sap:ActivityDesigner>
```

 Notare l'uso dell'associazione dati WPF per eseguire l'associazione a `ModelItem.Body`. `ModelItem`è la proprietà su <xref:System.Activities.Presentation.ActivityDesigner> che fa riferimento all'oggetto sottostante per il quale viene utilizzata la finestra di progettazione, in questo caso **SimpleNativeActivity**.

#### <a name="to-setup-build-and-run-the-sample"></a>Per impostare, compilare ed eseguire l'esempio

1. Aprire la soluzione in Visual Studio 2010.

2. Premere F5 per compilare ed eseguire l'applicazione.

> [!IMPORTANT]
> È possibile che gli esempi siano già installati nel computer. Verificare la directory seguente (impostazione predefinita) prima di continuare.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Se questa directory non esiste, passare a [Windows Communication Foundation (WCF) ed esempi di Windows Workflow Foundation (WF) per .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) per scaricare tutti i Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ed esempi. Questo esempio si trova nella directory seguente.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemPresenter`  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.Activities.Presentation.WorkflowItemPresenter>
- [Sviluppo di applicazioni con Progettazione flussi di lavoro](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
