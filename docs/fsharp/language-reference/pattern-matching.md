---
title: Criteri di ricerca
description: Informazioni sul modo in F# cui vengono usati i modelli per confrontare i dati con le strutture logiche, scomporre i dati in parti costituenti o estrarre informazioni dai dati.
ms.date: 10/27/2019
ms.openlocfilehash: 1acb795cbe5581898ae5e1439098f906a8a16b93
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/29/2019
ms.locfileid: "73041004"
---
# <a name="pattern-matching"></a>Criteri di ricerca

I modelli sono regole per la trasformazione dei dati di input. Vengono usati in tutto il F# linguaggio per confrontare i dati con una struttura o strutture logiche, scomporre i dati in parti costituenti o estrarre informazioni dai dati in diversi modi.

## <a name="remarks"></a>Note

I modelli vengono utilizzati in molti costrutti di linguaggio, ad esempio l'espressione `match`. Vengono usati quando si elaborano argomenti per le funzioni in associazioni `let`, espressioni lambda e nei gestori di eccezioni associati all'espressione `try...with`. Per altre informazioni, vedere [espressioni di corrispondenza](match-expressions.md), [associazioni let](./functions/let-bindings.md), [espressioni lambda: parola chiave `fun`](./functions/lambda-expressions-the-fun-keyword.md)ed [eccezioni: espressione `try...with`](./exception-handling/the-try-with-expression.md).

Nell'espressione `match`, ad esempio, il *modello* è quello che segue il simbolo della pipe.

```fsharp
match expression with
| pattern [ when condition ] -> result-expression
...
```

Ogni modello funge da regola per trasformare in qualche modo l'input. Nell'espressione `match` ogni modello viene esaminato a sua volta per verificare se i dati di input sono compatibili con il modello. Se viene trovata una corrispondenza, viene eseguita l'espressione di risultato. Se non viene trovata alcuna corrispondenza, viene testata la regola del modello successiva. La parte della *condizione* when facoltativa è illustrata nelle [Espressioni match](match-expressions.md).

Nella tabella seguente sono illustrati i modelli supportati. In fase di esecuzione, l'input viene testato rispetto a ognuno dei modelli seguenti nell'ordine elencato nella tabella e i modelli vengono applicati in modo ricorsivo, dal primo all'ultimo come appaiono nel codice e da sinistra a destra per i modelli in ogni riga.

|Name|Descrizione|Esempio|
|----|-----------|-------|
|Criterio costante|Qualsiasi valore letterale stringa, numerico o carattere, una costante di enumerazione o un identificatore di valore letterale definito|`1.0`, `"test"`, `30`, `Color.Red`|
|Modello di identificatore|Valore del case di un'unione discriminata, un'etichetta di eccezione o un case del criterio attivo|`Some(x)`<br /><br />`Failure(msg)`|
|Modello di variabile|*identifier*|`a`|
|modello di `as`|*modello* come *identificatore*|`(a, b) as tuple1`|
|Modello OR|&#124; *pattern2* Ripetizione piatta1|<code>([h] &#124; [h; _])</code>|
|Modello AND|*ripetizione piatta1* &amp; *pattern2*|`(a, b) & (_, "test")`|
|Modello cons|*identificatore:* : *List-Identifier*|`h :: t`|
|Modello di elenco|[ *pattern_1*;...; *pattern_n* ]|`[ a; b; c ]`|
|Modello di matrice|[&#124; *pattern_1*;..; *pattern_n* &#124;]|<code>[&#124; a; b; c &#124;]</code>|
|Modello racchiuso tra parentesi|( *modello* )|`( a )`|
|Modello tupla|( *pattern_1*,..., *pattern_n* )|`( a, b )`|
|Modello di record|{ *identificatore1* = *pattern_1*;...; *identifier_n* = *pattern_n* }|`{ Name = name; }`|
|Modello con caratteri jolly|_|`_`|
|Modello insieme all'annotazione del tipo|*modello* : *tipo*|`a : int`|
|Modello di test del tipo|:? *digitare* [come *identificatore* ]|`:? System.DateTime as dt`|
|Modello null|null|`null`|

## <a name="constant-patterns"></a>Modelli costanti

I modelli costanti sono numerici, caratteri e valori letterali stringa, costanti di enumerazione (con il nome del tipo di enumerazione incluso). Un'espressione `match` con solo modelli costanti può essere confrontata con un'istruzione case in altri linguaggi. L'input viene confrontato con il valore letterale e il criterio corrisponde se i valori sono uguali. Il tipo del valore letterale deve essere compatibile con il tipo di input.

Nell'esempio seguente viene illustrato l'utilizzo di modelli letterali e viene inoltre utilizzato un modello di variabile e un modello o.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4801.fs)]

Un altro esempio di modello letterale è un modello basato sulle costanti di enumerazione. Quando si utilizzano le costanti di enumerazione, è necessario specificare il nome del tipo di enumerazione.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4802.fs)]

