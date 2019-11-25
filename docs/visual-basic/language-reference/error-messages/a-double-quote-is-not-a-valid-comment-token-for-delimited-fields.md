---
title: Le virgolette non sono un token di commento valido per i campi delimitati se EscapeQuote è impostato su True
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_InvalidComment
ms.assetid: 636d4b81-00ba-4cfd-98f7-4d57036f494d
ms.openlocfilehash: df7868c510eaacbad1d4421259234f4187f60cd7
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976212"
---
# <a name="a-double-quote-is-not-a-valid-comment-token-for-delimited-fields-where-escapequote-is-set-to-true"></a><span data-ttu-id="9fa0c-102">Le virgolette non sono un token di commento valido per i campi delimitati se EscapeQuote è impostato su True</span><span class="sxs-lookup"><span data-stu-id="9fa0c-102">A double quote is not a valid comment token for delimited fields where EscapeQuote is set to True</span></span>

<span data-ttu-id="9fa0c-103">Sono state fornite le virgolette come delimitatore per `TextFieldParser`, ma `EscapeQuotes` è impostato su `True`.</span><span class="sxs-lookup"><span data-stu-id="9fa0c-103">A quotation mark has been supplied as the delimiter for the `TextFieldParser`, but `EscapeQuotes` is set to `True`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9fa0c-104">Per correggere l'errore</span><span class="sxs-lookup"><span data-stu-id="9fa0c-104">To correct this error</span></span>  
  
- <span data-ttu-id="9fa0c-105">Impostare `EscapeQuotes` su `False`.</span><span class="sxs-lookup"><span data-stu-id="9fa0c-105">Set `EscapeQuotes` to `False`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fa0c-106">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9fa0c-106">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>
- [<span data-ttu-id="9fa0c-107">Procedura: leggere da file di testo delimitati da virgola</span><span class="sxs-lookup"><span data-stu-id="9fa0c-107">How to: Read From Comma-Delimited Text Files</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
