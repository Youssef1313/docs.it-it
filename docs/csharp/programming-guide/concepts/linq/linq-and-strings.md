---
title: LINQ e stringhe (C#)
ms.date: 07/20/2015
ms.assetid: dbe2d657-b3f3-487e-b645-21fb2d71cd7b
ms.openlocfilehash: fb1714c54331ead80cd28435cf3ed1c4c54a704e
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2019
ms.locfileid: "74140904"
---
# <a name="linq-and-strings-c"></a>LINQ e stringhe (C#)

È possibile usare LINQ per eseguire query e trasformare stringhe e raccolte di stringhe. LINQ può essere particolarmente utile con i dati semistrutturati nei file di testo. Le query LINQ possono essere usate in associazione a funzioni per valori stringa tradizionali ed espressioni regolari. Ad esempio, è possibile usare il metodo <xref:System.String.Split%2A?displayProperty=nameWithType> o <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> per creare una matrice di stringhe in cui sarà possibile eseguire query o apportare modifiche usando LINQ. È possibile usare il metodo <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> nella clausola `where` di una query LINQ. È anche possibile usare LINQ per eseguire query o modificare i risultati <xref:System.Text.RegularExpressions.MatchCollection> restituiti da un'espressione regolare.

È anche possibile usare le tecniche descritte in questa sezione per trasformare dati di testo semistrutturati in XML. Per altre informazioni, vedere [Procedura: Generare XML da file CSV](how-to-generate-xml-from-csv-files.md).

Gli esempi di questa sezione sono suddivisi in due categorie:

## <a name="querying-a-block-of-text"></a>Esecuzione di query in un blocco di testo

È possibile eseguire query, analizzare e modificare blocchi di testo suddividendoli in una matrice di stringhe più piccole sottoponibile a query usando il metodo <xref:System.String.Split%2A?displayProperty=nameWithType> o <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType>. È possibile suddividere il testo di origine in parole, frasi, paragrafi, pagine o altri criteri e quindi eseguire altre suddivisioni se richieste nella query.

- [Come contare le occorrenze di una parola in una stringa (LINQ) (C#)](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
  Descrive come usare LINQ per eseguire query semplici nel testo.

- [Procedura: Eseguire una query per trovare frasi che contengono un set definito di parole (LINQ) (C#)](how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)

  Descrive come suddividere file di testo su limiti arbitrari e come eseguire query in ogni parte.

- [Procedura: Eseguire una query per trovare caratteri in una stringa (LINQ) (C#)](how-to-query-for-characters-in-a-string-linq.md)

  Dimostra che una stringa è un tipo sottoponibile a query.

- [Come combinare query LINQ con espressioni regolari (C#)](how-to-combine-linq-queries-with-regular-expressions.md)

  Descrive come usare le espressioni regolari nelle query LINQ per un modello complesso corrispondente ai risultati della query filtrati.

## <a name="querying-semi-structured-data-in-text-format"></a>Esecuzione di query di dati semistrutturati in formato testo

Numerosi tipi di file di testo sono costituiti da una serie di righe, spesso con formattazione simile, ad esempio file delimitati da tabulazione o virgola o righe a lunghezza fissa. Dopo la lettura del file di testo in memoria, è possibile usare LINQ per eseguire query e/o modificare le righe. Le query LINQ semplificano anche la combinazione di dati di più origini.

- [Procedura: Trovare la differenza dei set tra due elenchi (LINQ) (C#)](how-to-find-the-set-difference-between-two-lists-linq.md)

  Descrive come trovare tutte le stringhe presenti in un elenco ma non in un altro elenco.

- [Procedura: Ordinare o filtrare i dati di testo in base a qualsiasi parola o campo (LINQ) (C#)](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

  Descrive come ordinare le righe di testo in base a una parola o un campo.

- [Procedura: Riordinare i campi di un file delimitato (LINQ) (C#)](how-to-reorder-the-fields-of-a-delimited-file-linq.md)

  Descrive come riordinare i campi in una riga in un file con estensione csv.

- [Procedura: combinare e confrontare raccolte di stringhe (LINQ) (C#)](how-to-combine-and-compare-string-collections-linq.md)

  Descrive come combinare elenchi di stringhe in diversi modi.

- [Procedura: Popolare le raccolte di oggetti da più origini (LINQ) (C#)](how-to-populate-object-collections-from-multiple-sources-linq.md)

  Descrive come creare raccolte di oggetti usando più file di testo come origini dati.

- [Procedura: Creare un join del contenuto da file non analoghi (LINQ) (C#)](how-to-join-content-from-dissimilar-files-linq.md)
  
  Descrive come combinare le stringhe in due elenchi in un'unica stringa usando una chiave corrispondente.

- [Procedura: Suddividere un file in molti file usando i gruppi (LINQ) (C#)](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
  
  Descrive come creare file nuovi usando un singolo file come origine dati.

- [Come calcolare i valori di colonna in un file di testo CSV (LINQ)C#()](how-to-compute-column-values-in-a-csv-text-file-linq.md)
  
  Descrive come eseguire calcoli matematici in dati di testo in file con estensione csv.

## <a name="see-also"></a>Vedere anche

- [Language-Integrated Query (LINQ) (C#)](index.md)
- [Procedura: generare XML da file CSV](how-to-generate-xml-from-csv-files.md)
