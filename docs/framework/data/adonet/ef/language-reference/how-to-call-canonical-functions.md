---
title: 'Procedura: Chiamare funzioni canoniche'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b3d84873-7403-4957-8e20-b4ae39f50214
ms.openlocfilehash: 01a638d494b988e29ccf07763a7e0aecf54cc11c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936062"
---
# <a name="how-to-call-canonical-functions"></a>Procedura: Chiamare funzioni canoniche
La classe <xref:System.Data.Objects.EntityFunctions> contiene metodi che espongono funzioni canoniche da usare nelle query LINQ to Entities. Per informazioni sulle funzioni canoniche, vedere [Funzioni canoniche](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).  
  
> [!NOTE]
> I metodi <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> e <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> nella classe <xref:System.Data.Objects.EntityFunctions> non dispongono di equivalenti della funzione canonica.  
  
 Le funzioni canoniche che eseguono un calcolo su un set di valori e restituiscono un valore singolo (anche note come funzioni canoniche di aggregazione) possono essere richiamate direttamente. Altre funzioni canoniche possono essere chiamate solo come parte di una query LINQ to Entities. Per chiamare direttamente una funzione di aggregazione, è necessario passare un oggetto <xref:System.Data.Objects.ObjectQuery%601> alla funzione. Per altre informazioni, vedere il secondo esempio che segue.  
  
 È possibile chiamare alcune funzioni canoniche tramite metodi Common Language Runtime (CLR) nelle query LINQ to Entities. Per un elenco di metodi CLR mappati alle funzioni canoniche, vedere mapping tra il [metodo CLR](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md)e la funzione canonica.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene utilizzato il [modello Sales di AdventureWorks](https://archive.codeplex.com/?p=msftdbprodsamples). Nell'esempio viene eseguita una query LINQ to Entities che usa il metodo <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> per restituire tutti i prodotti per i quali la differenza tra `SellEndDate` e `SellStartDate` è inferiore a 365 giorni:  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#1)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#1)]  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene utilizzato il [modello Sales di AdventureWorks](https://archive.codeplex.com/?p=msftdbprodsamples). Nell'esempio viene chiamato direttamente il metodo di aggregazione <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A>  per restituire la deviazione standard dei subtotali `SalesOrderHeader`. Si noti che alla funzione viene passato un oggetto <xref:System.Data.Objects.ObjectQuery%601>, che consente alla funzione di essere chiamata senza essere parte di una query LINQ to Entities.  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#2)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Vedere anche

- [Chiamata di funzioni in query di LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)
- [Query in LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
