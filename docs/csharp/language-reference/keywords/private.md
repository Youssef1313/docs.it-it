---
title: Parola chiave private - Riferimenti per C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: a20c0a6fd729c2fc34449167eb92cb774bc3b84e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602016"
---
# <a name="private-c-reference"></a>private (Riferimenti per C#)

La parola chiave `private` è un modificatore di accesso ai membri.

> Questa pagina illustra l'accesso `private`. La parola chiave `private` fa anche parte del modificatore di accesso [`private protected`](./private-protected.md).

L'accesso privato è il livello di accesso più restrittivo. I membri privati sono accessibili solo all'interno del corpo della classe o dello struct in cui sono stati dichiarati, come nell'esempio seguente:

```csharp
class Employee
{
    private int i;
    double d;   // private access by default
}
```

Anche i tipi annidati dello stesso corpo possono accedere ai membri privati.

Fare riferimento a un membro privato all'esterno della classe o dello struct in cui è stato dichiarato genera un errore in fase di compilazione.

Per un confronto di `private` con altri modificatori di accesso, vedere [Livelli di accessibilità](accessibility-levels.md) e [Modificatori di accesso](../../programming-guide/classes-and-structs/access-modifiers.md).

## <a name="example"></a>Esempio

In questo esempio la classe `Employee` contiene due membri dati privati, `name` e `salary`. Essendo privati, i membri risulteranno accessibili solo ai metodi di membro. I metodi pubblici `GetName` e `Salary` vengono aggiunti per consentire il controllo dell'accesso ai membri privati. È possibile accedere al membro `name` tramite un metodo pubblico e al membro `salary` tramite una proprietà pubblica di sola lettura. Per altre informazioni, vedere [Proprietà](../../programming-guide/classes-and-structs/properties.md).

[!code-csharp[csrefKeywordsModifiers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#10)]

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
- [protected](protected.md)
- [internal](internal.md)
