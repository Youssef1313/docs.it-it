---
title: 'Procedura: creare stringhe usando StringBuilder in Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: 19e036abc9d25ec7fdfd6c33ebb420ec4f503cbc
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700100"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a><span data-ttu-id="4524d-102">Procedura: creare stringhe usando StringBuilder in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4524d-102">How to: create strings using a StringBuilder in Visual Basic</span></span>

<span data-ttu-id="4524d-103">Questo esempio crea una stringa lunga da molte stringhe più piccole usando la classe <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="4524d-103">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span></span> <span data-ttu-id="4524d-104">La classe <xref:System.Text.StringBuilder> è più efficiente dell'operatore `&=` per la concatenazione di molte stringhe.</span><span class="sxs-lookup"><span data-stu-id="4524d-104">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span></span>

## <a name="example"></a><span data-ttu-id="4524d-105">Esempio</span><span class="sxs-lookup"><span data-stu-id="4524d-105">Example</span></span>

<span data-ttu-id="4524d-106">Nell'esempio seguente viene creata un'istanza della classe <xref:System.Text.StringBuilder>, vengono accodate 1.000 stringhe a tale istanza, quindi viene restituita la relativa rappresentazione di stringa:</span><span class="sxs-lookup"><span data-stu-id="4524d-106">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation:</span></span>

 [!code-vb[VbVbalrStrings#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#70)]

## <a name="see-also"></a><span data-ttu-id="4524d-107">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4524d-107">See also</span></span>

- [<span data-ttu-id="4524d-108">Uso della classe StringBuilder</span><span class="sxs-lookup"><span data-stu-id="4524d-108">Using the StringBuilder Class</span></span>](../../../../standard/base-types/stringbuilder.md)
- [<span data-ttu-id="4524d-109">Operatore &=</span><span class="sxs-lookup"><span data-stu-id="4524d-109">&= Operator</span></span>](../../../language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="4524d-110">Stringhe</span><span class="sxs-lookup"><span data-stu-id="4524d-110">Strings</span></span>](index.md)
- [<span data-ttu-id="4524d-111">Creazione di nuove stringhe</span><span class="sxs-lookup"><span data-stu-id="4524d-111">Creating New Strings</span></span>](../../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="4524d-112">Modifica di stringhe</span><span class="sxs-lookup"><span data-stu-id="4524d-112">Manipulating Strings</span></span>](../../../../standard/base-types/manipulating-strings.md)
