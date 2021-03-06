---
title: 'Procedura: definire un operatore'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- operator procedures [Visual Basic], about operator procedures
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: d4b0e253-092a-4e6e-9fe2-01f562140a29
ms.openlocfilehash: b99af8ff4d5428f1749bfc1a4c51a136f12405ee
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344868"
---
# <a name="how-to-define-an-operator-visual-basic"></a>Procedura: definire un operatore (Visual Basic)
Se è stata definita una classe o una struttura, è possibile definire il comportamento di un operatore standard (ad esempio `*`, `<>`o `And`) quando uno o entrambi gli operandi sono del tipo della classe o della struttura.  
  
 Definire l'operatore standard come routine di operatore all'interno della classe o della struttura. Tutte le routine degli operatori devono essere `Public` `Shared`.  
  
 La definizione di un operatore in una classe o in una struttura è detta anche *Overload* dell'operatore.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene definito l'operatore `+` per una struttura denominata `height`. La struttura Usa altezze misurate in piedi e pollici. Un *pollice* è 2,54 centimetri e un *piede* è 12 pollici. Per garantire la normalizzazione dei valori (pollici < 12,0), il costruttore esegue l'aritmetica *modulo* 12. L'operatore `+` usa il costruttore per generare valori normalizzati.  
  
 [!code-vb[VbVbcnProcedures#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#25)]  
  
 È possibile testare la struttura `height` con il codice seguente.  
  
 [!code-vb[VbVbcnProcedures#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#26)]  

## <a name="see-also"></a>Vedere anche

- [Routine di operatore](./operator-procedures.md)
- [Procedura: Definire un operatore di conversione](./how-to-define-a-conversion-operator.md)
- [Procedura: Chiamare una routine di operatore](./how-to-call-an-operator-procedure.md)
- [Procedura: Usare una classe che definisce gli operatori](./how-to-use-a-class-that-defines-operators.md)
- [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Istruzione Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Procedura: Dichiarare una struttura](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Operatore Mod](../../../../visual-basic/language-reference/operators/mod-operator.md)
