---
title: Parola chiave protected - Riferimenti per C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: a0420dd10d81c4ae893ab0447244a611091ed7b0
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/19/2019
ms.locfileid: "69601969"
---
# <a name="protected-c-reference"></a>protected (Riferimenti per C#)

La parola chiave `protected` è un modificatore di accesso ai membri.

 > Questa pagina illustra l'accesso `protected`. La parola chiave `protected` fa anche parte dei modificatori di accesso [`protected internal`](protected-internal.md) e [`private protected`](private-protected.md).

Un membro protetto è accessibile all'interno della classe di appartenenza e dalle istanze della classe derivata.

Per un confronto di `protected` con altri modificatori di accesso, vedere [Livelli di accessibilità](accessibility-levels.md).

## <a name="example"></a>Esempio

Un membro protetto di una classe di base è accessibile in una classe derivata solo se viene eseguito l'accesso tramite il tipo di classe derivata. Si consideri il segmento di codice di esempio seguente:

[!code-csharp[csrefKeywordsModifiers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#11)]

L'istruzione `a.x = 10` genera un errore perché usata all'interno del metodo statico Main e non in un'istanza della classe B.

I membri struct non possono essere protetti perché struct non può essere ereditato.

## <a name="example"></a>Esempio

In questo esempio la classe `DerivedPoint` è derivata da `Point`. Pertanto, è possibile accedere i membri protetti della classe di base direttamente dalla classe derivata.

[!code-csharp[csrefKeywordsModifiers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#12)]  

Se si impostano i livelli di accesso di `x` e `y` su [privato](private.md), il compilatore genererà i messaggi di errore seguenti:

`'Point.y' is inaccessible due to its protection level.`

`'Point.x' is inaccessible due to its protection level.`

## <a name="c-language-specification"></a>Specifiche del linguaggio C#  

Per altre informazioni, vedere [Accessibilità dichiarata](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in [Specifica del linguaggio C#](../language-specification/index.md). La specifica del linguaggio costituisce il riferimento ufficiale principale per la sintassi e l'uso di C#.

## <a name="see-also"></a>Vedere anche

- [Riferimenti per C#](../index.md)
- [Guida per programmatori C#](../../programming-guide/index.md)
- [Parole chiave di C#](index.md)
- [Modificatori di accesso](access-modifiers.md)
- [Livelli di accessibilità](accessibility-levels.md)
- [Modificatori](modifiers.md)
- [public](public.md)
- [private](private.md)
- [internal](internal.md)
- [Problemi di sicurezza per le parole chiave virtuali interne](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))
