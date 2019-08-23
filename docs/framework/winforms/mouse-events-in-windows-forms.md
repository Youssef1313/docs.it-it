---
title: Eventi mouse in Windows Form
ms.date: 03/30/2017
helpviewer_keywords:
- MouseLeave event [Windows Forms]
- events [Windows Forms], mouse
- Click event [Windows Forms], raising order
- Windows Forms controls, click events
- MouseDoubleClick event [Windows Forms]
- MouseEnter event [Windows Forms]
- MouseHover event [Windows Forms]
- MouseDown event [Windows Forms]
- MouseClick event [Windows Forms]
- MouseMove event [Windows Forms]
- mouse [Windows Forms], events
- MouseUp event
ms.assetid: 8cf0070d-793b-4876-b09e-d20d28280fab
ms.openlocfilehash: 181d01f6e688b94876f77155bf598aba129e9fbf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949908"
---
# <a name="mouse-events-in-windows-forms"></a><span data-ttu-id="d56eb-102">Eventi mouse in Windows Form</span><span class="sxs-lookup"><span data-stu-id="d56eb-102">Mouse Events in Windows Forms</span></span>

<span data-ttu-id="d56eb-103">Quando si gestisce l'input del mouse, in genere si vogliono conoscere la posizione del puntatore del mouse e lo stato dei pulsanti.</span><span class="sxs-lookup"><span data-stu-id="d56eb-103">When you handle mouse input, you usually want to know the location of the mouse pointer and the state of the mouse buttons.</span></span> <span data-ttu-id="d56eb-104">Questo argomento descrive in dettaglio come reperire tali informazioni da eventi del mouse e illustra l'ordine in cui gli eventi Click del mouse vengono generati nei controlli Windows Form.</span><span class="sxs-lookup"><span data-stu-id="d56eb-104">This topic provides details on how to get this information from mouse events, and explains the order in which mouse click events are raised in Windows Forms controls.</span></span> <span data-ttu-id="d56eb-105">Per un elenco e una descrizione di tutti gli eventi del mouse, vedere funzionamento dell' [input del mouse in Windows Forms](how-mouse-input-works-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="d56eb-105">For a list and description of all of the mouse events, see [How Mouse Input Works in Windows Forms](how-mouse-input-works-in-windows-forms.md).</span></span>  <span data-ttu-id="d56eb-106">Vedere anche [Cenni preliminari sui gestori eventi (Windows Forms)](event-handlers-overview-windows-forms.md) e [Cenni preliminari sugli eventi (Windows Forms)](events-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="d56eb-106">Also see [Event Handlers Overview (Windows Forms)](event-handlers-overview-windows-forms.md) and [Events Overview (Windows Forms)](events-overview-windows-forms.md).</span></span>

## <a name="mouse-information"></a><span data-ttu-id="d56eb-107">Informazioni sul mouse</span><span class="sxs-lookup"><span data-stu-id="d56eb-107">Mouse Information</span></span>

<span data-ttu-id="d56eb-108">Un oggetto <xref:System.Windows.Forms.MouseEventArgs> viene inviato ai gestori degli eventi del mouse correlati alla pressione di un pulsante e alla registrazione dei movimenti del mouse.</span><span class="sxs-lookup"><span data-stu-id="d56eb-108">A <xref:System.Windows.Forms.MouseEventArgs> is sent to the handlers of mouse events related to clicking a mouse button and tracking mouse movements.</span></span> <span data-ttu-id="d56eb-109"><xref:System.Windows.Forms.MouseEventArgs> fornisce informazioni sullo stato corrente del mouse, fra cui la posizione del puntatore nelle coordinate del client, i pulsanti del mouse premuti e se la rotellina del mouse è stata fatta scorrere.</span><span class="sxs-lookup"><span data-stu-id="d56eb-109"><xref:System.Windows.Forms.MouseEventArgs> provides information about the current state of the mouse, including the location of the mouse pointer in client coordinates, which mouse buttons are pressed, and whether the mouse wheel has scrolled.</span></span> <span data-ttu-id="d56eb-110">Numerosi eventi del mouse, ad esempio quelli che notificano semplicemente il momento in cui il puntatore del mouse entra o esce dai limiti di un controllo, inviano un oggetto <xref:System.EventArgs> al gestore eventi senza altre informazioni.</span><span class="sxs-lookup"><span data-stu-id="d56eb-110">Several mouse events, such as those that simply notify when the mouse pointer has entered or left the bounds of a control, send an <xref:System.EventArgs> to the event handler with no further information.</span></span>