## <a name="identifier-patterns"></a>Modelli di identificatore

Se il modello è una stringa di caratteri che formano un identificatore valido, il formato dell'identificatore determina la modalità di corrispondenza del criterio. Se l'identificatore è più lungo di un singolo carattere e inizia con un carattere maiuscolo, il compilatore tenta di trovare una corrispondenza con il modello di identificatore. L'identificatore per questo modello può essere un valore contrassegnato con l'attributo Literal, un case di unione discriminata, un identificatore di eccezione o un caso di criterio attivo. Se non viene trovato alcun identificatore corrispondente, la corrispondenza ha esito negativo e la regola del criterio successiva, ovvero il modello di variabile, viene confrontata con l'input.

I modelli di Unione discriminati possono essere semplici casi denominati o possono avere un valore oppure una tupla contenente più valori. Se è presente un valore, è necessario specificare un identificatore per il valore. Nel caso di una tupla, è necessario fornire un modello di tupla con un identificatore per ogni elemento della tupla o un identificatore con un nome di campo per uno o più campi di unione denominati. Per esempi, vedere gli esempi di codice in questa sezione.

Il tipo di `option` è un'unione discriminata con due case, `Some` e `None`. Un case (`Some`) ha un valore, ma l'altro (`None`) è solo un case denominato. Pertanto, `Some` deve avere una variabile per il valore associato al `Some` case, ma `None` deve essere visualizzato da solo. Nel codice seguente, alla variabile `var1` viene assegnato il valore ottenuto mediante la corrispondenza con la `Some` case.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4803.fs)]

Nell'esempio seguente, l'`PersonName` unione discriminata contiene una combinazione di stringhe e caratteri che rappresentano le possibili forme di nomi. I case dell'unione discriminata sono `FirstOnly`, `LastOnly`e `FirstLast`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4804.fs)]

Per le unioni discriminate con campi denominati, è possibile usare il segno di uguale (=) per estrarre il valore di un campo denominato. Si consideri, ad esempio, un'unione discriminata con una dichiarazione simile alla seguente.

```fsharp
type Shape =
    | Rectangle of height : float * width : float
    | Circle of radius : float
```

È possibile utilizzare i campi denominati in un'espressione di criteri di ricerca come indicato di seguito.

```fsharp
let matchShape shape =
    match shape with
    | Rectangle(height = h) -> printfn "Rectangle with length %f" h
    | Circle(r) -> printfn "Circle with radius %f" r
```

L'uso del campo denominato è facoltativo, quindi nell'esempio precedente, sia `Circle(r)` che `Circle(radius = r)` hanno lo stesso effetto.

Quando si specificano più campi, usare il punto e virgola (;) come separatore.

```fsharp
match shape with
| Rectangle(height = h; width = w) -> printfn "Rectangle with height %f and width %f" h w
| _ -> ()
```

I criteri attivi consentono di definire criteri di ricerca personalizzati più complessi. Per ulteriori informazioni sui modelli attivi, vedere [modelli attivi](active-patterns.md).

Il caso in cui l'identificatore è un'eccezione viene usato nei criteri di ricerca nel contesto dei gestori di eccezioni. Per informazioni sui criteri di ricerca nella gestione delle eccezioni, vedere [eccezioni: espressione `try...with`](./exception-handling/the-try-with-expression.md).

## <a name="variable-patterns"></a>Modelli variabili

Il modello di variabile assegna il valore corrispondente a un nome di variabile, che è quindi disponibile per l'uso nell'espressione di esecuzione a destra del simbolo del `->`. Un modello variabile da solo corrisponde a qualsiasi input, ma i modelli variabili vengono spesso visualizzati all'interno di altri modelli, consentendo quindi di rendere le strutture più complesse, ad esempio le tuple e le matrici, da scomporre in variabili.

Nell'esempio seguente viene illustrato un modello di variabile all'interno di un modello di tupla.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4805.fs)]

## <a name="as-pattern"></a>Modello As

Il modello di `as` è un modello a cui è stata aggiunta una clausola di `as`. La clausola `as` associa il valore corrispondente a un nome che può essere utilizzato nell'espressione di esecuzione di un'espressione `match` oppure, nel caso in cui questo modello venga utilizzato in un'associazione `let`, il nome viene aggiunto come binding all'ambito locale.

Nell'esempio seguente viene usato un modello di `as`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4806.fs)]

## <a name="or-pattern"></a>Modello OR

Il modello o viene usato quando i dati di input possono corrispondere a più modelli e si vuole eseguire lo stesso codice di conseguenza. I tipi di entrambi i lati del modello o devono essere compatibili.

Nell'esempio seguente viene illustrato il modello o.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4807.fs)]

## <a name="and-pattern"></a>Modello AND

