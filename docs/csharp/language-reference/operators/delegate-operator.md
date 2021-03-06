---
title: Operatore delegate - Riferimenti per C#
ms.date: 07/18/2019
helpviewer_keywords:
- delegate [C#]
- anonymous method [C#]
ms.openlocfilehash: 9a78faaccffa9e7d4bf2829d8dfa0fa62a788bba
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039035"
---
# <a name="delegate-operator-c-reference"></a>Operatore delegate (Riferimenti per C#)

L'operatore `delegate` crea un metodo anonimo che può essere convertito in un tipo delegato:

[!code-csharp-interactive[anonymous method](~/samples/csharp/language-reference/operators/DelegateOperator.cs#AnonymousMethod)]

> [!NOTE]
> A partire C# da 3, le espressioni lambda forniscono un modo più conciso ed espressivo per creare una funzione anonima. Usare l'[operatore =>](lambda-operator.md) per costruire un'espressione lambda:
>
> [!code-csharp-interactive[lambda expression](~/samples/csharp/language-reference/operators/DelegateOperator.cs#Lambda)]
>
> Per altre informazioni sulle funzionalità delle espressioni lambda, ad esempio l'acquisizione di variabili esterne, vedere [Espressioni lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md).

Quando si usa l'operatore `delegate`, è possibile omettere l'elenco di parametri. In tal caso, il metodo anonimo creato può essere convertito in un tipo delegato con qualsiasi elenco di parametri, come illustrato nell'esempio seguente:

[!code-csharp-interactive[no parameter list](~/samples/csharp/language-reference/operators/DelegateOperator.cs#WithoutParameterList)]

Questa è l'unica funzionalità di metodi anonimi non supportata dalle espressioni lambda. In tutti gli altri casi, un'espressione lambda è la modalità preferita per scrivere codice inline.

È anche possibile usare la parola chiave `delegate` per dichiarare un [tipo delegato](../builtin-types/reference-types.md#the-delegate-type).

## <a name="c-language-specification"></a>Specifiche del linguaggio C#

Per altre informazioni, vedere la sezione [Espressioni di funzioni anonime](~/_csharplang/spec/expressions.md#anonymous-function-expressions) della [specifica del linguaggio C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Vedere anche

- [Riferimenti per C#](../index.md)
- [Operatori C#](index.md)
- [= operatore >](lambda-operator.md)
