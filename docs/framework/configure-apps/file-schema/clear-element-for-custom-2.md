---
title: elemento <clear> per NameValueSectionHandler e DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fff5a5c2a523480f2eaebb127ec98ff6e9908acf
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088706"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<elemento clear > per NameValueSectionHandler e DictionarySectionHandler

Cancella tutte le impostazioni definite in precedenza in una sezione.

[ **\<configuration>** ](configuration-element.md)\
&nbsp;&nbsp;[ **\<sectionname >** ](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<cancella >**

## <a name="syntax"></a>Sintassi

```xml
<clear />
```

## <a name="attributes"></a>Attributi

Nessuno

## <a name="parent-element"></a>Elemento padre

|     | Descrizione |
| --- | ------------|
| [ **\<sectionname >** Elemento](custom-element-2.md) | Definisce le impostazioni per le sezioni di configurazione personalizzate che usano le classi <xref:System.Configuration.NameValueSectionHandler> e <xref:System.Configuration.DictionarySectionHandler>. |

## <a name="child-elements"></a>Elementi figlio

Nessuno

## <a name="remarks"></a>Note

È possibile utilizzare l'elemento **\<clear >** per rimuovere tutte le impostazioni dall'applicazione definite a un livello superiore nella gerarchia dei file di configurazione.

## <a name="example"></a>Esempio

Questo esempio definisce un file di configurazione del computer e un file di configurazione dell'applicazione e Mostra come usare l'elemento **\<clear >** in un file di configurazione dell'applicazione per cancellare le sezioni definite in precedenza nel file di configurazione del computer.

Il seguente codice del file di configurazione del computer dichiara la sezione **\<sezione >** :

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
  </configSections>
  <mySection>
    <add key="key1" value="value1" />
    <add key="key2" value="value2" />
  </mySection>
</configuration>
```

Il codice del file di configurazione dell'applicazione seguente consente di rimuovere tutte le impostazioni da **\<> sezione**. L'applicazione non è in grado di recuperare le impostazioni dichiarate nella sezione **\<sezione >** del file di configurazione del computer.

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a>File di configurazione

Questo elemento può essere utilizzato nel file di configurazione dell'applicazione, nel file di configurazione del computer (*Machine. config*) e nei file *Web. config* che non sono a livello di directory dell'applicazione.

## <a name="see-also"></a>Vedere anche

- [Schema del file di configurazione per il .NET Framework](index.md)
