---
title: 'Procedura: Specificare la modalità di esecuzione in PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use execution mode
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 705b6bc364e2ecf00c3629814228157c90017a8b
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988445"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a>Procedura: Specificare la modalità di esecuzione in PLINQ
Questo esempio mostra come forzare PLINQ a ignorare l'euristica predefinita e parallelizzare una query indipendentemente dalla relativa forma.  
  
> [!WARNING]
> Lo scopo di questo esempio consiste nell'illustrare l'uso ed è possibile che l'esecuzione non sia più veloce rispetto alla query LINQ to Objects sequenziale equivalente. Per altre informazioni sull'aumento di velocità, vedere [Informazioni sull'aumento di velocità in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Esempio  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 PLINQ è progettato per sfruttare le opportunità di parallelizzazione. Tuttavia, l'esecuzione parallela non è vantaggiosa per tutte le query. Quando una query contiene un delegato utente singolo che esegue operazioni minime, ad esempio, risulta in genere più veloce l'esecuzione sequenziale. Il motivo è che il sovraccarico correlato all'abilitazione dell'esecuzione parallela è superiore all'aumento di velocità ottenuto. PLINQ pertanto non parallelizza automaticamente ogni query. Esamina prima di tutto la forma della query e i vari operatori inclusi. In base a questa analisi, in modalità di esecuzione predefinita PLINQ può decidere di eseguire alcune o tutte le query in sequenza. In alcuni casi, tuttavia, l'utente potrebbe avere più informazioni sulla query rispetto a quelle che PLINQ è in grado di determinare dall'analisi. Si potrebbe ad esempio sapere che un delegato è molto costoso e che la parallelizzazione offre sicuramente vantaggi per la query. In questi casi, è possibile usare il metodo <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> e specificare il valore <xref:System.Linq.ParallelExecutionMode.ForceParallelism> per indicare a PLINQ di eseguire sempre la query in parallelo.  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 Tagliare e incollare questo codice nell'[esempio di dati PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) e chiamare il metodo da `Main`.  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.Linq.ParallelEnumerable.AsSequential%2A>
- [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
