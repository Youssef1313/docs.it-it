---
title: Creazione del documento Office Open XML di origine
ms.date: 07/20/2015
ms.assetid: 61ccd6fb-0c47-4075-afdf-5b5021330f21
ms.openlocfilehash: 5f7a9baebd2d1db73ab17924e0ff8a7408637ee8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346423"
---
# <a name="creating-the-source-office-open-xml-document-visual-basic"></a><span data-ttu-id="22e0f-102">Creating the Source Office Open XML Document (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22e0f-102">Creating the Source Office Open XML Document (Visual Basic)</span></span>
<span data-ttu-id="22e0f-103">In questo argomento viene illustrato come creare il documento WordprocessingML di Office Open XML usato in altri esempi di questa esercitazione.</span><span class="sxs-lookup"><span data-stu-id="22e0f-103">This topic shows how to create the Office Open XML WordprocessingML document that the other examples in this tutorial use.</span></span> <span data-ttu-id="22e0f-104">Seguendo queste istruzioni, l'output ottenuto sarà uguale a quello indicato in ogni esempio.</span><span class="sxs-lookup"><span data-stu-id="22e0f-104">If you follow these instructions, your output will match the output provided in each example.</span></span>  
  
 <span data-ttu-id="22e0f-105">Tuttavia, gli esempi presentati in questa esercitazione funzioneranno con qualsiasi documento WordprocessingML valido.</span><span class="sxs-lookup"><span data-stu-id="22e0f-105">However, the examples in this tutorial will work with any valid WordprocessingML document.</span></span>  
  
 <span data-ttu-id="22e0f-106">Per creare il documento usato in questa esercitazione, è necessario che nel computer sia installato Microsoft Office 2007 o versione successiva oppure Microsoft Office 2003 con il pacchetto di compatibilità per Microsoft Office per i formati di file Word, Excel e PowerPoint 2007.</span><span class="sxs-lookup"><span data-stu-id="22e0f-106">To create the document that this tutorial uses, you must either have Microsoft Office 2007 or later installed, or you must have Microsoft Office 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="creating-the-wordprocessingml-document"></a><span data-ttu-id="22e0f-107">Creazione del documento WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="22e0f-107">Creating the WordprocessingML Document</span></span>  
  
#### <a name="to-create-the-wordprocessingml-document"></a><span data-ttu-id="22e0f-108">Per creare il documento WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="22e0f-108">To create the WordprocessingML document</span></span>  
  
1. <span data-ttu-id="22e0f-109">Creare un nuovo documento di Microsoft Word.</span><span class="sxs-lookup"><span data-stu-id="22e0f-109">Create a new Microsoft Word document.</span></span>  
  
2. <span data-ttu-id="22e0f-110">Incollare il testo seguente nel nuovo documento:</span><span class="sxs-lookup"><span data-stu-id="22e0f-110">Paste the following text into the new document:</span></span>  
  
    ```text  
    Parsing WordprocessingML with LINQ to XML  
  
    The following example prints to the console.  
  
    Imports System  
  
    Class Program  
        Public Shared  Sub Main(ByVal args() As String)  
            Console.WriteLine("Hello World")  
        End Sub  
    End Class  
  
    This example produces the following output:  
  
    Hello World  
    ```  
  
3. <span data-ttu-id="22e0f-111">Formattare la prima riga con lo stile "Intestazione 1".</span><span class="sxs-lookup"><span data-stu-id="22e0f-111">Format the first line with the style "Heading 1".</span></span>  
  
4. <span data-ttu-id="22e0f-112">Select the lines that contain the Visual Basic code.</span><span class="sxs-lookup"><span data-stu-id="22e0f-112">Select the lines that contain the Visual Basic code.</span></span> <span data-ttu-id="22e0f-113">La prima riga inizia con la parola chiave `Imports`.</span><span class="sxs-lookup"><span data-stu-id="22e0f-113">The first line starts with the `Imports` keyword.</span></span> <span data-ttu-id="22e0f-114">The last line is "End Class".</span><span class="sxs-lookup"><span data-stu-id="22e0f-114">The last line is "End Class".</span></span> <span data-ttu-id="22e0f-115">Formattare le righe con il tipo di carattere Courier.</span><span class="sxs-lookup"><span data-stu-id="22e0f-115">Format the lines with the courier font.</span></span> <span data-ttu-id="22e0f-116">Formattarle con un nuovo stile, da denominare "Code".</span><span class="sxs-lookup"><span data-stu-id="22e0f-116">Format them with a new style, and name the new style "Code".</span></span>  
  
5. <span data-ttu-id="22e0f-117">Infine, selezionare l'intera riga che contiene l'output e formattarla con lo stile `Code`.</span><span class="sxs-lookup"><span data-stu-id="22e0f-117">Finally, select the entire line that contains the output, and format it with the `Code` style.</span></span>  
  
6. <span data-ttu-id="22e0f-118">Salvare il documento e denominarlo SampleDoc.docx.</span><span class="sxs-lookup"><span data-stu-id="22e0f-118">Save the document, and name it SampleDoc.docx.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="22e0f-119">Se si usa Microsoft Word 2003, selezionare **Documento di Word 2007** nell'elenco a discesa **Tipo file**.</span><span class="sxs-lookup"><span data-stu-id="22e0f-119">If you are using Microsoft Word 2003, select **Word 2007 Document** in the **Save as Type** drop-down list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22e0f-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="22e0f-120">See also</span></span>

- [<span data-ttu-id="22e0f-121">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22e0f-121">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
