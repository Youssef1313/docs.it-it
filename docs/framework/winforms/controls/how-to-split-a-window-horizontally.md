---
title: 'Procedura: Dividere una finestra orizzontalmente'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SplitContainer control [Windows Forms], horizontal splitter
- splitter windows [Windows Forms], changing splitter orientation
- splitter windows [Windows Forms], horizontal
- windows [Windows Forms], splitting horizontally
ms.assetid: a1f74f29-048c-4723-85fa-b9d375ab8f4b
ms.openlocfilehash: 7ef3fe1210ae42c52a4fd7f23633d6566bc102a5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956065"
---
# <a name="how-to-split-a-window-horizontally"></a><span data-ttu-id="ee225-102">Procedura: Dividere una finestra orizzontalmente</span><span class="sxs-lookup"><span data-stu-id="ee225-102">How to: Split a Window Horizontally</span></span>
<span data-ttu-id="ee225-103">Nell'esempio di codice seguente viene reso la barra di divisione <xref:System.Windows.Forms.SplitContainer> che divide il controllo orizzontalmente.</span><span class="sxs-lookup"><span data-stu-id="ee225-103">The following code example makes the splitter that divides the <xref:System.Windows.Forms.SplitContainer> control horizontal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee225-104">La <xref:System.Windows.Forms.SplitContainer.Orientation%2A> proprietà<xref:System.Windows.Forms.SplitContainer> del controllo determina la direzione della barra di divisione, non del controllo stesso.</span><span class="sxs-lookup"><span data-stu-id="ee225-104">The <xref:System.Windows.Forms.SplitContainer.Orientation%2A> property of the <xref:System.Windows.Forms.SplitContainer> control determines the direction of the splitter, not of the control itself.</span></span>  
  
### <a name="to-split-a-window-horizontally"></a><span data-ttu-id="ee225-105">Per suddividere una finestra orizzontalmente</span><span class="sxs-lookup"><span data-stu-id="ee225-105">To split a window horizontally</span></span>  
  
1. <span data-ttu-id="ee225-106">All'interno di una routine, <xref:System.Windows.Forms.SplitContainer.Orientation%2A> impostare la proprietà <xref:System.Windows.Forms.SplitContainer> del controllo <xref:System.Windows.Forms.Orientation.Horizontal>su.</span><span class="sxs-lookup"><span data-stu-id="ee225-106">Within a procedure, set the <xref:System.Windows.Forms.SplitContainer.Orientation%2A> property of the <xref:System.Windows.Forms.SplitContainer> control to <xref:System.Windows.Forms.Orientation.Horizontal>.</span></span>  
  
    ```vb  
    Sub ShowSplitContainer()  
        Dim splitContainer1 as new SplitContainer()  
        splitContainer1.BorderStyle = BorderStyle.Fixed3D  
        splitContainer1.Location = New System.Drawing.Point(74, 20)  
        splitContainer1.Name = "DemoSplitContainer"  
        splitContainer1.Size = New System.Drawing.Size(212, 435)  
        splitContainer1.TabIndex = 0  
        splitContainer1.Orientation = Orientation.Horizontal  
        Controls.Add(splitContainer1)  
    End Sub  
    ```  
  
    ```csharp  
    public void showSplitContainer()  
    {  
        SplitContainer splitContainer1 = new SplitContainer ();  
        splitContainer1.BorderStyle = BorderStyle.Fixed3D;  
        splitContainer1.Location = new System.Drawing.Point (74, 20);  
        splitContainer1.Name = "DemoSplitContainer";  
        splitContainer1.Size = new System.Drawing.Size (212, 435);  
        splitContainer1.TabIndex = 0;  
        splitContainer1.Orientation = Orientation.Horizontal;  
        this.Controls.Add (splitContainer1);  
  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ee225-107">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ee225-107">See also</span></span>

- <xref:System.Windows.Forms.SplitContainer>
- [<span data-ttu-id="ee225-108">Controllo SplitContainer</span><span class="sxs-lookup"><span data-stu-id="ee225-108">SplitContainer Control</span></span>](splitcontainer-control-windows-forms.md)
