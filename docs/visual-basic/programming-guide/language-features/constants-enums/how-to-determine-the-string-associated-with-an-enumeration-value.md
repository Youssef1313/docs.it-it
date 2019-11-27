---
title: 'Procedura: determinare la stringa associata a un valore di enumerazione'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: c396a4e2ebe973f5be65c3fab5f22cdedb29be1a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351139"
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a><span data-ttu-id="1a332-102">Procedura: determinare la stringa associata a un valore di enumerazione (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1a332-102">How to: Determine the String Associated with an Enumeration Value (Visual Basic)</span></span>
<span data-ttu-id="1a332-103">I metodi <xref:System.Enum.GetValues%2A> e <xref:System.Enum.GetNames%2A> consentono di determinare le stringhe e i valori associati ai membri dell'enumerazione.</span><span class="sxs-lookup"><span data-stu-id="1a332-103">The <xref:System.Enum.GetValues%2A> and <xref:System.Enum.GetNames%2A> methods allow you to determine the strings and values associated with enumeration members.</span></span>  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a><span data-ttu-id="1a332-104">Per determinare la stringa associata a un'enumerazione</span><span class="sxs-lookup"><span data-stu-id="1a332-104">To determine the string associated with an enumeration</span></span>  
  
- <span data-ttu-id="1a332-105">Usare il metodo <xref:System.Enum.GetNames%2A> per recuperare le stringhe associate ai membri dell'enumerazione.</span><span class="sxs-lookup"><span data-stu-id="1a332-105">Use the <xref:System.Enum.GetNames%2A> method to retrieve the strings associated with the enumeration members.</span></span> <span data-ttu-id="1a332-106">Questo esempio dichiara un'enumerazione, `flavorEnum`, quindi usa il metodo <xref:System.Enum.GetNames%2A> per visualizzare le stringhe associate a ogni membro.</span><span class="sxs-lookup"><span data-stu-id="1a332-106">This example declares an enumeration, `flavorEnum`, then uses the <xref:System.Enum.GetNames%2A> method to display the strings associated with each member.</span></span>  
  
     [!code-vb[VbEnumsTask#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="1a332-107">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1a332-107">See also</span></span>

- <xref:System.Enum.GetValues%2A>
- <xref:System.Enum.GetNames%2A>
- <xref:System.Enum>
- [<span data-ttu-id="1a332-108">Procedura: dichiarare un'enumerazione</span><span class="sxs-lookup"><span data-stu-id="1a332-108">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="1a332-109">Procedura: Fare riferimento a un membro di enumerazione</span><span class="sxs-lookup"><span data-stu-id="1a332-109">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="1a332-110">Qualifica di nomi ed enumerazioni</span><span class="sxs-lookup"><span data-stu-id="1a332-110">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="1a332-111">Procedura: scorrere un'enumerazione in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1a332-111">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="1a332-112">Quando usare un'enumerazione</span><span class="sxs-lookup"><span data-stu-id="1a332-112">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [<span data-ttu-id="1a332-113">Istruzione Enum</span><span class="sxs-lookup"><span data-stu-id="1a332-113">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)
