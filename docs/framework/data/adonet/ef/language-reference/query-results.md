---
title: Risultati delle query
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bcd7b699-4e50-4523-8c33-2f54a103d94e
ms.openlocfilehash: 3ac80cfe06f8531dcd2343f676a6f78f8eb0e8f6
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854311"
---
# <a name="query-results"></a>Risultati delle query
Dopo che una query LINQ to Entities viene convertita in alberi dei comandi ed eseguita, i risultati della query vengono in genere restituiti come uno degli elementi seguenti:  
  
- Raccolta di zero o più oggetti entità tipizzate o proiezione di tipi complessi nel modello concettuale.  
  
- Tipi CLR supportati dal modello concettuale.  
  
- Raccolte inline.  
  
- Tipi anonimi.  
  
 Una volta eseguita la query sull'origine dati, i risultati vengono materializzati in tipi CLR e restituiti al client. Tutta la materializzazione degli oggetti viene eseguita da Entity Framework. Qualsiasi errore correlato all'impossibilità di eseguire il mapping tra Entity Framework e CLR comporterà la generazione di eccezioni durante la materializzazione degli oggetti.
  
 Se l'esecuzione della query restituisce tipi primitivi del modello concettuale, i risultati sono costituiti da tipi CLR autonomi e disconnessi dal Entity Framework. Se tuttavia la query restituisce una raccolta di oggetti entità tipizzati, rappresentati da <xref:System.Data.Objects.ObjectQuery%601>, questi tipi vengono registrati dal contesto dell'oggetto. Tutti i comportamenti degli oggetti, ad esempio raccolte figlio/padre, rilevamento delle modifiche, polimorfismo e così via, sono definiti nella Entity Framework. Questa funzionalità può essere utilizzata nella capacità, come definito nella Entity Framework. Per ulteriori informazioni, vedere [utilizzo di oggetti](../working-with-objects.md).
  
 I tipi di struct restituiti dalle query (ad esempio tipi anonimi e tipi complessi che ammettono i valori Null) possono avere valore `null`. Anche una proprietà <xref:System.Data.Objects.DataClasses.EntityCollection%601> di un'entità restituita può avere valore `null`. Questo può essere dovuto alla proiezione della proprietà della raccolta di un'entità con valore `null`, ad esempio la chiamata a <xref:System.Linq.Queryable.FirstOrDefault%2A> su un oggetto <xref:System.Data.Objects.ObjectQuery%601> che non dispone di elementi.  
  
 In alcune situazioni, potrebbe sembrare che una query generi un risultato materializzato durante la sua esecuzione, ma la query viene eseguita nel server e l'oggetto entità non viene mai materializzato in CLR. Questo può provocare problemi se si è legati agli effetti collaterali della materializzazione degli oggetti.  
  
 L'esempio seguente contiene una classe personalizzata, `MyContact`, con una proprietà `LastName`. Quando viene impostata la proprietà `LastName`, viene incrementata una variabile `count`. Se si eseguono le due query seguenti, tramite la prima query viene incrementata la variabile  `count`, mentre tramite la seconda query no. Questo avviene in quanto nella seconda query la proprietà `LastName` è proiettata dai risultati e la classe `MyContact` non viene mai creata, perché non è necessaria per eseguire la query sull'archivio.  
  
 [!code-csharp[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#materializationsideeffects)]
 [!code-vb[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#materializationsideeffects)]  
  
 [!code-csharp[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#mycontactclass)]
 [!code-vb[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#mycontactclass)]
