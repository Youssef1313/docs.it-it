---
title: Rilevamento visivo del flusso di lavoro
ms.date: 03/30/2017
ms.assetid: 0143448f-2044-40a0-8a3d-941f6d12468b
ms.openlocfilehash: 05f8fcf4c765998fc4e101d9dbef026d85b8b2fb
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715513"
---
# <a name="visual-workflow-tracking"></a>Rilevamento visivo del flusso di lavoro
In questo esempio viene illustrato come scrivere un'applicazione visiva di rilevamento flusso di lavoro usando la funzionalità di debug disponibile tramite [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].

## <a name="sample-details"></a>Dettagli dell'esempio
 L'applicazione esegue un semplice flusso di lavoro del diagramma di flusso (definito in Workflow.xaml) e rialloca la finestra di progettazione del flusso di lavoro per visualizzare il flusso di lavoro attualmente in esecuzione. Mentre viene eseguito il flusso di lavoro, l'attività attualmente in esecuzione viene visualizzata con un contorno giallo e una freccia di debug. Inoltre, i record di rilevamento generati dal flusso di lavoro vengono visualizzati anche nella finestra dell'applicazione. Per ulteriori informazioni sul rilevamento del flusso di lavoro, vedere [rilevamento e traccia del flusso di lavoro](../workflow-tracking-and-tracing.md). Per ulteriori informazioni sulla riallocazione di progettazione flussi di lavoro, vedere [riallocazione del progettazione flussi di lavoro](../rehosting-the-workflow-designer.md).

 Il funzionamento del simulatore del flusso di lavoro prevede l'uso di due dizionari. Uno contiene un mapping tra l'oggetto attività attualmente in esecuzione e il numero di riga del file XAML in cui viene creata un'istanza dell'attività. L'altro contiene un mapping tra l'ID istanza dell'attività e l'oggetto attività. Quando i record di rilevamento vengono generati usando un profilo di rilevamento personalizzato, l'applicazione determina l'ID istanza dell'attività attualmente in esecuzione e ne esegue di nuovo il mapping al file XAML che ha creato un'istanza dell'attività. In base alle istruzioni, la finestra di progettazione del flusso di lavoro riallocata evidenzia l'attività nell'area di progettazione e usa lo stesso metodo del debugger del flusso di lavoro, in particolare disegnando un bordo giallo intorno all'attività e visualizzando una freccia gialla lungo il lato sinistro della finestra di progettazione.

#### <a name="to-use-this-sample"></a>Per usare questo esempio

1. Aprire il file WorkflowSimulator. sln dalla directory di esempio in Visual Studio 2010.

2. Per compilare la soluzione, premere CTRL+MAIUSC+B.

3. Premere CTRL + F5 per eseguire l'esempio. Viene visualizzato il file Workflow.xaml in una finestra di progettazione del flusso di lavoro riallocata.

4. Scegliere **Esegui flusso di lavoro**dal menu **file** .

5. Come si noterà, l'attività attualmente in esecuzione è evidenziata come descritto in precedenza e i record di rilevamento vengono visualizzati sul lato destro della finestra dell'applicazione.

6. Una volta completato il flusso di lavoro, è possibile fare clic su qualsiasi record di rilevamento per controllare l'attività alla quale corrisponde.

> [!IMPORTANT]
> È possibile che gli esempi siano già installati nel computer. Verificare la directory seguente (impostazione predefinita) prima di continuare.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Se questa directory non esiste, passare a [Windows Communication Foundation (WCF) ed esempi di Windows Workflow Foundation (WF) per .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) per scaricare tutti i Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] esempi. Questo esempio si trova nella directory seguente.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\VisualWorkflowTracking`