<span data-ttu-id="d56eb-111">Se si desidera conoscere lo stato corrente dei pulsanti del mouse o la posizione del puntatore ed evitare la gestione di un evento del mouse, è anche possibile usare le proprietà <xref:System.Windows.Forms.Control.MouseButtons%2A> e <xref:System.Windows.Forms.Control.MousePosition%2A> della classe <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="d56eb-111">If you want to know the current state of the mouse buttons or the location of the mouse pointer, and you want to avoid handling a mouse event, you can also use the <xref:System.Windows.Forms.Control.MouseButtons%2A> and <xref:System.Windows.Forms.Control.MousePosition%2A> properties of the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="d56eb-112"><xref:System.Windows.Forms.Control.MouseButtons%2A> restituisce informazioni sui pulsanti del mouse attualmente premuti.</span><span class="sxs-lookup"><span data-stu-id="d56eb-112"><xref:System.Windows.Forms.Control.MouseButtons%2A> returns information about which mouse buttons are currently pressed.</span></span> <span data-ttu-id="d56eb-113"><xref:System.Windows.Forms.Control.MousePosition%2A> restituisce le coordinate dello schermo del puntatore del mouse e coincide con il valore restituito dalla proprietà <xref:System.Windows.Forms.Cursor.Position%2A>.</span><span class="sxs-lookup"><span data-stu-id="d56eb-113">The <xref:System.Windows.Forms.Control.MousePosition%2A> returns the screen coordinates of the mouse pointer and is equivalent to the value returned by <xref:System.Windows.Forms.Cursor.Position%2A>.</span></span>

## <a name="converting-between-screen-and-client-coordinates"></a><span data-ttu-id="d56eb-114">Conversione tra coordinate dello schermo e del client</span><span class="sxs-lookup"><span data-stu-id="d56eb-114">Converting Between Screen and Client Coordinates</span></span>

<span data-ttu-id="d56eb-115">Poiché alcune informazioni sulla posizione del mouse sono espresse con le coordinate del client e altre con le coordinate dello schermo, può essere necessario eseguire una conversione da un sistema di coordinate all'altro.</span><span class="sxs-lookup"><span data-stu-id="d56eb-115">Because some mouse location information is in client coordinates and some is in screen coordinates, you may need to convert a point from one coordinate system to the other.</span></span> <span data-ttu-id="d56eb-116">Questa operazione può essere eseguita facilmente usando i metodi <xref:System.Windows.Forms.Control.PointToClient%2A> e <xref:System.Windows.Forms.Control.PointToScreen%2A> disponibili nella classe <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="d56eb-116">You can do this easily by using the <xref:System.Windows.Forms.Control.PointToClient%2A> and <xref:System.Windows.Forms.Control.PointToScreen%2A> methods available on the <xref:System.Windows.Forms.Control> class.</span></span>

## <a name="standard-click-event-behavior"></a><span data-ttu-id="d56eb-117">Comportamento dell'evento Click standard</span><span class="sxs-lookup"><span data-stu-id="d56eb-117">Standard Click Event Behavior</span></span>

