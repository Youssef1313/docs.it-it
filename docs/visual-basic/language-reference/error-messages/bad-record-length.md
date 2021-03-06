---
title: Lunghezza del record non valida
ms.date: 07/20/2015
f1_keywords:
- vbrID59
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
ms.openlocfilehash: 7ec0a8c27f425ec717bca5d45d5dfd2b601c11d5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665725"
---
# <a name="bad-record-length"></a>Lunghezza del record non valida
Di seguito sono riportate le cause possibili dell'errore:  
  
- La lunghezza di una variabile di record specificata in un `FileGet`, `FileGetObject`, `FilePut` oppure `FilePutObject` istruzione è diversa da quella specificata nel corrispondente `FileOpen` istruzione.  
  
- La variabile in un `FilePut` o `FilePutObject` o istruzione include una stringa a lunghezza variabile.  
  
- La variabile in un `FilePut` oppure `FilePutObject` è o include un `Variant` tipo.  
  
## <a name="to-correct-this-error"></a>Per correggere l'errore  
  
1. Assicurarsi che la somma delle dimensioni delle variabili di lunghezza fissa nel tipo definito dall'utente che definisce il record del tipo di variabile è uguale al valore indicato nel `FileOpen` dell'istruzione `Len` clausola.  
  
2. Se la variabile in un `FilePut` o `FilePutObject` o istruzione include una stringa a lunghezza variabile, assicurarsi che la stringa di lunghezza variabile sia di almeno 2 caratteri più la lunghezza del record specificata nel breve il `Len` clausola del `FileOpen` istruzione.  
  
3. Se la variabile in un `FilePut` o `FilePutObject` è o include un `Variant` assicurarsi che la stringa di lunghezza variabile è almeno 4 byte più la lunghezza del record specificata nel breve il `Len` clausola del `FileOpen` istruzione.  
  
## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>
