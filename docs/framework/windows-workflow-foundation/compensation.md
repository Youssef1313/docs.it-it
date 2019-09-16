---
title: Compensazione
ms.date: 03/30/2017
ms.assetid: 722e9766-48d7-456c-9496-d7c5c8f0fa76
ms.openlocfilehash: 147da26fd297d41876815cffcc70450ae905ba85
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935435"
---
# <a name="compensation"></a>Compensazione
La compensazione in Windows Workflow Foundation (WF) è il meccanismo in base al quale il lavoro completato in precedenza può essere annullato o compensato (seguendo la logica definita dall'applicazione) quando si verifica un errore successivo. Contenuto della sezione viene illustrato come usare la compensazione nei flussi di lavoro.  
  
## <a name="compensation-vs-transactions"></a>Differenze tra compensazioni e Transazioni  
 Una transazione consente di combinare più operazioni in un'unica unità di lavoro. Quando viene usata una transazione, l'applicazione può annullare, ovvero eseguire il rollback, di tutte le modifiche eseguite dall'interno della transazione se si verificano errori durante qualsiasi parte del processo della transazione. L'utilizzo di transazioni potrebbe tuttavia non essere adatto per un lavoro a esecuzione prolungata. Ad esempio, un'applicazione di pianificazione di viaggi viene implementata come flusso di lavoro. I passaggi del flusso di lavoro possono essere costituiti dalla prenotazione di un volo, dall'attesa dell'approvazione da parte del responsabile e dal pagamento del volo. Questo processo potrebbe richiedere molti giorni e non è funzionale che i passaggi di prenotazione e pagamento del volo prendano parte alla stessa transazione. In uno scenario come questo, la compensazione potrebbe essere usata per annullare il passaggio di prenotazione del flusso di lavoro se, successivamente, si verifica un errore nell'elaborazione.  
  
> [!NOTE]
> In questo argomento viene illustrato il concetto di compensazione nei flussi di lavoro. Per ulteriori informazioni sulle transazioni nei flussi di lavoro, vedere [Transazioni](workflow-transactions.md) e <xref:System.Activities.Statements.TransactionScope>. Per ulteriori informazioni sulle transazioni, vedere <xref:System.Transactions?displayProperty=nameWithType> e <xref:System.Transactions.Transaction?displayProperty=nameWithType>.  
  
## <a name="using-compensableactivity"></a>Uso di CompensableActivity  
 L'oggetto <xref:System.Activities.Statements.CompensableActivity> è l'attività di compensazione principale di [!INCLUDE[wf1](../../../includes/wf1-md.md)]. Qualsiasi attività che esegue un lavoro che necessita di compensazione viene inserita nell'oggetto <xref:System.Activities.Statements.CompensableActivity.Body%2A> di un oggetto <xref:System.Activities.Statements.CompensableActivity>. In questo esempio il passaggio di prenotazione relativo all'acquisto di un volo viene inserito nell'oggetto <xref:System.Activities.Statements.CompensableActivity.Body%2A> di un oggetto <xref:System.Activities.Statements.CompensableActivity>, mentre l'annullamento della prenotazione viene inserito nell'oggetto <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>. Subito dopo l'oggetto <xref:System.Activities.Statements.CompensableActivity> nel flusso di lavoro si trovano due attività che attendono l'approvazione del responsabile e successivamente completano il passaggio di acquisto del volo. Se una condizione di errore provoca l'annullamento del flusso di lavoro dopo il corretto completamento dell'oggetto <xref:System.Activities.Statements.CompensableActivity>, le attività nel gestore <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> vengono pianificate e il volo viene annullato.  
  
 [!code-csharp[CFX_CompensationExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#1)]  
  
 L'esempio seguente è il flusso di lavoro in XAML.  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 Quando il flusso di lavoro viene richiamato, l'output seguente viene visualizzato nella console.  
  
 **ReserveFlight Ticket riservato.**  
**ManagerApproval: Approvazione del responsabile ricevuta.**    
**PurchaseFlight: Il ticket è stato acquistato.**    
**Il flusso di lavoro è stato completato correttamente con lo stato: Chiuso.**    
> [!NOTE]
> Nelle attività di esempio in questo argomento, quale `ReserveFlight`, vengono visualizzati nome e scopo nella console per consentire di illustrare l'ordine in cui vengono eseguite le attività quando si verifica la compensazione.  
  
### <a name="default-workflow-compensation"></a>Compensazione del flusso di lavoro predefinita  
 Per impostazione predefinita, se il flusso di lavoro viene annullato, viene eseguita la logica di compensazione per qualsiasi attività compensabile che è stata completata correttamente e non è stata già confermata o compensata.  
  
> [!NOTE]
> Quando un <xref:System.Activities.Statements.CompensableActivity> oggetto viene *confermato*, la compensazione per l'attività non può essere più richiamata. Il processo di conferma verrà illustrato più avanti in questa sezione.  
  
 In questo esempio viene generata un'eccezione dopo la prenotazione del volo ma prima del passaggio di approvazione da parte del responsabile.  
  
 [!code-csharp[CFX_CompensationExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#2)]  
  
 In questo esempio viene illustrato il flusso di lavoro in XAML.  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:SimulatedErrorCondition />  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 [!code-csharp[CFX_CompensationExample#100](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#100)]  
  
 Quando viene richiamato il flusso di lavoro, l'eccezione della condizione di errore simulata viene gestita dall'applicazione host in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, il flusso di lavoro viene annullato e la logica di compensazione viene richiamata.  
  
 **ReserveFlight Ticket riservato.**  
**SimulatedErrorCondition: Generazione di un'eccezione ApplicationException.**    
**Eccezione non gestita del flusso di lavoro:**    
**System. ApplicationException: Condizione di errore simulata nel flusso di lavoro.**    
**CancelFlight: Il ticket è stato annullato.**    
**Il flusso di lavoro è stato completato correttamente con lo stato: Annullata.**    
### <a name="cancellation-and-compensableactivity"></a>Annullamento e CompensableActivity  
 Se le attività in <xref:System.Activities.Statements.CompensableActivity.Body%2A> di un oggetto <xref:System.Activities.Statements.CompensableActivity> non sono state completate e l'attività è annullata, vengono eseguite le attività in <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>.  
  
> [!NOTE]
> <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> viene richiamato solo se le attività nell'oggetto <xref:System.Activities.Statements.CompensableActivity.Body%2A> dell'oggetto <xref:System.Activities.Statements.CompensableActivity> non sono state completate e l'attività è annullata. <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> viene eseguito solo se le attività nell'oggetto <xref:System.Activities.Statements.CompensableActivity.Body%2A> dell'oggetto <xref:System.Activities.Statements.CompensableActivity> sono state completate correttamente e viene successivamente richiamata la compensazione sull'attività.  
  
 <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> fornisce offre agli autori del flusso di lavoro la possibilità per fornire la logica di annullamento appropriata. Nell'esempio seguente viene generata un'eccezione durante l'esecuzione di <xref:System.Activities.Statements.CompensableActivity.Body%2A>, quindi viene richiamato <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>.  
  
```csharp  
Activity wf = new Sequence()  
{  
    Activities =  
    {  
        new CompensableActivity  
        {  
            Body = new Sequence  
            {  
                Activities =   
                {  
                    new ChargeCreditCard(),  
                    new SimulatedErrorCondition(),  
                    new ReserveFlight()  
                }  
            },  
            CompensationHandler = new CancelFlight(),  
            CancellationHandler = new CancelCreditCard()  
        },  
        new ManagerApproval(),  
        new PurchaseFlight()  
    }  
};  
```  
  
 Questo esempio è il flusso di lavoro in XAML  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <Sequence>  
      <c:ChargeCreditCard />  
      <c:SimulatedErrorCondition />  
      <c:ReserveFlight />  
    </Sequence>  
    <CompensableActivity.CancellationHandler>  
      <c:CancelCreditCard />  
    </CompensableActivity.CancellationHandler>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 Quando viene richiamato il flusso di lavoro, l'eccezione della condizione di errore simulata viene gestita dall'applicazione host in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, il flusso di lavoro viene annullato e viene richiamata la logica di cancellazione di <xref:System.Activities.Statements.CompensableActivity>. In questo esempio, la logica di compensazione e la logica di annullamento hanno obiettivi differenti. Se <xref:System.Activities.Statements.CompensableActivity.Body%2A> è stato completato correttamente, questo significa che è stato effettuato il prelievo dalla carta di credito e il volo è stato prenotato, pertanto la compensazione dovrebbe annullare entrambi i passaggi. In questo esempio, l'annullamento del volo annulla automaticamente l'addebito sulla carta di credito. Tuttavia, se <xref:System.Activities.Statements.CompensableActivity> viene annullato, questo significa che <xref:System.Activities.Statements.CompensableActivity.Body%2A> non è stato completato e la logica di <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> deve essere in grado di determinare il metodo migliore di gestire l'annullamento. In questo esempio, <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> annulla l'addebito sulla carta di credito, tuttavia, poiché `ReserveFlight` era l'ultima attività in <xref:System.Activities.Statements.CompensableActivity.Body%2A>, non tenta di annullare il volo. Dal momento che `ReserveFlight` era l'ultima attività in <xref:System.Activities.Statements.CompensableActivity.Body%2A>, se fosse stata completata correttamente, l'oggetto <xref:System.Activities.Statements.CompensableActivity.Body%2A> sarebbe stato completato e non sarebbe stato possibile alcun annullamento.  
  
 **ChargeCreditCard: Addebita la carta di credito per il volo.**  
**SimulatedErrorCondition: Generazione di un'eccezione ApplicationException.**    
**Eccezione non gestita del flusso di lavoro:**    
**System. ApplicationException: Condizione di errore simulata nel flusso di lavoro.**    
**CancelCreditCard: Annulla le tariffe della carta di credito.**    
**Il flusso di lavoro è stato completato correttamente con lo stato: Annullata.**  Per ulteriori informazioni sull'annullamento, vedere [annullamento](modeling-cancellation-behavior-in-workflows.md).  
  
### <a name="explicit-compensation-using-the-compensate-activity"></a>Compensazione esplicita tramite l'attività Compensate  
 Nella sezione precedente è stata illustrata la compensazione implicita. Si tratta di un tipo di compensazione che può risultare appropriata per scenari semplici, ma se occorre un controllo più esplicito sulla pianificazione della gestione della compensazione è possibile usare l'attività <xref:System.Activities.Statements.Compensate>. Per iniziare il processo di compensazione con l'attività <xref:System.Activities.Statements.Compensate>, viene usato l'oggetto <xref:System.Activities.Statements.CompensationToken> dell'oggetto <xref:System.Activities.Statements.CompensableActivity> per il quale si desidera la compensazione. L'attività <xref:System.Activities.Statements.Compensate> può essere usata per iniziare la compensazione su qualsiasi oggetto <xref:System.Activities.Statements.CompensableActivity> completato che non è stato confermato o compensato. Ad esempio, un'attività <xref:System.Activities.Statements.Compensate> potrebbe essere usata nella sezione <xref:System.Activities.Statements.TryCatch.Catches%2A> di un'attività <xref:System.Activities.Statements.TryCatch> o in qualsiasi momento dopo il completamento dell'oggetto <xref:System.Activities.Statements.CompensableActivity>. In questo esempio l'attività <xref:System.Activities.Statements.Compensate> viene usata nella sezione <xref:System.Activities.Statements.TryCatch.Catches%2A> di un'attività <xref:System.Activities.Statements.TryCatch> per invertire l'azione dell'oggetto <xref:System.Activities.Statements.CompensableActivity>.  
  
 [!code-csharp[CFX_CompensationExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#3)]  
  
 In questo esempio viene illustrato il flusso di lavoro in XAML.  
  
```xaml  
<TryCatch  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:s="clr-namespace:System;assembly=mscorlib"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <TryCatch.Variables>  
    <Variable  
       x:TypeArguments="CompensationToken"  
       x:Name="__ReferenceID0"  
       Name="token1" />  
  </TryCatch.Variables>  
  <TryCatch.Try>  
    <Sequence>  
      <CompensableActivity>  
        <CompensableActivity.Result>  
          <OutArgument  
             x:TypeArguments="CompensationToken">  
            <VariableReference  
               x:TypeArguments="CompensationToken"  
               Variable="{x:Reference __ReferenceID0}">  
              <VariableReference.Result>  
                <OutArgument  
                   x:TypeArguments="Location(CompensationToken)" />  
              </VariableReference.Result>  
            </VariableReference>  
          </OutArgument>  
        </CompensableActivity.Result>  
        <CompensableActivity.CompensationHandler>  
          <c:CancelFlight />  
        </CompensableActivity.CompensationHandler>  
        <CompensableActivity.ConfirmationHandler>  
          <c:ConfirmFlight />  
        </CompensableActivity.ConfirmationHandler>  
        <c:ReserveFlight />  
      </CompensableActivity>  
      <c:SimulatedErrorCondition />  
      <c:ManagerApproval />  
      <c:PurchaseFlight />  
    </Sequence>  
  </TryCatch.Try>  
  <TryCatch.Catches>  
    <Catch  
       x:TypeArguments="s:ApplicationException">  
      <ActivityAction  
         x:TypeArguments="s:ApplicationException">  
        <Compensate>  
          <Compensate.Target>  
            <InArgument  
               x:TypeArguments="CompensationToken">  
              <VariableValue  
                 x:TypeArguments="CompensationToken"  
                 Variable="{x:Reference __ReferenceID0}">  
                <VariableValue.Result>  
                  <OutArgument  
                     x:TypeArguments="CompensationToken" />  
                </VariableValue.Result>  
              </VariableValue>  
            </InArgument>  
          </Compensate.Target>  
        </Compensate>  
      </ActivityAction>  
    </Catch>  
  </TryCatch.Catches>  
</TryCatch>  
```  
  
 Quando il flusso di lavoro viene richiamato, l'output seguente viene visualizzato nella console.  
  
 **ReserveFlight Ticket riservato.**  
**SimulatedErrorCondition: Generazione di un'eccezione ApplicationException.**    
**CancelFlight: Il ticket è stato annullato.**    
**Il flusso di lavoro è stato completato correttamente con lo stato: Chiuso.**    
### <a name="confirming-compensation"></a>Conferma della compensazione  
 Per impostazione predefinita, le attività compensabili possono essere compensate in qualsiasi momento una volta completate. In alcuni casi però questo potrebbe non essere appropriato. Nell'esempio precedente la compensazione relativa alla prenotazione del biglietto consisteva nell'annullamento della prenotazione. Tuttavia, una volta completato il volo, questo passaggio di compensazione non è più valido. La conferma dell'attività compensabile richiama l'attività specificata da <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>. Un possibile utilizzo consiste nel consentire a qualsiasi risorsa necessaria di eseguire la compensazione da rilasciare. Una volta confermata, un'attività compensabile non può essere compensata e se si tenta tale operazione, verrà generata un'eccezione <xref:System.InvalidOperationException>. Quando un flusso di lavoro viene completato correttamente, tutte le attività compensabili non confermate e non compensate completate correttamente vengono confermate nell'ordine inverso rispetto al completamento. In questo esempio il volo è prenotato, acquistato e completato, quindi l'attività compensabile è confermata. Per confermare un oggetto <xref:System.Activities.Statements.CompensableActivity>, usare l'attività <xref:System.Activities.Statements.Confirm> e specificare l'oggetto <xref:System.Activities.Statements.CompensationToken> dell'oggetto <xref:System.Activities.Statements.CompensableActivity> da confermare.  
  
 [!code-csharp[CFX_CompensationExample#4](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#4)]  
  
 In questo esempio viene illustrato il flusso di lavoro in XAML.  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <Sequence.Variables>  
    <x:Reference>__ReferenceID0</x:Reference>  
  </Sequence.Variables>  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken">  
        <VariableReference  
           x:TypeArguments="CompensationToken">  
          <VariableReference.Result>  
            <OutArgument  
               x:TypeArguments="Location(CompensationToken)" />  
          </VariableReference.Result>  
          <VariableReference.Variable>  
            <Variable  
               x:TypeArguments="CompensationToken"  
               x:Name="__ReferenceID0"  
               Name="token1" />  
          </VariableReference.Variable>  
        </VariableReference>  
      </OutArgument>  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <CompensableActivity.ConfirmationHandler>  
      <c:ConfirmFlight />  
    </CompensableActivity.ConfirmationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
  <c:TakeFlight />  
  <Confirm>  
    <Confirm.Target>  
      <InArgument  
         x:TypeArguments="CompensationToken">  
        <VariableValue  
           x:TypeArguments="CompensationToken"  
           Variable="{x:Reference __ReferenceID0}">  
          <VariableValue.Result>  
            <OutArgument  
               x:TypeArguments="CompensationToken" />  
          </VariableValue.Result>  
        </VariableValue>  
      </InArgument>  
    </Confirm.Target>  
  </Confirm>  
</Sequence>  
```  
  
Quando il flusso di lavoro viene richiamato, l'output seguente viene visualizzato nella console.  
  
**ReserveFlight Ticket riservato.**  
**ManagerApproval: Approvazione del responsabile ricevuta.**    
**PurchaseFlight: Il ticket è stato acquistato.**    
**TakeFlight: Il volo è stato completato.**    
**ConfirmFlight: Il volo è stato effettuato, nessuna compensazione possibile.**    
**Il flusso di lavoro è stato completato correttamente con lo stato: Chiuso.**   

## <a name="nesting-compensation-activities"></a>Annidamento delle attività di compensazione  

Un oggetto <xref:System.Activities.Statements.CompensableActivity> può essere posizionato nella sezione <xref:System.Activities.Statements.CompensableActivity.Body%2A> di un altro oggetto <xref:System.Activities.Statements.CompensableActivity>. Un oggetto <xref:System.Activities.Statements.CompensableActivity> non può essere inserito in un gestore di un altro oggetto <xref:System.Activities.Statements.CompensableActivity>. È responsabilità di un oggetto <xref:System.Activities.Statements.CompensableActivity> padre garantire che quando viene annullato, confermato o compensato, tutte le attività figlio compensabili che sono state completate correttamente e non sono state già confermate o compensate siano confermate o compensate prima dell'annullamento, la conferma o la compensazione del padre. Se questo comportamento non è determinato in modo esplicito, l'oggetto <xref:System.Activities.Statements.CompensableActivity> padre compenserà in modo implicito le attività figlio compensabili se ha ricevuto l'indicazione di annullamento o compensazione. Se il padre ha ricevuto l'indicazione di conferma, confermerà in modo implicito le attività figlio compensabili. Se la logica di gestione di un annullamento, una conferma o una compensazione è modellata in modo esplicito nel gestore dell'oggetto <xref:System.Activities.Statements.CompensableActivity> padre, qualsiasi oggetto figlio non esplicitamente gestito verrà confermato in modo implicito.  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.Activities.Statements.CompensableActivity>
- <xref:System.Activities.Statements.Compensate>
- <xref:System.Activities.Statements.Confirm>
- <xref:System.Activities.Statements.CompensationToken>
