---
title: 'How to: read from comma-delimited text files'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- reading text files [Visual Basic], comma-delimited
- text files [Visual Basic], reading
ms.assetid: a8413fe4-0dba-49c8-8692-44fb67a9ec4f
ms.openlocfilehash: 9b93893e2221b156b65ce8e945089269ea28c989
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335068"
---
# <a name="how-to-read-from-comma-delimited-text-files-in-visual-basic"></a><span data-ttu-id="4ba75-102">Procedura: Leggere da file di testo con valori delimitati da virgole in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4ba75-102">How to: read from comma-delimited text files in Visual Basic</span></span>

<span data-ttu-id="4ba75-103">L'oggetto `TextFieldParser` consente di analizzare in modo facile ed efficace i file di testo strutturati, ad esempio i log.</span><span class="sxs-lookup"><span data-stu-id="4ba75-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span> <span data-ttu-id="4ba75-104">La proprietà `TextFieldType` definisce se si tratta di un file delimitato o di un file con campi di testo a larghezza fissa.</span><span class="sxs-lookup"><span data-stu-id="4ba75-104">The `TextFieldType` property defines whether it is a delimited file or one with fixed-width fields of text.</span></span>  
  
### <a name="to-parse-a-comma-delimited-text-file"></a><span data-ttu-id="4ba75-105">Per analizzare un file di testo con valori delimitati da virgole</span><span class="sxs-lookup"><span data-stu-id="4ba75-105">To parse a comma delimited text file</span></span>  
  
1. <span data-ttu-id="4ba75-106">Creare un nuovo oggetto `TextFieldParser`.</span><span class="sxs-lookup"><span data-stu-id="4ba75-106">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="4ba75-107">Il codice riportato di seguito crea l'oggetto `TextFieldParser` denominato `MyReader` e apre il file `test.txt`.</span><span class="sxs-lookup"><span data-stu-id="4ba75-107">The following code creates the `TextFieldParser` named `MyReader` and opens the file `test.txt`.</span></span>  
  
     [!code-vb[VbFileIORead#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#15)]  
  
2. <span data-ttu-id="4ba75-108">Definire il tipo `TextField` e il delimitatore.</span><span class="sxs-lookup"><span data-stu-id="4ba75-108">Define the `TextField` type and delimiter.</span></span> <span data-ttu-id="4ba75-109">Nel codice riportato di seguito viene definita la proprietà `TextFieldType` come `Delimited` e il delimitatore come ",".</span><span class="sxs-lookup"><span data-stu-id="4ba75-109">The following code defines the `TextFieldType` property as `Delimited` and the delimiter as ",".</span></span>  
  
     [!code-vb[VbFileIORead#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#16)]  
  
3. <span data-ttu-id="4ba75-110">Eseguire il ciclo attraverso i campi nel file.</span><span class="sxs-lookup"><span data-stu-id="4ba75-110">Loop through the fields in the file.</span></span> <span data-ttu-id="4ba75-111">Se sono presenti righe danneggiate, segnalare un errore e continuare l'analisi.</span><span class="sxs-lookup"><span data-stu-id="4ba75-111">If any lines are corrupt, report an error and continue parsing.</span></span> <span data-ttu-id="4ba75-112">Nel codice riportato di seguito viene eseguito un ciclo attraverso il file, visualizzando ogni campo e segnalando eventuali campi formattati in modo errato.</span><span class="sxs-lookup"><span data-stu-id="4ba75-112">The following code loops through the file, displaying each field in turn and reporting any fields that are formatted incorrectly.</span></span>  
  
     [!code-vb[VbFileIORead#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#17)]  
  
4. <span data-ttu-id="4ba75-113">Chiudere i blocchi `While` e `Using` con `End While` ed `End Using`.</span><span class="sxs-lookup"><span data-stu-id="4ba75-113">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#18)]  
  
## <a name="example"></a><span data-ttu-id="4ba75-114">Esempio</span><span class="sxs-lookup"><span data-stu-id="4ba75-114">Example</span></span>  

 <span data-ttu-id="4ba75-115">Nell'esempio riportato di seguito viene letto il file `test.txt`.</span><span class="sxs-lookup"><span data-stu-id="4ba75-115">This example reads from the file `test.txt`.</span></span>  
  
 [!code-vb[VbFileIORead#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a><span data-ttu-id="4ba75-116">Programmazione efficiente</span><span class="sxs-lookup"><span data-stu-id="4ba75-116">Robust programming</span></span>  

 <span data-ttu-id="4ba75-117">Le seguenti condizioni possono generare un'eccezione:</span><span class="sxs-lookup"><span data-stu-id="4ba75-117">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="4ba75-118">Impossibile analizzare la riga usando il formato specificato (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span><span class="sxs-lookup"><span data-stu-id="4ba75-118">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="4ba75-119">Il messaggio di eccezione specifica la riga che ha generato l'eccezione, mentre alla proprietà <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> viene assegnato il testo contenuto nella riga.</span><span class="sxs-lookup"><span data-stu-id="4ba75-119">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned the text contained in the line.</span></span>  
  
- <span data-ttu-id="4ba75-120">File specificato inesistente (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="4ba75-120">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="4ba75-121">Un contesto di attendibilità parziale in cui gli utenti non dispongono di autorizzazioni sufficienti per accedere al file</span><span class="sxs-lookup"><span data-stu-id="4ba75-121">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="4ba75-122">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="4ba75-122">(<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="4ba75-123">Percorso del file troppo lungo (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="4ba75-123">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="4ba75-124">L'utente non dispone di autorizzazioni sufficienti per accedere al file (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="4ba75-124">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ba75-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4ba75-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [<span data-ttu-id="4ba75-126">Procedura: leggere da file di testo a larghezza fissa</span><span class="sxs-lookup"><span data-stu-id="4ba75-126">How to: Read From Fixed-width Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="4ba75-127">Procedura: leggere da file di testo con più formati</span><span class="sxs-lookup"><span data-stu-id="4ba75-127">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="4ba75-128">Analisi dei file di testo con l'oggetto TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="4ba75-128">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="4ba75-129">Procedura dettagliata: Modifica di file e directory in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4ba75-129">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="4ba75-130">Risoluzione dei problemi: lettura e scrittura nei file di testo</span><span class="sxs-lookup"><span data-stu-id="4ba75-130">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
