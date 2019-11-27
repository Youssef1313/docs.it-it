---
title: 'Procedura: convertire una matrice di byte in una stringa'
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- byte arrays [Visual Basic], converting to strings
- examples [Visual Basic], strings
- arrays [Visual Basic], converting to strings
ms.assetid: d0dc8317-9ab3-4324-99f7-3f5788c0e72a
ms.openlocfilehash: 8c1d9d1d2e89390873bc1c3dbb9623f047433a9a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351981"
---
# <a name="how-to-convert-an-array-of-bytes-into-a-string-in-visual-basic"></a><span data-ttu-id="42830-102">Procedura: convertire una matrice di byte in una stringa in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="42830-102">How to: Convert an Array of Bytes into a String in Visual Basic</span></span>
<span data-ttu-id="42830-103">In questo argomento viene illustrato come convertire i byte da una matrice di byte in una stringa.</span><span class="sxs-lookup"><span data-stu-id="42830-103">This topic shows how to convert the bytes from a byte array into a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42830-104">Esempio</span><span class="sxs-lookup"><span data-stu-id="42830-104">Example</span></span>  
 <span data-ttu-id="42830-105">In questo esempio viene usato il metodo <xref:System.Text.Encoding.GetString%2A> della classe di codifica <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> per convertire tutti i byte da una matrice di byte in una stringa.</span><span class="sxs-lookup"><span data-stu-id="42830-105">This example uses the <xref:System.Text.Encoding.GetString%2A> method of the <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> encoding class to convert all the bytes from a byte array into a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#72)]  
  
 <span data-ttu-id="42830-106">È possibile scegliere tra diverse opzioni di codifica per convertire una matrice di byte in una stringa:</span><span class="sxs-lookup"><span data-stu-id="42830-106">You can choose from several encoding options to convert a byte array into a string:</span></span>  
  
- <span data-ttu-id="42830-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: ottiene una codifica per il set di caratteri ASCII (7 bit).</span><span class="sxs-lookup"><span data-stu-id="42830-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Gets an encoding for the ASCII (7-bit) character set.</span></span>  
  
- <span data-ttu-id="42830-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: ottiene una codifica per il formato UTF-16 utilizzando l'ordine dei byte big-endian.</span><span class="sxs-lookup"><span data-stu-id="42830-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the big-endian byte order.</span></span>  
  
- <span data-ttu-id="42830-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: ottiene una codifica per la tabella codici ANSI corrente del sistema.</span><span class="sxs-lookup"><span data-stu-id="42830-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Gets an encoding for the system's current ANSI code page.</span></span>  
  
- <span data-ttu-id="42830-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: ottiene una codifica per il formato UTF-16 utilizzando l'ordine dei byte little-endian.</span><span class="sxs-lookup"><span data-stu-id="42830-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the little-endian byte order.</span></span>  
  
- <span data-ttu-id="42830-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: ottiene una codifica per il formato UTF-32 usando l'ordine dei byte little-endian.</span><span class="sxs-lookup"><span data-stu-id="42830-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-32 format using the little-endian byte order.</span></span>  
  
- <span data-ttu-id="42830-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: ottiene una codifica per il formato UTF-7.</span><span class="sxs-lookup"><span data-stu-id="42830-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-7 format.</span></span>  
  
- <span data-ttu-id="42830-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: ottiene una codifica per il formato UTF-8.</span><span class="sxs-lookup"><span data-stu-id="42830-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-8 format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42830-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="42830-114">See also</span></span>

- <xref:System.Text.Encoding?displayProperty=nameWithType>
- <xref:System.Text.Encoding.GetString%2A>
- [<span data-ttu-id="42830-115">Procedura: convertire stringhe in una matrice di byte in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="42830-115">How to: Convert Strings into an Array of Bytes in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-strings-into-an-array-of-bytes.md)