<span data-ttu-id="d56eb-118">Se si vogliono gestire gli eventi Click del mouse nell'ordine corretto, è necessario conoscere l'ordine in cui gli eventi Click vengono generati nei controlli Windows Form.</span><span class="sxs-lookup"><span data-stu-id="d56eb-118">If you want to handle mouse click events in the proper order, you need to know the order in which click events are raised in Windows Forms controls.</span></span> <span data-ttu-id="d56eb-119">Tutti i controlli Windows Form generano eventi Click nello stesso ordine quando viene premuto e rilasciato un pulsante del mouse (indipendentemente dal pulsante), fatta eccezione per i singoli controlli segnalati nell'elenco seguente.</span><span class="sxs-lookup"><span data-stu-id="d56eb-119">All Windows Forms controls raise click events in the same order when a mouse button is pressed and released (regardless of which mouse button), except where noted in the following list for individual controls.</span></span> <span data-ttu-id="d56eb-120">L'ordine degli eventi generati per un singolo clic del pulsante del mouse è il seguente:</span><span class="sxs-lookup"><span data-stu-id="d56eb-120">The following list shows the order of events raised for a single mouse-button click:</span></span>

1. <span data-ttu-id="d56eb-121">Evento<xref:System.Windows.Forms.Control.MouseDown> .</span><span class="sxs-lookup"><span data-stu-id="d56eb-121"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

2. <span data-ttu-id="d56eb-122">Evento<xref:System.Windows.Forms.Control.Click> .</span><span class="sxs-lookup"><span data-stu-id="d56eb-122"><xref:System.Windows.Forms.Control.Click> event.</span></span>

3. <span data-ttu-id="d56eb-123">Evento<xref:System.Windows.Forms.Control.MouseClick> .</span><span class="sxs-lookup"><span data-stu-id="d56eb-123"><xref:System.Windows.Forms.Control.MouseClick> event.</span></span>

4. <span data-ttu-id="d56eb-124">Evento<xref:System.Windows.Forms.Control.MouseUp> .</span><span class="sxs-lookup"><span data-stu-id="d56eb-124"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

<span data-ttu-id="d56eb-125">L'ordine degli eventi generati per un doppio clic del pulsante del mouse è il seguente:</span><span class="sxs-lookup"><span data-stu-id="d56eb-125">Following is the order of events raised for a double mouse-button click:</span></span>

1. <span data-ttu-id="d56eb-126">Evento<xref:System.Windows.Forms.Control.MouseDown> .</span><span class="sxs-lookup"><span data-stu-id="d56eb-126"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

2. <span data-ttu-id="d56eb-127">Evento<xref:System.Windows.Forms.Control.Click> .</span><span class="sxs-lookup"><span data-stu-id="d56eb-127"><xref:System.Windows.Forms.Control.Click> event.</span></span>

3. <span data-ttu-id="d56eb-128">Evento<xref:System.Windows.Forms.Control.MouseClick> .</span><span class="sxs-lookup"><span data-stu-id="d56eb-128"><xref:System.Windows.Forms.Control.MouseClick> event.</span></span>

4. <span data-ttu-id="d56eb-129">Evento<xref:System.Windows.Forms.Control.MouseUp> .</span><span class="sxs-lookup"><span data-stu-id="d56eb-129"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

5. <span data-ttu-id="d56eb-130">Evento<xref:System.Windows.Forms.Control.MouseDown> .</span><span class="sxs-lookup"><span data-stu-id="d56eb-130"><xref:System.Windows.Forms.Control.MouseDown> event.</span></span>

6. <span data-ttu-id="d56eb-131">Evento<xref:System.Windows.Forms.Control.DoubleClick> .</span><span class="sxs-lookup"><span data-stu-id="d56eb-131"><xref:System.Windows.Forms.Control.DoubleClick> event.</span></span> <span data-ttu-id="d56eb-132">Può variare se il controllo in questione ha il bit di stile <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> impostato su `true`.</span><span class="sxs-lookup"><span data-stu-id="d56eb-132">(This can vary, depending on whether the control in question has the <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> style bit set to `true`.</span></span> <span data-ttu-id="d56eb-133">Per altre informazioni sulla modalità di impostazione di un bit <xref:System.Windows.Forms.Control.SetStyle%2A>, vedere il metodo <xref:System.Windows.Forms.ControlStyles>.</span><span class="sxs-lookup"><span data-stu-id="d56eb-133">For more information about how to set a <xref:System.Windows.Forms.ControlStyles> bit, see the <xref:System.Windows.Forms.Control.SetStyle%2A> method.)</span></span>

