---
title: "Procedura: Supportare l'interoperabilità COM visualizzando ogni Windows Form nel proprio thread"
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: a9e04765-d2de-4389-a494-a9a6d07aa6ee
ms.openlocfilehash: 41af4d81995a0a4eac912ecce7dc70cf04f012cd
ms.sourcegitcommit: 1e72e2990220b3635cebc39586828af9deb72d8c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/26/2019
ms.locfileid: "71306383"
---
# <a name="how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread"></a><span data-ttu-id="c32c4-102">Procedura: Supportare l'interoperabilità COM visualizzando ogni Windows Form nel relativo thread</span><span class="sxs-lookup"><span data-stu-id="c32c4-102">How to: Support COM interop by displaying each Windows Form on its own thread</span></span>

<span data-ttu-id="c32c4-103">È possibile risolvere i problemi di interoperabilità COM visualizzando il form in un ciclo di messaggi .NET Framework, che è possibile creare <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> tramite il metodo.</span><span class="sxs-lookup"><span data-stu-id="c32c4-103">You can resolve COM interoperability problems by displaying your form on a .NET Framework message loop, which you can create by using the <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="c32c4-104">Perché un Windows Form funzioni correttamente da un'applicazione client COM, è necessario eseguire il form in un ciclo di messaggi Windows Form.</span><span class="sxs-lookup"><span data-stu-id="c32c4-104">To make a Windows Form work correctly from a COM client application, you must run the form on a Windows Forms message loop.</span></span> <span data-ttu-id="c32c4-105">Per eseguire questa operazione, adottare uno degli approcci seguenti:</span><span class="sxs-lookup"><span data-stu-id="c32c4-105">To do this, use one of the following approaches:</span></span>

