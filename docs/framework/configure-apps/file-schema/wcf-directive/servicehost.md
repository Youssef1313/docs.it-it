---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: a56fb1bb9395425222347914fe3f4c17f1a451b7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920331"
---
# <a name="servicehost"></a>\@ServiceHost
Associa la factory usata per creare l'host del servizio al servizio da ospitare e agli altri aspetti di programmazione necessari per accedere al codice host fornito nel file .svc o per compilarlo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<% @ServiceHost   
Service = "Service, ServiceNamespace"   
Factory = "Factory, FactoryNamespace"  
Debug = "Debug"  
Language = "Language"   
CodeBehind = "CodeBehind"%>  
```  
  
## <a name="attributes"></a>Attributi  
  
#### <a name="service"></a>Service  
 Nome del tipo CLR del servizio ospitato. Deve essere un nome completo di un tipo che implementa uno o più dei contatti del servizio.  
  
#### <a name="factory"></a>Factory  
 Nome del tipo CLR della factory dell'host del servizio usato per creare un'istanza dell'host del servizio. L'attributo è facoltativo. Se non viene specificato, viene usata la factory <xref:System.ServiceModel.Activation.ServiceHostFactory> predefinita, che restituisce un'istanza dell'host <xref:System.ServiceModel.ServiceHost>.  
  
#### <a name="debug"></a>Debug  
 Indica se il servizio Windows Communication Foundation (WCF) deve essere compilato con simboli di debug. `true`Se il servizio WCF deve essere compilato con i simboli di debug; in caso `false`contrario,.  
  
#### <a name="language"></a>Linguaggio  
 Specifica il linguaggio usato per la compilazione di tutto il codice inline contenuto nel file con estensione svc. I valori possono rappresentare qualsiasi linguaggio supportato da .NET, inclusi C#, VB e JS, che fanno riferimento, rispettivamente, a C#, Visual Basic .NET e JScript .NET. L'attributo è facoltativo.  
  
#### <a name="codebehind"></a>CodeBehind  
 Specifica il file di origine per l'implementazione del servizio Web XML, quando la classe di implementazione non si trova nello stesso file e non è stata compilata in un assembly e inserita nella directory \Bin.  
  
## <a name="remarks"></a>Note  
 L' <xref:System.ServiceModel.ServiceHost> oggetto utilizzato per ospitare il servizio è un punto di estendibilità all'interno del modello di programmazione Windows Communication Foundation (WCF). Poiché un modello di factory può essere un tipo polimorfico di cui l'ambiente host non deve creare un'istanza direttamente, tale modello viene usato per creare un'istanza dell'host <xref:System.ServiceModel.ServiceHost>.  
  
 L'implementazione predefinita usa la factory <xref:System.ServiceModel.Activation.ServiceHostFactory> per creare un'istanza dell'host <xref:System.ServiceModel.ServiceHost>. È tuttavia possibile specificare una factory personalizzata, ovvero una che restituisce l'host derivato, specificando il nome del tipo CLR dell'implementazione Factory nella [ \@direttiva ServiceHost](servicehost.md) .  
  
 Per usare la factory host del servizio personalizzata anziché la factory predefinita, è sufficiente specificare il nome del tipo nella [@ServiceHost](servicehost.md) direttiva, come indicato di seguito:  
  
```xml  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 È consigliabile garantire che le implementazioni presentino la massima semplicità possibile. Se si usa un'elevata quantità di logica personalizzata, quest'ultima è più riutilizzabile se inserita nell'host anziché nella factory.  
  
 Per abilitare un endpoint abilitato per AJAX per `MyService`, ad esempio, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> specificare `Factory` per il valore dell'attributo [@ServiceHost](servicehost.md) , anziché quello predefinito <xref:System.ServiceModel.Activation.ServiceHostFactory>, nella direttiva, come illustrato nell'esempio seguente.  
  
## <a name="example"></a>Esempio  
  
```  
<% @ServiceHost   
Service="MyService"  
Language="C#"  
Debug="true"  
Factory="WebScriptServiceHostFactory"  
%>  
```  
  
## <a name="see-also"></a>Vedere anche

- [Host di servizi personalizzati](../../../wcf/samples/custom-service-host.md)