Per il modello AND è necessario che l'input corrisponda a due modelli. I tipi di entrambi i lati del modello e devono essere compatibili.

L'esempio seguente è simile a `detectZeroTuple` illustrato nella sezione relativa al [modello di tupla](https://msdn.microsoft.com/library/#tuple) più avanti in questo argomento, ma in questo caso `var1` e `var2` vengono ottenuti come valori utilizzando il modello e.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4808.fs)]

## <a name="cons-pattern"></a>Modello cons

Il modello cons viene usato per scomporre un elenco nel primo elemento, la *testa*e un elenco che contiene gli elementi rimanenti, ovvero la *coda*.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4809.fs)]

## <a name="list-pattern"></a>Modello di elenco

Il modello elenco consente di scomporre gli elenchi in un numero di elementi. Il pattern list stesso può corrispondere solo a elenchi di un numero specifico di elementi.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4810.fs)]

## <a name="array-pattern"></a>Modello di matrice

Il modello di matrice è simile al modello di elenco e può essere usato per scomporre le matrici di una lunghezza specifica.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4811.fs)]

## <a name="parenthesized-pattern"></a>Modello racchiuso tra parentesi

Le parentesi possono essere raggruppate intorno ai modelli per ottenere l'associatività desiderata. Nell'esempio seguente, le parentesi vengono utilizzate per controllare l'associatività tra un pattern AND e un modello cons.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4812.fs)]

## <a name="tuple-pattern"></a>Modello tupla

Il modello di tupla corrisponde all'input nel modulo di tupla e consente di scomporre la tupla nei relativi elementi costitutivi usando variabili di criteri di ricerca per ogni posizione nella tupla.

Nell'esempio seguente viene illustrato il modello di tupla e vengono utilizzati anche modelli letterali, modelli variabili e il modello con caratteri jolly.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4813.fs)]

## <a name="record-pattern"></a>Modello di record

Il pattern di record viene usato per scomporre i record per estrarre i valori dei campi. Il modello non deve fare riferimento a tutti i campi del record; tutti i campi omessi non partecipano alla corrispondenza e non vengono estratti.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4814.fs)]

## <a name="wildcard-pattern"></a>Modello con caratteri jolly

Il modello con caratteri jolly è rappresentato dal carattere di sottolineatura (`_`) e corrisponde a qualsiasi input, proprio come il modello di variabile, ad eccezione del fatto che l'input viene eliminato anziché assegnato a una variabile. Il modello con caratteri jolly viene spesso utilizzato all'interno di altri modelli come segnaposto per i valori che non sono necessari nell'espressione a destra del simbolo del `->`. Il modello con caratteri jolly viene usato spesso anche alla fine di un elenco di modelli per trovare la corrispondenza con qualsiasi input senza corrispondenza. Il modello con caratteri jolly è illustrato in molti esempi di codice in questo argomento. Per un esempio, vedere il codice precedente.

## <a name="patterns-that-have-type-annotations"></a>Modelli con annotazioni di tipo

I modelli possono avere annotazioni di tipo. Si comportano come altre annotazioni di tipo e inferenza guida come altre annotazioni di tipo. Le parentesi sono obbligatorie intorno alle annotazioni di tipo nei modelli. Il codice seguente illustra un modello con un'annotazione di tipo.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4815.fs)]

## <a name="type-test-pattern"></a>Modello di test del tipo

Il modello di test del tipo viene usato per trovare la corrispondenza con l'input rispetto a un tipo. Se il tipo di input corrisponde a (o a un tipo derivato di) il tipo specificato nel criterio, la corrispondenza ha esito positivo.

Nell'esempio seguente viene illustrato il modello di test del tipo.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4816.fs)]

Se si verifica solo se un identificatore è di un tipo derivato particolare, non è necessario il `as identifier` parte del modello, come illustrato nell'esempio seguente:

```fsharp
type A() = class end
type B() = inherit A()
type C() = inherit A()

let m (a: A) =
    match a with
    | :? B -> printfn "It's a B"
    | :? C -> printfn "It's a C"
    | _ -> ()
```

## <a name="null-pattern"></a>Modello null

Il criterio null corrisponde al valore null che può essere visualizzato quando si utilizzano tipi che consentono un valore null. I modelli null vengono spesso usati quando si interopera con .NET Framework codice. Il valore restituito di un'API .NET, ad esempio, può essere l'input di un'espressione `match`. È possibile controllare il flusso del programma in base al fatto che il valore restituito sia null e anche ad altre caratteristiche del valore restituito. È possibile usare il modello null per impedire che i valori null vengano propagati al resto del programma.

Nell'esempio seguente vengono utilizzati il modello null e il modello di variabile.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4817.fs)]

## <a name="see-also"></a>Vedere anche

- [Espressioni match](match-expressions.md)
- [Criteri attivi](active-patterns.md)
- [Riferimenti per il linguaggio F#](index.md)
