---
title: -nologo (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: 07e1718554b158635b9d8b04958834e804e1fe9f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964383"
---
# <a name="-nologo-visual-basic"></a>-nologo (Visual Basic)
Evita la visualizzazione del banner sul copyright e dei messaggi informativi durante la compilazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
-nologo  
```  
  
## <a name="remarks"></a>Note  
 Se si specifica `-nologo`, il compilatore non visualizza un banner sul copyright. Per impostazione predefinita, l'opzione `-nologo` non è attiva.  
  
> [!NOTE]
> L' `-nologo` opzione non è disponibile nell'ambiente di sviluppo di Visual Studio. è disponibile solo quando si esegue la compilazione dalla riga di comando.  
  
## <a name="example"></a>Esempio  
 Il codice seguente compila `T2.vb` e non visualizza un banner sul copyright.  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a>Vedere anche

- [Compilatore della riga di comando di Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Esempi di righe di comando di compilazione](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
