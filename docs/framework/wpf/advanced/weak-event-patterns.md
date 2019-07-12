---
title: Modelli di eventi deboli
ms.date: 03/30/2017
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
ms.openlocfilehash: 61e7f6d29cf9275004238ca776d5af9bf027004f
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859919"
---
# <a name="weak-event-patterns"></a><span data-ttu-id="439cd-102">Modelli di eventi deboli</span><span class="sxs-lookup"><span data-stu-id="439cd-102">Weak Event Patterns</span></span>
<span data-ttu-id="439cd-103">Nelle applicazioni, è possibile che i gestori associati alle origini evento non verranno distrutto in combinazione con l'oggetto listener che è associato il gestore per l'origine.</span><span class="sxs-lookup"><span data-stu-id="439cd-103">In applications, it is possible that handlers that are attached to event sources will not be destroyed in coordination with the listener object that attached the handler to the source.</span></span> <span data-ttu-id="439cd-104">Questa situazione può causare perdite di memoria.</span><span class="sxs-lookup"><span data-stu-id="439cd-104">This situation can lead to memory leaks.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="439cd-105">introduce un modello di progettazione che può essere utilizzato per risolvere questo problema, fornendo una classe di gestione dedicato per determinati eventi e implementando un'interfaccia nei listener per l'evento.</span><span class="sxs-lookup"><span data-stu-id="439cd-105">introduces a design pattern that can be used to address this issue, by providing a dedicated manager class for particular events and implementing an interface on listeners for that event.</span></span> <span data-ttu-id="439cd-106">Questo schema progettuale è noto come il *modello di eventi deboli*.</span><span class="sxs-lookup"><span data-stu-id="439cd-106">This design pattern is known as the *weak event pattern*.</span></span>  
  
