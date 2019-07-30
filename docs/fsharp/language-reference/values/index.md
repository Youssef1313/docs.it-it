---
title: Valori
description: Informazioni sul modo in F# cui i valori in sono quantità che hanno un tipo specifico.
ms.date: 05/16/2016
ms.openlocfilehash: ed7a5b069a5a47aacf0cce4cfa754ded46f6e84a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630791"
---
# <a name="values"></a>Valori

I valori in F# sono quantità che hanno un tipo specifico. I valori possono essere numeri interi o numeri a virgola mobile, caratteri o testo, elenchi, sequenze, matrici, tuple, unioni discriminate, record, tipi di classe o valori di funzioni.

## <a name="binding-a-value"></a>Associazione di un valore

Il termine *associazione* indica il processo di associare, ovvero collegare, un nome a una definizione. La parola chiave `let` associa un valore, come illustrato negli esempi seguenti:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet601.fs)]

Il tipo di valore viene dedotto dalla definizione. Per un tipo primitivo, ad esempio un numero intero o a virgola mobile, il tipo è determinato dal tipo di valore letterale. Nell'esempio precedente il compilatore deduce quindi il tipo di `b` come `unsigned int`, mentre il tipo di `a` come `int`. Il tipo di valore di una funzione è determinato dal valore restituito nel corpo della funzione. Per altre informazioni sui tipi di valori delle funzioni, vedere [Funzioni](../functions/index.md). Per altre informazioni sui tipi di valori letterali, vedere [Valori letterali](../literals.md).

Per impostazione predefinita, il compilatore non rilascia la diagnostica sulle associazioni inutilizzate. Per ricevere questi messaggi, abilitare l'avviso 1182 nel file di progetto o quando si richiama il compilatore ( `--warnon` vedere in [Opzioni del compilatore](../compiler-options.md)).

## <a name="why-immutable"></a>Valori non modificabili

I valori non modificabili sono valori che non possono essere modificati nel corso dell'esecuzione del programma. Se si ha familiarità con i linguaggi di programmazione, ad esempio, C++, Visual Basic o C#, potrebbe sembrare inconsueto che F# dia più importanza ai valori non modificabili piuttosto che alle variabili alle quali è possibile assegnare nuovi valori durante l'esecuzione di un programma. I dati non modificabili sono elementi importanti nella programmazione funzionale. In un ambiente a thread multipli, è molto difficile gestire le variabili condivise che possono essere modificate da thread diversi. Con le variabili modificabili può talvolta essere anche difficile sapere se una variabile può essere modificata quando viene passata a un'altra funzione.

Nei linguaggi funzionali puri, non ci sono variabili e le funzioni si comportano esattamente come le funzioni matematiche. Se un codice di un linguaggio procedurale usa un'assegnazione di variabile per modificare un valore, l'equivalente codice in un linguaggio funzionale ha un valore non modificabile che è l'input, una funzione non modificabile e diversi valori non modificabili come output. Questa precisione matematica consente un ragionamento più rigido sul comportamento del programma. Questo ragionamento più specifico è ciò che consente ai compilatori di controllare il codice in modo più rigoroso e ottimizzarlo in modo più efficace, rendendo più semplice l'analisi e la scrittura di codice corretto per gli sviluppatori. È quindi probabilmente più semplice eseguire il debug di codice funzionale rispetto al debug di un codice procedurale ordinario.

F# non è un linguaggio funzionale puro, ma supporta completamente la programmazione funzionale. L'uso di valori non modificabili è una buona pratica perché ciò consente al codice di trarre vantaggio da un importante aspetto delle programmazione funzionale.

## <a name="mutable-variables"></a>Variabili modificabili

È possibile usare la parola chiave `mutable` per specificare una variabile modificabile. Le variabili modificabili in F# dovrebbero in genere avere un ambito limitato, ad esempio un campo di un tipo o un valore locale. Le variabili modificabili con un ambito limitato sono più semplici da controllare e hanno meno probabilità di essere modificate in modo incorretto.

È possibile assegnare un valore iniziale a una variabile modificabile tramite la parola chiave `let` nello stesso modo in cui si definisce un valore. La differenza tuttavia è che successivamente è possibile assegnare nuovi valori alle variabili modificabili tramite l'operatore `<-`, come illustrato nell'esempio seguente.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet602.fs)]

I valori `mutable` contrassegnati possono essere promossi `'a ref` automaticamente a se acquisiti da una chiusura, inclusi i form che creano le `seq` chiusure, ad esempio i generatori. Se si desidera ricevere una notifica quando si verifica questa situazione, abilitare l'avviso 3180 nel file di progetto o quando si richiama il compilatore.

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----|-----------|
|[Associazioni let](../functions/let-bindings.md)|Vengono fornite informazioni sull'utilizzo `let` della parola chiave per associare nomi a valori e funzioni.|
|[Funzioni](../functions/index.md)|Include una panoramica delle funzioni in F#.|

## <a name="see-also"></a>Vedere anche

- [Valori Null](null-Values.md)
- [Riferimenti per il linguaggio F#](../index.md)
