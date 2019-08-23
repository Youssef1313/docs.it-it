---
title: 'Procedura: Creare gestori eventi in fase di esecuzione per Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, event handling
- event handlers [Windows Forms], creating
- run time [Windows Forms], creating event handlers at
- examples [Windows Forms], event handling
- Button control [Windows Forms], event handlers
ms.assetid: 2e7c9e1a-61fe-444d-8113-3c5bacf1c8cb
ms.openlocfilehash: 440086bfd5384fc46aec2997dbdd9937f7a1b65f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964324"
---
# <a name="how-to-create-event-handlers-at-run-time-for-windows-forms"></a><span data-ttu-id="f952a-102">Procedura: Creare gestori eventi in fase di esecuzione per Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f952a-102">How to: Create Event Handlers at Run Time for Windows Forms</span></span>

<span data-ttu-id="f952a-103">Oltre a creare eventi usando il Progettazione Windows Form in Visual Studio, è anche possibile creare un gestore eventi in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="f952a-103">In addition to creating events using the Windows Forms Designer in Visual Studio, you can also create an event handler at run time.</span></span> <span data-ttu-id="f952a-104">Questa azione consente di connettere i gestori eventi in base alle condizioni nel codice in fase di esecuzione invece di connetterli all'avvio iniziale del programma.</span><span class="sxs-lookup"><span data-stu-id="f952a-104">This action allows you to connect event handlers based on conditions in code at run time as opposed to having them connected when the program initially starts.</span></span>

## <a name="create-an-event-handler-at-run-time"></a><span data-ttu-id="f952a-105">Creare un gestore eventi in fase di esecuzione</span><span class="sxs-lookup"><span data-stu-id="f952a-105">Create an event handler at run time</span></span>

1. <span data-ttu-id="f952a-106">Aprire il modulo a cui si desidera aggiungere un gestore eventi.</span><span class="sxs-lookup"><span data-stu-id="f952a-106">Open the form that you want to add an event handler to.</span></span>

2. <span data-ttu-id="f952a-107">Aggiungere un metodo al modulo con la firma del metodo per l'evento che si desidera gestire.</span><span class="sxs-lookup"><span data-stu-id="f952a-107">Add a method to your form with the method signature for the event that you want to handle.</span></span>

     <span data-ttu-id="f952a-108">Se, ad esempio, si stava gestendo l' <xref:System.Windows.Forms.Control.Click> evento di un <xref:System.Windows.Forms.Button> controllo, si creerebbe un metodo come il seguente:</span><span class="sxs-lookup"><span data-stu-id="f952a-108">For example, if you were handling the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control, you would create a method such as the following:</span></span>

    ```vb
    Private Sub Button1_Click(ByVal sender As Object, ByVal e As EventArgs)
       ' Add event handler code here.
    End Sub
    ```

    ```csharp
    private void button1_Click(object sender, System.EventArgs e)
    {
    // Add event handler code here.
    }
    ```

    ```cpp
    private:
       void button1_Click(System::Object ^ sender,
          System::EventArgs ^ e)
       {
          // Add event handler code here.
       }
    ```

3. <span data-ttu-id="f952a-109">Aggiungere un codice al gestore dell'evento appropriato per l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="f952a-109">Add code to the event handler as appropriate to your application.</span></span>

4. <span data-ttu-id="f952a-110">Stabilire per quale modulo o controllo si desidera creare un gestore eventi.</span><span class="sxs-lookup"><span data-stu-id="f952a-110">Determine which form or control you want to create an event handler for.</span></span>

5. <span data-ttu-id="f952a-111">In un metodo nella classe del modulo, aggiungere il codice che specifica il gestore eventi per gestire l'evento.</span><span class="sxs-lookup"><span data-stu-id="f952a-111">In a method within your form's class, add code that specifies the event handler to handle the event.</span></span> <span data-ttu-id="f952a-112">Ad esempio, il codice seguente specifica che il gestore `button1_Click` eventi gestisce <xref:System.Windows.Forms.Control.Click> l'evento di <xref:System.Windows.Forms.Button> un controllo:</span><span class="sxs-lookup"><span data-stu-id="f952a-112">For example, the following code specifies the event handler `button1_Click` handles the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control:</span></span>

    ```vb
    AddHandler Button1.Click, AddressOf Button1_Click
    ```

    ```csharp
    button1.Click += new EventHandler(button1_Click);
    ```

    ```cpp
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);
    ```

     <span data-ttu-id="f952a-113">Il <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> metodo illustrato nel codice Visual Basic precedente stabilisce un gestore dell'evento click per il pulsante.</span><span class="sxs-lookup"><span data-stu-id="f952a-113">The <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> method demonstrated in the Visual Basic code above establishes a click event handler for the button.</span></span>

## <a name="see-also"></a><span data-ttu-id="f952a-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f952a-114">See also</span></span>

- [<span data-ttu-id="f952a-115">Creazione di gestori eventi in Windows Form</span><span class="sxs-lookup"><span data-stu-id="f952a-115">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="f952a-116">Informazioni generali sui gestori eventi</span><span class="sxs-lookup"><span data-stu-id="f952a-116">Event Handlers Overview</span></span>](event-handlers-overview-windows-forms.md)
- [<span data-ttu-id="f952a-117">Risoluzione dei problemi relativi ai gestori eventi ereditati in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f952a-117">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
