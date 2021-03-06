---
title: Operatore nameof - Riferimenti per C#
ms.custom: seodec18
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof operator [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: fa858db918cdaf04c757f2741265e359acb74f7b
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036344"
---
# <a name="nameof-operator-c-reference"></a>Operatore nameof (Riferimenti per C#)

L'operatore `nameof` ottiene il nome di una variabile, di un tipo o di un membro come costante stringa:

[!code-csharp-interactive[nameof operator](~/samples/csharp/language-reference/operators/NameOfOperator.cs#Examples)]

Come illustrato nell'esempio precedente, nel caso di un tipo e di uno spazio dei nomi, il nome prodotto in genere non è [completo](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).

L'operatore `nameof` viene valutato in fase di compilazione e non ha alcun effetto in fase di esecuzione.

È possibile usare l'operatore `nameof` per rendere più gestibile il codice per il controllo degli argomenti:

[!code-csharp[nameof and argument check](~/samples/csharp/language-reference/operators/NameOfOperator.cs#ExceptionMessage)]

L'operatore `nameof` è disponibile in C# 6 e versioni successive.

## <a name="c-language-specification"></a>Specifiche del linguaggio C#

Per altre informazioni, vedere la sezione [Espressioni Nameof](~/_csharplang/spec/expressions.md#nameof-expressions) in [Specifica del linguaggio C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Vedere anche

- [Riferimenti per C#](../index.md)
- [Operatori C#](index.md)