- <span data-ttu-id="c32c4-106">Usare il metodo <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> per visualizzare il Windows Form.</span><span class="sxs-lookup"><span data-stu-id="c32c4-106">Use the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to display the Windows Form.</span></span> <span data-ttu-id="c32c4-107">Per altre informazioni, vedere [Procedura: Supportare l'interoperabilità COM visualizzando un Windows Form con il](com-interop-by-displaying-a-windows-form-shadow.md)metodo ShowDialog.</span><span class="sxs-lookup"><span data-stu-id="c32c4-107">For more information, see [How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method](com-interop-by-displaying-a-windows-form-shadow.md).</span></span>

- <span data-ttu-id="c32c4-108">Visualizzare ogni Windows Form in un thread separato.</span><span class="sxs-lookup"><span data-stu-id="c32c4-108">Display each Windows Form on a separate thread.</span></span>

<span data-ttu-id="c32c4-109">In Visual Studio è disponibile un supporto completo per questa funzionalità.</span><span class="sxs-lookup"><span data-stu-id="c32c4-109">There is extensive support for this feature in Visual Studio.</span></span>

<span data-ttu-id="c32c4-110">Vedere [anche procedura dettagliata: Supporto dell'interoperabilità COM mediante la visualizzazione di ogni Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100))form nel relativo thread.</span><span class="sxs-lookup"><span data-stu-id="c32c4-110">Also see [Walkthrough: Supporting COM Interop by Displaying Each Windows Form on Its Own Thread](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100)).</span></span>

## <a name="example"></a><span data-ttu-id="c32c4-111">Esempio</span><span class="sxs-lookup"><span data-stu-id="c32c4-111">Example</span></span>

<span data-ttu-id="c32c4-112">L'esempio di codice seguente illustra come visualizzare il form in un thread separato e chiamare il metodo <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> per avviare un message pump Windows Form su tale thread.</span><span class="sxs-lookup"><span data-stu-id="c32c4-112">The following code example demonstrates how to display the form on a separate thread and call the <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> method to start a Windows Forms message pump on that thread.</span></span> <span data-ttu-id="c32c4-113">Per adottare questo approccio, è necessario effettuare il marshalling di tutte le chiamate al form dall'applicazione non gestita usando il metodo <xref:System.Windows.Forms.Control.Invoke%2A> .</span><span class="sxs-lookup"><span data-stu-id="c32c4-113">To use this approach, you must marshal any calls to the form from the unmanaged application by using the <xref:System.Windows.Forms.Control.Invoke%2A> method.</span></span>

<span data-ttu-id="c32c4-114">Questo approccio richiede che ogni istanza di un form venga eseguita nel rispettivo thread usando il proprio ciclo di messaggi.</span><span class="sxs-lookup"><span data-stu-id="c32c4-114">This approach requires that each instance of a form runs on its own thread by using its own message loop.</span></span> <span data-ttu-id="c32c4-115">Non è possibile eseguire più di un ciclo di messaggi per ogni thread.</span><span class="sxs-lookup"><span data-stu-id="c32c4-115">You cannot have more than one message loop running per thread.</span></span> <span data-ttu-id="c32c4-116">Quindi non è possibile modificare il ciclo di messaggi dell'applicazione client.</span><span class="sxs-lookup"><span data-stu-id="c32c4-116">Therefore, you cannot change the client application's message loop.</span></span> <span data-ttu-id="c32c4-117">Tuttavia, è possibile modificare il componente .NET Framework per avviare un nuovo thread che usa il proprio ciclo di messaggi.</span><span class="sxs-lookup"><span data-stu-id="c32c4-117">However, you can modify the .NET Framework component to start a new thread that uses its own message loop.</span></span>

[!code-vb[System.Windows.Forms.ComInterop#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/COMForm.vb#1)]

[!code-vb[System.Windows.Forms.ComInterop#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/FormManager.vb#10)]

[!code-vb[System.Windows.Forms.ComInterop#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/Form1.vb#100)]

## <a name="compile-the-code"></a><span data-ttu-id="c32c4-118">Compilare il codice</span><span class="sxs-lookup"><span data-stu-id="c32c4-118">Compile the code</span></span>

<span data-ttu-id="c32c4-119">Compilare i tipi `COMForm`, `Form1`e `FormManager` in un assembly denominato `COMWinform.dll`.</span><span class="sxs-lookup"><span data-stu-id="c32c4-119">Compile the `COMForm`, `Form1`, and `FormManager` types into an assembly called `COMWinform.dll`.</span></span> <span data-ttu-id="c32c4-120">Registrare l'assembly per l'interoperabilità COM usando uno dei metodi descritti in [Packaging an Assembly for COM](../../interop/packaging-an-assembly-for-com.md).</span><span class="sxs-lookup"><span data-stu-id="c32c4-120">Register the assembly for COM interop by using one of the methods described in [Packaging an Assembly for COM](../../interop/packaging-an-assembly-for-com.md).</span></span> <span data-ttu-id="c32c4-121">Ora è possibile usare l'assembly e il file libreria dei tipi (tlb) corrispondente nelle applicazioni non gestite.</span><span class="sxs-lookup"><span data-stu-id="c32c4-121">You can now use the assembly and its corresponding type library (.tlb) file in unmanaged applications.</span></span> <span data-ttu-id="c32c4-122">Ad esempio, è possibile usare la libreria dei tipi come riferimento in un progetto eseguibile di Visual Basic 6.0.</span><span class="sxs-lookup"><span data-stu-id="c32c4-122">For example, you can use the type library as a reference in a Visual Basic 6.0 executable project.</span></span>

## <a name="see-also"></a><span data-ttu-id="c32c4-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c32c4-123">See also</span></span>

- [<span data-ttu-id="c32c4-124">Esposizione di componenti .NET Framework a COM</span><span class="sxs-lookup"><span data-stu-id="c32c4-124">Exposing .NET Framework Components to COM</span></span>](../../interop/exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="c32c4-125">Preparazione di un assembly per COM</span><span class="sxs-lookup"><span data-stu-id="c32c4-125">Packaging an Assembly for COM</span></span>](../../interop/packaging-an-assembly-for-com.md)
- [<span data-ttu-id="c32c4-126">Registrazione di assembly presso COM</span><span class="sxs-lookup"><span data-stu-id="c32c4-126">Registering Assemblies with COM</span></span>](../../interop/registering-assemblies-with-com.md)
- [<span data-ttu-id="c32c4-127">Procedura: Supportare l'interoperabilità COM visualizzando un Windows Form con il metodo ShowDialog</span><span class="sxs-lookup"><span data-stu-id="c32c4-127">How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method</span></span>](com-interop-by-displaying-a-windows-form-shadow.md)
- [<span data-ttu-id="c32c4-128">Panoramica su Windows Form e applicazioni non gestite</span><span class="sxs-lookup"><span data-stu-id="c32c4-128">Windows Forms and Unmanaged Applications Overview</span></span>](windows-forms-and-unmanaged-applications-overview.md)
