---
title: in (modificatore generico) - Riferimenti per C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.openlocfilehash: 0806169b9b1c3521dcf89f5ea0fa5aec188030c2
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422778"
---
# <a name="in-generic-modifier-c-reference"></a>in (Modificatore generico) (Riferimenti per C#)

Per i parametri di tipo generico, la parola chiave `in` specifica che il parametro di tipo è controvariante. È possibile usare la parola chiave `in` in interfacce e delegati generici.

La controvarianza consente di usare un tipo meno derivato di quello specificato dal parametro generico. Ciò consente la conversione implicita di classi che implementano interfacce controvarianti e la conversione implicita di tipi delegati. Nei parametri di tipo generico la covarianza e la controvarianza sono supportate per i tipi di riferimento, ma non per i tipi di valore.

Un tipo può essere dichiarato controvariante in un'interfaccia o in un delegato generico solo se definisce il tipo dei parametri di un metodo e non di un tipo restituito dal metodo. I parametri `In`, `ref` e `out` devono essere invarianti, ovvero non sono né covariante né controvariante.

Un'interfaccia che dispone di un parametro di tipo controvariante consente ai metodi di accettare argomenti di tipi meno derivati di quelli specificati dal parametro di tipo di interfaccia. Ad esempio, nell'interfaccia <xref:System.Collections.Generic.IComparer%601>, il tipo T è controvariante, è possibile assegnare un oggetto di tipo `IComparer<Person>` a un oggetto di tipo `IComparer<Employee>` senza usare alcun metodo di conversione speciale se `Employee` eredita `Person`.

A un delegato controvariante può essere assegnato un altro delegato dello stesso tipo, ma con un parametro di tipo generico meno derivato.

Per altre informazioni, vedere [Covarianza e controvarianza](../../programming-guide/concepts/covariance-contravariance/index.md).

## <a name="contravariant-generic-interface"></a>Interfaccia generica controvariante

L'esempio seguente illustra come dichiarare, estendere e implementare un'interfaccia generica controvariante. L'esempio descrive anche come usare la conversione implicita per le classi che implementano quest'interfaccia.

[!code-csharp[csVarianceKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#1)]

## <a name="contravariant-generic-delegate"></a>Delegato generico controvariante

L'esempio seguente illustra come dichiarare, creare un'istanza e chiamare un delegato generico controvariante. Illustra anche come convertire in modo implicito un tipo delegato.

[!code-csharp[csVarianceKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#2)]

## <a name="c-language-specification"></a>Specifiche del linguaggio C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Vedere anche

- [out](out-generic-modifier.md)
- [Covarianza e controvarianza](../../programming-guide/concepts/covariance-contravariance/index.md)
- [Modificatori](index.md)
