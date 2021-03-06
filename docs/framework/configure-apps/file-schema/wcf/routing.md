---
title: <routing>
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: fcf2d4eec93fd7127c6f800e1c739ad1fac49203
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399970"
---
# <a name="routing"></a>\<routing>

Rappresenta una sezione di configurazione per la definizione di un set di filtri di routing che determinano il tipo di <xref:System.ServiceModel.Dispatcher.MessageFilter> Windows Communication Foundation (WCF) da utilizzare durante la valutazione di messaggi in arrivo, nonché di tabelle di routing che definiscono gli endpoint di destinazione Invia messaggi a quando viene individuato un filtro.

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<> di routing**
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<system.serviceModel>
  <routing>
    <filters>
      <filter customType="String"
              filterData="String"
              filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"
              name="String" />
    </filters>
    <routingTables>
      <table name="String">
        <entries>
          <add endpoint="String"
               filterName="String"
               priority="Integer" />
        </entries>
      </table>
    </routingTables>
  </routing>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

Nessuna

### <a name="child-elements"></a>Elementi figlio

|     | Descrizione |
| --- | ----------- |
| [ **\<Filtra >** ](filters-of-routing.md) | Contiene un set di filtri di routing che determinano il tipo di Windows Communication Foundation (WCF) MessageFilter verrà usato durante la valutazione di messaggi in arrivo. |
| [ **\<filterTables>** ](filtertables.md) | Contiene i mapping tra i filtri di routing e gli endpoint di destinazione per la specifica dell'endpoint da usare quando viene trovata una corrispondenza di filtro. |

### <a name="parent-elements"></a>Elementi padre

|     | Descrizione |
| --- | ----------- |
| **\<system.ServiceModel>** | Elemento radice di tutti gli elementi di configurazione WCF. |

## <a name="see-also"></a>Vedere anche

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
