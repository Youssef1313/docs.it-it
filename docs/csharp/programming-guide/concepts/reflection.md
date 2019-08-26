---
title: Reflection (C#)
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: 9b4322d83ad43cd3e49647df49c15bb5c917e1be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924096"
---
# <a name="reflection-c"></a>Reflection (C#)
La reflection specifica oggetti di tipo <xref:System.Type> che descrivono assembly, moduli e tipi. È possibile usare la reflection per creare in modo dinamico un'istanza di un tipo, associare il tipo a un oggetto esistente oppure ottenere il tipo da un oggetto esistente e richiamarne i metodi o accedere ai relativi campi e proprietà. Se si usano attributi nel codice, la reflection consente di accedervi. Per altre informazioni, vedere [Attributi](../../../standard/attributes/index.md).  
  
 Di seguito è riportato un esempio semplice di reflection che usa il metodo statico `GetType` ereditato da tutti i tipi dalla classe di base `Object` per ottenere il tipo di una variabile:  
  
```csharp  
// Using GetType to obtain type information:  
int i = 42;  
System.Type type = i.GetType();  
System.Console.WriteLine(type);  
```  
  
 L'output è:  
  
 `System.Int32`  
  
 L'esempio seguente usa la reflection per ottenere il nome completo dell'assembly caricato.  
  
```csharp  
// Using Reflection to get information of an Assembly:  
System.Reflection.Assembly info = typeof(System.Int32).Assembly;  
System.Console.WriteLine(info);  
```  
  
 L'output è:  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
> [!NOTE]
> Le parole chiave di C# `protected` e `internal` non hanno significato in IL e non sono usate nelle API di reflection. I termini corrispondenti in IL sono *Famiglia* e *Assembly*. Per identificare un metodo `internal` tramite reflection, usare la proprietà <xref:System.Reflection.MethodBase.IsAssembly%2A>. Per identificare un metodo `protected internal`, usare <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.  
  
## <a name="reflection-overview"></a>Panoramica della reflection  
 La reflection è utile nelle situazioni seguenti:  
  
- Quando è necessario accedere agli attributi nei metadati del programma. Per altre informazioni, vedere [Recupero di informazioni memorizzate negli attributi](../../../standard/attributes/retrieving-information-stored-in-attributes.md).  
  
- Per esaminare e creare istanze di tipi in un assembly.  
  
- Per creare nuovi tipi in fase di esecuzione. Usare le classi in <xref:System.Reflection.Emit>.  
  
- Per eseguire l'associazione tardiva, accedere ai metodi per i tipi creati in fase di esecuzione. Vedere l'argomento relativo a [caricamento e uso dinamico dei tipi](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).  
  
## <a name="related-sections"></a>Sezioni correlate  
 Per ulteriori informazioni:  
  
- [Reflection](../../../framework/reflection-and-codedom/reflection.md)  
  
- [Visualizzazione delle informazioni sul tipo](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
- [Reflection e tipi generici](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
- <xref:System.Reflection.Emit>  
  
- [Recupero di informazioni memorizzate negli attributi](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a>Vedere anche

- [Guida per programmatori C#](../index.md)
- [Assembly in Common Language Runtime](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md)
