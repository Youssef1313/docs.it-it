---
title: Tabella dei valori predefiniti - Informazioni di riferimento per C#
ms.custom: seodec18
description: Informazioni sui valori predefiniti dei tipi C#.
ms.date: 07/29/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 48aa294fa9e37e2e138444e493faa5474011097e
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2019
ms.locfileid: "74551816"
---
# <a name="default-values-table-c-reference"></a>Tabella dei valori predefiniti (Informazioni di riferimento per C#)

La tabella seguente mostra i valori predefiniti dei tipi C#:

|Tipo di|Valore predefinito|
|---------|------------------|
|Qualsiasi tipo riferimento|`null`|
|Qualsiasi [tipo numerico integrale incorporato](../builtin-types/integral-numeric-types.md)|0 (zero)|
|Qualsiasi [tipo numerico a virgola mobile incorporato](../builtin-types/floating-point-numeric-types.md)|0 (zero)|
|[bool](../builtin-types/bool.md)|`false`|
|[char](../builtin-types/char.md)|`'\0'` (U+0000)|
|[enum](enum.md)|Valore prodotto dall'espressione `(E)0`, dove `E` è l'identificatore di enumerazione.|
|[struct](struct.md)|Valore prodotto impostando tutti i campi dei tipi valore sui rispettivi valori predefiniti e tutti i campi dei tipi riferimento su `null`.|
|Qualsiasi [tipo valore nullable](../builtin-types/nullable-value-types.md)|Un'istanza per la quale la proprietà <xref:System.Nullable%601.HasValue%2A> è `false` e la proprietà <xref:System.Nullable%601.Value%2A> non è definita. Il valore predefinito è noto anche come valore *null* di un tipo di valore Nullable.|

Usare l'[operatore predefinito](../operators/default.md) per produrre il valore predefinito di un tipo, come illustrato nell'esempio seguente:

```csharp
int a = default(int);
```

A partire da C# 7.1 è possibile usare il [ valore letterale `default`](../operators/default.md#default-literal) per inizializzare una variabile con il valore predefinito del relativo tipo:

```csharp
int a = default;
```

Per un tipo valore, anche il costruttore senza parametri implicito produce il valore predefinito del tipo, come mostrato nell'esempio seguente:

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

## <a name="c-language-specification"></a>Specifiche del linguaggio C#

Per altre informazioni, vedere le sezioni seguenti delle [specifiche del linguaggio C#](~/_csharplang/spec/introduction.md):

- [Valori predefiniti](~/_csharplang/spec/variables.md#default-values)
- [Costruttori predefiniti](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a>Vedere anche

- [Riferimenti per C#](../index.md)
- [Parole chiave C#](index.md)
- [Tabella dei tipi incorporati](built-in-types-table.md)
- [Costruttori](../../programming-guide/classes-and-structs/constructors.md)
