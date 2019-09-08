---
title: 'Procedura: Visualizzare il codice SQL generato'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 626492c0-5ee3-4675-88e8-8c40379510b6
ms.openlocfilehash: f3ed431709266b636804c6c00450b26684550d8b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793752"
---
# <a name="how-to-display-generated-sql"></a><span data-ttu-id="0f4c8-102">Procedura: Visualizzare il codice SQL generato</span><span class="sxs-lookup"><span data-stu-id="0f4c8-102">How to: Display Generated SQL</span></span>
<span data-ttu-id="0f4c8-103">È possibile visualizzare il codice SQL generato per le query e modificare l'elaborazione usando la proprietà <xref:System.Data.Linq.DataContext.Log%2A>.</span><span class="sxs-lookup"><span data-stu-id="0f4c8-103">You can view the SQL code generated for queries and change processing by using the <xref:System.Data.Linq.DataContext.Log%2A> property.</span></span> <span data-ttu-id="0f4c8-104">Questo approccio può essere utile per comprendere la funzionalità di [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] e per eseguire il debug di problemi specifici.</span><span class="sxs-lookup"><span data-stu-id="0f4c8-104">This approach can be useful for understanding [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] functionality and for debugging specific problems.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f4c8-105">Esempio</span><span class="sxs-lookup"><span data-stu-id="0f4c8-105">Example</span></span>  
 <span data-ttu-id="0f4c8-106">Nell'esempio riportato di seguito viene usata la proprietà <xref:System.Data.Linq.DataContext.Log%2A> per visualizzare il codice SQL nella finestra della console prima di eseguirlo.</span><span class="sxs-lookup"><span data-stu-id="0f4c8-106">The following example uses the <xref:System.Data.Linq.DataContext.Log%2A> property to display SQL code in the console window before the code is executed.</span></span>  <span data-ttu-id="0f4c8-107">È possibile usare questa proprietà con comandi di query, inserimento, aggiornamento ed eliminazione.</span><span class="sxs-lookup"><span data-stu-id="0f4c8-107">You can use this property with query, insert, update, and delete commands.</span></span>  
  
 <span data-ttu-id="0f4c8-108">Le linee dalla finestra della console sono quelle visualizzate quando si esegue il Visual Basic o C# il codice seguente.</span><span class="sxs-lookup"><span data-stu-id="0f4c8-108">The lines from the console window are what you see when you execute the Visual Basic or C# code that follows.</span></span>  
  
```  
SELECT [t0].[CustomerID], [t0].[CompanyName], [t0].[ContactName], [t0].[ContactT  
itle], [t0].[Address], [t0].[City], [t0].[Region], [t0].[PostalCode], [t0].[Coun  
try], [t0].[Phone], [t0].[Fax]  
FROM [dbo].[Customers] AS [t0]  
WHERE [t0].[City] = @p0  
-- @p0: Input String (Size = 6; Prec = 0; Scale = 0) [London]  
-- Context: SqlProvider(Sql2005) Model: AttributedMetaModel Build: 3.5.20810.0  
```  
  
```  
AROUT  
BSBEV  
CONSH  
EASTC  
NORTS  
SEVES  
```  
  
 [!code-csharp[DLinqDebuggingSupport#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#1)]
 [!code-vb[DLinqDebuggingSupport#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0f4c8-109">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0f4c8-109">See also</span></span>

- [<span data-ttu-id="0f4c8-110">Supporto per il debug</span><span class="sxs-lookup"><span data-stu-id="0f4c8-110">Debugging Support</span></span>](debugging-support.md)
