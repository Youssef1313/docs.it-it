---
title: Regasm.exe (strumento di registrazione di assembly)
ms.date: 03/30/2017
helpviewer_keywords:
- Assembly Registration tool
- assemblies [.NET Framework], registering
- Regasm.exe
- registering assemblies
ms.assetid: e190e342-36ef-4651-a0b4-0e8c2c0281cb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 44ab00322419b99aeac51da0d836c60264da5194
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894657"
---
# <a name="regasmexe-assembly-registration-tool"></a>Regasm.exe (strumento di registrazione di assembly)

Lo strumento di registrazione di assembly legge i metadati all'interno di un assembly e aggiunge al Registro di sistema le voci necessarie per consentire ai client COM di creare classi di .NET Framework in modo trasparente. Quando una classe è stata registrata, qualsiasi client COM può utilizzarla come se si trattasse di una classe COM. La classe viene registrata una sola volta, al momento dell'installazione dell'assembly. Non è possibile creare da COM istanze di classi nell'assembly finché tali classi non sono state effettivamente registrate.

Per eseguire lo strumento, usare il Prompt dei comandi per gli sviluppatori per Visual Studio. Per altre informazioni, vedere [Prompt dei comandi](../../../docs/framework/tools/developer-command-prompt-for-vs.md).

Al prompt dei comandi digitare quanto segue:

## <a name="syntax"></a>Sintassi

```console
regasm assemblyFile [options]
```

## <a name="parameters"></a>Parametri

|Parametro|Descrizione|
|---------------|-----------------|
|*fileAssembly*|Assembly da registrare con COM.|

|Opzione|Descrizione|
|------------|-----------------|
|**/codebase**|Crea una voce Codebase nel Registro di sistema che specifica il percorso del file di un assembly non installato nella Global Assembly Cache. È consigliabile non specificare questa opzione se successivamente si intende installare nella Global Assembly Cache l'assembly che si sta registrando. L'argomento *fileAssembly* specificato con l'opzione **/codebase** deve essere un [assembly con nome sicuro](../../../docs/framework/app-domains/strong-named-assemblies.md).|
|**/registered**|Specifica che questo strumento includerà riferimenti solo alle librerie dei tipi che sono già state registrate.|
|**/asmpath:directory**|Specifica una directory contenente riferimenti agli assembly. Deve essere usato insieme all'opzione **/regfile**.|
|**/nologo**|Evita la visualizzazione del messaggio di avvio Microsoft.|
|**/regfile** [ **:** *fileRegistrosistema*]|Genera il file .reg specificato per l'assembly, che contiene le voci del Registro di sistema necessarie. Se si specifica questa opzione, il Registro di sistema non viene modificato. Non è possibile usare questa opzione insieme alle opzioni **/u** o **/tlb**.|
|**/silent** o **/s**|Evita la visualizzazione dei messaggi di operazione riuscita.|
|**/tlb** [ **:** *fileLibreriaTipi*]|Genera, dall'assembly specificato, una libreria dei tipi contenente le definizioni dei tipi accessibili definiti all'interno dell'assembly stesso.|
|**/unregister** o **/u**|Annulla la registrazione delle classi che possono essere create e trovate in *fileAssembly*. Se questa opzione viene omessa, le classi nell'assembly verranno registrate.|
|**/verbose**|Specifica la modalità dettagliata. Se viene definita con l'opzione **/tlb**, visualizza l'elenco di tutti gli assembly a cui si fa riferimento e per i quali è necessario generare una libreria dei tipi.|
|**/?** o **/help**|Visualizza la sintassi e le opzioni di comando dello strumento.|

> [!NOTE]
> Le opzioni della riga di comando di Regasm.exe non sono soggette alla distinzione tra maiuscole e minuscole. Per identificarle in modo univoco, è sufficiente digitare solo una parte dell'opzione. Ad esempio, **/n** equivale a **/nologo** e **/t:** *outfile.tlb* equivale a **/tlb:** *outfile.tlb*.

## <a name="remarks"></a>Note

