---
title: Schema delle impostazioni di crittografia
ms.date: 03/30/2017
helpviewer_keywords:
- configuration schema [.NET Framework], cryptography
- elements [.NET Framework], cryptography
- schema configuration settings
- cryptography, settings schema
- cryptography, mapping algorithm names
- configuration sections [.NET Framework]
- configuration settings [.NET Framework], cryptography
ms.assetid: 1f55050a-b2a3-4868-a3c0-da20826150f3
ms.openlocfilehash: c632a15552c8ba5743aac1309098b7d7ef949bbd
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087999"
---
# <a name="cryptography-settings-schema"></a>Schema delle impostazioni di crittografia
Lo schema delle impostazioni di crittografia contiene gli elementi che specificano come eseguire il mapping dei nomi descrittivi degli algoritmi alle classi che implementano gli algoritmi di crittografia.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptographySettings**](cryptographysettings-element.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**cryptoNameMapping**](cryptonamemapping-element.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptoClasses**](cryptoclasses-element.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<CryptoClass**](cryptoclass-element.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<nameEntry**](nameentry-element.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**oidMap**](oidmap-element.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<oidEntry** >](oidentry-element.md)

|Elemento|Descrizione|  
|-------------|-----------------|  
|[ **\<cryptoClasses**>](cryptoclasses-element.md)|Contiene un elenco delle classi di crittografia per le quali è stato eseguito il mapping a un nome descrittivo nell'elemento **\<nameEntry>** .|  
|[ **\<cryptoClass**>](cryptoclass-element.md)|Contiene una classe di crittografia per la quale è stato eseguito il mapping a un nome descrittivo nell'elemento **\<nameEntry>** .|  
|[ **\<cryptographySettings**>](cryptographysettings-element.md)|Contiene le impostazioni di crittografia.|  
|[ **\<cryptoNameMapping**>](cryptonamemapping-element.md)|Contiene i mapping di classi e nomi descrittivi.|  
|[**Elemento \<mscorlib>** per le impostazioni di crittografia](mscorlib-element-for-cryptography-settings.md)|Contiene l'elemento **\<cryptographySettings>** .|  
|[ **\<nameEntry>** ](nameentry-element.md)|Esegue il mapping di un nome di classe a un nome di algoritmo descrittivo, in modo da poter associare più nomi descrittivi a una classe.|  
|[ **\<oidEntry>** ](oidentry-element.md)|Esegue il mapping di un identificatore di oggetto (OID) ASN.1 a un nome descrittivo.|  
|[ **\<oidMap>** ](oidmap-element.md)|Contiene i mapping di OID ASN.1 e classi.|  
  
## <a name="see-also"></a>Vedere anche

- [Schema dei file di configurazione](../index.md)
- [Servizi di crittografia](../../../../standard/security/cryptographic-services.md)
