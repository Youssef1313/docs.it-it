---
title: Direttive per il compilatore
description: Informazioni sulle F# direttive per il preprocessore del linguaggio, le direttive di compilazione condizionale, le direttive di riga e le direttive del compilatore.
ms.date: 12/10/2018
ms.openlocfilehash: 16db2efb2fee2c2c5e94aa98eb0a13183a4e0e0b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630410"
---
# <a name="compiler-directives"></a>Direttive per il compilatore

In questo argomento vengono descritte le direttive per il preprocessore e le direttive del compilatore.

## <a name="preprocessor-directives"></a>Direttive per il preprocessore

Una direttiva per il preprocessore è preceduta dal simbolo # e viene visualizzata in una riga da sola. Viene interpretata dal preprocessore, che viene eseguito prima del compilatore stesso.

Nella tabella riportata di seguito sono elencate le direttive per il preprocessore disponibili in F#.

|Direttiva|Descrizione|
|---------|-----------|
|`#if`*simbolo* di|Supporta la compilazione condizionale. Se il simbolo è definito, `#if` il codice nella sezione dopo è incluso. Il simbolo può anche essere negato con `!`.|
|`#else`|Supporta la compilazione condizionale. Contrassegna una sezione di codice da includere se il simbolo usato nella precedente direttiva `#if` non è definito.|
|`#endif`|Supporta la compilazione condizionale. Contrassegna la fine di una sezione condizionale di codice.|
|`#`linea *int*,<br/>`#`linea *int* *stringa*,<br/>`#`linea *int* *stringa Verbatim*|Indica la riga e il nome di file del codice sorgente originale per il debug. Questa funzionalità viene fornita per gli strumenti che generano codice sorgente F#.|
|`#nowarn`*WarningCode*|Disabilita un avviso o più avvisi del compilatore. Per disabilitare un avviso, individuare il numero dall'output del compilatore e includerlo tra virgolette. Omettere il prefisso "FS". Per disabilitare più numeri di avviso sulla stessa riga, racchiudere ogni numero tra virgolette e separare ogni stringa con uno spazio. Ad esempio:

`#nowarn "9" "40"`

L'effetto della disabilitazione di un avviso viene applicato all'intero file, incluse le parti del file che precedono la direttiva. |

## <a name="conditional-compilation-directives"></a>Direttive di compilazione condizionale

Il codice disattivato da una di queste direttive viene visualizzato in grigio nell'editor Visual Studio Code.

> [!NOTE]
> Il comportamento delle direttive di compilazione condizionale non è lo stesso come in altri linguaggi. Ad esempio, è possibile usare espressioni booleane che includono simboli e `true` e `false` non hanno alcun significato speciale. I simboli usati nella direttiva `if` devono essere definiti dalla riga di comando o nelle impostazioni del progetto e non esiste alcuna direttiva per il preprocessore `define`.

Nel codice di esempio che segue viene illustrato l'uso delle direttive `#if`, `#else` e `#endif`. In questo esempio, il codice contiene due versioni della definizione di `function1`. Quando `VERSION1` viene definito tramite l' [opzione del compilatore-define](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04), viene attivato il codice `#if` tra la direttiva `#else` e la direttiva. In caso contrario, viene attivato il codice tra `#else` e `#endif`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7301.fs)]

Non esiste alcuna direttiva per il preprocessore `#define` in F#. È necessario usare l'opzione del compilatore o le impostazioni di progetto per definire i simboli usati per la direttiva `#if`.

Le direttive di compilazione condizionale possono essere annidate. Il rientro non è significativo per le direttive per il preprocessore.

È anche possibile negare un simbolo con `!`. In questo esempio il valore di una stringa è qualcosa solo quando _non_ si esegue il debug:

```fsharp
#if !DEBUG
let str = "Not debugging!"
#else
let str = "Debugging!"
#endif
```

## <a name="line-directives"></a>Direttive di riga

Durante la compilazione, il compilatore segnala errori nel codice F# facendo riferimento ai numeri di riga in cui si verifica ogni errore. Questi numeri di riga iniziano da 1 per la prima riga in un file. Tuttavia, se si genera codice sorgente F# da un altro strumento, i numeri di riga nel codice generato non sono generalmente di interesse, perché nel codice F# generato probabilmente gli errori sono causati da un'altra origine. La direttiva `#line` consente agli autori di strumenti che generano codice sorgente F# di passare le informazioni relative ai numeri di riga e ai file di origine originali al codice F# generato.

Quando si usa la direttiva `#line`, i nomi di file devono essere racchiusi tra virgolette. A meno che il token verbatim (`@`) venga visualizzato all'inizio della stringa, è necessario eseguire l'escape dei caratteri barra rovesciata usando due barre rovesciate anziché una per poterli usare nel percorso. Di seguito sono riportati dei token di riga validi. In questi esempi si presuppone che il file originale `Script1` risulti in un file di codice F# generato automaticamente quando viene eseguito tramite uno strumento e che il codice nella posizione di tali direttive venga generato dagli stessi token alla riga 25 nel file `Script1`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7303.fs)]

Questi token indicano che il codice F# generato in questa posizione è derivato da alcuni costrutti alla riga o vicino alla riga `25` in `Script1`.

## <a name="compiler-directives"></a>Direttive per il compilatore

Le direttive del compilatore sono simili alle direttive per il preprocessore perché sono precedute da un simbolo #, ma anziché essere interpretate dal preprocessore, vengono interpretate dal compilatore.

Nella tabella seguente viene elencata la direttiva del compilatore disponibile in F#.

|Direttiva|DESCRIZIONE|
|---------|-----------|
|`#light` ["on"&#124;"off"]|Abilita o disabilita la sintassi leggera per la compatibilità con altre versioni di ML. Per impostazione predefinita, la sintassi leggera è abilitata. La sintassi dettagliata è sempre abilitata. Pertanto, è possibile usare sia sintassi leggera che sintassi dettagliata. La direttiva `#light` da sola equivale a `#light "on"`. Se si specifica `#light "off"`, è necessario usare la sintassi dettagliata per tutti i costrutti del linguaggio. La sintassi nella documentazione per F# viene presentata partendo dal presupposto che venga usata la sintassi leggera. Per ulteriori informazioni, vedere [sintassi dettagliata](verbose-syntax.md).|

Per le direttive dell'interprete (FSI. exe), vedere [programmazione F#interattiva con ](../tutorials/fsharp-interactive/index.md).

## <a name="see-also"></a>Vedere anche

- [Riferimenti per il linguaggio F#](index.md)
- [Opzioni del compilatore](compiler-options.md)
