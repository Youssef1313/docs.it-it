---
title: -bugreport (opzioni del compilatore C#s)
ms.date: 07/20/2015
f1_keywords:
- /bugreport
helpviewer_keywords:
- /bugreport compiler option [C#]
- -bugreport compiler option [C#]
- bugreport compiler option [C#]
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
ms.openlocfilehash: 0989678be070910c410d71717fe66679e1b70557
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/19/2019
ms.locfileid: "69603075"
---
# <a name="-bugreport-c-compiler-options"></a>-bugreport (opzioni del compilatore C#s)
Specifica che le informazioni di debug devono essere inserite in un file per analisi successive.  
  
## <a name="syntax"></a>Sintassi  
  
```console  
-bugreport:file  
```  
  
## <a name="arguments"></a>Argomenti  
 `file`  
 Nome del file in cui si vuole inserire il report sui bug.  
  
## <a name="remarks"></a>Osservazioni  
 L'opzione **-bugreport** specifica che in `file` devono essere inserite le informazioni seguenti:  
  
- Una copia di tutti i file di codice sorgente nella compilazione.  
  
- Un elenco delle opzioni del compilatore usate nella compilazione.  
  
- Informazioni sulla versione per il compilatore, il runtime e il sistema operativo.  
  
- Assembly e moduli di riferimento, salvati come cifre esadecimali, ad eccezione degli assembly forniti con .NET Framework e SDK.  
  
- L'eventuale output del compilatore.  
  
- Una descrizione del problema, che verrà richiesta.  
  
- Una descrizione del modo in cui si può risolvere il problema, che verrà richiesta.  
  
 Se questa opzione viene usata con **-errorreport:prompt** o **-errorreport:send**, le informazioni nel file verranno inviate a Microsoft Corporation.  
  
 Dato che una copia di tutti i file di codice sorgente verrà inserita in `file`, potrebbe essere utile riprodurre il sospetto difetto del codice nel programma più breve possibile.  
  
 Questa opzione del compilatore non è disponibile in Visual Studio e non può essere modificata a livello di codice.  
  
 Si noti che contenuto del file generato espone il codice sorgente e ciò potrebbe causare la divulgazione accidentale di informazioni.  
  
## <a name="see-also"></a>Vedere anche

- [Opzioni del compilatore C#](./index.md)
- [-errorreport (opzioni del compilatore C#)](./errorreport-compiler-option.md)
- [Gestione delle proprietà di progetti e soluzioni](/visualstudio/ide/managing-project-and-solution-properties)