## <a name="why-implement-the-weak-event-pattern"></a><span data-ttu-id="439cd-107">Il motivo per cui implementare il modello di eventi deboli?</span><span class="sxs-lookup"><span data-stu-id="439cd-107">Why Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="439cd-108">In ascolto degli eventi può causare perdite di memoria.</span><span class="sxs-lookup"><span data-stu-id="439cd-108">Listening for events can lead to memory leaks.</span></span> <span data-ttu-id="439cd-109">La tecnica tipica per l'ascolto di un evento consiste nell'usare la sintassi specifica del linguaggio che associa un gestore a un evento su un'origine.</span><span class="sxs-lookup"><span data-stu-id="439cd-109">The typical technique for listening to an event is to use the language-specific syntax that attaches a handler to an event on a source.</span></span> <span data-ttu-id="439cd-110">Ad esempio, in C#, che la sintassi è: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.</span><span class="sxs-lookup"><span data-stu-id="439cd-110">For example, in C#, that syntax is: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.</span></span>  
  
 <span data-ttu-id="439cd-111">Questa tecnica consente di creare un riferimento sicuro dall'origine evento per il listener di eventi.</span><span class="sxs-lookup"><span data-stu-id="439cd-111">This technique creates a strong reference from the event source to the event listener.</span></span> <span data-ttu-id="439cd-112">In genere, collegare un gestore eventi per un listener, fa sì che il listener avere una durata degli oggetti che è influenzata dalla durata dell'oggetto di origine (a meno che il gestore eventi viene rimosso in modo esplicito).</span><span class="sxs-lookup"><span data-stu-id="439cd-112">Ordinarily, attaching an event handler for a listener causes the listener to have an object lifetime that is influenced by the object lifetime of the source (unless the event handler is explicitly removed).</span></span> <span data-ttu-id="439cd-113">Ma in alcune circostanze, potrebbe essere consigliabile la durata dell'oggetto del listener da parte di altri fattori, ad esempio se attualmente a cui appartiene la struttura ad albero visuale dell'applicazione e non dalla durata dell'origine.</span><span class="sxs-lookup"><span data-stu-id="439cd-113">But in certain circumstances, you might want the object lifetime of the listener to be controlled by other factors, such as whether it currently belongs to the visual tree of the application, and not by the lifetime of the source.</span></span> <span data-ttu-id="439cd-114">Ogni volta che la durata dell'oggetto di origine si estende oltre la durata dell'oggetto del listener, il modello di eventi normali comporta una perdita di memoria: il listener viene mantenuto attivo più a lungo del previsto.</span><span class="sxs-lookup"><span data-stu-id="439cd-114">Whenever the source object lifetime extends beyond the object lifetime of the listener, the normal event pattern leads to a memory leak: the listener is kept alive longer than intended.</span></span>  
  
 <span data-ttu-id="439cd-115">Il modello di eventi deboli è progettato per risolvere questo problema di perdita di memoria.</span><span class="sxs-lookup"><span data-stu-id="439cd-115">The weak event pattern is designed to solve this memory leak problem.</span></span> <span data-ttu-id="439cd-116">Il modello di eventi deboli può essere usato ogni volta che un listener deve effettuare la registrazione per un evento, ma il listener non sa in modo esplicito quando annullare la registrazione.</span><span class="sxs-lookup"><span data-stu-id="439cd-116">The weak event pattern can be used whenever a listener needs to register for an event, but the listener does not explicitly know when to unregister.</span></span> <span data-ttu-id="439cd-117">Il modello di eventi deboli può essere usato anche ogni volta che la durata dell'oggetto di origine supera la durata utile del listener.</span><span class="sxs-lookup"><span data-stu-id="439cd-117">The weak event pattern can also be used whenever the object lifetime of the source exceeds the useful object lifetime of the listener.</span></span> <span data-ttu-id="439cd-118">(In questo caso *utile* è determinato dall'utente.) Il modello di eventi deboli consente il listener per registrarsi e ricevere l'evento senza influire sulle caratteristiche di durata del listener in alcun modo.</span><span class="sxs-lookup"><span data-stu-id="439cd-118">(In this case, *useful* is determined by you.) The weak event pattern allows the listener to register for and receive the event without affecting the object lifetime characteristics of the listener in any way.</span></span> <span data-ttu-id="439cd-119">In effetti, il riferimento implicito dall'origine non determina se il listener è idoneo per garbage collection.</span><span class="sxs-lookup"><span data-stu-id="439cd-119">In effect, the implied reference from the source does not determine whether the listener is eligible for garbage collection.</span></span> <span data-ttu-id="439cd-120">Il riferimento è un riferimento debole, in questo modo la denominazione del modello di eventi deboli e le API correlate.</span><span class="sxs-lookup"><span data-stu-id="439cd-120">The reference is a weak reference, thus the naming of the weak event pattern and the related APIs.</span></span> <span data-ttu-id="439cd-121">Il listener può essere garbage collection o altrimenti eliminato e l'origine può continuare senza mantenere riferimenti al gestore creare per un oggetto ora eliminato.</span><span class="sxs-lookup"><span data-stu-id="439cd-121">The listener can be garbage collected or otherwise destroyed, and the source can continue without retaining noncollectible handler references to a now destroyed object.</span></span>  
  
