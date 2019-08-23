---
title: 'Procedura: Aggiungere un percorso personalizzato a una finestra di dialogo File'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Custom Place to dialog box
- adding Custom Place to dialog box
- CustomPlaces collection
ms.assetid: 63f6469b-59cd-40f6-9e61-8b5831856780
ms.openlocfilehash: 824c948fafd0a0995ad261389414d2d79918c8a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916342"
---
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="30f4d-102">Procedura: Aggiungere un percorso personalizzato a una finestra di dialogo File</span><span class="sxs-lookup"><span data-stu-id="30f4d-102">How To: Add a Custom Place to a File Dialog Box</span></span>
<span data-ttu-id="30f4d-103">Le finestre di dialogo predefinite Apri e Salva in [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] dispongono di un'area sul lato sinistro della finestra di dialogo denominata **Collegamenti preferiti**,</span><span class="sxs-lookup"><span data-stu-id="30f4d-103">The default open and save dialog boxes on [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] have an area on the left side of the dialog box titled **Favorite Links**.</span></span> <span data-ttu-id="30f4d-104">che contiene percorsi personalizzati.</span><span class="sxs-lookup"><span data-stu-id="30f4d-104">This area is called custom places.</span></span> <span data-ttu-id="30f4d-105">Le <xref:System.Windows.Forms.OpenFileDialog> classi <xref:System.Windows.Forms.SaveFileDialog> e consentono<xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> di aggiungere cartelle alla raccolta.</span><span class="sxs-lookup"><span data-stu-id="30f4d-105">The <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> classes allow you to add folders to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="30f4d-106">Affinché una posizione personalizzata venga visualizzata <xref:System.Windows.Forms.OpenFileDialog> in o <xref:System.Windows.Forms.SaveFileDialog>, la <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> proprietà deve essere impostata su `true` (impostazione predefinita).</span><span class="sxs-lookup"><span data-stu-id="30f4d-106">In order for a custom place to appear in the <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog>, the <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> property must be set to `true` (the default).</span></span>  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="30f4d-107">Per aggiungere un percorso personalizzato a una finestra di dialogo File</span><span class="sxs-lookup"><span data-stu-id="30f4d-107">To add a custom place to a file dialog box</span></span>  
  
- <span data-ttu-id="30f4d-108">Aggiungere un percorso, un GUID della cartella nota o un <xref:System.Windows.Forms.FileDialogCustomPlace> oggetto <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> alla raccolta della finestra di dialogo.</span><span class="sxs-lookup"><span data-stu-id="30f4d-108">Add a path, a Known Folder GUID, or a <xref:System.Windows.Forms.FileDialogCustomPlace> object to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection of the dialog box.</span></span>  
  
     <span data-ttu-id="30f4d-109">L'esempio di codice riportato di seguito illustra come aggiungere un percorso:</span><span class="sxs-lookup"><span data-stu-id="30f4d-109">The following code example shows how to add a path:</span></span>  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="30f4d-110">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="30f4d-110">See also</span></span>

- <xref:System.Windows.Forms.FileDialog>
- <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=nameWithType>
- [<span data-ttu-id="30f4d-111">GUID di cartella nota per percorsi personalizzati della finestra di dialogo File</span><span class="sxs-lookup"><span data-stu-id="30f4d-111">Known Folder GUIDs for File Dialog Custom Places</span></span>](known-folder-guids-for-file-dialog-custom-places.md)
