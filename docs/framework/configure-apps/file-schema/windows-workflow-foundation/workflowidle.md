---
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: 1d8ddaf5d69d87ff6112b5cbb285f0ccfda724e2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397543"
---
# <a name="workflowidle"></a>\<> workflowIdle
Un comportamento del servizio che controlla quando istanze del flusso di lavoro inattive vengono scaricate e rese persistenti.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<sistema. > ServiceModel**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamenti >** ](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceBehaviors**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamento >** ](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> workflowIdle**  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowIdle timeToPersist="TimeSpan" 
                    timeToUnload="TimeSpan" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|timeToPersist|Valore TimeSpan che specifica l'intervallo di tempo tra il momento in cui il flusso di lavoro diventa inattivo e viene reso permanente. Il valore predefinito è TimeSpan. MaxValue.<br /><br /> L'intervallo di tempo inizia quando l'istanza del flusso di lavoro diventa inattiva. Questo attributo è utile se si desidera mantenere un'istanza del flusso di lavoro in modo più aggressivo mantenendo comunque l'istanza in memoria per il periodo di tempo più lungo possibile. Questo attributo è valido solo se il relativo valore è minore dell'attributo **TimeToUnload** . Se è superiore, verrà ignorato. Se questo attributo scade prima del valore specificato dall'attributo **TimeToUnload** , è necessario completare la persistenza prima di scaricare il flusso di lavoro. Questo significa che l'operazione di scaricamento può essere ritardata fino a quando il flusso di lavoro non verrà reso persistente. Il livello di persistenza è responsabile della gestione dei tentativi effettuati in presenza di errori temporanei e genera eccezioni solo per gli errori irreversibili. Le eventuali eccezioni generate durante la persistenza vengono pertanto considerate fatali e l'istanza del flusso di lavoro viene interrotta.|  
|timeToUnload|Valore TimeSpan che specifica l'intervallo di tempo tra l'ora in cui il flusso di lavoro diventa inattivo e quella in cui viene scaricato. Il valore predefinito è 1 minuto.<br /><br /> Lo scaricamento di un flusso di lavoro lo rende anche persistente. Se questo attributo è impostato su zero, l'istanza del flusso di lavoro viene resa permanente e scaricata immediatamente dopo che il flusso di lavoro diventa inattivo. Se si imposta questo attributo su TimeSpan. MaxValue, l'operazione di scaricamento viene disabilitata. Le istanze del flusso di lavoro inattive non vengono mai scaricate.|  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|DESCRIZIONE|  
|-------------|-----------------|  
|[\<comportamento > di \<serviceBehaviors >](behavior-of-servicebehaviors-of-workflow.md)|Specifica un elemento di comportamento.|  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
