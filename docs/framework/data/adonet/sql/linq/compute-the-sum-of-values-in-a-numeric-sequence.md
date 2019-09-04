---
title: Calcolare la somma dei valori in una sequenza numerica
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 24e335b0-984e-4825-8721-0a91b533b7c3
ms.openlocfilehash: 3a404068c2d89610aa9b01b392bca40f82e17707
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247920"
---
# <a name="compute-the-sum-of-values-in-a-numeric-sequence"></a><span data-ttu-id="f9a7c-102">Calcolare la somma dei valori in una sequenza numerica</span><span class="sxs-lookup"><span data-stu-id="f9a7c-102">Compute the Sum of Values in a Numeric Sequence</span></span>
<span data-ttu-id="f9a7c-103">Per calcolare la somma di valori numerici in una sequenza, usare l'operatore <xref:System.Linq.Enumerable.Sum%2A>.</span><span class="sxs-lookup"><span data-stu-id="f9a7c-103">Use the <xref:System.Linq.Enumerable.Sum%2A> operator to compute the sum of numeric values in a sequence.</span></span>  
  
 <span data-ttu-id="f9a7c-104">Di seguito sono riportate le caratteristiche dell'operatore `Sum` in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="f9a7c-104">Note the following characteristics of the `Sum` operator in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span></span>  
  
- <span data-ttu-id="f9a7c-105">L'operatore di aggregazione `Sum` dell'operatore di query standard restituisce valori zero per tutte le sequenze vuote o che contengono solo valori null.</span><span class="sxs-lookup"><span data-stu-id="f9a7c-105">The Standard Query Operator aggregate operator `Sum` evaluates to zero for an empty sequence or a sequence that contains only nulls.</span></span> <span data-ttu-id="f9a7c-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] la semantica di SQL rimane invariata.</span><span class="sxs-lookup"><span data-stu-id="f9a7c-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the semantics of SQL are left unchanged.</span></span> <span data-ttu-id="f9a7c-107">Per questo motivo `Sum` restituisce null anziché zero per una sequenza vuota o per una sequenza che contiene solo valori null.</span><span class="sxs-lookup"><span data-stu-id="f9a7c-107">For this reason, `Sum` evaluates to null instead of to zero for an empty sequence or for a sequence that contains only nulls.</span></span>  
  
- <span data-ttu-id="f9a7c-108">Le limitazioni di SQL sui risultati intermedi vengono applicate agli aggregati in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f9a7c-108">SQL limitations on intermediate results apply to aggregates in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="f9a7c-109">La somma delle quantità Integer a 32 bit non viene calcolata usando risultati a 64 bit e l'overflow può verificarsi per la [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] conversione di `Sum`.</span><span class="sxs-lookup"><span data-stu-id="f9a7c-109">Sum of 32-bit integer quantities is not computed by using 64-bit results, and overflow can occur for the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of `Sum`.</span></span> <span data-ttu-id="f9a7c-110">Questa possibilità esiste anche se l'implementazione dell'operatore di query standard non provoca un overflow per la corrispondente sequenza in memoria.</span><span class="sxs-lookup"><span data-stu-id="f9a7c-110">This possibility exists even if the Standard Query Operator implementation does not cause an overflow for the corresponding in-memory sequence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9a7c-111">Esempio</span><span class="sxs-lookup"><span data-stu-id="f9a7c-111">Example</span></span>  
 <span data-ttu-id="f9a7c-112">Nell'esempio seguente viene cercato il costo di trasporto complessivo di tutti gli ordini contenuti nella tabella `Order`.</span><span class="sxs-lookup"><span data-stu-id="f9a7c-112">The following example finds the total freight of all orders in the `Order` table.</span></span>  
  
 <span data-ttu-id="f9a7c-113">Se si esegue questa query sul database di esempio Northwind, l'output sarà: `64942.6900`.</span><span class="sxs-lookup"><span data-stu-id="f9a7c-113">If you run this query against the Northwind sample database, the output is: `64942.6900`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#12](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#12)]
 [!code-vb[DLinqQueryExamples#12](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="f9a7c-114">Esempio</span><span class="sxs-lookup"><span data-stu-id="f9a7c-114">Example</span></span>  
 <span data-ttu-id="f9a7c-115">Nell'esempio seguente viene cercato il numero complessivo di unità ordinate per tutti i prodotti.</span><span class="sxs-lookup"><span data-stu-id="f9a7c-115">The following example finds the total number of units on order for all products.</span></span>  
  
 <span data-ttu-id="f9a7c-116">Se si esegue questa query sul database di esempio Northwind, l'output sarà: `780`.</span><span class="sxs-lookup"><span data-stu-id="f9a7c-116">If you run this query against the Northwind sample database, the output is: `780`.</span></span>  
  
 <span data-ttu-id="f9a7c-117">Notare che è necessario eseguire il cast dei tipi `short`, ad esempio `UnitsOnOrder`, in quanto in `Sum` non è disponibile alcun overload per tali tipi.</span><span class="sxs-lookup"><span data-stu-id="f9a7c-117">Note that you must cast `short` types (for example, `UnitsOnOrder`) because `Sum` has no overload for short types.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#13](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#13)]
 [!code-vb[DLinqQueryExamples#13](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="f9a7c-118">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f9a7c-118">See also</span></span>

- [<span data-ttu-id="f9a7c-119">Query di aggregazione</span><span class="sxs-lookup"><span data-stu-id="f9a7c-119">Aggregate Queries</span></span>](aggregate-queries.md)
- [<span data-ttu-id="f9a7c-120">Download di database di esempio</span><span class="sxs-lookup"><span data-stu-id="f9a7c-120">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
