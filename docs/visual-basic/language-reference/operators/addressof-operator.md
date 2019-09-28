---
title: Operatore AddressOf (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
ms.openlocfilehash: 2ebadf5ded1a23fe46b8e16cf18ae265b5d3c255
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591661"
---
# <a name="addressof-operator-visual-basic"></a><span data-ttu-id="d5677-102">Operatore AddressOf (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5677-102">AddressOf Operator (Visual Basic)</span></span>
<span data-ttu-id="d5677-103">Crea un'istanza di delegato che fa riferimento alla procedura specifica.</span><span class="sxs-lookup"><span data-stu-id="d5677-103">Creates a delegate instance that references the specific procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5677-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d5677-104">Syntax</span></span>  
  
```vb  
AddressOf procedurename  
```  
  
## <a name="parts"></a><span data-ttu-id="d5677-105">Parti</span><span class="sxs-lookup"><span data-stu-id="d5677-105">Parts</span></span>  
 `procedurename`  
 <span data-ttu-id="d5677-106">Obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="d5677-106">Required.</span></span> <span data-ttu-id="d5677-107">Specifica la procedura a cui fa riferimento il delegato appena creato.</span><span class="sxs-lookup"><span data-stu-id="d5677-107">Specifies the procedure to be referenced by the newly created delegate.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5677-108">Note</span><span class="sxs-lookup"><span data-stu-id="d5677-108">Remarks</span></span>  
 <span data-ttu-id="d5677-109">L'operatore `AddressOf` crea un delegato che punta alla subroutine o alla funzione specificata da `procedurename`.</span><span class="sxs-lookup"><span data-stu-id="d5677-109">The `AddressOf` operator creates a delegate that points to the sub or function specified by `procedurename`.</span></span> <span data-ttu-id="d5677-110">Quando la procedura specificata è un metodo di istanza, il delegato fa riferimento sia all'istanza sia al metodo.</span><span class="sxs-lookup"><span data-stu-id="d5677-110">When the specified procedure is an instance method then the delegate refers to both the instance and the method.</span></span> <span data-ttu-id="d5677-111">Quindi, quando viene richiamato il delegato, viene chiamato il metodo specificato dell'istanza specificata.</span><span class="sxs-lookup"><span data-stu-id="d5677-111">Then, when the  delegate is invoked the specified method of the specified instance is called.</span></span>  
  
 <span data-ttu-id="d5677-112">L'operatore `AddressOf` può essere usato come operando di un costruttore di delegato o può essere usato in un contesto in cui il tipo del delegato può essere determinato dal compilatore.</span><span class="sxs-lookup"><span data-stu-id="d5677-112">The `AddressOf` operator can be used as the operand of a delegate constructor or it can be used in a context in which the type of the delegate can be determined by the compiler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5677-113">Esempio</span><span class="sxs-lookup"><span data-stu-id="d5677-113">Example</span></span>  
 <span data-ttu-id="d5677-114">In questo esempio viene usato l'operatore `AddressOf` per designare un delegato per gestire l'evento `Click` di un pulsante.</span><span class="sxs-lookup"><span data-stu-id="d5677-114">This example uses the `AddressOf` operator to designate a delegate to handle the `Click` event of a button.</span></span>  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="d5677-115">Esempio</span><span class="sxs-lookup"><span data-stu-id="d5677-115">Example</span></span>  
 <span data-ttu-id="d5677-116">Nell'esempio seguente viene usato l'operatore `AddressOf` per designare la funzione di avvio per un thread.</span><span class="sxs-lookup"><span data-stu-id="d5677-116">The following example uses the `AddressOf` operator to designate the startup function for a thread.</span></span>  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="d5677-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d5677-117">See also</span></span>

- [<span data-ttu-id="d5677-118">Istruzione Declare</span><span class="sxs-lookup"><span data-stu-id="d5677-118">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="d5677-119">Istruzione Function</span><span class="sxs-lookup"><span data-stu-id="d5677-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="d5677-120">Istruzione Sub</span><span class="sxs-lookup"><span data-stu-id="d5677-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="d5677-121">Delegati</span><span class="sxs-lookup"><span data-stu-id="d5677-121">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
