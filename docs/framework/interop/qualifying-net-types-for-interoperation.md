---
title: Qualificazione di tipi .NET per l'interoperabilità
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, qualifying .NET types
- qualifying .NET types for interoperation
- interoperation with unmanaged code, qualifying .NET types
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: 4b8afb52-fb8d-4e65-b47c-fd82956a3cdd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8b2e14a7508d4a5e8069a3b98dee38a0ac62750c
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363978"
---
# <a name="qualifying-net-types-for-interoperation"></a>Qualificazione di tipi .NET per l'interoperabilità
Se si vuole esporre i tipi contenuti in un assembly alle applicazioni COM, tenere presenti i requisiti di interoperabilità COM in fase di progettazione. Rispettando le linee guida seguenti, è possibile ottenere una facile integrazione tra i tipi gestiti (classi, interfacce, strutture ed enumerazioni) e i tipi COM:  
  
- Le classi devono implementare le interfacce in modo esplicito.  
  
     Anche se l'interoperabilità COM fornisce un meccanismo per generare automaticamente un'interfaccia contenente tutti i membri della classe e i membri della relativa classe di base, è decisamente preferibile fornire interfacce esplicite. L'interfaccia generata automaticamente è detta interfaccia di classe. Per informazioni, vedere [Introduzione all'interfaccia della classe](com-callable-wrapper.md#introducing-the-class-interface).  
  
     Per incorporare le definizioni di interfaccia nel codice, è possibile usare Visual Basic, C# e C++ invece del linguaggio di definizione dell'interfaccia (IDL, Interface Definition Language) o di soluzioni equivalenti. Per informazioni dettagliate sulla sintassi, vedere la documentazione relativa al linguaggio.  
  
- I tipi gestiti devono essere pubblici.  
  
     Solo i tipi pubblici di un assembly vengono registrati ed esportati nella libreria dei tipi. Di conseguenza, solo i tipi pubblici sono visibili in COM.  
  
     I tipi gestiti espongono ad altro codice gestito funzionalità che potrebbero non essere esposte a COM. Non vengono ad esempio esposti ai client COM i costruttori con parametri, i metodi statici e i campi costanti. Poiché inoltre il runtime esegue il marshalling dei dati in entrata e in uscita da un tipo, è possibile che i dati vengano copiati o trasformati.  
  
- Metodi, proprietà, campi ed eventi devono essere pubblici.  
  
     Anche i membri dei tipi pubblici devono essere pubblici per essere visibili in COM. È possibile limitare la visibilità di un assembly, di un tipo pubblico o dei membri pubblici di un tipo pubblico applicando l'oggetto <xref:System.Runtime.InteropServices.ComVisibleAttribute>. Per impostazione predefinita, tutti i membri e i tipi pubblici sono visibili.  
  
- I tipi devono avere un costruttore senza parametri pubblico per essere attivati da COM.  
  
     I tipi pubblici gestiti sono visibili in COM. Senza un costruttore senza parametri pubblico (un costruttore senza argomenti), tuttavia, i client COM non possono creare il tipo. I client COM possono comunque usare il tipo se viene attivato in un altro modo.  
  
- I tipi non possono essere astratti.  
  
     Né i client COM né i client .NET possono creare tipi astratti.  
  
 Quando si esegue l'esportazione in COM, la gerarchia di ereditarietà di un tipo gestito viene appiattita. Anche il controllo delle versioni varia tra ambiente gestito e ambiente non gestito. I tipi esposti a COM non hanno le stesse caratteristiche di controllo delle versioni degli altri tipi gestiti.  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.Runtime.InteropServices.ComVisibleAttribute>
- [Esposizione di componenti .NET Framework a COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)
- [Introduzione all'interfaccia della classe](com-callable-wrapper.md#introducing-the-class-interface)
- [Applicazione di attributi di interoperabilità](../../../docs/framework/interop/applying-interop-attributes.md)
- [Preparazione di un assembly per COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md)
