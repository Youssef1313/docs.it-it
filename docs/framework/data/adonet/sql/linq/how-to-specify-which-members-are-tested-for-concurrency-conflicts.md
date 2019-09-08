---
title: 'Procedura: Specificare per quali membri viene eseguito il test dei conflitti di concorrenza'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d2cda293-1e2f-4878-af0e-5aaf0d092120
ms.openlocfilehash: de7109e0fed0eb7c1975ad7360a7588ef9b294ef
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793150"
---
# <a name="how-to-specify-which-members-are-tested-for-concurrency-conflicts"></a><span data-ttu-id="0f62c-102">Procedura: Specificare per quali membri viene eseguito il test dei conflitti di concorrenza</span><span class="sxs-lookup"><span data-stu-id="0f62c-102">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>
<span data-ttu-id="0f62c-103">Applicare una delle tre enumerazioni alla [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> proprietà su un <xref:System.Data.Linq.Mapping.ColumnAttribute> attributo per specificare i membri da includere nei controlli di aggiornamento per il rilevamento dei conflitti di concorrenza ottimistica.</span><span class="sxs-lookup"><span data-stu-id="0f62c-103">Apply one of three enums to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify which members are to be included in update checks for the detection of optimistic concurrency conflicts.</span></span>  
  
 <span data-ttu-id="0f62c-104">La proprietà <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>, di cui è stato eseguito il mapping in fase di progettazione, viene usata insieme alle funzionalità di concorrenza in fase di esecuzione in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0f62c-104">The <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property (mapped at design time) is used together with run-time concurrency features in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="0f62c-105">Per ulteriori informazioni, vedere [concorrenza ottimistica: Panoramica](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0f62c-105">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0f62c-106">I valori del membro originali vengono confrontati con lo stato corrente del database, a condizione che nessun membro sia designato come `IsVersion=true`.</span><span class="sxs-lookup"><span data-stu-id="0f62c-106">Original member values are compared with the current database state as long as no member is designated as `IsVersion=true`.</span></span> <span data-ttu-id="0f62c-107">Per altre informazioni, vedere <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="0f62c-107">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
 <span data-ttu-id="0f62c-108">Per esempi di codice, vedere <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="0f62c-108">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
### <a name="to-always-use-this-member-for-detecting-conflicts"></a><span data-ttu-id="0f62c-109">Per usare sempre questo membro per il rilevamento dei conflitti</span><span class="sxs-lookup"><span data-stu-id="0f62c-109">To always use this member for detecting conflicts</span></span>  
  
1. <span data-ttu-id="0f62c-110">Aggiungere la proprietà <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> all'attributo <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="0f62c-110">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="0f62c-111">Impostare il valore della proprietà <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> su `Always`.</span><span class="sxs-lookup"><span data-stu-id="0f62c-111">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `Always`.</span></span>  
  
### <a name="to-never-use-this-member-for-detecting-conflicts"></a><span data-ttu-id="0f62c-112">Per non usare mai questo membro per il rilevamento dei conflitti</span><span class="sxs-lookup"><span data-stu-id="0f62c-112">To never use this member for detecting conflicts</span></span>  
  
1. <span data-ttu-id="0f62c-113">Aggiungere la proprietà <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> all'attributo <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="0f62c-113">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="0f62c-114">Impostare il valore della proprietà <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> su `Never`.</span><span class="sxs-lookup"><span data-stu-id="0f62c-114">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `Never`.</span></span>  
  
### <a name="to-use-this-member-for-detecting-conflicts-only-when-the-application-has-changed-the-value-of-the-member"></a><span data-ttu-id="0f62c-115">Per usare questo membro per il rilevamento dei conflitti solo quando il valore del membro è stato modificato dall'applicazione</span><span class="sxs-lookup"><span data-stu-id="0f62c-115">To use this member for detecting conflicts only when the application has changed the value of the member</span></span>  
  
1. <span data-ttu-id="0f62c-116">Aggiungere la proprietà <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> all'attributo <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="0f62c-116">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="0f62c-117">Impostare il valore della proprietà <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> su `WhenChanged`.</span><span class="sxs-lookup"><span data-stu-id="0f62c-117">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `WhenChanged`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f62c-118">Esempio</span><span class="sxs-lookup"><span data-stu-id="0f62c-118">Example</span></span>  
 <span data-ttu-id="0f62c-119">Nell'esempio seguente viene specificato che gli oggetti `HomePage` non dovranno mai essere testati durante i controlli di aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="0f62c-119">The following example specifies that `HomePage` objects should never be tested during update checks.</span></span> <span data-ttu-id="0f62c-120">Per altre informazioni, vedere <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="0f62c-120">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0f62c-121">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0f62c-121">See also</span></span>

- [<span data-ttu-id="0f62c-122">Procedura: Gestione dei conflitti di modifica</span><span class="sxs-lookup"><span data-stu-id="0f62c-122">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="0f62c-123">Creazione e invio di modifiche dei dati</span><span class="sxs-lookup"><span data-stu-id="0f62c-123">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
