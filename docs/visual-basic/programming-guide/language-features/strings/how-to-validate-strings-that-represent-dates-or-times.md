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
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a><span data-ttu-id="5a5ff-102">Procedura: convalidare le stringhe che rappresentano date o ore (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a5ff-102">How to: Validate Strings That Represent Dates or Times (Visual Basic)</span></span>
<span data-ttu-id="5a5ff-103">The following code example sets a `Boolean` value that indicates whether a string represents a valid date or time.</span><span class="sxs-lookup"><span data-stu-id="5a5ff-103">The following code example sets a `Boolean` value that indicates whether a string represents a valid date or time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a5ff-104">Esempio</span><span class="sxs-lookup"><span data-stu-id="5a5ff-104">Example</span></span>  
 [!code-vb[VbVbcnRegEx#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5a5ff-105">Compilazione del codice</span><span class="sxs-lookup"><span data-stu-id="5a5ff-105">Compiling the Code</span></span>  
 <span data-ttu-id="5a5ff-106">Replace `("01/01/03")` and `"9:30 PM"` with the date and time you want to validate.</span><span class="sxs-lookup"><span data-stu-id="5a5ff-106">Replace `("01/01/03")` and `"9:30 PM"` with the date and time you want to validate.</span></span> <span data-ttu-id="5a5ff-107">You can replace the string with another hard-coded string, with a `String` variable, or with a method that returns a string, such as `InputBox`.</span><span class="sxs-lookup"><span data-stu-id="5a5ff-107">You can replace the string with another hard-coded string, with a `String` variable, or with a method that returns a string, such as `InputBox`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="5a5ff-108">Programmazione efficiente</span><span class="sxs-lookup"><span data-stu-id="5a5ff-108">Robust Programming</span></span>  
 <span data-ttu-id="5a5ff-109">Use this method to validate the string before trying to convert the `String` to a `DateTime` variable.</span><span class="sxs-lookup"><span data-stu-id="5a5ff-109">Use this method to validate the string before trying to convert the `String` to a `DateTime` variable.</span></span> <span data-ttu-id="5a5ff-110">By checking the date or time first, you can avoid generating an exception at run time.</span><span class="sxs-lookup"><span data-stu-id="5a5ff-110">By checking the date or time first, you can avoid generating an exception at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a5ff-111">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5a5ff-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [<span data-ttu-id="5a5ff-112">Convalida delle stringhe in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5a5ff-112">Validating Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
