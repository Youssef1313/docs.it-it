---
title: ByVal
ms.date: 07/20/2015
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
ms.openlocfilehash: a96f871c6ce119f65ebbec54fdb1471ae105d504
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351591"
---
# <a name="byval-visual-basic"></a>ByVal (Visual Basic)
Specifies that an argument is passed [by value](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), so that the called procedure or property cannot change the value of a variable underlying the argument in the calling code. If no modifier is specified, ByVal is the default.

> [!NOTE]
> Because it is the default, you do not have to explicitly specify the `ByVal` keyword in method signatures. It tends to produce noisy code and often leads to the non-default `ByRef` keyword being overlooked.

## <a name="remarks"></a>Note
 Il modificatore `ByVal` può essere usato nei contesti seguenti:

 [Istruzione Declare](../../../visual-basic/language-reference/statements/declare-statement.md)

 [Istruzione Function](../../../visual-basic/language-reference/statements/function-statement.md)
  
 [Istruzione Operator](../../../visual-basic/language-reference/statements/operator-statement.md)
  
 [Istruzione Property](../../../visual-basic/language-reference/statements/property-statement.md)
  
 [Istruzione Sub](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="example"></a>Esempio
 The following example demonstrates the use of the `ByVal` parameter passing mechanism with a reference type argument. In the example, the argument is `c1`, an instance of class `Class1`. `ByVal` prevents the code in the procedures from changing the underlying value of the reference argument, `c1`, but does not protect the accessible fields and properties of `c1`.

 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]

## <a name="see-also"></a>Vedere anche

- [Parole chiave](../../../visual-basic/language-reference/keywords/index.md)
- [Passaggio di argomenti per valore e per riferimento](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
