---
title: Iteratore
ms.date: 07/20/2015
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
ms.openlocfilehash: 9d7eaf186bae544031487ce027505e1e0d4ae0f3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351529"
---
# <a name="iterator-visual-basic"></a>Iteratore (Visual Basic)
Specifies that a function or `Get` accessor is an iterator.  
  
## <a name="remarks"></a>Note  
 An *iterator* performs a custom iteration over a collection. An iterator uses the [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element in the collection one at a time. When a `Yield` statement is reached, the current location in code is retained. L'esecuzione viene riavviata a partire da quella posizione la volta successiva che viene chiamata la funzione iteratore.  
  
 An iterator can be implemented as a function or as a `Get` accessor of a property definition. The `Iterator` modifier appears in the declaration of the iterator function or `Get` accessor.  
  
 You call an iterator from client code by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
 The return type of an iterator function or `Get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.  
  
 An iterator cannot have any `ByRef` parameters.  
  
 Un iteratore non può verificarsi in un evento, costruttore di istanza, costruttore statico o distruttore statico.  
  
 An iterator can be an anonymous function. Per altre informazioni, vedere [Iteratori](../../programming-guide/concepts/iterators.md).  
  
## <a name="usage"></a>Utilizzo  
 Il modificatore `Iterator` può essere usato nei contesti seguenti:  
  
- [Istruzione Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
- [Istruzione Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a>Esempio  
 The following example demonstrates an iterator function. The iterator function has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop. Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function. Ogni chiamata alla funzione iteratore procede fino alla prossima esecuzione dell'istruzione `Yield`, che si verifica durante l'iterazione successiva del ciclo `For…Next`.  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrata una funzione di accesso `Get` che è un iteratore. The `Iterator` modifier is in the property declaration.  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>
- [Iteratori](../../programming-guide/concepts/iterators.md)
- [Istruzione Yield](../../../visual-basic/language-reference/statements/yield-statement.md)
