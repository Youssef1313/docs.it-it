---
title: Più contratti
ms.date: 03/30/2017
ms.assetid: 2bef319b-fe9c-4d49-ac6c-dfb23eb35099
ms.openlocfilehash: 257b3f7946a7185cdb82bda88e64e543afa85707
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039198"
---
# <a name="multiple-contracts"></a>Più contratti
Nell'esempio dei contratti multipli viene illustrato come implementare più di un contratto in un servizio e come configurare gli endpoint per comunicare con ognuno dei contratti implementati. Questo esempio è basato sul [Introduzione](../../../../docs/framework/wcf/samples/getting-started-sample.md). Il servizio è stato modificato per definire due contratti, il contratto `ICalculator` e il contratto `ICalculatorSession`.  
  
> [!NOTE]
> La procedura di installazione e le istruzioni di compilazione per questo esempio si trovano alla fine di questo argomento.  
  
 La classe del servizio implementa sia il contratto il servizio Web da `ICalculator` che il contratto `ICalculatorSession`. Poiché uno dei contratti richiede una sessione, il servizio utilizza la modalità dell'istanza <xref:System.ServiceModel.InstanceContextMode.PerSession> per gestire lo stato per tutta la durata della sessione.  
  
 La configurazione del servizio è stata modificata per definire due endpoint allo scopo di esporre ogni contratto. L'endpoint `ICalculator` viene esposto all'indirizzo di base utilizzando `basicHttpBinding`. L'endpoint `ICalculatorSession` viene esposto all'indirizzo/sessione di base utilizzando `wsHttpBinding` con l'attributo `bindingConfiguration` impostato su `BindingWithSession`, come illustrato nella configurazione dell'esempio seguente.  
  
```xml  
<service   
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <!-- ICalculator endpoint is exposed using BasicBinding at the base  
       address provided by host:   
       http://localhost/servicemodelsamples/service.svc  -->  
  <endpoint address=""  
            binding="basicHttpBinding"  
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  <!-- ICalculatorSession endpoint is exposed using BindingWithSession  
       at {baseaddress}/session:  
       http://localhost/servicemodelsamples/service.svc/session -->  
  <endpoint address="session"  
            binding="wsHttpBinding"  
            bindingConfiguration="BindingWithSession"   
           contract="Microsoft.ServiceModel.Samples.ICalculatorSession" />  
  ...  
</service>  
```  
  
 Il codice client generato include ora una classe client sia per il contratto `ICalculator` originale che per il contratto `ICalculatorSession` nuovo. La configurazione client e il codice sono stati modificati per comunicare con ogni contratto all'endpoint del servizio appropriato.  
  
 Il client è un'applicazione console Windows (con estensione exe). Il servizio è ospitato da Internet Information Services (IIS).  
  
 Nella finestra della console client vengono visualizzate le operazioni inviate a ognuno degli endpoint, prima all'endpoint di base, seguito dall'endpoint protetto.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Per impostare, compilare ed eseguire l'esempio  
  
1. Assicurarsi di avere eseguito la [procedura di installazione singola per gli esempi di Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Per compilare l'edizione in C# o Visual Basic .NET della soluzione, seguire le istruzioni in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Per eseguire l'esempio in una configurazione con un solo computer o tra computer diversi, seguire le istruzioni in [esecuzione degli esempi di Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> È possibile che gli esempi siano già installati nel computer. Verificare la directory seguente (impostazione predefinita) prima di continuare.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Se questa directory non esiste, passare a [Windows Communication Foundation (WCF) ed esempi di Windows Workflow Foundation (WF) per .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) per scaricare tutti i Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ed esempi. Questo esempio si trova nella directory seguente.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleContracts`  
