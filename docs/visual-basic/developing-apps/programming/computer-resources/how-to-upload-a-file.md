---
title: 'Procedura: caricare un file'
ms.date: 07/20/2015
helpviewer_keywords:
- networks, uploading files
- files [Visual Basic], uploading
- uploading files [Visual Basic]
- UploadFile method [Visual Basic]
- My.Computer.Network.UploadFile method
ms.assetid: a8b37924-c523-4fd3-b5ca-cb0074df29cd
ms.openlocfilehash: 52b731606c74ab7ff06a42dfdbe078616ba33d88
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345565"
---
# <a name="how-to-upload-a-file-in-visual-basic"></a><span data-ttu-id="e168b-102">Procedura: caricare un file in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e168b-102">How to: Upload a File in Visual Basic</span></span>

<span data-ttu-id="e168b-103">Il metodo <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> consente di caricare un file e archiviarlo in un percorso remoto.</span><span class="sxs-lookup"><span data-stu-id="e168b-103">The <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> method can be used to upload a file and store it to a remote location.</span></span> <span data-ttu-id="e168b-104">Se il parametro `ShowUI` è impostato su `True`, viene visualizzata una finestra di dialogo che mostra lo stato di avanzamento del processo di caricamento e consente agli utenti di annullare l'operazione.</span><span class="sxs-lookup"><span data-stu-id="e168b-104">If the `ShowUI` parameter is set to `True`, a dialog box is displayed that shows the progress of the upload and allows users to cancel the operation.</span></span>  
  
### <a name="to-upload-a-file"></a><span data-ttu-id="e168b-105">Per caricare un file</span><span class="sxs-lookup"><span data-stu-id="e168b-105">To upload a file</span></span>  
  
- <span data-ttu-id="e168b-106">Usare il metodo `UploadFile` per caricare un file, specificando il percorso del file di origine e il percorso della directory di destinazione come stringa o URI (Uniform Resource Identifier). Nell'esempio riportato di seguito il file `Order.txt` viene caricato in `http://www.cohowinery.com/uploads.aspx`.</span><span class="sxs-lookup"><span data-stu-id="e168b-106">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI (Uniform Resource Identifier).This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`.</span></span>  
  
     [!code-vb[VbResourceTasks#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#6)]  
  
### <a name="to-upload-a-file-and-show-the-progress-of-the-operation"></a><span data-ttu-id="e168b-107">Per caricare un file e visualizzare lo stato di avanzamento dell'operazione</span><span class="sxs-lookup"><span data-stu-id="e168b-107">To upload a file and show the progress of the operation</span></span>  
  
- <span data-ttu-id="e168b-108">Usare il metodo `UploadFile` per caricare un file, specificando il percorso del file di origine e il percorso della directory di destinazione come stringa o URI.</span><span class="sxs-lookup"><span data-stu-id="e168b-108">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI.</span></span> <span data-ttu-id="e168b-109">Nell'esempio riportato di seguito il file `Order.txt` viene caricato in `http://www.cohowinery.com/uploads.aspx` senza specificare un nome utente o una password, viene visualizzato lo stato di avanzamento del processo di caricamento ed è previsto un intervallo di timeout di 500 millisecondi.</span><span class="sxs-lookup"><span data-stu-id="e168b-109">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx` without supplying a user name or password, shows the progress of the upload, and has a time-out interval of 500 milliseconds.</span></span>  
  
     [!code-vb[VbResourceTasks#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#7)]  
  
### <a name="to-upload-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="e168b-110">Per caricare un file, specificando un nome utente e una password</span><span class="sxs-lookup"><span data-stu-id="e168b-110">To upload a file, supplying a user name and password</span></span>  
  
- <span data-ttu-id="e168b-111">Usare il metodo `UploadFile` per caricare un file, specificando il percorso del file di origine e il percorso della directory di destinazione come stringa o URI e indicando il nome utente e la password.</span><span class="sxs-lookup"><span data-stu-id="e168b-111">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI, and specifying the user name and the password.</span></span> <span data-ttu-id="e168b-112">Nell'esempio riportato di seguito il file `Order.txt` viene caricato in `http://www.cohowinery.com/uploads.aspx` specificando il nome utente `anonymous` e una password vuota.</span><span class="sxs-lookup"><span data-stu-id="e168b-112">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`, supplying the user name `anonymous` and a blank password.</span></span>  
  
     [!code-vb[VbResourceTasks#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="e168b-113">Programmazione efficiente</span><span class="sxs-lookup"><span data-stu-id="e168b-113">Robust Programming</span></span>  

 <span data-ttu-id="e168b-114">Le condizioni seguenti possono generare un'eccezione:</span><span class="sxs-lookup"><span data-stu-id="e168b-114">The following conditions may throw an exception:</span></span>  
  
- <span data-ttu-id="e168b-115">Il percorso file locale non è valido (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="e168b-115">The local file path is not valid (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="e168b-116">Autenticazione non riuscita (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="e168b-116">Authentication failed (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="e168b-117">Timeout della connessione (<xref:System.TimeoutException>).</span><span class="sxs-lookup"><span data-stu-id="e168b-117">The connection timed out (<xref:System.TimeoutException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e168b-118">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e168b-118">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>
- [<span data-ttu-id="e168b-119">Procedura: Scaricare file</span><span class="sxs-lookup"><span data-stu-id="e168b-119">How to: Download a File</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-download-a-file.md)
- [<span data-ttu-id="e168b-120">Procedura: analizzare percorsi di file</span><span class="sxs-lookup"><span data-stu-id="e168b-120">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
