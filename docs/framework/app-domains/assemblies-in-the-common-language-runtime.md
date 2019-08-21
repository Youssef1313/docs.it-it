---
title: Assembly in Common Language Runtime
ms.date: 03/30/2017
helpviewer_keywords:
- dynamic assemblies
- security [.NET Framework], boundaries
- boundaries of assemblies
- assemblies [.NET Framework], about
- assemblies [.NET Framework], boundaries
- reference scope boundaries
- assemblies [.NET Framework]
- version boundaries
- type boundaries
ms.assetid: 2cfebe19-7436-49f1-bd99-3c4019f0b676
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b27a8d89b0345082b8cf06c3eb141e73e2bf0faf
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567356"
---
# <a name="assemblies-in-the-common-language-runtime"></a>Assembly in Common Language Runtime
Gli assembly sono i blocchi costitutivi delle applicazioni .NET Framework. Costituiscono la base per la distribuzione, il controllo della versione, il riutilizzo, la definizione dell'ambito di attivazione e le autorizzazioni di sicurezza. Un assembly è una raccolta di tipi e risorse creati per essere usati insieme e per formare un'unità logica di funzionalità. Un assembly offre a Common Language Runtime le informazioni necessarie per il riconoscimento delle implementazioni di tipi. Per il runtime, un tipo non esiste all'esterno del contesto di un assembly.  
  
 Un assembly svolge le funzioni seguenti:  
  
- Include codice eseguito da Common Language Runtime. Il codice MSIL (Microsoft Intermediate Language) in un file eseguibile portabile sarà eseguito solo se dispone di un manifesto di assembly associato. Si noti che ogni assembly può avere solo un punto di ingresso, ovvero, `DllMain`, `WinMain` o `Main`.  
  
- Forma un limite di sicurezza. Un assembly è l'unità presso cui sono richieste e concesse le autorizzazioni. Per altre informazioni sui limiti di sicurezza e l'applicazione di questi agli assembly, vedere [Considerazioni sulla sicurezza degli assembly](../../../docs/framework/app-domains/assembly-security-considerations.md).  
  
- Forma un limite di tipi. L'identità di ogni tipo include il nome dell'assembly in cui risiede. Un tipo con nome `MyType` caricato nell'ambito di un assembly è diverso da un tipo con nome `MyType` caricato nell'ambito di un altro assembly.  
  
- Forma un limite dell'ambito dei riferimenti. Il manifesto dell'assembly contiene metadati dell'assembly usati per risolvere i tipi e soddisfare le richieste di risorse. Specifica i tipi e le risorse esposti all'esterno dell'assembly. Il manifesto enumera anche altri assembly da cui dipende.  
  
- Forma un limite delle versioni. L'assembly è l'unità più piccola di cui si possono creare versioni in Common Language Runtime. Tutti i tipi e tutte le risorse nello stesso assembly sono considerati come un'unità in caso di creazione di versioni. Il manifesto dell'assembly descrive le dipendenze delle versioni specificate per eventuali assembly dipendenti. Per altre informazioni sul controllo delle versioni, vedere [Controllo delle versioni degli assembly](../../../docs/framework/app-domains/assembly-versioning.md).  
  
- Forma un'unità di distribuzione. All'avvio di un'applicazione, devono essere presenti solo gli assembly chiamati inizialmente dall'applicazione. Gli altri assembly, ad esempio le risorse di localizzazione o gli assembly che contengono classi di utilità, possono essere recuperati su richiesta. Le applicazioni appena scaricate saranno quindi semplici e agili. Per altre informazioni sulla distribuzione di assembly, vedere [Distribuzione di applicazioni](../../../docs/framework/deployment/index.md).  
  
- Corrisponde all'unità in cui è supportata l'esecuzione side-by-side. Per altre informazioni sull'esecuzione di più versioni di un assembly, vedere [Assembly ed esecuzione side-by-side](../../../docs/framework/app-domains/assemblies-and-side-by-side-execution.md).  
  
 Gli assembly possono essere statici o dinamici. Gli assembly statici possono includere tipi di .NET Framework (interfacce e classi), oltre a risorse per l'assembly (bitmap, file JPEG, file di risorse e così via). Gli assembly statici sono archiviati su disco in file eseguibili portabili. È anche possibile usare .NET Framework per creare assembly dinamici, eseguiti direttamente dalla memoria e non salvati su disco prima dell'esecuzione. È possibile salvare gli assembly dinamici su disco dopo l'esecuzione.  
  
 Esistono diversi modi per creare assembly. È possibile usare gli strumenti di sviluppo, ad esempio Visual Studio, usati in precedenza per creare file con estensione dll o exe. Si possono usare gli strumenti disponibili in Windows SDK per creare assembly con i moduli creati in altri ambienti di sviluppo. Per creare assembly dinamici è anche possibile usare le API di Common Language Runtime come <xref:System.Reflection.Emit?displayProperty=nameWithType>.  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|DESCRIZIONE|  
|-----------|-----------------|  
|[Contenuto degli assembly](../../../docs/framework/app-domains/assembly-contents.md)|Descrive gli elementi che costituiscono un assembly.|  
|[Manifesto dell'assembly](../../../docs/framework/app-domains/assembly-manifest.md)|Descrive i dati nel manifesto dell'assembly e il modo in cui sono archiviati negli assembly.|  
|[Global Assembly Cache](../../../docs/framework/app-domains/gac.md)|Descrive la Global Assembly Cache e il relativo uso con gli assembly.|  
|[Assembly con nomi sicuri](../../../docs/framework/app-domains/strong-named-assemblies.md)|Descrive le caratteristiche degli assembly con nome sicuro.|  
|[Considerazioni sulla sicurezza degli assembly](../../../docs/framework/app-domains/assembly-security-considerations.md)|Illustra il funzionamento della sicurezza con gli assembly.|  
|[Controllo delle versioni degli assembly](../../../docs/framework/app-domains/assembly-versioning.md)|Offre una panoramica dei criteri di .NET Framework relativi al controllo delle versioni.|  
|[Ubicazione degli assembly](../../../docs/framework/app-domains/assembly-placement.md)|Indica dove posizionare gli assembly.|  
|[Assembly ed esecuzione side-by-side](../../../docs/framework/app-domains/assemblies-and-side-by-side-execution.md)|Offre una panoramica dell'uso contemporaneo di più versioni del runtime o di un assembly.|  
|[Programmazione con gli assembly](../../../docs/framework/app-domains/programming-with-assemblies.md)|Descrive come creare, firmare e impostare attributi sugli assembly.|  
|[Creazione di assembly e metodi dinamici](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)|Descrive come creare gli assembly dinamici.|  
|[Come il runtime individua gli assembly](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|Descrive il modo in cui .NET Framework risolve i riferimenti agli assembly in fase di esecuzione.|  
  
## <a name="reference"></a>Riferimenti  
 <xref:System.Reflection.Assembly?displayProperty=nameWithType>
