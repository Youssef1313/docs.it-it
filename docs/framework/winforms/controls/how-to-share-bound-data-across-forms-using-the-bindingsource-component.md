---
title: 'Procedura: Condividere i dati associati tra moduli usando il componente BindingSource'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], BindingSource component
- data binding [Windows Forms], sharing data across forms
- BindingSource component [Windows Forms], examples
- BindingSource [Windows Forms], using with multiple forms
ms.assetid: a1a49630-db9c-4485-b888-1f62a373a4f7
ms.openlocfilehash: aa497194fd4ac65f48773a45175333a1d862b453
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956067"
---
# <a name="how-to-share-bound-data-across-forms-using-the-bindingsource-component"></a><span data-ttu-id="d546e-102">Procedura: Condividere i dati associati tra moduli usando il componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="d546e-102">How to: Share Bound Data Across Forms Using the BindingSource Component</span></span>
<span data-ttu-id="d546e-103">È possibile condividere facilmente i dati tra i form con il componente <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="d546e-103">You can easily share data across forms using the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="d546e-104">Ad esempio, è possibile visualizzare un form di sola lettura che riepiloga i dati dell'origine dati e un altro form modificabile che contiene informazioni dettagliate sull'elemento attualmente selezionato nell'origine dati.</span><span class="sxs-lookup"><span data-stu-id="d546e-104">For example, you may want to display one read-only form that summarizes the data-source data and another editable form that contains detailed information about the currently selected item in the data source.</span></span> <span data-ttu-id="d546e-105">L'esempio illustra questo scenario.</span><span class="sxs-lookup"><span data-stu-id="d546e-105">This example demonstrates this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d546e-106">Esempio</span><span class="sxs-lookup"><span data-stu-id="d546e-106">Example</span></span>  
 <span data-ttu-id="d546e-107">L'esempio di codice seguente illustra come condividere un oggetto <xref:System.Windows.Forms.BindingSource> e i dati associati tra i form.</span><span class="sxs-lookup"><span data-stu-id="d546e-107">The following code example demonstrates how to share a <xref:System.Windows.Forms.BindingSource> and its bound data across forms.</span></span> <span data-ttu-id="d546e-108">In questo esempio, l'oggetto <xref:System.Windows.Forms.BindingSource> condiviso viene passato al costruttore del form figlio.</span><span class="sxs-lookup"><span data-stu-id="d546e-108">In this example, the shared <xref:System.Windows.Forms.BindingSource> is passed to the constructor of the child form.</span></span> <span data-ttu-id="d546e-109">Il form figlio consente all'utente di modificare i dati per l'elemento attualmente selezionato nel form principale.</span><span class="sxs-lookup"><span data-stu-id="d546e-109">The child form allows the user to edit the data for the currently selected item in the main form.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d546e-110">Nell'esempio viene gestito l'evento <xref:System.Windows.Forms.BindingSource.BindingComplete> del componente <xref:System.Windows.Forms.BindingSource> per essere certi che i due form rimangano sincronizzati</span><span class="sxs-lookup"><span data-stu-id="d546e-110">The <xref:System.Windows.Forms.BindingSource.BindingComplete> event for the <xref:System.Windows.Forms.BindingSource> component is handled in the example to ensure that the two forms remain synchronized.</span></span> <span data-ttu-id="d546e-111">Per ulteriori informazioni sul motivo per cui questa operazione viene [eseguita, vedere Procedura: Assicurarsi che più controlli associati alla stessa origine dati rimangano](../multiple-controls-bound-to-data-source-synchronized.md)sincronizzati.</span><span class="sxs-lookup"><span data-stu-id="d546e-111">For more information about why this is done, see [How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized](../multiple-controls-bound-to-data-source-synchronized.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleForms#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleForms#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d546e-112">Compilazione del codice</span><span class="sxs-lookup"><span data-stu-id="d546e-112">Compiling the Code</span></span>  
 <span data-ttu-id="d546e-113">L'esempio presenta i requisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="d546e-113">This example requires:</span></span>  
  
- <span data-ttu-id="d546e-114">Riferimenti agli assembly System, System.Windows.Forms, System.Drawing, System.Data e System.Xml.</span><span class="sxs-lookup"><span data-stu-id="d546e-114">References to the System, System.Windows.Forms, System.Drawing, System.Data, and System.Xml assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d546e-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d546e-115">See also</span></span>

- [<span data-ttu-id="d546e-116">Componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="d546e-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="d546e-117">Data binding in Windows Form</span><span class="sxs-lookup"><span data-stu-id="d546e-117">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="d546e-118">Procedura: Gestire gli errori e le eccezioni che si verificano con l'associazione dati</span><span class="sxs-lookup"><span data-stu-id="d546e-118">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