## <a name="who-should-implement-the-weak-event-pattern"></a><span data-ttu-id="439cd-122">Chi deve implementare il modello di eventi deboli?</span><span class="sxs-lookup"><span data-stu-id="439cd-122">Who Should Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="439cd-123">Implementazione del pattern di eventi deboli è interessante principalmente per gli autori di controlli.</span><span class="sxs-lookup"><span data-stu-id="439cd-123">Implementing the weak event pattern is interesting primarily for control authors.</span></span> <span data-ttu-id="439cd-124">Quando si crea un controllo, si è in gran parte responsabile per il comportamento e il contenimento del proprio controllo e l'impatto che ha su applicazioni in cui viene inserito.</span><span class="sxs-lookup"><span data-stu-id="439cd-124">As a control author, you are largely responsible for the behavior and containment of your control and the impact it has on applications in which it is inserted.</span></span> <span data-ttu-id="439cd-125">Ciò include il comportamento della durata degli oggetti controllo, in particolare la gestione del problema di perdita di memoria descritta.</span><span class="sxs-lookup"><span data-stu-id="439cd-125">This includes the control object lifetime behavior, in particular the handling of the described memory leak problem.</span></span>  
  
 <span data-ttu-id="439cd-126">Alcuni scenari intrinsecamente si prestano all'applicazione del modello di eventi deboli.</span><span class="sxs-lookup"><span data-stu-id="439cd-126">Certain scenarios inherently lend themselves to the application of the weak event pattern.</span></span> <span data-ttu-id="439cd-127">Uno di questi scenari è l'associazione dati.</span><span class="sxs-lookup"><span data-stu-id="439cd-127">One such scenario is data binding.</span></span> <span data-ttu-id="439cd-128">Nel data binding, è comune per l'oggetto di origine sia completamente indipendente da dell'oggetto del listener, ovvero una destinazione di un'associazione.</span><span class="sxs-lookup"><span data-stu-id="439cd-128">In data binding, it is common for the source object to be completely independent of the listener object, which is a target of a binding.</span></span> <span data-ttu-id="439cd-129">Molti aspetti di [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] un data binding già sono il modello di eventi deboli applicato nel modo in cui vengono implementati gli eventi.</span><span class="sxs-lookup"><span data-stu-id="439cd-129">Many aspects of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] data binding already have the weak event pattern applied in how the events are implemented.</span></span>  
  
## <a name="how-to-implement-the-weak-event-pattern"></a><span data-ttu-id="439cd-130">Come implementare il modello di eventi deboli</span><span class="sxs-lookup"><span data-stu-id="439cd-130">How to Implement the Weak Event Pattern</span></span>  
 <span data-ttu-id="439cd-131">Esistono tre modi per implementare il modello di eventi deboli.</span><span class="sxs-lookup"><span data-stu-id="439cd-131">There are three ways to implement weak event pattern.</span></span> <span data-ttu-id="439cd-132">Nella tabella seguente sono elencati tre approcci e fornisce alcune linee guida per quando è consigliabile utilizzarlo.</span><span class="sxs-lookup"><span data-stu-id="439cd-132">The following table lists the three approaches and provides some guidance for when you should use each.</span></span>  
  