7. <span data-ttu-id="d56eb-134">Evento<xref:System.Windows.Forms.Control.MouseDoubleClick> .</span><span class="sxs-lookup"><span data-stu-id="d56eb-134"><xref:System.Windows.Forms.Control.MouseDoubleClick> event.</span></span>

8. <span data-ttu-id="d56eb-135">Evento<xref:System.Windows.Forms.Control.MouseUp> .</span><span class="sxs-lookup"><span data-stu-id="d56eb-135"><xref:System.Windows.Forms.Control.MouseUp> event.</span></span>

<span data-ttu-id="d56eb-136">Per un esempio di codice che illustra l'ordine degli eventi click del mouse, [vedere Procedura: Gestire gli eventi di input utente nei](how-to-handle-user-input-events-in-windows-forms-controls.md)controlli Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d56eb-136">For a code example that demonstrates the order of the mouse click events, see [How to: Handle User Input Events in Windows Forms Controls](how-to-handle-user-input-events-in-windows-forms-controls.md).</span></span>

### <a name="individual-controls"></a><span data-ttu-id="d56eb-137">Controlli autonomi</span><span class="sxs-lookup"><span data-stu-id="d56eb-137">Individual Controls</span></span>

<span data-ttu-id="d56eb-138">I controlli seguenti non sono conformi al comportamento standard dell'evento Click del mouse:</span><span class="sxs-lookup"><span data-stu-id="d56eb-138">The following controls do not conform to the standard mouse click event behavior:</span></span>

- <span data-ttu-id="d56eb-139">Controlli <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.ComboBox> e <xref:System.Windows.Forms.RadioButton></span><span class="sxs-lookup"><span data-stu-id="d56eb-139"><xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.ComboBox>, and <xref:System.Windows.Forms.RadioButton> controls</span></span>

  > [!NOTE]
  > <span data-ttu-id="d56eb-140">Per il controllo <xref:System.Windows.Forms.ComboBox>, il comportamento dell'evento descritto di seguito si verifica se l'utente fa clic sul campo di modifica, sul pulsante o su una voce dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="d56eb-140">For the <xref:System.Windows.Forms.ComboBox> control, the event behavior detailed later occurs if the user clicks on the edit field, the button, or on an item within the list.</span></span>

  - <span data-ttu-id="d56eb-141">Clic con pulsante sinistro: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="d56eb-141">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="d56eb-142">Clic con pulsante destro: Nessun evento Click generato</span><span class="sxs-lookup"><span data-stu-id="d56eb-142">Right click: No click events raised</span></span>

  - <span data-ttu-id="d56eb-143">Doppio clic con pulsante sinistro: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="d56eb-143">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="d56eb-144">Doppio clic con il pulsante destro del mouse: Nessun evento Click generato</span><span class="sxs-lookup"><span data-stu-id="d56eb-144">Right double-click: No click events raised</span></span>

- <span data-ttu-id="d56eb-145">Controlli <xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox> e <xref:System.Windows.Forms.CheckedListBox></span><span class="sxs-lookup"><span data-stu-id="d56eb-145"><xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox>, and <xref:System.Windows.Forms.CheckedListBox> controls</span></span>

  > [!NOTE]
  > <span data-ttu-id="d56eb-146">Il comportamento dell'evento descritto di seguito si verifica se l'utente fa clic in un punto qualsiasi di tali controlli.</span><span class="sxs-lookup"><span data-stu-id="d56eb-146">The event behavior detailed later occurs when the user clicks anywhere within these controls.</span></span>

  - <span data-ttu-id="d56eb-147">Clic con pulsante sinistro: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="d56eb-147">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="d56eb-148">Clic con pulsante destro: Nessun evento Click generato</span><span class="sxs-lookup"><span data-stu-id="d56eb-148">Right click: No click events raised</span></span>

  - <span data-ttu-id="d56eb-149">Doppio clic con pulsante sinistro: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="d56eb-149">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="d56eb-150">Doppio clic con il pulsante destro del mouse: Nessun evento Click generato</span><span class="sxs-lookup"><span data-stu-id="d56eb-150">Right double-click: No click events raised</span></span>

