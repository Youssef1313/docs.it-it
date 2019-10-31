---
title: Assembly ritirabili per la generazione di tipi dinamici
description: ''
ms.date: 08/29/2017
helpviewer_keywords:
- reflection, dynamic assembly
- assemblies, collectible
- collectible assemblies, retrieving
ms.openlocfilehash: 85eacff22cf2e1c0b8c3d74a4971de035dfafbe4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130285"
---
# <a name="collectible-assemblies-for-dynamic-type-generation"></a>Assembly ritirabili per la generazione di tipi dinamici

Gli *assembly ritirabili* sono assembly dinamici che possono essere scaricati senza scaricare il dominio dell'applicazione in cui sono stati creati. È possibile recuperare tutta la memoria gestita e non gestita usata da un assembly ritirabile e dai tipi che contiene. Le informazioni quali il nome dell'assembly vengono rimosse dalle tabelle interne.

Per abilitare lo scaricamento, usare il flag <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndCollect?displayProperty=nameWithType> quando si crea un assembly dinamico. L'assembly è temporaneo (ovvero, non è possibile salvarlo) ed è soggetto alle limitazioni descritte nella sezione [Limitazioni per gli assembly ritirabili](#restrictions-on-collectible-assemblies). Quando si rilasciano tutti gli oggetti associati a un assembly ritirabile, Common Language Runtime (CLR) scarica automaticamente l'assembly. Da tutti gli altri punti di vista, gli assembly ritirabili vengono creati e usati nello stesso modo degli altri assembly dinamici.

## <a name="lifetime-of-collectible-assemblies"></a>Durata degli assembly ritirabili

La durata di un assembly ritirabile è determinata dall'esistenza di riferimenti ai tipi che contiene e agli oggetti creati da tali tipi. Common Language Runtime non scarica un assembly fino a quando esistono uno o più degli elementi seguenti (`T` è qualsiasi tipo definito nell'assembly): 

- Istanza di `T`.

- Un'istanza di una matrice di `T`.
 
- Un'istanza di un tipo generico con `T` come uno dei relativi argomenti di tipo. Sono incluse le raccolte generiche di `T`, anche se la raccolta è vuota.

- Un'istanza di <xref:System.Type> o di <xref:System.Reflection.Emit.TypeBuilder> che rappresenta `T`. 

   > [!IMPORTANT]
   > È necessario rilasciare tutti gli oggetti che rappresentano parti dell'assembly. Il <xref:System.Reflection.Emit.ModuleBuilder> che definisce `T` mantiene un riferimento a <xref:System.Reflection.Emit.TypeBuilder> e l'oggetto <xref:System.Reflection.Emit.AssemblyBuilder> mantiene un riferimento a <xref:System.Reflection.Emit.ModuleBuilder>, pertanto è necessario rilasciare i riferimenti a questi oggetti. Anche l'esistenza di un <xref:System.Reflection.Emit.LocalBuilder> o <xref:System.Reflection.Emit.ILGenerator> usato nella costruzione di `T` impedisce lo scaricamento.

- Un riferimento statico a `T` da un altro tipo definito in modo dinamico `T1` che è ancora raggiungibile mediante l'esecuzione del codice. Ad esempio, `T1` potrebbe derivare da `T` o `T` potrebbe essere il tipo di un parametro in un metodo di `T1`.
 
- **ByRef** a un campo statico appartenente a `T`.

- <xref:System.RuntimeTypeHandle>, <xref:System.RuntimeFieldHandle> o <xref:System.RuntimeMethodHandle> che fa riferimento a `T` o a un componente di `T`.

- Un'istanza di qualsiasi oggetto di reflection che può essere usato indirettamente o direttamente per accedere all'oggetto <xref:System.Type> che rappresenta `T`. Ad esempio, l'oggetto <xref:System.Type> per `T` può essere ottenuto da un tipo di matrice il cui tipo di elemento è `T` o da un tipo generico che ha `T` come argomento di tipo. 

- Un metodo `M` nello stack di chiamate di qualsiasi thread, in cui `M` è un metodo di `T` o un metodo a livello di modulo che viene definito nell'assembly.

- Un delegato a un metodo statico definito in un modulo dell'assembly.

Se esiste un solo elemento in questo elenco per un solo tipo o metodo nell'assembly, il runtime non è in grado di scaricare l'assembly.

> [!NOTE]
> Il runtime non scarica effettivamente l'assembly fino a quando non vengono eseguiti i finalizzatori per tutti gli elementi nell'elenco.

Per tener traccia della durata, si suppone che un tipo generico costruito, ad esempio `List<int>` (in C#) o `List(Of Integer)` (in Visual Basic), creato e usato nella generazione di un assembly ritirabile sia stato definito nell'assembly che contiene la definizione del tipo generico o in un assembly che contiene la definizione di uno dei relativi argomenti di tipo. L'assembly esatto usato è un dettaglio di implementazione e soggetto a modifiche.
 
## <a name="restrictions-on-collectible-assemblies"></a>Limitazioni degli assembly ritirabili

Agli assembly ritirabili si applicano le seguenti restrizioni: 

- **Riferimenti statici**   
  I tipi in un assembly dinamico comune non possono avere riferimenti statici a tipi definiti in un assembly ritirabile. Ad esempio, se si definisce un tipo comune che eredita da un tipo in un assembly ritirabile, viene generata un'eccezione <xref:System.NotSupportedException>. Un tipo in un assembly ritirabile può avere riferimenti statici a un tipo in un altro assembly ritirabile, ma estende la durata dell'assembly di destinazione del riferimento alla durata dell'assembly di origine del riferimento.

- **Interoperabilità COM**   
   Nessuna interfaccia COM può essere definita all'interno di un assembly ritirabile e nessuna istanza di tipi all'interno di un assembly ritirabile può essere convertita in oggetti COM. Un tipo in un assembly ritirabile non può fungere da COM Callable Wrapper (CCW) o da Runtime Callable Wrapper (RCW). Tuttavia, i tipi negli assembly ritirabili possono usare oggetti che implementano interfacce COM.

- **Platform invoke**   
   I metodi con l'attributo <xref:System.Runtime.InteropServices.DllImportAttribute> non verranno compilati quando vengono dichiarati in un assembly ritirabile. Non è possibile usare l'istruzione <xref:System.Reflection.Emit.OpCodes.Calli?displayProperty=nameWithType> nell'implementazione di un tipo in un assembly ritirabile e non è possibile eseguire il marshalling di tali tipi in codice non gestito. È comunque possibile effettuare chiamate nel codice nativo tramite un punto di ingresso dichiarato in un assembly non ritirabile.
 
- **Marshalling**   
   Gli oggetti, in particolare i delegati, definiti in assembly ritirabili non possono essere sottoposti a marshalling. Si tratta di una restrizione per tutti i tipi creati temporanei.

- **Caricamento degli assembly**   
   La reflection emit è l'unico meccanismo supportato per il caricamento degli assembly ritirabili. Gli assembly caricati con qualsiasi altra forma di caricamento non possono essere scaricati.
 
- **Oggetti legati al contesto**    
   Le variabili statiche a livello di contesto non sono supportate. Non è possibile estendere i tipi in un assembly ritirabile <xref:System.ContextBoundObject>. Tuttavia, il codice negli assembly ritirabili può usare oggetti associati al contesto definiti altrove.

- **Dati statici a livello di thread**       
   Le variabili statiche a livello di thread non sono supportate.

## <a name="see-also"></a>Vedere anche

- [Creazione di assembly e metodi dinamici](emitting-dynamic-methods-and-assemblies.md)