|<span data-ttu-id="439cd-133">Approccio</span><span class="sxs-lookup"><span data-stu-id="439cd-133">Approach</span></span>|<span data-ttu-id="439cd-134">Quando implementare</span><span class="sxs-lookup"><span data-stu-id="439cd-134">When to Implement</span></span>|  
|--------------|-----------------------|  
|<span data-ttu-id="439cd-135">Usare una classe di gestione di eventi deboli esistente</span><span class="sxs-lookup"><span data-stu-id="439cd-135">Use an existing weak event manager class</span></span>|<span data-ttu-id="439cd-136">Se l'evento che si desidera eseguire la sottoscrizione ha un corrispondente <xref:System.Windows.WeakEventManager>, usare il gestore di eventi deboli esistente.</span><span class="sxs-lookup"><span data-stu-id="439cd-136">If the event you want to subscribe to has a corresponding <xref:System.Windows.WeakEventManager>, use the existing weak event manager.</span></span> <span data-ttu-id="439cd-137">Per un elenco di gestori di eventi deboli incluse in WPF, vedere la gerarchia di ereditarietà nel <xref:System.Windows.WeakEventManager> classe.</span><span class="sxs-lookup"><span data-stu-id="439cd-137">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span> <span data-ttu-id="439cd-138">Poiché i gestori di eventi deboli incluso sono limitati, probabilmente sarà necessario scegliere uno degli altri approcci.</span><span class="sxs-lookup"><span data-stu-id="439cd-138">Because the included weak event managers are limited, you will probably need to choose one of the other approaches.</span></span>|  
|<span data-ttu-id="439cd-139">Usare una classe di gestione di eventi deboli generico</span><span class="sxs-lookup"><span data-stu-id="439cd-139">Use a generic weak event manager class</span></span>|<span data-ttu-id="439cd-140">Usare un oggetto generico <xref:System.Windows.WeakEventManager%602> quando un oggetto esistente <xref:System.Windows.WeakEventManager> sono non disponibile, è necessario un modo semplice per implementare e non si è preoccupati dell'efficienza.</span><span class="sxs-lookup"><span data-stu-id="439cd-140">Use a generic <xref:System.Windows.WeakEventManager%602> when an existing <xref:System.Windows.WeakEventManager> is not available, you want an easy way to implement, and you are not concerned about efficiency.</span></span> <span data-ttu-id="439cd-141">Il tipo generico <xref:System.Windows.WeakEventManager%602> è meno efficiente rispetto a un gestore di eventi deboli esistenti o personalizzate.</span><span class="sxs-lookup"><span data-stu-id="439cd-141">The generic <xref:System.Windows.WeakEventManager%602> is less efficient than an existing or custom weak event manager.</span></span> <span data-ttu-id="439cd-142">Ad esempio, la classe generica non più la reflection per individuare l'evento specificato il nome dell'evento.</span><span class="sxs-lookup"><span data-stu-id="439cd-142">For example, the generic class does more reflection to discover the event given the event's name.</span></span> <span data-ttu-id="439cd-143">Inoltre, il codice per registrare l'evento utilizzando il tipo generico <xref:System.Windows.WeakEventManager%602> è più dettagliato rispetto all'uso di un oggetto esistente o personalizzato <xref:System.Windows.WeakEventManager>.</span><span class="sxs-lookup"><span data-stu-id="439cd-143">Also, the code to register the event by using the generic <xref:System.Windows.WeakEventManager%602> is more verbose than using an existing or custom <xref:System.Windows.WeakEventManager>.</span></span>|  
|<span data-ttu-id="439cd-144">Creare una classe di gestione di eventi deboli personalizzato</span><span class="sxs-lookup"><span data-stu-id="439cd-144">Create a custom weak event manager class</span></span>|<span data-ttu-id="439cd-145">Creare una classe personalizzata <xref:System.Windows.WeakEventManager> quando un oggetto esistente <xref:System.Windows.WeakEventManager> non è disponibile e si desidera che un sistema più efficiente.</span><span class="sxs-lookup"><span data-stu-id="439cd-145">Create a custom <xref:System.Windows.WeakEventManager> when an existing <xref:System.Windows.WeakEventManager> is not available and you want the best efficiency.</span></span> <span data-ttu-id="439cd-146">Usando un oggetto personalizzato <xref:System.Windows.WeakEventManager> per sottoscrivere un evento sarà più efficiente, ma è necessario sostenere il costo di scrivere altro codice all'inizio.</span><span class="sxs-lookup"><span data-stu-id="439cd-146">Using a custom <xref:System.Windows.WeakEventManager> to subscribe to an event will be more efficient, but you do incur the cost of writing more code at the beginning.</span></span>|  
|<span data-ttu-id="439cd-147">Usare un gestore di eventi deboli di terze parti</span><span class="sxs-lookup"><span data-stu-id="439cd-147">Use a third-party weak event manager</span></span>|<span data-ttu-id="439cd-148">NuGet ha [alcuni gestori di eventi deboli](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) e molti framework WPF supportano anche il modello (ad esempio, vedere [documentazione di Prism nella sottoscrizione di eventi loosely-coupled](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/Communication.md#subscribing-to-events)).</span><span class="sxs-lookup"><span data-stu-id="439cd-148">NuGet has [several weak event managers](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) and many WPF frameworks also support the pattern (for instance, see [Prism's documentation on loosely coupled event subscription](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/Communication.md#subscribing-to-events)).</span></span>|

 <span data-ttu-id="439cd-149">Le sezioni seguenti descrivono come implementare il modello di eventi deboli.</span><span class="sxs-lookup"><span data-stu-id="439cd-149">The following sections describe how to implement the weak event pattern.</span></span>  <span data-ttu-id="439cd-150">Ai fini di questa discussione, l'evento da sottoscrivere presenta le caratteristiche seguenti.</span><span class="sxs-lookup"><span data-stu-id="439cd-150">For purposes of this discussion, the event to subscribe to has the following characteristics.</span></span>  
  
- <span data-ttu-id="439cd-151">Il nome dell'evento è `SomeEvent`.</span><span class="sxs-lookup"><span data-stu-id="439cd-151">The event name is `SomeEvent`.</span></span>  
  
- <span data-ttu-id="439cd-152">L'evento viene generato dal `EventSource` classe.</span><span class="sxs-lookup"><span data-stu-id="439cd-152">The event is raised by the `EventSource` class.</span></span>  
  
- <span data-ttu-id="439cd-153">Il gestore dell'evento è di tipo: `SomeEventEventHandler` (o `EventHandler<SomeEventEventArgs>`).</span><span class="sxs-lookup"><span data-stu-id="439cd-153">The event handler has type: `SomeEventEventHandler` (or `EventHandler<SomeEventEventArgs>`).</span></span>  
  
- <span data-ttu-id="439cd-154">L'evento passato un parametro di tipo `SomeEventEventArgs` ai gestori eventi.</span><span class="sxs-lookup"><span data-stu-id="439cd-154">The event passes a parameter of type `SomeEventEventArgs` to the event handlers.</span></span>  
  
### <a name="using-an-existing-weak-event-manager-class"></a><span data-ttu-id="439cd-155">Usando una classe di gestore di eventi deboli esistente</span><span class="sxs-lookup"><span data-stu-id="439cd-155">Using an Existing Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="439cd-156">Trovare un evento debole esistente di gestione.</span><span class="sxs-lookup"><span data-stu-id="439cd-156">Find an existing weak event manager.</span></span>  
  
     <span data-ttu-id="439cd-157">Per un elenco di gestori di eventi deboli incluse in WPF, vedere la gerarchia di ereditarietà nel <xref:System.Windows.WeakEventManager> classe.</span><span class="sxs-lookup"><span data-stu-id="439cd-157">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
2. <span data-ttu-id="439cd-158">Utilizzare la gestione degli eventi debole anziché l'associazione dell'evento normale.</span><span class="sxs-lookup"><span data-stu-id="439cd-158">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="439cd-159">Ad esempio, se il codice Usa il modello seguente per sottoscrivere un evento:</span><span class="sxs-lookup"><span data-stu-id="439cd-159">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="439cd-160">Sostituirlo con il modello seguente:</span><span class="sxs-lookup"><span data-stu-id="439cd-160">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="439cd-161">Analogamente, se il codice Usa il modello seguente per annullare la sottoscrizione a un evento:</span><span class="sxs-lookup"><span data-stu-id="439cd-161">Similarly, if your code uses the following pattern to unsubscribe from an event:</span></span>  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="439cd-162">Sostituirlo con il modello seguente:</span><span class="sxs-lookup"><span data-stu-id="439cd-162">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a><span data-ttu-id="439cd-163">Usando la classe generica di gestione degli eventi deboli</span><span class="sxs-lookup"><span data-stu-id="439cd-163">Using the Generic Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="439cd-164">Usare il tipo generico <xref:System.Windows.WeakEventManager%602> classe invece l'associazione dell'evento normale.</span><span class="sxs-lookup"><span data-stu-id="439cd-164">Use the generic <xref:System.Windows.WeakEventManager%602> class instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="439cd-165">Quando si usa <xref:System.Windows.WeakEventManager%602> per registrare i listener di eventi, è specificare l'origine evento e <xref:System.EventArgs> tipo dei parametri di tipo di classe e chiamare <xref:System.Windows.WeakEventManager%602.AddHandler%2A> come illustrato nel codice seguente:</span><span class="sxs-lookup"><span data-stu-id="439cd-165">When you use <xref:System.Windows.WeakEventManager%602> to register event listeners, you supply the event source and <xref:System.EventArgs> type as the type parameters to the class and call <xref:System.Windows.WeakEventManager%602.AddHandler%2A> as shown in the following code:</span></span>  
  
    ```  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a><span data-ttu-id="439cd-166">Creazione di una classe di gestione di eventi deboli personalizzato</span><span class="sxs-lookup"><span data-stu-id="439cd-166">Creating a Custom Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="439cd-167">Copiare il modello di classe seguente al progetto.</span><span class="sxs-lookup"><span data-stu-id="439cd-167">Copy the following class template to your project.</span></span>  
  
     <span data-ttu-id="439cd-168">Questa classe eredita dal <xref:System.Windows.WeakEventManager> classe.</span><span class="sxs-lookup"><span data-stu-id="439cd-168">This class inherits from the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2. <span data-ttu-id="439cd-169">Sostituire il `SomeEventWeakEventManager` nome con il proprio nome.</span><span class="sxs-lookup"><span data-stu-id="439cd-169">Replace the `SomeEventWeakEventManager` name with your own name.</span></span>  
  
3. <span data-ttu-id="439cd-170">Sostituire i nomi di tre descritti in precedenza con i nomi corrispondenti per l'evento.</span><span class="sxs-lookup"><span data-stu-id="439cd-170">Replace the three names described previously with the corresponding names for your event.</span></span> <span data-ttu-id="439cd-171">(`SomeEvent`, `EventSource`, e `SomeEventEventArgs`)</span><span class="sxs-lookup"><span data-stu-id="439cd-171">(`SomeEvent`, `EventSource`, and `SomeEventEventArgs`)</span></span>  
  
4. <span data-ttu-id="439cd-172">Impostare la visibilità (pubblica / interna / privata) della classe della gestione di eventi deboli per eventi che gestisce la stessa visibilità.</span><span class="sxs-lookup"><span data-stu-id="439cd-172">Set the visibility (public / internal / private) of the weak event manager class to the same visibility as event it manages.</span></span>  
  
5. <span data-ttu-id="439cd-173">Utilizzare la gestione degli eventi debole anziché l'associazione dell'evento normale.</span><span class="sxs-lookup"><span data-stu-id="439cd-173">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="439cd-174">Ad esempio, se il codice Usa il modello seguente per sottoscrivere un evento:</span><span class="sxs-lookup"><span data-stu-id="439cd-174">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="439cd-175">Sostituirlo con il modello seguente:</span><span class="sxs-lookup"><span data-stu-id="439cd-175">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="439cd-176">Analogamente, se il codice Usa il modello seguente per annullare la sottoscrizione a un evento:</span><span class="sxs-lookup"><span data-stu-id="439cd-176">Similarly, if your code uses the following pattern to unsubscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     <span data-ttu-id="439cd-177">Sostituirlo con il modello seguente:</span><span class="sxs-lookup"><span data-stu-id="439cd-177">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="439cd-178">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="439cd-178">See also</span></span>

- <xref:System.Windows.WeakEventManager>
- <xref:System.Windows.IWeakEventListener>
- [<span data-ttu-id="439cd-179">Cenni preliminari sugli eventi indirizzati</span><span class="sxs-lookup"><span data-stu-id="439cd-179">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="439cd-180">Panoramica sul data binding</span><span class="sxs-lookup"><span data-stu-id="439cd-180">Data Binding Overview</span></span>](../data/data-binding-overview.md)
