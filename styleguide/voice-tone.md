---
ms.openlocfilehash: cb8cc6574caad6da25b3fced70c58175a33ec896
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68616331"
---
# <a name="voice-and-tone-guidelines"></a>Linee guida per la voce e il tono

Molte persone, inclusi sviluppatori e professionisti IT, leggono i documenti sia per apprendere la tecnologia .NET sia per applicarli alle attività giornaliere.
L'obiettivo degli autori, quindi, è quello di creare documentazione efficace che assista il lettore nelle varie attività. Le nostre linee guida contribuiscono a questo scopo. La guida di stile contiene le indicazioni seguenti:
- [Usare un tono colloquiale](#use-a-conversational-tone)
- [Scrivere in seconda persona](#write-in-2nd-person)
- [Usare la forma attiva](#use-active-voice)
- [Scrivere per una capacità di lettura di quinta elementare](#target-a-fifth-grade-reading-level)
- [Evitare tempi futuri](#avoid-future-tense)
- [Cos'è e a cosa serve?](#what-is-it-so-what)

In questa guida di stile sono presenti esempi di ciascuno di questi elementi. La guida è stata scritta seguendo le linee guida per fornire esempi che è possibile seguire durante la creazione della documentazione per .NET. Vengono inoltre forniti alcuni esempi contrastanti, in modo da avere un'idea degli articoli che non seguono le linee guida.

## <a name="details-on-each-guideline"></a>Informazioni dettagliate su ciascuna delle linee guida

### <a name="use-a-conversational-tone"></a>Usare un tono colloquiale
#### <a name="appropriate-style"></a>Stile appropriato:
Vogliamo che la nostra documentazione abbia un tono colloquiale. Durante la lettura di un'esercitazione o di una descrizione, il lettore deve provare la sensazione di avere una conversazione con l'autore.
L'esperienza del lettore deve essere informale, colloquiale e informativa. Deve sentirsi come se stesse ascoltando l'autore che gli spiega i concetti.

#### <a name="inappropriate-style"></a>Stile non appropriato:
Lo stile colloquiale potrebbe risultare in contrasto con lo stile solitamente impiegato per la redazione di articoli accademici su argomenti tecnici. Queste risorse sono molto utili, ma gli autori hanno scritto tali articoli in uno stile molto diverso da quello della presente documentazione. Quando si legge un articolo accademico, il tono e lo stile di scrittura sono molto diversi.
La sensazione è quella di leggere un resoconto distaccato di un argomento piuttosto noioso.  

Il primo paragrafo precedente segue la raccomandazione relativa allo stile colloquiale. Il secondo usa uno stile più accademico. È possibile notare immediatamente la differenza. 

### <a name="write-in-second-person"></a>Scrivere in seconda persona
#### <a name="appropriate-style"></a>Stile appropriato:
Ti consigliamo di scrivere gli articoli come se stessi parlando direttamente al lettore. Devi usare spesso la seconda persona (com'è stato fatto in queste due frasi). Parlare in seconda persona non significa usare sempre la parola "tu". Scrivi direttamente per il lettore. Scrivi frasi imperative.
Comunica al lettore le nozioni che apprenderà.

#### <a name="inappropriate-style"></a>Stile non appropriato: 
Un autore può anche scegliere di scrivere in terza persona. In questo caso, un autore deve trovare un pronome o un sostantivo da usare quando fa riferimento al lettore. Un lettore spesso può trovare questo stile in persona terza meno accattivante e meno piacevole da leggere.

Il primo paragrafo segue lo stile consigliato. Nel secondo viene usata la terza persona. Scrivere in seconda persona. Generalmente, in questo modo il testo risulta molto più semplice da leggere.

### <a name="use-active-voice"></a>Usare la forma attiva

Scrivere gli articoli in forma attiva. Nella forma attiva, il soggetto esegue l'azione (verbo) descritta nella frase. Nella forma passiva, al contrario, la frase è organizzata in modo tale che il soggetto subisce l'azione. Confrontare i due esempi seguenti:

>Il compilatore ha trasformato il codice sorgente in un file eseguibile.

>Il codice sorgente è stato trasformato in un file eseguibile dal compilatore.

Nella prima frase viene usata la forma attiva. La seconda frase è stata scritta nella forma passiva.
Queste due frasi forniscono un altro esempio di ciascuno stile.

È consigliabile usare la forma attiva perché risulta più leggibile. La forma passiva può essere più difficile da leggere.

### <a name="target-a-fifth-grade-reading-level"></a>Scrivere per una capacità di lettura di quinta elementare

Quest'ultima indicazione viene fornita perché molti lettori non sono di madrelingua inglese.
Gli articoli sono destinati a un pubblico internazionale. È necessario tenere conto che il vocabolario dei lettori potrebbe essere limitato.

Si sta comunque scrivendo per professionisti tecnici. I lettori generalmente dispongono di competenze di programmazione e conoscono la specifica terminologia relativa alla programmazione. Programmazione orientata agli oggetti, classe, oggetto, funzione e metodo saranno termini familiari. Tuttavia, non tutti i lettori degli articoli hanno una laurea in informatica. Sarà probabilmente necessario definire termini quali "idempotente", se si sceglie di usarli:

>Il metodo Close() è idempotente, ovvero può essere chiamato più volte e l'effetto è lo stesso che si otterrebbe con un'unica chiamata.

### <a name="avoid-future-tense"></a>Evitare tempi futuri
In alcune lingue, il concetto di futuro è diverso rispetto all'inglese. L'uso del futuro rende difficoltosa la lettura di molti documenti. Se si usa il futuro, inoltre, la domanda che ovviamente sorge è "Quando accadrà?" Quindi, se ad esempio si dice "Sarà importante conoscere PowerShell", il lettore si domanderà ovviamente quando sarà importante. È invece meglio scrivere "È importante conoscere PowerShell".

### <a name="what-is-it---so-what"></a>Cos'è e a cosa serve?
Quando si presenta al lettore un nuovo concetto, definire il concetto prima di spiegare perché è utile. È importante che il lettore capisca cos'è prima di capirne i vantaggi o eventualmente gli svantaggi. 