- <span data-ttu-id="d56eb-151">Controllo <xref:System.Windows.Forms.ListView></span><span class="sxs-lookup"><span data-stu-id="d56eb-151"><xref:System.Windows.Forms.ListView> control</span></span>

  > [!NOTE]
  > <span data-ttu-id="d56eb-152">Il comportamento dell'evento descritto di seguito si verifica solo quando l'utente fa clic sugli elementi nel controllo <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="d56eb-152">The event behavior detailed later occurs only when the user clicks on the items in the <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="d56eb-153">Per i clic in altri punti del controllo non verranno generati eventi.</span><span class="sxs-lookup"><span data-stu-id="d56eb-153">No events are raised for clicks anywhere else on the control.</span></span> <span data-ttu-id="d56eb-154">Oltre agli eventi descritti di seguito esistono gli eventi <xref:System.Windows.Forms.ListView.BeforeLabelEdit> e <xref:System.Windows.Forms.ListView.AfterLabelEdit>, rilevanti se si desidera usare la convalida con il controllo <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="d56eb-154">In addition to the events described later, there are the <xref:System.Windows.Forms.ListView.BeforeLabelEdit> and <xref:System.Windows.Forms.ListView.AfterLabelEdit> events, which may be of interest to you if you want to use validation with the <xref:System.Windows.Forms.ListView> control.</span></span>

  - <span data-ttu-id="d56eb-155">Clic con pulsante sinistro: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="d56eb-155">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="d56eb-156">Clic con pulsante destro: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="d56eb-156">Right click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="d56eb-157">Doppio clic con pulsante sinistro: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="d56eb-157">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="d56eb-158">Doppio clic con pulsante destro: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="d56eb-158">Right double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

- <span data-ttu-id="d56eb-159">Controllo <xref:System.Windows.Forms.TreeView></span><span class="sxs-lookup"><span data-stu-id="d56eb-159"><xref:System.Windows.Forms.TreeView> control</span></span>

  > [!NOTE]
  > <span data-ttu-id="d56eb-160">Il comportamento dell'evento descritto di seguito si verifica solo quando l'utente fa clic sugli elementi stessi o a destra degli elementi nel controllo <xref:System.Windows.Forms.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="d56eb-160">The event behavior detailed later occurs only when the user clicks on the items themselves or to the right of the items in the <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="d56eb-161">Per i clic in altri punti del controllo non verranno generati eventi.</span><span class="sxs-lookup"><span data-stu-id="d56eb-161">No events are raised for clicks anywhere else on the control.</span></span> <span data-ttu-id="d56eb-162">Oltre agli eventi descritti di seguito, esistono gli eventi <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck> e <xref:System.Windows.Forms.TreeView.AfterLabelEdit>, rilevanti se si desidera usare la convalida con il controllo <xref:System.Windows.Forms.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="d56eb-162">In addition to those described later, there are the <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck>, and <xref:System.Windows.Forms.TreeView.AfterLabelEdit> events, which may be of interest to you if you want to use validation with the <xref:System.Windows.Forms.TreeView> control.</span></span>

  - <span data-ttu-id="d56eb-163">Clic con pulsante sinistro: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="d56eb-163">Left click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="d56eb-164">Clic con pulsante destro: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span><span class="sxs-lookup"><span data-stu-id="d56eb-164">Right click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick></span></span>

  - <span data-ttu-id="d56eb-165">Doppio clic con pulsante sinistro: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="d56eb-165">Left double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

  - <span data-ttu-id="d56eb-166">Doppio clic con pulsante destro: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span><span class="sxs-lookup"><span data-stu-id="d56eb-166">Right double-click: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick></span></span>

### <a name="painting-behavior-of-toggle-controls"></a><span data-ttu-id="d56eb-167">Comportamento del disegno di controlli di attivazione/disattivazione</span><span class="sxs-lookup"><span data-stu-id="d56eb-167">Painting Behavior of Toggle Controls</span></span>

