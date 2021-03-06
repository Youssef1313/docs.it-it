---
title: <qualifyAssembly> Elemento
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#qualifyAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/qualifyAssembly
helpviewer_keywords:
- container tags, <qualifyAssembly> element
- <qualifyAssembly> element
- qualifyAssembly element
ms.assetid: ad6442f6-1a9d-43b6-b733-04ac1b7f9b82
ms.openlocfilehash: 17cfe9fc39d65f146beef5d02c701f5e3e2fbbe1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115779"
---
# <a name="qualifyassembly-element"></a>\<elemento > qualifyAssembly
Specifica il nome completo dell'assembly da caricare in modo dinamico quando viene usato un nome parziale.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) \
&nbsp; &nbsp;[ **&nbsp; &nbsp; \<assemblyBinding > \** ](assemblybinding-element-for-runtime.md)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<qualifyAssembly** >  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`partialName`|Attributo obbligatorio.<br /><br /> Specifica il nome parziale dell'assembly come appare nel codice.|  
|`fullName`|Attributo obbligatorio.<br /><br /> Specifica il nome completo dell'assembly visualizzato nel Global Assembly Cache.|  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuna.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|`assemblyBinding`|Contiene le informazioni sul reindirizzamento della versione degli assembly e i relativi percorsi.|  
|`configuration`|Elemento radice in ciascun file di configurazione usato in Common Language Runtime e nelle applicazioni .NET Framework.|  
|`runtime`|Contiene informazioni sull'associazione degli assembly e sull'operazione di Garbage Collection.|  
  
## <a name="remarks"></a>Note  
 Quando si chiama il metodo <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> utilizzando nomi di assembly parziali, l'Common Language Runtime cerca l'assembly solo nella directory di base dell'applicazione. Usare l'elemento **\<qualifyAssembly >** nel file di configurazione dell'applicazione per fornire le informazioni complete sull'assembly (nome, versione, token di chiave pubblica e impostazioni cultura) e fare in modo che il Common Language Runtime cerchi l'assembly in Global Assembly Cache.  
  
 L'attributo **FullName** deve includere i quattro campi dell'identità dell'assembly: nome, versione, token di chiave pubblica e impostazioni cultura. L'attributo **parzialname** deve fare riferimento parzialmente a un assembly. È necessario specificare almeno il nome di testo dell'assembly (caso più comune), ma è anche possibile includere la versione, il token di chiave pubblica o le impostazioni cultura (o qualsiasi combinazione dei quattro, ma non tutti e quattro). Il parametro **partial** deve corrispondere al nome specificato nella chiamata. Non è possibile, ad esempio, specificare `"math"` come attributo **parzialname** nel file di configurazione e chiamare `Assembly.Load("math, Version=3.3.3.3")` nel codice.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene trasformato logicamente la chiamata `Assembly.Load("math")` in `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <qualifyAssembly partialName="math"   
                         fullName=  
"math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Vedere anche

- [Schema delle impostazioni di runtime](index.md)
- [Come il runtime individua gli assembly](../../../deployment/how-the-runtime-locates-assemblies.md)
- [Riferimenti a assembly parziali](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))
