---
title: Elemento <appSettings> per <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6112d87afcca8b2f54508d03d3ea4c0781d7e475
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119276"
---
# <a name="appsettings-element-for-configuration"></a>\<elemento > appSettings per \<Configuration >

Contiene le impostazioni dell'applicazione personalizzata. Si tratta di una sezione di configurazione predefinita fornita dal .NET Framework.

[ **\<configuration>** ](../configuration-element.md)   
&nbsp;&nbsp; **\<appSettings>**

## <a name="syntax"></a>Sintassi

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a>Attributo

|           | description |
| --------- | ----------- |
| **file**  | Attributo facoltativo.<br><br>Specifica un percorso relativo di un file esterno contenente le impostazioni di configurazione dell'applicazione personalizzate. Il file specificato contiene lo stesso tipo di impostazioni specificato nell' **\<aggiungere >** , **\<rimuovere >** e **\<deselezionare** gli elementi > e usa lo stesso formato di coppia chiave/valore di tali elementi.<br><br>Il percorso specificato è relativo al file di configurazione principale. Per un Windows Forms Application, si tratta della cartella binaria (ad esempio */bin/debug verranno incluse*), non del percorso del file di configurazione dell'applicazione. Per le applicazioni Web Form, il percorso è relativo alla radice dell'applicazione, in cui si trova il file *Web. config* .<br><br>Si noti che il runtime ignora l'attributo se non è possibile trovare il file specificato. |

## <a name="parent-element"></a>Elemento padre

|     | description |
| --- | ----------- |
| [ **> di configurazione\<** Elemento](../configuration-element.md) | Elemento radice in ciascun file di configurazione usato in Common Language Runtime e nelle applicazioni .NET Framework. |

## <a name="child-elements"></a>Elemento figlio

|     | description |
| --- | ----------- |
| [ **\<add>** ](add-element-for-appsettings.md) | Aggiunge un'impostazione dell'applicazione personalizzata. |
| [ **\<clear>** ](clear-element-for-appsettings.md) | Cancella tutte le impostazioni dell'applicazione definite in precedenza. |
| [ **\<remove>** ](remove-element-for-appsettings.md) | Rimuove un'impostazione dell'applicazione definita in precedenza. |

## <a name="remarks"></a>Osservazioni

L'elemento **\<appSettings >** archivia informazioni di configurazione dell'applicazione personalizzate, ad esempio stringhe di connessione del database, percorsi di file, URL di servizi Web XML o qualsiasi altra informazione di configurazione personalizzata per un'applicazione. Le coppie chiave/valore specificate nell'elemento **\<appSettings >** sono accessibili nel codice usando la classe <xref:System.Configuration.ConfigurationSettings>.

È possibile usare l'attributo **file** nell'elemento **\<appSettings >** dei file di configurazione *Web. config* e dell'applicazione. Questo attributo specifica un file di configurazione che fornisce impostazioni aggiuntive oppure esegue l'override delle impostazioni specificate nell'elemento **> di\<appSettings** . L'attributo **file** può essere utilizzato negli scenari di sviluppo del team del controllo del codice sorgente, ad esempio quando un utente desidera eseguire l'override delle impostazioni del progetto specificate in un file di configurazione dell'applicazione.

I file di configurazione specificati dall'attributo **file** devono avere un nodo radice di **\<appSettings >** piuttosto che **\<> di configurazione**.

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato un file di impostazioni dell'applicazione esterno (*custom.config*) che definisce un'impostazione personalizzata dell'applicazione:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

Nell'esempio seguente viene illustrato un file di configurazione dell'applicazione che usa l'impostazione nel file di impostazioni esterno e imposta un aspetto specifico dell'applicazione:

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a>File di configurazione

Questo elemento può essere utilizzato nel file di configurazione dell'applicazione, nel file di configurazione del computer (*Machine. config*) e nei file *Web. config* che non sono a livello di directory dell'applicazione.

## <a name="see-also"></a>Vedere anche

- [Schema del file di configurazione per il .NET Framework](../index.md)
