---
title: Elemento <add> per bypasslist (impostazioni di rete)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <bypasslist>, add element
- bypasslist, add element
- <add> element, bypasslist
- add element, bypasslist
ms.assetid: a0b86e28-86b4-4497-abe8-d5fd614c7926
ms.openlocfilehash: 1db0ba3b0a213de1175e6e0cee347753d2a413b7
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699606"
---
# <a name="add-element-for-bypasslist-network-settings"></a>\<aggiungere > elemento per l'elemento bypass (impostazioni di rete)
Aggiunge un indirizzo IP o un nome DNS all'elenco di bypass del proxy.  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<defaultProxy >** ](defaultproxy-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<di [ **bypass** >](bypasslist-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**aggiungi >**  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<add   
  address="regular expression"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Le sezioni seguenti descrivono gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|**Attributo**|**Descrizione**|  
|-------------------|---------------------|  
|**address**|Espressione regolare che descrive un indirizzo IP o un nome DNS.|  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|**Elemento**|**Descrizione**|  
|-----------------|---------------------|  
|[bypasslist](bypasslist-element-network-settings.md)|Fornisce un set di espressioni regolari che descrivono gli indirizzi che non utilizzano un proxy.|  
  
## <a name="remarks"></a>Osservazioni  
 L'elemento `add` inserisce le espressioni regolari che descrivono gli indirizzi IP o i nomi dei server DNS nell'elenco di indirizzi che ignorano un server proxy.  
  
 Il valore dell'attributo `address` deve essere un'espressione regolare che descrive un set di indirizzi IP o nomi host.  
  
 È necessario prestare attenzione quando si specifica un'espressione regolare per questo elemento. L'espressione regolare "[a-z] +\\. contoso\\. com" corrisponde a qualsiasi host nel dominio contoso.com, ma corrisponde anche a qualsiasi host nel dominio contoso.com.cpandl.com. Per trovare la corrispondenza con un solo host nel dominio contoso.com, usare un ancoraggio ("$"): "[a-z] +\\. contoso\\. com $".  
  
 Per ulteriori informazioni sulle espressioni regolari, vedere. [.NET Framework espressioni regolari](../../../../standard/base-types/regular-expressions.md).  
  
## <a name="configuration-files"></a>File di configurazione  
 Questo elemento può essere usato nel file di configurazione dell'applicazione o nel file di configurazione del computer (Machine.config).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente vengono aggiunti due indirizzi all'elenco di bypass. Il primo ignora il proxy per tutti i server nel dominio contoso.com. il secondo ignora il proxy per tutti i server il cui indirizzo IP inizia con 192,168.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [Schema delle impostazioni di rete](index.md)
