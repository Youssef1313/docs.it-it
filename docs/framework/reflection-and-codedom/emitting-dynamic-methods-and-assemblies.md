---
title: Creazione di assembly e metodi dinamici
ms.date: 08/30/2017
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
ms.openlocfilehash: 578851bed188921324e3c25e533b3466068dee3d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446791"
---
# <a name="emitting-dynamic-methods-and-assemblies"></a>Creazione di assembly e metodi dinamici

Questa sezione descrive un insieme di tipi gestiti dello spazio dei nomi <xref:System.Reflection.Emit> che consentono la creazione di metadati e codice MSIL (Microsoft Intermediate Language) da parte di compilatori o strumenti in fase di esecuzione ed eventualmente la generazione su disco di un file eseguibile portabile (PE, Portable Executable). Questo spazio dei nomi viene usato principalmente da moduli di gestione di script e compilatori. In questa sezione si farà riferimento alle funzionalità fornite dallo spazio dei nomi <xref:System.Reflection.Emit> con l'espressione reflection emit (creazione tramite la reflection).  
  
La reflection emit offre le funzionalità seguenti:  
  
- Definizione di metodi globali di tipo lightweight in fase di esecuzione mediante la classe <xref:System.Reflection.Emit.DynamicMethod> ed esecuzione di tali metodi mediante delegati.  
  
- Definizione di assembly in fase di esecuzione, quindi esecuzione e/o salvataggio di tali assembly su disco.  
  
- Definizione di assembly in fase di esecuzione, quindi esecuzione e scaricamento per consentire al processo di Garbage Collection di recuperare le risorse.  
  
- Definizione di moduli in nuovi assembly in fase di esecuzione, quindi esecuzione e/o salvataggio di tali assembly su disco.  
  
- Definizione di tipi in moduli in fase di esecuzione, creazione di istanze di tali tipi e chiamate ai relativi metodi.  
  
- Definizione di informazioni relative ai simboli per i moduli definiti, che possono essere usate da strumenti quali debugger e analizzatori di codice.  
  
Oltre ai tipi gestiti dello spazio dei nomi <xref:System.Reflection.Emit>, sono disponibili interfacce di metadati non gestite, descritte nella documentazione di riferimento per le [interfacce di metadati](../unmanaged-api/metadata/metadata-interfaces.md). La reflection emit gestita garantisce un controllo degli errori semantici più completo e un livello di astrazione dei metadati più alto rispetto alle interfacce di metadati non gestite.  
  
Un'altra risorsa per l'uso di metadati e codice MSIL è la documentazione CLI (Common Language Infrastructure), in particolare la seconda e la terza parte, relative rispettivamente alla semantica e alla definizione dei metadati e all'insieme di istruzioni. La documentazione è disponibile online nel [sito Web ECMA](https://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
## <a name="in-this-section"></a>Contenuto della sezione
  
[Problemi di sicurezza nella reflection emit](security-issues-in-reflection-emit.md)  
Descrive i problemi di sicurezza relativi alla creazione di assembly dinamici mediante la reflection emit.  

[Procedura: Definire ed eseguire metodi dinamici](how-to-define-and-execute-dynamic-methods.md)   
Mostra come eseguire un metodo dinamico semplice e un metodo dinamico associato a un'istanza di una classe.

[Procedura: Definire un tipo generico tramite reflection emit](how-to-define-a-generic-type-with-reflection-emit.md)   
Illustra come creare un tipo generico semplice con due parametri di tipo, come applicare vincoli di classe, di interfaccia e speciali ai parametri di tipo e come creare membri che usano i parametri di tipo della classe come tipi di parametro o tipi restituiti.

[Procedura: Definire un metodo generico tramite reflection emit](how-to-define-a-generic-method-with-reflection-emit.md)   
Illustra le procedure di creazione, emit e richiamo di un metodo generico semplice.

[Assembly ritirabili per la generazione di tipi dinamici](collectible-assemblies.md)   
Offre un'introduzione degli assembly ritirabili, ovvero assembly dinamici che possono essere scaricati senza scaricare il dominio dell'applicazione in cui sono stati creati.
  
## <a name="reference"></a>Riferimenti  

<xref:System.Reflection.Emit.OpCodes>  
Cataloga i codici di istruzioni MSIL che è possibile usare per compilare i corpi dei metodi.  
  
<xref:System.Reflection.Emit>  
Contiene le classi gestite usate per creare metodi, assembly e tipi dinamici.  
  
<xref:System.Type>  
Illustra la classe <xref:System.Type>, che rappresenta i tipi nella reflection gestita e nella reflection emit, e descrive i concetti fondamentali relativi all'uso di queste tecnologie.  
  
<xref:System.Reflection>  
Contiene le classi gestite usate per esaminare i metadati e il codice gestito.  
  
## <a name="related-sections"></a>Sezioni correlate  

[Reflection](reflection.md)  
Illustra come esaminare i metadati e il codice gestito.  
  
[Assembly in .NET](../../standard/assembly/index.md)  
Fornisce una panoramica degli assembly nelle implementazioni .NET.
