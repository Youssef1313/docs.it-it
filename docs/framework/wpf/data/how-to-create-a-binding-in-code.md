---
title: 'Procedura: creare associazioni nel codice'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], creating
- data binding [WPF], creating
ms.assetid: 1a606db9-cf5f-42ed-a1c5-9e4722ec77a0
ms.openlocfilehash: 616487a16ebbe6e23fe067fb7ce72644aa3f919f
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458854"
---
# <a name="how-to-create-a-binding-in-code"></a><span data-ttu-id="ed9f8-102">Procedura: creare associazioni nel codice</span><span class="sxs-lookup"><span data-stu-id="ed9f8-102">How to: Create a Binding in Code</span></span>
<span data-ttu-id="ed9f8-103">Questo esempio illustra come creare e impostare un <xref:System.Windows.Data.Binding> nel codice.</span><span class="sxs-lookup"><span data-stu-id="ed9f8-103">This example shows how to create and set a <xref:System.Windows.Data.Binding> in code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed9f8-104">Esempio</span><span class="sxs-lookup"><span data-stu-id="ed9f8-104">Example</span></span>  
 <span data-ttu-id="ed9f8-105">La classe <xref:System.Windows.FrameworkElement> e la classe <xref:System.Windows.FrameworkContentElement> espongono entrambi un metodo di `SetBinding`.</span><span class="sxs-lookup"><span data-stu-id="ed9f8-105">The <xref:System.Windows.FrameworkElement> class and the <xref:System.Windows.FrameworkContentElement> class both expose a `SetBinding` method.</span></span> <span data-ttu-id="ed9f8-106">Se si associa un elemento che eredita una di queste classi, è possibile chiamare direttamente il metodo <xref:System.Windows.FrameworkElement.SetBinding%2A>.</span><span class="sxs-lookup"><span data-stu-id="ed9f8-106">If you are binding an element that inherits either of these classes, you can call the <xref:System.Windows.FrameworkElement.SetBinding%2A> method directly.</span></span>  
  
 <span data-ttu-id="ed9f8-107">Nell'esempio seguente viene creata una classe denominata, `MyData`, che contiene una proprietà denominata `MyDataProperty`.</span><span class="sxs-lookup"><span data-stu-id="ed9f8-107">The following example creates a class named, `MyData`, which contains a property named `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 <span data-ttu-id="ed9f8-108">Nell'esempio seguente viene illustrato come creare un oggetto Binding per impostare l'origine dell'associazione.</span><span class="sxs-lookup"><span data-stu-id="ed9f8-108">The following example shows how to create a binding object to set the source of the binding.</span></span>  <span data-ttu-id="ed9f8-109">Nell'esempio viene usato <xref:System.Windows.FrameworkElement.SetBinding%2A> per associare la proprietà <xref:System.Windows.Controls.TextBlock.Text%2A> di `myText`, ovvero un controllo <xref:System.Windows.Controls.TextBlock>, per `MyDataProperty`.</span><span class="sxs-lookup"><span data-stu-id="ed9f8-109">The example uses <xref:System.Windows.FrameworkElement.SetBinding%2A> to bind the <xref:System.Windows.Controls.TextBlock.Text%2A> property of `myText`, which is a <xref:System.Windows.Controls.TextBlock> control, to `MyDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 <span data-ttu-id="ed9f8-110">Per l'esempio di codice completo, vedere [esempio di associazione di solo codice](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="ed9f8-110">For the complete code sample, see [Code-only Binding Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90)).</span></span>  
  
 <span data-ttu-id="ed9f8-111">Anziché chiamare <xref:System.Windows.FrameworkElement.SetBinding%2A>, è possibile usare il metodo statico <xref:System.Windows.Data.BindingOperations.SetBinding%2A> della classe <xref:System.Windows.Data.BindingOperations>.</span><span class="sxs-lookup"><span data-stu-id="ed9f8-111">Instead of calling <xref:System.Windows.FrameworkElement.SetBinding%2A>, you can use the <xref:System.Windows.Data.BindingOperations.SetBinding%2A> static method of the <xref:System.Windows.Data.BindingOperations> class.</span></span> <span data-ttu-id="ed9f8-112">Nell'esempio seguente viene chiamato <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> anziché <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> per associare `myText` a `myDataProperty`.</span><span class="sxs-lookup"><span data-stu-id="ed9f8-112">The following example, calls <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> instead of <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> to bind `myText` to `myDataProperty`.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a><span data-ttu-id="ed9f8-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ed9f8-113">See also</span></span>

- [<span data-ttu-id="ed9f8-114">Panoramica sul data binding</span><span class="sxs-lookup"><span data-stu-id="ed9f8-114">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="ed9f8-115">Procedure relative alle proprietà</span><span class="sxs-lookup"><span data-stu-id="ed9f8-115">How-to Topics</span></span>](data-binding-how-to-topics.md)
