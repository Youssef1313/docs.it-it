---
title: 'Procedura: convalidare le stringhe che rappresentano date o ore'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: 34af6dffeb0d05eaeed38354f8007554b60e91b0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344348"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a>Procedura: convalidare le stringhe che rappresentano date o ore (Visual Basic)
The following code example sets a `Boolean` value that indicates whether a string represents a valid date or time.  
  
## <a name="example"></a>Esempio  
 [!code-vb[VbVbcnRegEx#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#2)]  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 Replace `("01/01/03")` and `"9:30 PM"` with the date and time you want to validate. You can replace the string with another hard-coded string, with a `String` variable, or with a method that returns a string, such as `InputBox`.  
  
## <a name="robust-programming"></a>Programmazione efficiente  
 Use this method to validate the string before trying to convert the `String` to a `DateTime` variable. By checking the date or time first, you can avoid generating an exception at run time.  
  
## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [Convalida delle stringhe in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
