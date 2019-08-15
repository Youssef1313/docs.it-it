---
title: 'Procedura: Ereditare dalla classe Control'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- Control class [Windows Forms], inheriting from
- custom controls [Windows Forms], inheritance
- OnPaint method [Windows Forms]
- custom controls [Windows Forms], creating
ms.assetid: 46ba0df3-5cf7-443c-a3b4-a72660172476
ms.openlocfilehash: 535827db660ab1113a25a01b7a0553a1c4414c74
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037781"
---
# <a name="how-to-inherit-from-the-control-class"></a><span data-ttu-id="01ffb-102">Procedura: Ereditare dalla classe Control</span><span class="sxs-lookup"><span data-stu-id="01ffb-102">How to: Inherit from the Control Class</span></span>
<span data-ttu-id="01ffb-103">Se si vuole creare un controllo completamente personalizzato da usare in un Windows Form, è necessario ereditare dalla <xref:System.Windows.Forms.Control> classe.</span><span class="sxs-lookup"><span data-stu-id="01ffb-103">If you want to create a completely custom control to use on a Windows Form, you should inherit from the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="01ffb-104">Mentre l'ereditarietà dalla <xref:System.Windows.Forms.Control> classe richiede l'esecuzione di una maggiore pianificazione e implementazione, offre anche la più ampia gamma di opzioni.</span><span class="sxs-lookup"><span data-stu-id="01ffb-104">While inheriting from the <xref:System.Windows.Forms.Control> class requires that you perform more planning and implementation, it also provides you with the largest range of options.</span></span> <span data-ttu-id="01ffb-105">Quando si eredita da <xref:System.Windows.Forms.Control>, si ereditano le funzionalità di base che rendono i controlli funzionanti.</span><span class="sxs-lookup"><span data-stu-id="01ffb-105">When inheriting from <xref:System.Windows.Forms.Control>, you inherit the very basic functionality that makes controls work.</span></span> <span data-ttu-id="01ffb-106">La funzionalità inerente <xref:System.Windows.Forms.Control> alla classe gestisce l'input dell'utente attraverso la tastiera e il mouse, definisce i limiti e le dimensioni del controllo, fornisce un handle di Windows e fornisce la gestione e la sicurezza dei messaggi.</span><span class="sxs-lookup"><span data-stu-id="01ffb-106">The functionality inherent in the <xref:System.Windows.Forms.Control> class handles user input through the keyboard and mouse, defines the bounds and size of the control, provides a windows handle, and provides message handling and security.</span></span> <span data-ttu-id="01ffb-107">Non incorpora nessun disegno, che in questo caso è il rendering reale dell'interfaccia grafica del controllo, e non consente di incorporare alcuna funzionalità di interazione utente specifica.</span><span class="sxs-lookup"><span data-stu-id="01ffb-107">It does not incorporate any painting, which in this case is the actual rendering of the graphical interface of the control, nor does it incorporate any specific user interaction functionality.</span></span> <span data-ttu-id="01ffb-108">È necessario fornire tutti questi aspetti tramite codice personalizzato.</span><span class="sxs-lookup"><span data-stu-id="01ffb-108">You must provide all of these aspects through custom code.</span></span>

## <a name="to-create-a-custom-control"></a><span data-ttu-id="01ffb-109">Per creare un controllo personalizzato</span><span class="sxs-lookup"><span data-stu-id="01ffb-109">To create a custom control</span></span>

1. <span data-ttu-id="01ffb-110">Creare una nuova **Applicazione Windows** o un progetto **Libreria di controllo Windows**.</span><span class="sxs-lookup"><span data-stu-id="01ffb-110">Create a new **Windows Application** or **Windows Control Library** project.</span></span>

2. <span data-ttu-id="01ffb-111">Scegliere **Aggiungi classe** dal menu **Progetto**.</span><span class="sxs-lookup"><span data-stu-id="01ffb-111">From the **Project** menu, choose **Add Class**.</span></span>

3. <span data-ttu-id="01ffb-112">Nella finestra di dialogo **Aggiungi nuovo elemento**, fare clic su **Controllo personalizzato**.</span><span class="sxs-lookup"><span data-stu-id="01ffb-112">In the **Add New Item** dialog box, click **Custom Control**.</span></span>

     <span data-ttu-id="01ffb-113">Un nuovo controllo personalizzato viene aggiunto al progetto.</span><span class="sxs-lookup"><span data-stu-id="01ffb-113">A new custom control is added to your project.</span></span>

4. <span data-ttu-id="01ffb-114">Premere F7 per aprire l'**Editor di codice** per il controllo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="01ffb-114">Press F7 to open the **Code Editor** for your custom control.</span></span>

5. <span data-ttu-id="01ffb-115">Individuare il <xref:System.Windows.Forms.Control.OnPaint%2A> metodo, che sarà vuoto ad eccezione di una chiamata <xref:System.Windows.Forms.Control.OnPaint%2A> al metodo della classe di base.</span><span class="sxs-lookup"><span data-stu-id="01ffb-115">Locate the <xref:System.Windows.Forms.Control.OnPaint%2A> method, which will be empty except for a call to the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class.</span></span>

6. <span data-ttu-id="01ffb-116">Modificare il codice per incorporare il disegno personalizzato desiderato per il controllo.</span><span class="sxs-lookup"><span data-stu-id="01ffb-116">Modify the code to incorporate any custom painting you want for your control.</span></span>

     <span data-ttu-id="01ffb-117">Per informazioni sul codice di scrittura per eseguire il rendering della grafica dei controlli, vedere [Disegno e rendering di controlli personalizzati](custom-control-painting-and-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="01ffb-117">For information about writing code to render graphics for controls, see [Custom Control Painting and Rendering](custom-control-painting-and-rendering.md).</span></span>

7. <span data-ttu-id="01ffb-118">Implementare eventuali metodi, proprietà o eventi personalizzati da incorporare nel controllo.</span><span class="sxs-lookup"><span data-stu-id="01ffb-118">Implement any custom methods, properties, or events that your control will incorporate.</span></span>

8. <span data-ttu-id="01ffb-119">Salvare ed eseguire il test del controllo.</span><span class="sxs-lookup"><span data-stu-id="01ffb-119">Save and test your control.</span></span>

## <a name="see-also"></a><span data-ttu-id="01ffb-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="01ffb-120">See also</span></span>

- [<span data-ttu-id="01ffb-121">Tipi di controlli personalizzati</span><span class="sxs-lookup"><span data-stu-id="01ffb-121">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="01ffb-122">Procedura: Ereditare dalla classe UserControl</span><span class="sxs-lookup"><span data-stu-id="01ffb-122">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)
- [<span data-ttu-id="01ffb-123">Procedura: Ereditare da controlli Windows Forms esistenti</span><span class="sxs-lookup"><span data-stu-id="01ffb-123">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)
- [<span data-ttu-id="01ffb-124">Procedura: Controlli autore per Windows Forms</span><span class="sxs-lookup"><span data-stu-id="01ffb-124">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="01ffb-125">Risoluzione dei problemi relativi ai gestori eventi ereditati in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="01ffb-125">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [<span data-ttu-id="01ffb-126">Sviluppo di controlli Windows Form in fase di progettazione</span><span class="sxs-lookup"><span data-stu-id="01ffb-126">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
