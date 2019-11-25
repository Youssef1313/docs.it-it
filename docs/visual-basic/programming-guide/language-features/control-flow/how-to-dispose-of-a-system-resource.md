---
title: 'Procedura: eliminare una risorsa di sistema'
ms.date: 07/20/2015
helpviewer_keywords:
- Using statement [Visual Basic], disposing of system resources
- Visual Basic code, control flow
- system resources, disposing of
- resources [Visual Basic], disposing of system
- system resources
- Using statement [Visual Basic], Using...End Using
- Using block
ms.assetid: 8be2b239-8090-419b-8e7e-bcaa75b0ecc8
ms.openlocfilehash: c493051050442597196ba484fb9ce8e99249dbb7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353949"
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a><span data-ttu-id="57784-102">Procedura: eliminare una risorsa di sistema (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57784-102">How to: Dispose of a System Resource (Visual Basic)</span></span>
<span data-ttu-id="57784-103">You can use a `Using` block to guarantee that the system disposes of a resource when your code exits the block.</span><span class="sxs-lookup"><span data-stu-id="57784-103">You can use a `Using` block to guarantee that the system disposes of a resource when your code exits the block.</span></span> <span data-ttu-id="57784-104">This is useful if you are using a system resource that consumes a large amount of memory, or that other components also want to use.</span><span class="sxs-lookup"><span data-stu-id="57784-104">This is useful if you are using a system resource that consumes a large amount of memory, or that other components also want to use.</span></span>  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a><span data-ttu-id="57784-105">To dispose of a database connection when your code is finished with it</span><span class="sxs-lookup"><span data-stu-id="57784-105">To dispose of a database connection when your code is finished with it</span></span>  
  
1. <span data-ttu-id="57784-106">Make sure you include the appropriate [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) for the database connection at the beginning of your source file (in this case, <xref:System.Data.SqlClient>).</span><span class="sxs-lookup"><span data-stu-id="57784-106">Make sure you include the appropriate [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) for the database connection at the beginning of your source file (in this case, <xref:System.Data.SqlClient>).</span></span>  
  
2. <span data-ttu-id="57784-107">Create a `Using` block with the `Using` and `End Using` statements.</span><span class="sxs-lookup"><span data-stu-id="57784-107">Create a `Using` block with the `Using` and `End Using` statements.</span></span> <span data-ttu-id="57784-108">Inside the block, put the code that deals with the database connection.</span><span class="sxs-lookup"><span data-stu-id="57784-108">Inside the block, put the code that deals with the database connection.</span></span>  
  
3. <span data-ttu-id="57784-109">Declare the connection and create an instance of it as part of the `Using` statement.</span><span class="sxs-lookup"><span data-stu-id="57784-109">Declare the connection and create an instance of it as part of the `Using` statement.</span></span>  
  
    ```vb  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     <span data-ttu-id="57784-110">The system disposes of the resource no matter how you exit the block, including the case of an unhandled exception.</span><span class="sxs-lookup"><span data-stu-id="57784-110">The system disposes of the resource no matter how you exit the block, including the case of an unhandled exception.</span></span>  
  
     <span data-ttu-id="57784-111">Note that you cannot access `sqc` from outside the `Using` block, because its scope is limited to the block.</span><span class="sxs-lookup"><span data-stu-id="57784-111">Note that you cannot access `sqc` from outside the `Using` block, because its scope is limited to the block.</span></span>  
  
     <span data-ttu-id="57784-112">You can use this same technique on a system resource such as a file handle or a COM wrapper.</span><span class="sxs-lookup"><span data-stu-id="57784-112">You can use this same technique on a system resource such as a file handle or a COM wrapper.</span></span> <span data-ttu-id="57784-113">You use a `Using` block when you want to be sure to leave the resource available for other components after you have exited the `Using` block.</span><span class="sxs-lookup"><span data-stu-id="57784-113">You use a `Using` block when you want to be sure to leave the resource available for other components after you have exited the `Using` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57784-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="57784-114">See also</span></span>

- <xref:System.Data.SqlClient.SqlConnection>
- [<span data-ttu-id="57784-115">Flusso di controllo</span><span class="sxs-lookup"><span data-stu-id="57784-115">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="57784-116">Strutture decisionali</span><span class="sxs-lookup"><span data-stu-id="57784-116">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="57784-117">Strutture di ciclo</span><span class="sxs-lookup"><span data-stu-id="57784-117">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="57784-118">Altre strutture di controllo</span><span class="sxs-lookup"><span data-stu-id="57784-118">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [<span data-ttu-id="57784-119">Strutture di controllo annidate</span><span class="sxs-lookup"><span data-stu-id="57784-119">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="57784-120">Istruzione Using</span><span class="sxs-lookup"><span data-stu-id="57784-120">Using Statement</span></span>](../../../../visual-basic/language-reference/statements/using-statement.md)
