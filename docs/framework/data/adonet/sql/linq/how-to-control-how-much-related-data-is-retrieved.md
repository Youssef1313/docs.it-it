---
title: 'Procedura: Controllare la quantità di dati correlati recuperata'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: efdc203e-3da9-4477-815e-54f10c3d7c6c
ms.openlocfilehash: 342583cdbf6a1501f1bc70c6a9be5d7009c390eb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940257"
---
# <a name="how-to-control-how-much-related-data-is-retrieved"></a><span data-ttu-id="8feab-102">Procedura: Controllare la quantità di dati correlati recuperata</span><span class="sxs-lookup"><span data-stu-id="8feab-102">How to: Control How Much Related Data Is Retrieved</span></span>
<span data-ttu-id="8feab-103">Usare il metodo <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> per specificare quali dati correlati alla destinazione principale devono essere recuperati contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="8feab-103">Use the <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> method to specify which data related to your main target should be retrieved at the same time.</span></span> <span data-ttu-id="8feab-104">Ad esempio, se le informazioni necessarie sono relative agli ordini dei clienti, è possibile usare <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> per assicurarsi che le informazioni sugli ordini vengano recuperate contestualmente alle informazioni sui clienti.</span><span class="sxs-lookup"><span data-stu-id="8feab-104">For example, if you know you will need information about customers' orders, you can use <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> to make sure that the order information is retrieved at the same time as the customer information.</span></span> <span data-ttu-id="8feab-105">Questo approccio comporta un solo accesso al database per entrambi i set di informazioni.</span><span class="sxs-lookup"><span data-stu-id="8feab-105">This approach results in only one trip to the database for both sets of information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8feab-106">È possibile recuperare dati riferiti alla destinazione principale della query recuperando un prodotto incrociato come una proiezione estesa, ad esempio gli ordini quando la destinazione della query sono i clienti.</span><span class="sxs-lookup"><span data-stu-id="8feab-106">You can retrieve data related to the main target of your query by retrieving a cross-product as one large projection, such as retrieving orders when you target customers.</span></span> <span data-ttu-id="8feab-107">Questo approccio, tuttavia, presenta spesso svantaggi.</span><span class="sxs-lookup"><span data-stu-id="8feab-107">But this approach often has disadvantages.</span></span> <span data-ttu-id="8feab-108">Ad esempio, i risultati sono solo proiezioni e non entità che possono essere modificate ed essere salvate in modo permanente da [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8feab-108">For example, the results are just projections and not entities that can be changed and persisted by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="8feab-109">Inoltre è possibile che vengano recuperate grandi quantità di dati non necessari.</span><span class="sxs-lookup"><span data-stu-id="8feab-109">And you can be retrieving lots of data that you do not need.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8feab-110">Esempio</span><span class="sxs-lookup"><span data-stu-id="8feab-110">Example</span></span>  
 <span data-ttu-id="8feab-111">Nell'esempio seguente tutti gli oggetti `Orders` di tutti gli oggetti `Customers` residenti nell'area londinese vengono recuperati quando viene eseguita la query.</span><span class="sxs-lookup"><span data-stu-id="8feab-111">In the following example, all the `Orders` for all the `Customers` who are located in London are retrieved when the query is executed.</span></span> <span data-ttu-id="8feab-112">Di conseguenza, l'accesso successivo alla proprietà `Orders` su un oggetto `Customer` non avvia una nuova query di database.</span><span class="sxs-lookup"><span data-stu-id="8feab-112">As a result, successive access to the `Orders` property on a `Customer` object does not trigger a new database query.</span></span>  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="8feab-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8feab-113">See also</span></span>

- [<span data-ttu-id="8feab-114">Esecuzione di query sul database</span><span class="sxs-lookup"><span data-stu-id="8feab-114">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
