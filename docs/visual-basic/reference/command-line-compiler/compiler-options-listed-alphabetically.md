---
title: Opzioni del compilatore elencate in ordine alfabetico
ms.date: 04/12/2018
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: e67febba-bacf-4e1f-a143-c141e063f90e
ms.openlocfilehash: c529c03fd3856bbd3d3b26371415907c94ca8d30
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343510"
---
# <a name="visual-basic-compiler-options-listed-alphabetically"></a>Visual Basic compiler options listed alphabetically
The Visual Basic command-line compiler is provided as an alternative to compiling programs from the Visual Studio integrated development environment (IDE). The following is a list of the Visual Basic command-line compiler options sorted alphabetically.  

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]
  
|Opzione|Scopo|  
|------------|-------------|  
|[@ (Specifica di un file di risposta)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)|Specifica un file di risposta.|  
|[-?](../../../visual-basic/reference/command-line-compiler/help.md)|Visualizza le opzioni del compilatore. Questo comando ha la stessa funzione dell'opzione `-help`. Non viene effettuata alcuna compilazione.|  
|`-additionalfile`|Assegna un nome ad altri file che non influiscono direttamente sulla generazione del codice, ma possono essere usati dagli analizzatori per produrre errori o avvisi.|  
|[-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)|Fa sì che il compilatore renda disponibili per il progetto in compilazione tutte le informazioni sui tipi presenti nei file specificati.|  
|`-analyzer`|Esegue gli analizzatori da questo assembly (forma breve: -a)|  
|[-baseaddress](../../../visual-basic/reference/command-line-compiler/baseaddress.md)|Specifica l'indirizzo di base di una DLL.|  
|[-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)|Crea un file contenente informazioni che rendono più semplice segnalare un bug.|  
|`-checksumalgorithm:<alg>`|Specificare l'algoritmo per il calcolo del checksum del file di origine archiviato nel file PDB.  I valori supportati sono: SHA1 (predefinito) o SHA256. <br>Due to collision problems with SHA1, Microsoft recommends SHA256 or better.|  
|[-codepage](../../../visual-basic/reference/command-line-compiler/codepage.md)|Specifica la tabella codici da usare per tutti i file del codice sorgente nella compilazione.|  
|[-debug](../../../visual-basic/reference/command-line-compiler/debug.md)|Crea informazioni di debug.|  
|[-define](../../../visual-basic/reference/command-line-compiler/define.md)|Definisce simboli per la compilazione condizionale.|  
|[-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)|Specifica se l'assembly avrà firma completa o parziale.|  
|[-deterministic](../../../visual-basic/reference/command-line-compiler/deterministic.md)|Fa sì che l'output del compilatore sia un assembly il cui contenuto binario è identico in tutte le compilazioni se gli input sono identici.|
|[-doc](../../../visual-basic/reference/command-line-compiler/doc.md)|Elabora commenti sulla documentazione in un file XML.|  
|[-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)|Specifies how the Visual Basic compiler should report internal compiler errors.|  
|[-filealign](../../../visual-basic/reference/command-line-compiler/filealign.md)|Specifica la posizione di allineamento per le sezioni del file di output.|  
|[-help](../../../visual-basic/reference/command-line-compiler/help.md)|Visualizza le opzioni del compilatore. Questo comando ha la stessa funzione dell'opzione `-?`. Non viene effettuata alcuna compilazione.|  
|[-highentropyva](../../../visual-basic/reference/command-line-compiler/highentropyva.md)|Indica se un particolare eseguibile supporta ASLR (Address Space Layout Randomization) a entropia elevata.|  
|[-imports](../../../visual-basic/reference/command-line-compiler/imports.md)|Importa uno spazio dei nomi dall'assembly specificato.|  
|[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)|Specifica il nome di un contenitore di chiavi per una coppia di chiavi allo scopo di assegnare a un assembly un nome sicuro.|  
|[-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)|Specifica un file che contiene una chiave o una coppia di chiavi allo scopo di assegnare a un assembly un nome sicuro.|  
|[-langversion](../../../visual-basic/reference/command-line-compiler/langversion.md)|Specify language version: 9&#124;9.0&#124;10&#124;10.0&#124;11&#124;11.0.|  
|[-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)|Specifies the location of assemblies referenced by the [-reference](../../../visual-basic/reference/command-line-compiler/reference.md) option.|  
|[-linkresource](../../../visual-basic/reference/command-line-compiler/linkresource.md)|Crea un collegamento a una risorsa gestita.|  
|[-main](../../../visual-basic/reference/command-line-compiler/main.md)|Specifies the class that contains the `Sub Main` procedure to use at startup.|  
|[-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)|Specifica il nome dell'assembly che conterrà un modulo.|  
|`-modulename:<string>`|Specificare il nome del modulo di origine|  
|[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)|Sets the compiler to target the .NET Compact Framework.|  
|[-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)|La compilazione non viene eseguita con Vbc.rsp.|  
|[-nologo](../../../visual-basic/reference/command-line-compiler/nologo.md)|Elimina i messaggi informativi del compilatore.|  
|[-nostdlib](../../../visual-basic/reference/command-line-compiler/nostdlib.md)|Indica al compilatore di non fare riferimento alle librerie standard.|  
|[-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)|Inibisce la capacità del compilatore di generare avvisi.|  
|[-nowin32manifest](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)|Indica al compilatore di non incorporare un manifesto dell'applicazione nel file eseguibile.|  
|[-optimize](../../../visual-basic/reference/command-line-compiler/optimize.md)|Abilita/disabilita l'ottimizzazione del codice.|  
|[-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)|Specifica se il confronto si verifica tra stringhe di tipo binario oppure se usare una semantica basata sul testo specifica delle impostazioni locali definite.|  
|[-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)|Richiede la dichiarazione esplicita delle variabili.|  
|[-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)|Consente di usare l'inferenza del tipo di variabile locale nelle dichiarazioni di variabile.|  
|[-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)|Attiva la semantica del linguaggio rigorosa.|  
|[-out](../../../visual-basic/reference/command-line-compiler/out.md)|Specifica un file di output.|  
|`-parallel[+&#124;-]`|Specifica se usare la compilazione simultanea (+).|  
|[-platform](../../../visual-basic/reference/command-line-compiler/platform.md)|Specifica la piattaforma del processore da impostare come destinazione del file di output.|  
|`-preferreduilang`|Specificare il nome della lingua di output preferita.|  
|[-quiet](../../../visual-basic/reference/command-line-compiler/quiet.md)|Impedisce al compilatore di visualizzare codice per avvisi ed errori relativi alla sintassi.|  
|[-recurse](../../../visual-basic/reference/command-line-compiler/recurse.md)|Cerca nelle sottodirectory i file di origine da compilare.|  
|[-reference](../../../visual-basic/reference/command-line-compiler/reference.md)|Importa metadati da un assembly.|  
|[/refonly](refonly-compiler-option.md)|Outputs only a reference assembly.|
|[/refout](refout-compiler-option.md)|Specifies the output path of a reference assembly.|
|[-removeintchecks](../../../visual-basic/reference/command-line-compiler/removeintchecks.md)|Disabilita il controllo dell'overflow di Integer.|  
|[-resource](../../../visual-basic/reference/command-line-compiler/resource.md)|Incorpora una risorsa gestita in un assembly.|  
|[-rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)|Specifica uno spazio dei nomi per tutte le dichiarazioni di tipo.|  
|`-ruleset:<file>`|Specificare un file di set di regole che disabilita la diagnostica specifica.|  
|[-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)|Specifica il percorso dei file Mscorlib.dll e Microsoft.VisualBasic.dll.|  
|[-subsystemversion](../../../visual-basic/reference/command-line-compiler/subsystemversion.md)|Specifica la versione minima del sottosistema che può essere usata dal file eseguibile generato.|  
|[-target](../../../visual-basic/reference/command-line-compiler/target.md)|Specifica il formato del file di output.|  
|[-utf8output](../../../visual-basic/reference/command-line-compiler/utf8output.md)|Visualizza l'output del compilatore usando la codifica UTF-8.|  
|[-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)|Indica che il compilatore deve compilare senza un riferimento alla libreria di runtime di Visual Basic oppure con un riferimento a una libreria di runtime specifica.|  
|[-verbose](../../../visual-basic/reference/command-line-compiler/verbose.md)|Restituisce informazioni supplementari durante la compilazione.|  
|[-warnaserror](../../../visual-basic/reference/command-line-compiler/warnaserror.md)|Alza il livello degli avvisi a errori.|  
|[-win32icon](../../../visual-basic/reference/command-line-compiler/win32icon.md)|Inserisce un file ico nel file di output.|  
|[-win32manifest](../../../visual-basic/reference/command-line-compiler/win32manifest.md)|Identifica un file manifesto dell'applicazione Win32 definito dall'utente da incorporare nel file eseguibile di tipo PE di un progetto.|  
|[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)|Inserisce una risorsa Win32 nel file di output.|  
  
## <a name="see-also"></a>Vedere anche

- [Opzioni del compilatore Visual Basic elencate per categoria](../../../visual-basic/reference/command-line-compiler/compiler-options-listed-by-category.md)
- [Gestione delle proprietà di progetti e soluzioni](/visualstudio/ide/managing-project-and-solution-properties)
