---
title: 'Procedura: Recuperare informazioni sui conflitti tra membri'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
ms.openlocfilehash: 40caa07488cb40ca8e9e3eb3a570c325b92de491
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793300"
---
# <a name="how-to-retrieve-member-conflict-information"></a><span data-ttu-id="1eb52-102">Procedura: Recuperare informazioni sui conflitti tra membri</span><span class="sxs-lookup"><span data-stu-id="1eb52-102">How to: Retrieve Member Conflict Information</span></span>
<span data-ttu-id="1eb52-103">È possibile usare la classe <xref:System.Data.Linq.MemberChangeConflict> per recuperare informazioni sui singoli membri in conflitto.</span><span class="sxs-lookup"><span data-stu-id="1eb52-103">You can use the <xref:System.Data.Linq.MemberChangeConflict> class to retrieve information about individual members in conflict.</span></span> <span data-ttu-id="1eb52-104">In questo stesso contesto è possibile provvedere alla gestione personalizzata del conflitto per qualsiasi membro.</span><span class="sxs-lookup"><span data-stu-id="1eb52-104">In this same context you can provide for custom handling of the conflict for any member.</span></span> <span data-ttu-id="1eb52-105">Per ulteriori informazioni, vedere [concorrenza ottimistica: Panoramica](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1eb52-105">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1eb52-106">Esempio</span><span class="sxs-lookup"><span data-stu-id="1eb52-106">Example</span></span>  
 <span data-ttu-id="1eb52-107">Il codice riportato di seguito consente di scorrere gli oggetti <xref:System.Data.Linq.ObjectChangeConflict></span><span class="sxs-lookup"><span data-stu-id="1eb52-107">The following code iterates through the <xref:System.Data.Linq.ObjectChangeConflict> objects.</span></span> <span data-ttu-id="1eb52-108">quindi, per ogni oggetto, di scorrere gli oggetti <xref:System.Data.Linq.MemberChangeConflict>.</span><span class="sxs-lookup"><span data-stu-id="1eb52-108">For each object, it then iterates through the <xref:System.Data.Linq.MemberChangeConflict> objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1eb52-109">Includere <xref:System.Reflection> in modo da fornire informazioni su <xref:System.Data.Linq.MemberChangeConflict.Member%2A>.</span><span class="sxs-lookup"><span data-stu-id="1eb52-109">Include <xref:System.Reflection> in order to provide <xref:System.Data.Linq.MemberChangeConflict.Member%2A> information.</span></span>  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="1eb52-110">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1eb52-110">See also</span></span>

- [<span data-ttu-id="1eb52-111">Procedura: Gestione dei conflitti di modifica</span><span class="sxs-lookup"><span data-stu-id="1eb52-111">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
