---
title: <compilers> Elemento
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compilers
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers
helpviewer_keywords:
- compiler configuration elements, <compilers> element
- <compilers> element
- compilers element
ms.assetid: d40fba59-98f9-4783-ae0c-2ebea27ce77b
ms.openlocfilehash: b09c2a1f67974a67a3f9d58af7cb8cf66a197026
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088691"
---
# <a name="compilers-element"></a>\<> elemento compilatori
Contenitore per gli elementi di configurazione del compilatore. Contiene zero o più [elementi \<compiler>](compiler-element.md).  

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. codedom >** ](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp; **\<&nbsp;compilatori** >

## <a name="syntax"></a>Sintassi  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
 Nessuna.  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[\<compiler> Element](compiler-element.md) (Elemento <compiler>)|Specifica gli attributi di configurazione del compilatore per un provider del linguaggio.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento \<configuration>](../configuration-element.md)|Elemento radice in ciascun file di configurazione usato in Common Language Runtime e nelle applicazioni .NET Framework.|  
|[Elemento \<System. CodeDom >](system-codedom-element.md)|Specifica le impostazioni di configurazione del compilatore per i provider di linguaggi disponibili.|  
  
## <a name="remarks"></a>Note  
 L'elemento [\<compilatori](compilers-element.md) contiene le impostazioni di configurazione del compilatore per i provider di linguaggio in un computer. Ogni elemento [\<> del compilatore](compiler-element.md) specifica gli attributi di configurazione del compilatore per un provider di linguaggio specifico.  
  
 Il .NET Framework definisce le impostazioni iniziali del compilatore e del provider del linguaggio nel file di configurazione del computer (Machine. config). Gli sviluppatori e i fornitori di compilatori possono aggiungere impostazioni di configurazione per una nuova implementazione di <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>. Usare il metodo <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> per enumerare a livello di codice le impostazioni di configurazione dei provider di linguaggi e di configurazione del compilatore in un computer.  
  
## <a name="configuration-file"></a>File di configurazione  
 Questo elemento può essere utilizzato nel file di configurazione del computer e nel file di configurazione dell'applicazione.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra un elemento di configurazione del compilatore tipico.  
  
```xml  
<configuration>  
   <system.codedom>  
     <compilers>  
       <!-- zero or more compiler elements -->  
       <compiler   
          language="c#;cs;csharp"   
          extension=".cs"  
          type="Microsoft.CSharp.CSharpCodeProvider, System, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
          compilerOptions=""    
          warningLevel="1" />  
     </compilers>  
   </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [Schema dei file di configurazione](../index.md)
- [Schema di impostazioni del compilatore e del provider di linguaggi](index.md)
- [\<compiler> Element](compiler-element.md) (Elemento <compiler>)