È possibile usare l'opzione **/regfile** per generare un file REG contenente le voci del Registro di sistema, anziché apportare le modifiche direttamente in tale Registro. Per aggiornare il Registro di sistema su un computer è necessario importare il file .reg con lo strumento Editor del Registro di sistema (Regedit.exe). Si noti che il file .reg non contiene alcun aggiornamento del Registro di sistema che può essere effettuato mediante funzioni del Registro di sistema definite dall'utente.  Si noti che l'opzione **/regfile** crea solo voci del Registro di sistema per le classi gestite.  Non vengono create voci per `TypeLibID` o `InterfaceID`.

Quando si specifica l'opzione **/tlb**, Regasm.exe genera e registra una libreria dei tipi che descrive i tipi trovati nell'assembly. Le librerie dei tipi generate vengono inserite nella directory di lavoro corrente o nella directory specificata per il file di output. Se viene generata una libreria dei tipi per un assembly che fa riferimento ad altri assembly, è possibile che vengano generate più librerie dei tipi contemporaneamente. La libreria dei tipi può essere usata per fornire informazioni sui tipi a strumenti di sviluppo come Visual Studio. L'opzione **/tlb** non deve essere usata se l'assembly che si sta registrando è stato prodotto dall'utilità di importazione della libreria dei tipi, [Tlbimp.exe](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md). Non è possibile esportare una libreria dei tipi da un assembly importato da una libreria dei tipi. L'uso dell'opzione **/tlb** equivale all'uso dell'utilità di esportazione della libreria dei tipi ([Tlbexp.exe](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)) e di Regasm.exe, con l'eccezione che Tlbexp.exe non registra la libreria dei tipi che produce.  Se si usa **/tlb** per registrare una libreria dei tipi, è possibile usare **/tlb** con l'opzione **/unregister** per annullare la registrazione. L'utilizzo congiunto di queste due opzioni determina l'annullamento della registrazione delle voci di interfaccia e di libreria dei tipi, con conseguente pulitura del Registro di sistema.

Quando si registra un assembly per consentirne l'utilizzo da parte di COM, sul computer locale vengono aggiunte delle voci al Registro di sistema. In particolare, vengono create chiavi del Registro di sistema dipendenti dalla versione che consentono l'esecuzione side-by-side di più versioni dello stesso assembly su un computer. Alla prima registrazione di un assembly, viene creata una chiave di primo livello per l'assembly e una sottochiave univoca per la versione specifica. Ogni volta che si registra una nuova versione dell'assembly, viene creata una sottochiave per la nuova versione.

Si consideri, ad esempio, uno scenario in cui si registra il componente gestito myComp.dll, versione 1.0.0.0 per consentirne l'utilizzo da parte di COM. Successivamente si registra myComp.dll, versione 2.0.0.0. Viene verificato che tutte le applicazioni client COM presenti nel computer usano myComp.dll versione 2.0.0.0 e si decide di annullare la registrazione di myComponent.dll versione 1.0.0.0. Questo schema del Registro di sistema consente di annullare la registrazione di myComp.dll versione 1.0.0.0 in quanto viene rimossa solo la sottochiave della versione 1.0.0.0.

Dopo aver registrato un assembly tramite Regasm.exe, è possibile installarlo nella [Global Assembly Cache](../../../docs/framework/app-domains/gac.md) in modo che possa essere attivato da qualsiasi client COM. Se l'assembly dovrà essere attivato da un'unica applicazione, è possibile inserirlo nella directory di tale applicazione.

## <a name="examples"></a>Esempi

Il comando che segue registra tutte le classi pubbliche contenute in `myTest.dll`.

```console
regasm myTest.dll
```

Il comando che segue genera il file `myTest.reg` contenente tutte le voci di Registro di sistema necessarie. Questo comando non aggiorna il Registro di sistema.

```console
regasm myTest.dll /regfile:myTest.reg
```

Il comando che segue registra tutte le classi pubbliche contenute in `myTest.dll` e genera e registra la libreria dei tipi `myTest.tlb` che contiene le definizioni di tutti i tipi pubblici definiti in `myTest.dll`.

```console
regasm myTest.dll /tlb:myTest.tlb
```

## <a name="see-also"></a>Vedere anche

- [Strumenti](../../../docs/framework/tools/index.md)
- [Tlbexp.exe (utilità di esportazione della libreria dei tipi)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)
- [Tlbimp.exe (utilità di importazione della libreria dei tipi)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)
- [Registrazione di assembly presso COM](../../../docs/framework/interop/registering-assemblies-with-com.md)
- [Prompt dei comandi](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
