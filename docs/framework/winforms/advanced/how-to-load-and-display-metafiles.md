---
title: 'Procedura: caricare e visualizzare metafile'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], metafiles
- metafiles [Windows Forms], displaying
ms.assetid: 60af1714-f148-4d85-a739-0557965ffa73
ms.openlocfilehash: 6c17e0b2d023ccf80b0d32301b7ee6765edcae9f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424806"
---
# <a name="how-to-load-and-display-metafiles"></a><span data-ttu-id="4f12e-102">Procedura: caricare e visualizzare metafile</span><span class="sxs-lookup"><span data-stu-id="4f12e-102">How to: Load and Display Metafiles</span></span>
<span data-ttu-id="4f12e-103">La classe <xref:System.Drawing.Imaging.Metafile>, che eredita dalla classe <xref:System.Drawing.Image>, fornisce metodi per la registrazione, la visualizzazione e l'analisi di immagini vettoriali.</span><span class="sxs-lookup"><span data-stu-id="4f12e-103">The <xref:System.Drawing.Imaging.Metafile> class, which inherits from the <xref:System.Drawing.Image> class, provides methods for recording, displaying, and examining vector images.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f12e-104">Esempio</span><span class="sxs-lookup"><span data-stu-id="4f12e-104">Example</span></span>  
 <span data-ttu-id="4f12e-105">Per visualizzare un'immagine vettoriale (Metafile) sullo schermo, è necessario un oggetto <xref:System.Drawing.Imaging.Metafile> e un oggetto <xref:System.Drawing.Graphics>.</span><span class="sxs-lookup"><span data-stu-id="4f12e-105">To display a vector image (metafile) on the screen, you need a <xref:System.Drawing.Imaging.Metafile> object and a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="4f12e-106">Passare il nome di un file (o di un flusso) a un costruttore <xref:System.Drawing.Imaging.Metafile>.</span><span class="sxs-lookup"><span data-stu-id="4f12e-106">Pass the name of a file (or a stream) to a <xref:System.Drawing.Imaging.Metafile> constructor.</span></span> <span data-ttu-id="4f12e-107">Dopo aver creato un oggetto <xref:System.Drawing.Imaging.Metafile>, passare l'oggetto <xref:System.Drawing.Imaging.Metafile> al metodo <xref:System.Drawing.Graphics.DrawImage%2A> di un oggetto <xref:System.Drawing.Graphics>.</span><span class="sxs-lookup"><span data-stu-id="4f12e-107">After you have created a <xref:System.Drawing.Imaging.Metafile> object, pass that <xref:System.Drawing.Imaging.Metafile> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 <span data-ttu-id="4f12e-108">Nell'esempio viene creato un oggetto <xref:System.Drawing.Imaging.Metafile> da un file EMF (Enhanced Metafile), quindi viene disegnata l'immagine con l'angolo superiore sinistro in (60, 10).</span><span class="sxs-lookup"><span data-stu-id="4f12e-108">The example creates a <xref:System.Drawing.Imaging.Metafile> object from an EMF (enhanced metafile) file and then draws the image with its upper-left corner at (60, 10).</span></span>  
  
 <span data-ttu-id="4f12e-109">Nella figura seguente viene illustrato il metafile disegnato nella posizione specificata.</span><span class="sxs-lookup"><span data-stu-id="4f12e-109">The following illustration shows the metafile drawn at the specified location.</span></span>  
  
 <span data-ttu-id="4f12e-110">![Screenshot che mostra la posizione dell'immagine.](./media/how-to-load-and-display-metafiles/metafile-drawn-specified-location.png "imageposition2")</span><span class="sxs-lookup"><span data-stu-id="4f12e-110">![Screenshot showing image position.](./media/how-to-load-and-display-metafiles/metafile-drawn-specified-location.png "imageposition2")</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.WorkingWithImages#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4f12e-111">Compilazione del codice</span><span class="sxs-lookup"><span data-stu-id="4f12e-111">Compiling the Code</span></span>  
 <span data-ttu-id="4f12e-112">L'esempio precedente è progettato per l'uso con Windows Forms e richiede <xref:System.Windows.Forms.PaintEventArgs> `e`, ovvero un parametro del gestore dell'evento <xref:System.Windows.Forms.Control.Paint>.</span><span class="sxs-lookup"><span data-stu-id="4f12e-112">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f12e-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4f12e-113">See also</span></span>

- [<span data-ttu-id="4f12e-114">Utilizzo di immagini, bitmap, icone e metafile</span><span class="sxs-lookup"><span data-stu-id="4f12e-114">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
