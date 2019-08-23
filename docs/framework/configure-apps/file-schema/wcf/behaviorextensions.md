---
title: <behaviorExtensions>
ms.date: 03/30/2017
ms.assetid: 59f2791a-c78f-40d7-aa80-0d9cd10135d9
ms.openlocfilehash: bcf1f1dcdba50c3e7fba8eb170132d0cf47c4271
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919812"
---
# <a name="behaviorextensions"></a>\<behaviorExtensions>
Le estensioni di comportamento consentono all'utente di creare elementi di comportamento definiti dall'utente. Questi elementi possono essere usati insieme agli elementi di comportamento standard di Windows Communication Foundation (WCF). Nella sezione `behaviorExtensions` l'elemento viene definito in modo tale che possa essere usato nella configurazione. Di seguito viene fornito l'esempio di una tipica estensione di comportamento.  
  
```xml  
<system.serviceModel>
  <extensions>
    <behaviorExtensions>
      <add name="myBehavior"
           type="Microsoft.ServiceModel.Samples.MyBehaviorSection, MyBehavior,
                 Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
    </behaviorExtensions>
  </extensions>
</system.serviceModel>
```  
  
 Per aggiungere capacità di configurazione all'elemento è necessario scrivere e registrare un elemento di configurazione. Per altre informazioni a tal proposito, vedere la documentazione di <xref:System.Configuration>.  
  
 Dopo che l'elemento e il relativo tipo di configurazione sono stati definiti, è possibile usare l'estensione come illustrato nell'esempio seguente.  
  
```xml  
<behaviors>
  <behavior configurationName="testChannelBehavior">
    <myBehavior />
    <channelSecurity cacheCookies="false"
                     detectReplays="false"
                     maxCachedNonces="9"
                     maxClockSkew="00:00:03"
                     maxCookieCachingTime="00:07:24"
                     replayWindow="00:07:22.2190000" />
  </behavior>
</behaviors>
```  
  
## <a name="security"></a>Security  
 È consigliato fortemente l'uso di nomi di assembly completi per la registrazione di tipi nei file `machine.config` e `app.config`. Se il tipo non è definito in modo univoco, il caricatore dei tipi CLR lo cerca nei percorsi seguenti nell'ordine specificato:  
  
 Se l'assembly del tipo è conosciuto, il caricatore esegue una ricerca nei percorsi di reindirizzamento del file di configurazione, in GAC, nell'assembly corrente usando le informazioni di configurazione e la directory base dell'applicazione. Se l'assembly è sconosciuto, il caricatore esegue una ricerca nell'assembly corrente, in mscorlib e nel percorso restituito dal gestore eventi `TypeResolve`. Questo ordine di ricerca CLR può essere modificato con hook quali il meccanismo di inoltro dei tipi e l'evento AppDomain.TypeResolve.  
  
 Un autore di un attacco può sfruttare l'ordine di ricerca CLR ed eseguire codice non autorizzato. L'uso di nomi univoci completi (sicuri) identifica un tipo e aumenta ulteriormente la sicurezza del sistema.  
  
 Per ulteriori informazioni, vedere [come il runtime individua gli assembly](https://go.microsoft.com/fwlink/?LinkId=95336) e <xref:System.AppDomain.TypeResolve>.  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>
- [Configurazione ed estensione del runtime con i comportamenti](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
