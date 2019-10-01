---
title: <trace> Elemento
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace
- http://schemas.microsoft.com/.NetConfiguration/v2.0#trace
helpviewer_keywords:
- <trace> element
- listeners
- trace element
- trace listener, <trace> element
ms.assetid: 7931c942-63c1-47c3-a045-9d9de3cacdbf
ms.openlocfilehash: 02fd794eb7b7b7f46f7f7bc4e43036cb4a4758ed
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699174"
---
# <a name="trace-element"></a>Elemento > \<trace
Contiene i listener che raccolgono, archiviano e indirizzano i messaggi di traccia.  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **\<system. diagnostics >** ](system-diagnostics-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<trace >**  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<trace autoflush="true|false"   
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`autoflush`|Attributo facoltativo.<br /><br /> Specifica se i listener di traccia scaricano automaticamente il buffer di output dopo ogni operazione di scrittura.|  
|`indentsize`|Attributo facoltativo.<br /><br /> Specifica il numero di spazi da rientrare.|  
|`useGlobalLock`|Attributo facoltativo.<br /><br /> Indica se deve essere utilizzato il blocco globale.|  
  
## <a name="autoflush-attribute"></a>AutoFlush (attributo)  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`false`|Non Scarica automaticamente il buffer di output. Questa è l'impostazione predefinita.|  
|`true`|Scarica automaticamente il buffer di output.|  
  
## <a name="usegloballock-attribute"></a>Attributo useGlobalLock  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`false`|Non utilizza il blocco globale se il listener è thread-safe. in caso contrario, utilizza il blocco globale.|  
|`true`|Usa il blocco globale indipendentemente dal fatto che il listener sia thread-safe. Questa è l'impostazione predefinita.|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[\<listeners>](listeners-element-for-trace.md)|Specifica un listener che raccoglie, archivia e instrada i messaggi.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|`configuration`|Elemento radice in ciascun file di configurazione usato in Common Language Runtime e nelle applicazioni .NET Framework.|  
|`system.diagnostics`|Specifica i listener di traccia per raccogliere, archiviare e indirizzare i messaggi, oltre al livello di impostazione di un'opzione di traccia.|  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare l'elemento `<trace>` per aggiungere il listener `MyListener` alla raccolta `Listeners`. `MyListener` crea un file denominato `MyListener.log` e scrive l'output nel file. L'attributo `useGlobalLock` è impostato su `false`, che impedisce l'utilizzo del blocco globale se il listener di traccia è thread-safe. L'attributo `autoflush` è impostato su `true`, che fa sì che il listener di traccia scriva nel file indipendentemente dal fatto che venga chiamato il metodo <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType>. L'attributo `indentsize` è impostato su 0 (zero), che fa sì che il listener rientri zero spazi quando viene chiamato il metodo <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType>.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace useGlobalLock="false" autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [Schema delle impostazioni di traccia e debug](index.md)
