---
title: Operatore NameOf-Visual Basic
description: Informazioni su come usare l'operatore NameOf in Visual Basic
ms.date: 10/27/2019
helpviewer_keywords:
- NameOf operator [Visual Basic]
ms.openlocfilehash: 8416bb1a1715c1c37b62cac6a9e0b427a9c72547
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/29/2019
ms.locfileid: "73041317"
---
# <a name="nameof-operator---visual-basic"></a><span data-ttu-id="2eed2-103">Operatore NameOf-Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2eed2-103">NameOf operator - Visual Basic</span></span>

<span data-ttu-id="2eed2-104">L'operatore `NameOf` ottiene il nome di una variabile, di un tipo o di un membro come costante stringa:</span><span class="sxs-lookup"><span data-stu-id="2eed2-104">The `NameOf` operator obtains the name of a variable, type, or member as the string constant:</span></span>

```vb
Console.WriteLine(NameOf(System.Collections.Generic))  ' output: Generic
Console.WriteLine(NameOf(List(Of Integer)))  ' output: List
Console.WriteLine(NameOf(List(Of Integer).Count))  ' output: Count
Console.WriteLine(NameOf(List(Of Integer).Add))  ' output: Add

Dim numbers As New List(Of Integer) From { 1, 2, 3 }
Console.WriteLine(NameOf(numbers))  ' output: numbers
Console.WriteLine(NameOf(numbers.Count))  ' output: Count
Console.WriteLine(NameOf(numbers.Add))  ' output: Add
```

<span data-ttu-id="2eed2-105">Come illustrato nell'esempio precedente, nel caso di un tipo e di uno spazio dei nomi, il nome prodotto in genere non è [completo](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span><span class="sxs-lookup"><span data-stu-id="2eed2-105">As the preceding example shows, in the case of a type and a namespace, the produced name is usually not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="2eed2-106">L'operatore `NameOf` viene valutato in fase di compilazione e non ha alcun effetto in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="2eed2-106">The `NameOf` operator is evaluated at compile time, and has no effect at run time.</span></span>

<span data-ttu-id="2eed2-107">È possibile usare l'operatore `NameOf` per rendere più gestibile il codice per il controllo degli argomenti:</span><span class="sxs-lookup"><span data-stu-id="2eed2-107">You can use the `NameOf` operator to make the argument-checking code more maintainable:</span></span>

```vb
Private _name As String

Public Property Name As String
    Get
        Return _name
    End Get
    Set
        If value Is Nothing Then
            Throw New ArgumentNullException(NameOf(value), $"{NameOf(name)} cannot be null.")
        End If
    End Set
End Property
```

<span data-ttu-id="2eed2-108">L'operatore `NameOf` è disponibile in Visual Basic 14 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="2eed2-108">The `NameOf` operator is available in Visual Basic 14 and later.</span></span>

## <a name="see-also"></a><span data-ttu-id="2eed2-109">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2eed2-109">See also</span></span>

- [<span data-ttu-id="2eed2-110">Riferimenti per il linguaggio Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2eed2-110">Visual Basic Language Reference</span></span>](../index.md)
- [<span data-ttu-id="2eed2-111">Operatori (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2eed2-111">Operators (Visual Basic)</span></span>](index.md)