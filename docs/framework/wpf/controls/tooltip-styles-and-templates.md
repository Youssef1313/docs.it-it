---
title: Stili e modelli di ToolTip
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ToolTip
- styles [WPF], ToolTip
- states [WPF], ToolTip
- ToolTip [WPF], styles and templates
- ControlTemplate [WPF], ToolTip
- templates [WPF], ToolTip
ms.assetid: 405fe385-4de9-49ee-a448-d8f4d1f740dd
ms.openlocfilehash: 626d0b4d49d653f820d1506f0aa09f06d26352c2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458641"
---
# <a name="tooltip-styles-and-templates"></a><span data-ttu-id="55454-102">Stili e modelli di ToolTip</span><span class="sxs-lookup"><span data-stu-id="55454-102">ToolTip Styles and Templates</span></span>
<span data-ttu-id="55454-103">In questo argomento vengono descritti gli stili e i modelli per il controllo <xref:System.Windows.Controls.ToolTip>.</span><span class="sxs-lookup"><span data-stu-id="55454-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolTip> control.</span></span> <span data-ttu-id="55454-104">È possibile modificare il <xref:System.Windows.Controls.ControlTemplate> predefinito per dare al controllo un aspetto univoco.</span><span class="sxs-lookup"><span data-stu-id="55454-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="55454-105">Per altre informazioni, vedere [Personalizzazione dell'aspetto di un controllo esistente mediante la creazione di un oggetto ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="55454-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="tooltip-parts"></a><span data-ttu-id="55454-106">Parti della descrizione comando</span><span class="sxs-lookup"><span data-stu-id="55454-106">ToolTip Parts</span></span>  
 <span data-ttu-id="55454-107">Il controllo <xref:System.Windows.Controls.ToolTip> non dispone di parti denominate.</span><span class="sxs-lookup"><span data-stu-id="55454-107">The <xref:System.Windows.Controls.ToolTip> control does not have any named parts.</span></span>  
  
## <a name="tooltip-states"></a><span data-ttu-id="55454-108">Stati descrizione comando</span><span class="sxs-lookup"><span data-stu-id="55454-108">ToolTip States</span></span>  
 <span data-ttu-id="55454-109">Nella tabella seguente sono elencati gli Stati di visualizzazione per il controllo <xref:System.Windows.Controls.ToolTip>.</span><span class="sxs-lookup"><span data-stu-id="55454-109">The following table lists the visual states for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
|<span data-ttu-id="55454-110">Nome VisualState</span><span class="sxs-lookup"><span data-stu-id="55454-110">VisualState Name</span></span>|<span data-ttu-id="55454-111">Nome VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="55454-111">VisualStateGroup Name</span></span>|<span data-ttu-id="55454-112">Descrizione</span><span class="sxs-lookup"><span data-stu-id="55454-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="55454-113">Closed</span><span class="sxs-lookup"><span data-stu-id="55454-113">Closed</span></span>|<span data-ttu-id="55454-114">OpenStates</span><span class="sxs-lookup"><span data-stu-id="55454-114">OpenStates</span></span>|<span data-ttu-id="55454-115">Lo stato predefinito.</span><span class="sxs-lookup"><span data-stu-id="55454-115">The default state.</span></span>|  
|<span data-ttu-id="55454-116">Apri</span><span class="sxs-lookup"><span data-stu-id="55454-116">Open</span></span>|<span data-ttu-id="55454-117">OpenStates</span><span class="sxs-lookup"><span data-stu-id="55454-117">OpenStates</span></span>|<span data-ttu-id="55454-118">Il <xref:System.Windows.Controls.ToolTip> è visibile.</span><span class="sxs-lookup"><span data-stu-id="55454-118">The <xref:System.Windows.Controls.ToolTip> is visible.</span></span>|  
|<span data-ttu-id="55454-119">Valido</span><span class="sxs-lookup"><span data-stu-id="55454-119">Valid</span></span>|<span data-ttu-id="55454-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="55454-120">ValidationStates</span></span>|<span data-ttu-id="55454-121">Il controllo Usa la classe <xref:System.Windows.Controls.Validation> e la proprietà <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> associata è `false`.</span><span class="sxs-lookup"><span data-stu-id="55454-121">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="55454-122">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="55454-122">InvalidFocused</span></span>|<span data-ttu-id="55454-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="55454-123">ValidationStates</span></span>|<span data-ttu-id="55454-124">Il <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> proprietà associata è `true` il controllo ha lo stato attivo.</span><span class="sxs-lookup"><span data-stu-id="55454-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="55454-125">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="55454-125">InvalidUnfocused</span></span>|<span data-ttu-id="55454-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="55454-126">ValidationStates</span></span>|<span data-ttu-id="55454-127">Il <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> proprietà associata è `true` ha il controllo non ha lo stato attivo.</span><span class="sxs-lookup"><span data-stu-id="55454-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="tooltip-controltemplate-example"></a><span data-ttu-id="55454-128">Esempio di ControlTemplate della descrizione comando</span><span class="sxs-lookup"><span data-stu-id="55454-128">ToolTip ControlTemplate Example</span></span>  
 <span data-ttu-id="55454-129">Nell'esempio seguente viene illustrato come definire un <xref:System.Windows.Controls.ControlTemplate> per il controllo <xref:System.Windows.Controls.ToolTip>.</span><span class="sxs-lookup"><span data-stu-id="55454-129">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/tooltip.xaml#tooltip)]  
  
 <span data-ttu-id="55454-130">L'esempio precedente usa una o più delle seguenti risorse.</span><span class="sxs-lookup"><span data-stu-id="55454-130">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="55454-131">Per l'esempio completo, vedere [Esempio di applicazione di stili con ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="55454-131">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55454-132">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="55454-132">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="55454-133">Stili e modelli di Control</span><span class="sxs-lookup"><span data-stu-id="55454-133">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="55454-134">Personalizzazione dei controlli</span><span class="sxs-lookup"><span data-stu-id="55454-134">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="55454-135">Applicazione di stili e modelli</span><span class="sxs-lookup"><span data-stu-id="55454-135">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="55454-136">Personalizzazione dell'aspetto di un controllo esistente mediante la creazione di un oggetto ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="55454-136">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
