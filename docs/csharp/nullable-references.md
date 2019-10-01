---
title: Tipi riferimento nullable
description: Questo articolo offre una panoramica dei tipi riferimento nullable, aggiunti in C# 8. Si apprenderà come la funzionalità offra sicurezza contro le eccezioni dei riferimenti Null, per progetti nuovi ed esistenti.
ms.date: 02/19/2019
ms.openlocfilehash: 213f0e3d9ad84628dab02a1dc483513783b2ad6e
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699950"
---
# <a name="nullable-reference-types"></a>Tipi riferimento nullable

In C# 8.0 sono stati introdotti i **tipi riferimento nullable** e i **tipi riferimento non nullable** che consentono di creare istruzioni importanti sulle proprietà delle variabili dei tipi riferimento:

- **Non si presume che un riferimento sia Null**. Quando le variabili non devono essere Null, il compilatore applica regole che garantiscono che sia sicuro dereferenziare queste variabili senza prima controllare che non siano Null:
  - La variabile deve essere inizializzata come valore non Null.
  - Alla variabile non può mai essere assegnato il valore `null`.
- **Un riferimento potrebbe essere Null**. Quando le variabili possono essere Null, il compilatore applica regole diverse per assicurarsi che sia stata verificata correttamente la presenza di un riferimento Null:
  - La variabile può essere dereferenziata solo quando il compilatore può garantire che il valore non sia Null.
  - Queste variabili possono essere inizializzate con il valore predefinito `null` e possono ricevere l'assegnazione del valore `null` in un altro codice.

Questa nuova funzionalità offre vantaggi significativi rispetto alla gestione delle variabili di riferimento nelle versioni precedenti di C# in cui la finalità della progettazione non poteva essere determinata dalla dichiarazione di variabile. Il compilatore non offriva sicurezza contro le eccezioni dei riferimenti Null per i tipi riferimento:

- **Un riferimento può essere Null**. Non vengono generati avvisi quando un tipo riferimento viene inizializzato come Null o successivamente assegnato a Null.
- **Si suppone che un riferimento sia non Null**. Il compilatore non genera avvisi quando i tipi riferimento sono dereferenziati. Con i riferimenti nullable, il compilatore genera avvisi quando si dereferenzia una variabile che potrebbe essere Null.

Con l'aggiunta di tipi riferimento nullable, è possibile dichiarare in modo più chiaro la finalità. Il valore `null` è il modo corretto di indicare che una variabile non fa riferimento a un valore. Non usare questa funzionalità per rimuovere tutti i valori `null` dal codice. È invece consigliabile dichiarare la finalità al compilatore e agli altri sviluppatori che leggono il codice. Dichiarando la finalità, il compilatore informa l'utente quando scrive codice non coerente con tale finalità.

Viene inserita una nota in un **tipo riferimento nullable** usando la stessa sintassi dei [tipi valore nullable](programming-guide/nullable-types/index.md): viene aggiunto `?` al tipo della variabile. La dichiarazione della variabile seguente, ad esempio, rappresenta una variabile di stringa nullable, `name`:

```csharp
string? name;
```

Le variabili in cui `?` non viene aggiunto al nome del tipo sono **tipi riferimento non nullable**, incluse tutte le variabili dei tipi riferimento nel codice esistente quando questa funzionalità è abilitata.

Il compilatore usa l'analisi statica per determinare se un riferimento nullable è notoriamente non null. Il compilatore genera un avviso se si dereferenzia un riferimento nullable quando potrebbe essere null. È possibile eseguire l'override di questo comportamento usando l' **operatore** `!` che perdona i valori null dopo un nome di variabile. Se ad esempio si è certi che la variabile `name` non sia Null, ma il compilatore genera un avviso, è possibile scrivere il codice seguente per eseguire l'override dell'analisi del compilatore:

```csharp
name!.Length;
```

Per informazioni dettagliate su questo operatore, vedere la proposta di specifica sulla [bozza di tipi riferimento nullable](../../_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) in GitHub.

## <a name="nullability-of-types"></a>Supporto dei valori Null dei tipi

Qualsiasi tipo riferimento può avere una delle quattro tipologie di *supporto dei valori Null*, che descrive quando vengono generati gli avvisi:

- *Non nullable*: Null non può essere assegnato alle variabili di questo tipo. Non è necessario verificare la presenza di valori Null nelle variabili di questo tipo prima della dereferenziazione.
- *Nullable*: Null può essere assegnato alle variabili di questo tipo. Se si dereferenziano le variabili di questo tipo senza prima verificare la presenza di valori `null`, viene generato un avviso.
- *Indipendente dai valori*: si tratta dello stato precedente a C# 8. Le variabili di questo tipo possono essere dereferenziate o assegnate senza avvisi.
- *Sconosciuto*: in genere viene usato per i parametri di tipo in cui non sono previsti vincoli che indicano al compilatore che il tipo deve essere *nullable* o *non nullable*.

Il supporto dei valori Null di un tipo in una dichiarazione di variabile viene controllato dal *contesto nullable* in cui viene dichiarata la variabile.

## <a name="nullable-contexts"></a>Contesti nullable

I contesti nullable consentono il controllo con granularità fine di come il compilatore interpreta le variabili dei tipi riferimento. Il **contesto dell'annotazione nullable** di una determinata riga di origine è `enabled` o `disabled`. Nel compilatore delle versioni precedenti a C# 8 la compilazione di tutto il codice viene eseguita in un contesto nullable `disabled`: Qualsiasi tipo riferimento potrebbe essere null. Il **contesto degli avvisi Nullable** può essere impostato `enabled` su `disabled`o su. Il contesto degli avvisi nullable specifica gli avvisi generati dal compilatore usando l'analisi del flusso.

