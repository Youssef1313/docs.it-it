---
title: Creazione di un dataset
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
ms.openlocfilehash: d496167b7bce31491402414c43ae0bcdee423b89
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786498"
---
# <a name="creating-a-dataset"></a><span data-ttu-id="60418-102">Creazione di un dataset</span><span class="sxs-lookup"><span data-stu-id="60418-102">Creating a DataSet</span></span>
<span data-ttu-id="60418-103">È possibile creare un'istanza di un tipo<xref:System.Data.DataSet> chiamando il costruttore <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="60418-103">You create an instance of a <xref:System.Data.DataSet> by calling the <xref:System.Data.DataSet> constructor.</span></span> <span data-ttu-id="60418-104">Facoltativamente, specificare un nome di argomento.</span><span class="sxs-lookup"><span data-stu-id="60418-104">Optionally specify a name argument.</span></span> <span data-ttu-id="60418-105">Se non si specifica alcun nome per il tipo <xref:System.Data.DataSet>, verrà usato il nome "NewDataSet".</span><span class="sxs-lookup"><span data-stu-id="60418-105">If you do not specify a name for the <xref:System.Data.DataSet>, the name is set to "NewDataSet".</span></span>  
  
 <span data-ttu-id="60418-106">È inoltre possibile creare un nuovo tipo <xref:System.Data.DataSet> basato su un tipo <xref:System.Data.DataSet> esistente.</span><span class="sxs-lookup"><span data-stu-id="60418-106">You can also create a new <xref:System.Data.DataSet> based on an existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="60418-107">Il nuovo tipo <xref:System.Data.DataSet> può essere una copia esatta del <xref:System.Data.DataSet> esistente; un duplicato del tipo <xref:System.Data.DataSet> in cui viene copiata la struttura relazionale o lo schema ma in cui non è presente alcun dato proveniente dal <xref:System.Data.DataSet> esistente; oppure un subset del tipo <xref:System.Data.DataSet>, contenente solo le righe modificate del <xref:System.Data.DataSet> esistente usando il metodo <xref:System.Data.DataSet.GetChanges%2A>.</span><span class="sxs-lookup"><span data-stu-id="60418-107">The new <xref:System.Data.DataSet> can be an exact copy of the existing <xref:System.Data.DataSet>; a clone of the <xref:System.Data.DataSet> that copies the relational structure or schema but that does not contain any of the data from the existing <xref:System.Data.DataSet>; or a subset of the <xref:System.Data.DataSet>, containing only the modified rows from the existing <xref:System.Data.DataSet> using the <xref:System.Data.DataSet.GetChanges%2A> method.</span></span> <span data-ttu-id="60418-108">Per ulteriori informazioni, vedere [copia del contenuto del set di dati](copying-dataset-contents.md).</span><span class="sxs-lookup"><span data-stu-id="60418-108">For more information, see [Copying DataSet Contents](copying-dataset-contents.md).</span></span>  
  
 <span data-ttu-id="60418-109">Nell'esempio di codice seguente viene illustrata la creazione di un'istanza di un tipo <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="60418-109">The following code example demonstrates how to construct an instance of a <xref:System.Data.DataSet>.</span></span>  
  
```vb  
Dim customerOrders As DataSet = New DataSet("CustomerOrders")  
```  
  
```csharp  
DataSet customerOrders = new DataSet("CustomerOrders");  
```  
  
## <a name="see-also"></a><span data-ttu-id="60418-110">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="60418-110">See also</span></span>

- [<span data-ttu-id="60418-111">Popolamento di un set di dati da un oggetto DataAdapter</span><span class="sxs-lookup"><span data-stu-id="60418-111">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)
- [<span data-ttu-id="60418-112">Oggetti DataSet, DataTable e DataView</span><span class="sxs-lookup"><span data-stu-id="60418-112">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="60418-113">Panoramica di ADO.NET</span><span class="sxs-lookup"><span data-stu-id="60418-113">ADO.NET Overview</span></span>](../ado-net-overview.md)
