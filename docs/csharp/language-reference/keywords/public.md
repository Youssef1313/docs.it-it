---
title: Parola chiave public - Riferimenti per C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: dfb6e341ea0740225d7600f07af2813d39141b45
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422549"
---
# <a name="public-c-reference"></a>public (Riferimenti per C#)

La parola chiave `public` è un modificatore di accesso per tipi e membri dei tipi. L'accesso pubblico è il livello di accesso più permissivo. Non esistono restrizioni per i membri dell'accesso pubblico, come nel seguente esempio:

```csharp
class SampleClass
{
    public int x; // No access restrictions.
}
```

Per altre informazioni, vedere [Modificatori di accesso](../../programming-guide/classes-and-structs/access-modifiers.md) e [Livelli di accessibilità](accessibility-levels.md).

## <a name="example"></a>Esempio

Nell'esempio seguente vengono dichiarate due classi, `PointTest` e `MainClass`. I membri pubblici `x` e `y` di `PointTest` sono accessibili direttamente da `MainClass`.

[!code-csharp[csrefKeywordsModifiers#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#13)]

Se si modifica il livello di accesso `public` impostandolo su [private](private.md) o [protected](protected.md), viene visualizzato un messaggio di errore che

indica che PointTest.y è inaccessibile a causa del livello di protezione.

## <a name="c-language-specification"></a>Specifiche del linguaggio C#  

Per altre informazioni, vedere [Accessibilità dichiarata](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in [Specifica del linguaggio C#](/dotnet/csharp/language-reference/language-specification/introduction). La specifica del linguaggio costituisce il riferimento ufficiale principale per la sintassi e l'uso di C#.

## <a name="see-also"></a>Vedere anche

- [Riferimenti per C#](../index.md)
- [Guida per programmatori C#](../../programming-guide/index.md)
- [Modificatori di accesso](../../programming-guide/classes-and-structs/access-modifiers.md)
- [Parole chiave di C#](index.md)
- [Modificatori di accesso](access-modifiers.md)
- [Livelli di accessibilità](accessibility-levels.md)
- [Modificatori](index.md)
- [private](private.md)
- [protected](protected.md)
- [internal](internal.md)