Il contesto di annotazione nullable e il contesto di avviso nullable possono essere impostati `Nullable` per un progetto utilizzando l'elemento nel file con *estensione csproj* . Questo elemento configura come il compilatore interpreta il supporto dei valori Null dei tipi e quali avvisi vengono generati. Le impostazioni valide sono:

- `enable`: il contesto dell'annotazione nullable è **enabled**. Il contesto dell'avviso nullable è **enabled**.
  - Le variabili di un tipo riferimento, ad esempio `string`, sono non nullable.  Tutti gli avvisi relativi al supporto dei valori Null sono abilitati.
- `warnings`: il contesto dell'annotazione nullable è **disabled**. Il contesto dell'avviso nullable è **enabled**.
  - Le variabili di un tipo riferimento sono indipendenti dai valori. Tutti gli avvisi relativi al supporto dei valori Null sono abilitati.
- `annotations`: il contesto dell'annotazione nullable è **enabled**. Il contesto dell'avviso nullable è **disabled**.
  - Le variabili di un tipo riferimento sono indipendenti dai valori. Tutti gli avvisi relativi al supporto dei valori Null sono disabilitati.
- `disable`: il contesto dell'annotazione nullable è **disabled**. Il contesto dell'avviso nullable è **disabled**.
  - Le variabili di un tipo riferimento sono indipendenti dai valori, come nelle versioni precedenti di C#. Tutti gli avvisi relativi al supporto dei valori Null sono disabilitati.

È anche possibile usare le direttive per impostare questi stessi contesti ovunque nel progetto:

- `#nullable enable`: imposta il contesto dell'annotazione nullable e il contesto dell'avviso nullable su **enabled**.
- `#nullable disable`: imposta il contesto dell'annotazione nullable e il contesto dell'avviso nullable su **disabled**.
- `#nullable restore`: ripristina le impostazioni di progetto per il contesto dell'annotazione nullable e il contesto dell'avviso nullable.
- `#nullable disable warnings`: impostare il contesto dell'avviso nullable su **disabled**.
- `#nullable enable warnings`: impostare il contesto dell'avviso nullable su **enabled**.
- `#nullable restore warnings`: ripristina le impostazioni di progetto per il contesto dell'avviso nullable.
- `#nullable disable annotations`: Impostare il contesto di annotazione Nullable su **disabled**.
- `#nullable enable annotations`: Impostare il contesto di annotazione Nullable su **Enabled**.
- `#nullable restore annotations`: Ripristina il contesto di avviso delle annotazioni nelle impostazioni del progetto.

I contesti dell'annotazione e dell'avviso nullable predefiniti sono `disabled`. Tale decisione significa che il codice esistente viene compilato senza modifiche e senza generare nuovi avvisi.

## <a name="nullable-annotation-context"></a>Contesto dell'annotazione nullable

Il compilatore usa le regole seguenti in un contesto di annotazione nullable disabilitato:

- Non è possibile dichiarare riferimenti nullable in un contesto disabilitato.
- Tutte le variabili di riferimento possono essere assegnate a null.
- Non vengono generati avvisi quando una variabile di un tipo riferimento viene dereferenziata.
- L'operatore null-forgiving non può essere usato in un contesto disabilitato.

Il comportamento è lo stesso delle versioni precedenti di C#.

Il compilatore usa le regole seguenti in un contesto di annotazione nullable abilitato:

- Qualsiasi variabile di un tipo riferimento è un **riferimento non nullable**.
- Qualsiasi riferimento non nullable può essere dereferenziato in modo sicuro.
- Qualsiasi tipo riferimento nullable (indicato da `?` dopo il tipo nella dichiarazione della variabile) può essere null. L'analisi statica determina se il valore è non null quando viene dereferenziato. In caso contrario, il compilatore genera un avviso.
- È possibile usare l'operatore null-forgiving per dichiarare che un riferimento nullable non è Null.

In un contesto di annotazione nullable abilitato il carattere `?` aggiunto al tipo riferimento dichiara un **tipo riferimento nullable**. L' **operatore** `!` che perdona i valori null può essere aggiunto a un'espressione per dichiarare che l'espressione non è null.

## <a name="nullable-warning-context"></a>Contesto dell'avviso nullable

Il contesto dell'avviso nullable è diverso dal contesto dell'annotazione nullable. Gli avvisi possono essere abilitati anche quando le nuove annotazioni sono disabilitate. Il compilatore usa l'analisi statica del flusso per determinare lo **stato null** di qualsiasi riferimento. Lo stato null è **not null** o **maybe null** quando il *contesto dell'avviso nullable* non è **disabled**. Se si dereferenzia un riferimento quando il compilatore ha determinato che è **maybe null**, il compilatore genera un avviso. Lo stato di un riferimento è **maybe null** a meno che il compilatore non riesca a determinare una di due condizioni:

1. La variabile è stata assegnata in modo definito a un valore non null.
1. La variabile o l'espressione è stata confrontata con null prima di dereferenziarla.

Il compilatore genera avvisi quando si dereferenzia una variabile o un'espressione in uno stato **forse null** quando il contesto di avviso `enabled`Nullable è. Vengono generati avvisi anche quando un'espressione o una variabile **maybe null** è assegnata a un tipo riferimento non nullable quando il contesto dell'annotazione nullable è `enabled`.

## <a name="learn-more"></a>Altre informazioni

- [Draft Nullable reference specification](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-8.0/nullable-reference-types-specification.md) (Bozza della specifica del riferimento nullable)
- [Introduzione all'esercitazione sui riferimenti nullable](tutorials/nullable-reference-types.md)
- [Eseguire la migrazione di una base di codice esistente a riferimenti nullable](tutorials/upgrade-to-nullable-references.md)
