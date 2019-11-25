---
title: Clausola Skip
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
ms.openlocfilehash: c582b014bad4fa8fa3165d2b756f4bc955840cfc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349649"
---
# <a name="skip-clause-visual-basic"></a>Clausola Skip (Visual Basic)
Ignora un numero specificato di elementi in una raccolta e quindi restituisce gli elementi rimanenti.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
Skip count  
```  
  
## <a name="parts"></a>Parti  
 `count`  
 Obbligatorio. A value or an expression that evaluates to the number of elements of the sequence to skip.  
  
## <a name="remarks"></a>Note  
 The `Skip` clause causes a query to bypass elements at the beginning of a results list and return the remaining elements. The number of elements to skip is identified by the `count` parameter.  
  
 You can use the `Skip` clause with the `Take` clause to return a range of data from any segment of a query. To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.  
  
 When you use the `Skip` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Skip` clause to bypass the intended results. For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 You can use the `SkipWhile` clause to specify that only certain elements are ignored, depending on a supplied condition.  
  
## <a name="example"></a>Esempio  
 The following code example uses the `Skip` clause together with the `Take` clause to return data from a query in pages. The `GetCustomers` function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>Vedere anche

- [Introduzione a LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Query](../../../visual-basic/language-reference/queries/index.md)
- [Clausola Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Clausola From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Clausola Order By](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Clausola Skip While](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Clausola Take](../../../visual-basic/language-reference/queries/take-clause.md)
