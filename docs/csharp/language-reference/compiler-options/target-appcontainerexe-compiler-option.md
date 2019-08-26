---
title: -target:appcontainerexe (opzioni del compilatore C#)
ms.date: 07/20/2015
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
ms.openlocfilehash: 09ae01d95138b72a0012f294189d288fc71c74b2
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606543"
---
# <a name="-targetappcontainerexe-c-compiler-options"></a>-target:appcontainerexe (opzioni del compilatore C#)
Se si usa l'opzione del compilatore **-target:appcontainerexe**, il compilatore crea un file eseguibile Windows (con estensione exe) che deve essere eseguito in un contenitore di app. Questa opzione equivale a [-target:winexe](./target-winexe-compiler-option.md), ma è progettata per le app [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```console  
-target:appcontainerexe  
```  
  
## <a name="remarks"></a>Osservazioni  
 Per richiedere che l'app venga eseguita in un contenitore di app, questa opzione imposta un bit nel file [eseguibile di tipo PE](/windows/desktop/Debug/pe-format). Quando questo bit è impostato, viene generato un errore se il metodo CreateProcess tenta di avviare il file eseguibile all'esterno di un contenitore di app.  
  
 A meno che non si usi l'opzione [-out](./out-compiler-option.md), il nome del file di output corrisponderà al nome del file di input contenente il metodo [Main](../../programming-guide/main-and-command-args/index.md).  
  
 Quando si specifica questa opzione al prompt dei comandi, tutti i file fino alla successiva opzione **-out** o **-target** vengono usati per creare il file eseguibile.  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a>Per impostare l'opzione del compilatore nell'IDE  
  
1. In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto e scegliere **Proprietà**.  
  
2. Nell'elenco **Tipo di output** della scheda **Applicazione** scegliere **Applicazione Windows Store**.  
  
     Questa opzione è disponibile solo per i modelli di app [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)].  
  
 Per informazioni su come impostare questa opzione del compilatore a livello di codice, vedere <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Esempio  
 Il seguente comando consente di compilare `filename.cs` in un file eseguibile di Windows che può essere eseguito solo in un contenitore di app.  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a>Vedere anche

- [-target (opzioni del compilatore C#)](./target-compiler-option.md)
- [-target:winexe (opzioni del compilatore C#)](./target-winexe-compiler-option.md)
- [Opzioni del compilatore C#](./index.md)