<span data-ttu-id="d56eb-168">I controlli di attivazione/disattivazione, quali quelli che derivano dalla classe <xref:System.Windows.Forms.ButtonBase>, presentano il seguente comportamento di disegno distintivo in combinazione con eventi Click del mouse:</span><span class="sxs-lookup"><span data-stu-id="d56eb-168">Toggle controls, such as the controls deriving from the <xref:System.Windows.Forms.ButtonBase> class, have the following distinctive painting behavior in combination with mouse click events:</span></span>

1. <span data-ttu-id="d56eb-169">L'utente preme il pulsante del mouse.</span><span class="sxs-lookup"><span data-stu-id="d56eb-169">The user presses the mouse button.</span></span>

2. <span data-ttu-id="d56eb-170">Il controllo viene disegnato nello stato premuto.</span><span class="sxs-lookup"><span data-stu-id="d56eb-170">The control paints in the pressed state.</span></span>

3. <span data-ttu-id="d56eb-171">Viene generato l'evento <xref:System.Windows.Forms.Control.MouseDown>.</span><span class="sxs-lookup"><span data-stu-id="d56eb-171">The <xref:System.Windows.Forms.Control.MouseDown> event is raised.</span></span>

4. <span data-ttu-id="d56eb-172">L'utente rilascia il pulsante del mouse.</span><span class="sxs-lookup"><span data-stu-id="d56eb-172">The user releases the mouse button.</span></span>

5. <span data-ttu-id="d56eb-173">Il controllo viene disegnato nello stato generato.</span><span class="sxs-lookup"><span data-stu-id="d56eb-173">The control paints in the raised state.</span></span>

6. <span data-ttu-id="d56eb-174">Viene generato l'evento <xref:System.Windows.Forms.Control.Click>.</span><span class="sxs-lookup"><span data-stu-id="d56eb-174">The <xref:System.Windows.Forms.Control.Click> event is raised.</span></span>

7. <span data-ttu-id="d56eb-175">Viene generato l'evento <xref:System.Windows.Forms.Control.MouseClick>.</span><span class="sxs-lookup"><span data-stu-id="d56eb-175">The <xref:System.Windows.Forms.Control.MouseClick> event is raised.</span></span>

8. <span data-ttu-id="d56eb-176">Viene generato l'evento <xref:System.Windows.Forms.Control.MouseUp>.</span><span class="sxs-lookup"><span data-stu-id="d56eb-176">The <xref:System.Windows.Forms.Control.MouseUp> event is raised.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d56eb-177">Se l'utente sposta il puntatore all'esterno del controllo di attivazione/disattivazione mentre il pulsante del mouse è premuto, ad esempio spostando il mouse dal controllo <xref:System.Windows.Forms.Button> mentre il pulsante è premuto, il controllo di attivazione/disattivazione viene disegnato nello stato generato e si verifica solo l'evento <xref:System.Windows.Forms.Control.MouseUp>.</span><span class="sxs-lookup"><span data-stu-id="d56eb-177">If the user moves the pointer out of the toggle control while the mouse button is down (such as moving the mouse off the <xref:System.Windows.Forms.Button> control while it is pressed), the toggle control will paint in the raised state and only the <xref:System.Windows.Forms.Control.MouseUp> event occurs.</span></span> <span data-ttu-id="d56eb-178">In tale situazione l'evento <xref:System.Windows.Forms.Control.Click> o <xref:System.Windows.Forms.Control.MouseClick> non si verificherà.</span><span class="sxs-lookup"><span data-stu-id="d56eb-178">The <xref:System.Windows.Forms.Control.Click> or <xref:System.Windows.Forms.Control.MouseClick> events will not occur in this situation.</span></span>

## <a name="see-also"></a><span data-ttu-id="d56eb-179">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d56eb-179">See also</span></span>

- [<span data-ttu-id="d56eb-180">Input del mouse in un'applicazione Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d56eb-180">Mouse Input in a Windows Forms Application</span></span>](mouse-input-in-a-windows-forms-application.md)
