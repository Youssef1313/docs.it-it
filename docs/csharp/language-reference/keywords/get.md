---
title: get - Riferimenti per C#
ms.custom: seodec18
ms.date: 03/10/2017
f1_keywords:
- get_CSharpKeyword
- get
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
ms.openlocfilehash: 783814a575e95fc9deb5c9cdef235a5636f5f529
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602141"
---
# <a name="get-c-reference"></a>get (Riferimenti per C#)

La parola chiave `get` definisce un metodo *funzione di accesso* in una proprietà o indicizzatore che restituisce il valore della proprietà o l'elemento dell'indicizzatore. Per altre informazioni, vedere [Proprietà](../../programming-guide/classes-and-structs/properties.md), [Proprietà implementate automaticamente](../../programming-guide/classes-and-structs/auto-implemented-properties.md) e [Indicizzatori](../../programming-guide/indexers/index.md).  
  
L'esempio seguente definisce le funzioni di accesso `get` e `set` per una proprietà denominata `Seconds`. Usa il campo privato denominato `_seconds` per portare in secondo piano il valore della proprietà.  
 
 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
Spesso la funzione di accesso `get` è costituita da una singola istruzione che restituisce un valore, come nell'esempio precedente. A partire da C# 7.0, è possibile implementare la funzione di accesso `get` come membro con corpo di espressione. L'esempio seguente implementa entrambe le funzioni di accesso `get` e `set` come membri con corpo di espressione.

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]   
 
Per i casi semplici in cui le funzioni di accesso `get` e `set` di una proprietà non eseguono operazioni diverse dall'impostazione o recupero di un valore in un campo sottostante, è possibile sfruttare il supporto del compilatore C# per le proprietà implementate automaticamente. L'esempio seguente implementa `Hours` come una proprietà implementata automaticamente. 
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a>Specifiche del linguaggio C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Riferimenti per C#](../index.md)
- [Guida per programmatori C#](../../programming-guide/index.md)
- [Parole chiave di C#](./index.md)
- [Proprietà](../../programming-guide/classes-and-structs/properties.md)
