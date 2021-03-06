---
title: "Procedura: eseguire la ricerca all'interno di una stringa-Visual Basic"
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
ms.openlocfilehash: fe9e50dc5458fdf8546094e5f41c2f001f1d2791
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700069"
---
# <a name="how-to-search-within-a-string-visual-basic"></a>Procedura: eseguire la ricerca all'interno di una stringa (Visual Basic)

Questo articolo illustra un esempio di come eseguire una ricerca all'interno di una stringa in Visual Basic.

## <a name="example"></a>Esempio

In questo esempio viene chiamato il metodo <xref:System.String.IndexOf%2A> su un oggetto <xref:System.String> per segnalare l'indice della prima occorrenza di una sottostringa:

 [!code-vb[VbVbalrStrings#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#71)]

## <a name="robust-programming"></a>Programmazione efficiente

Il metodo <xref:System.String.IndexOf%2A> restituisce la posizione del primo carattere della prima occorrenza della sottostringa. L'indice è in base 0, il che significa che il primo carattere di una stringa ha un indice pari a 0.

Se <xref:System.String.IndexOf%2A> non trova la sottostringa, viene restituito-1.

Il metodo <xref:System.String.IndexOf%2A> fa distinzione tra maiuscole e minuscole e usa le impostazioni cultura correnti.

Per un controllo degli errori ottimale, potrebbe essere necessario racchiudere la ricerca della stringa nel blocco `Try` di un [try... Rileva... Costruzione di istruzioni finally](../../../language-reference/statements/try-catch-finally-statement.md) .

## <a name="see-also"></a>Vedere anche

- <xref:System.String.IndexOf%2A>
- [Istruzione Try...Catch...Finally](../../../language-reference/statements/try-catch-finally-statement.md)
- [Introduzione alle stringhe in Visual Basic](introduction-to-strings.md)
- [Stringhe](index.md)
