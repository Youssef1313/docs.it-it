---
title: Ottimizzazione dell'applicazione Async
ms.date: 07/20/2015
ms.assetid: 4c3e7997-a95f-4fbe-a6ac-60ba042d30b9
ms.openlocfilehash: 51786993cf16cd12b39cde3d47832191b3fdca8d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345829"
---
# <a name="fine-tuning-your-async-application-visual-basic"></a>Ottimizzazione dell'applicazione asincrona (Visual Basic)
È possibile rendere più precise e flessibili le applicazioni asincrone usando le proprietà e i metodi resi disponibili dal tipo <xref:System.Threading.Tasks.Task>. Gli argomenti di questa sezione mostrano esempi che usano <xref:System.Threading.CancellationToken> e metodi `Task` importanti, ad esempio <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.  
  
 Usando `WhenAny` e `WhenAll`, è possibile avviare più attività e attenderne il completamento da una singola attività di monitoraggio in modo più facile.  
  
- `WhenAny` restituisce un'attività completata quando una qualsiasi attività in una raccolta viene completata.  
  
     Per esempi che usano `WhenAny`, vedere [annullare le attività asincrone rimanenti dopo che ne è stata completata una (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)e [avviare più attività asincrone ed elaborarle quando vengono completate (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).  
  
- `WhenAll` restituisce un'attività completata quando tutte le attività in una raccolta vengono completate.  
  
     Per ulteriori informazioni e un esempio di utilizzo di `WhenAll`, vedere [procedura: estendere la procedura dettagliata asincrona tramite Task. WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
 Questa sezione presenta i seguenti esempi.  
  
- [Annullare un'attività asincrona o un elenco di attività (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).  
  
- [Annulla le attività asincrone dopo un periodo di tempo (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
- [Annulla le attività asincrone rimanenti dopo che ne è stata completata una (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [Avviare più attività asincrone ed elaborarle quando vengono completate (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
> Per eseguire gli esempi, è necessario che nel computer siano installati Visual Studio 2012 o versioni successive e .NET Framework 4.5 o versioni successive.  
  
 I progetti creano un'interfaccia utente che contiene un pulsante che consente di avviare il processo e un pulsante che consente di annullarlo, come illustrato nell'immagine seguente. I pulsanti sono denominati `startButton` e `cancelButton`.  
  
 ![Finestra WPF con pulsante Annulla](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Finestra di dialogo con un pulsante avvia e arresta")  
  
 È possibile scaricare i progetti completi di Windows Presentation Foundation (WPF) da [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) (Esempio di attività asincrona: ottimizzazione dell'applicazione).  
  
## <a name="see-also"></a>Vedere anche

- [Programmazione asincrona con Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
