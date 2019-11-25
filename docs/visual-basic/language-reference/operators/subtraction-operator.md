---
title: '- ??'
ms.date: 07/20/2015
f1_keywords:
- vb.Negate
- vb.-
helpviewer_keywords:
- operator [Visual Basic]
- operators [Visual Basic], subtraction
- operators [Visual Basic], difference
- negation operator [Visual Basic]
- operators [Visual Basic], arithmetic
- subtraction operator [Visual Basic], syntax
- arithmetic operators [Visual Basic], subtraction
- difference operator [Visual Basic]
- math operators [Visual Basic]
- operators [Visual Basic], negation
- minus operator [Visual Basic]
ms.assetid: bff2c368-662d-4c92-ac87-1d9bdfd3426a
ms.openlocfilehash: 9687c366c5b23693c05ab5c6b34f50c04131dfda
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348230"
---
# <a name="--operator-visual-basic"></a>Operatore - (Visual Basic)
Returns the difference between two numeric expressions or the negative value of a numeric expression.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
expression1 – expression2
```
  
Oppure

```vb  
–expression1  
```  
  
## <a name="parts"></a>Parti  
 `expression1`  
 Obbligatorio. Qualsiasi espressione numerica.  
  
 `expression2`  
 Required unless the `–` operator is calculating a negative value. Qualsiasi espressione numerica.  
  
## <a name="result"></a>Risultato  
 The result is the difference between `expression1` and `expression2`, or the negated value of `expression1`.  
  
 The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`. See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="supported-types"></a>Tipi supportati  
 tutti i tipi numerici. This includes the unsigned and floating-point types and `Decimal`.  
  
## <a name="remarks"></a>Note  
 In the first usage shown in the syntax shown previously, the `–` operator is the *binary* arithmetic subtraction operator for the difference between two numeric expressions.  
  
 In the second usage shown in the syntax shown previously, the `–` operator is the *unary* negation operator for the negative value of an expression. In this sense, the negation consists of reversing the sign of `expression1` so that the result is positive if `expression1` is negative.  
  
 If either expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the `–` operator treats it as zero.  
  
> [!NOTE]
> The `–` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure. If your code uses this operator on such a class or structure, make sure that you understand its redefined behavior. Per altre informazioni, vedere [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Esempio  
 The following example uses the `–` operator to calculate and return the difference between two numbers, and then to negate a number.  
  
 [!code-vb[VbVbalrOperators#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#10)]  
  
 Following the execution of these statements, `binaryResult` contains 124.45 and `unaryResult` contains –334.90.  
  
## <a name="see-also"></a>Vedere anche

- [-= Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [Operatori aritmetici](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Precedenza tra gli operatori in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Elenco degli operatori per funzionalità](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
