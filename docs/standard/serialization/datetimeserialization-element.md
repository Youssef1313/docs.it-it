---
title: <dateTimeSerialization> Elemento
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: 180a4942dd4b701b56fe4788d5f8cd8607faaedd
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459270"
---
# <a name="datetimeserialization-element"></a>\<elemento > dateTimeSerialization
Determina la modalità di serializzazione degli oggetti <xref:System.DateTime>.  
  
 \<configuration>  
\<dateTimeSerialization>  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip|Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributi|Descrizione|  
|----------------|-----------------|  
|`mode`|Parametro facoltativo. Specifica la modalità di serializzazione. Impostarlo a uno dei valori di <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>. Il valore predefinito è **RoundTrip**.|  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuna.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|system.xml.serialization|L'elemento di primo livello per il controllo della serializzazione XML.|  
  
## <a name="remarks"></a>Note  
 Nelle versioni 1.0, 1.1, 2.0 e successive di .NET Framework, se la proprietà è impostata su **Local**, gli oggetti <xref:System.DateTime> vengono sempre formattati come ora locale. Vale a dire che le informazioni relative al fuso orario locale vengono sempre incluse tra dati serializzati. Impostare questa proprietà su **Local** per garantire la compatibilità con le versioni precedenti di .NET Framework.  
  
 Nella versione 2.0 e nelle versioni successive di .NET Framework in cui la proprietà è impostata su **Roundtrip**, gli oggetti <xref:System.DateTime> vengono esaminati in modo da determinare se si trovano nel fuso orario locale, nel fuso orario UTC o in un fuso orario non specificato. Gli oggetti <xref:System.DateTime> vengono quindi serializzati in modo tale che tali informazioni vengano preservate. Si tratta del comportamento predefinito, consigliato per tutte le nuove applicazioni che non comunicano con le versioni precedenti del framework.  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [Schema dei file di configurazione](../../../docs/framework/configure-apps/file-schema/index.md)
- [Elemento \<schemaImporterExtensions>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [\<aggiungere > elemento per \<schemaImporterExtensions >](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [Elemento \<system.xml.serialization>](../../../docs/standard/serialization/system-xml-serialization-element.md)
