---
title: Esecuzione remota e locale
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ee50e943-9349-4c84-ab1c-c35d3ada1a9c
ms.openlocfilehash: a21d5bbffdb1a78d3062929a1ca384a750af59a7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781163"
---
# <a name="remote-vs-local-execution"></a>Esecuzione remota e locale
È possibile scegliere di eseguire le query in modalità remota, dove il motore di database esegue la query sul database, oppure localmente, dove [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] esegue la query sulla cache locale.  
  
## <a name="remote-execution"></a>Esecuzione remota  
 Si consideri la query riportata di seguito:  
  
 [!code-csharp[DLinqQueryConcepts#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#7)]
 [!code-vb[DLinqQueryConcepts#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#7)]  
  
 Se nel database sono presenti migliaia di righe di ordini, non è opportuno recuperarli tutti per elaborare un piccolo subset. In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] la classe <xref:System.Data.Linq.EntitySet%601> implementa l'interfaccia <xref:System.Linq.IQueryable>. Questo approccio assicura che tali query possano essere eseguite in modalità remota. Questa tecnica offre due vantaggi principali:  
  
- I dati non necessari non vengono recuperati.  
  
- Una query eseguita dal motore di database è spesso più efficiente grazie agli indici del database.  
  
## <a name="local-execution"></a>e locale  
 In altre situazioni può essere necessario disporre del set completo di entità correlate nella cache locale. A questo scopo <xref:System.Data.Linq.EntitySet%601> fornisce il metodo <xref:System.Data.Linq.EntitySet%601.Load%2A> per caricare in modo esplicito tutti i membri di <xref:System.Data.Linq.EntitySet%601>.  
  
 Se <xref:System.Data.Linq.EntitySet%601> è già caricato, le query successive vengono eseguite localmente. Questo approccio risulta utile in due modi:  
  
- Se il set completo deve essere usato localmente o più volte, è possibile evitare l'esecuzione di query remote e le latenze che ne derivano.  
  
- L'entità può essere serializzata come un'entità completa.  
  
 Il frammento di codice seguente illustra come è possibile ottenere l'esecuzione locale:  
  
 [!code-csharp[DLinqQueryConcepts#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#8)]
 [!code-vb[DLinqQueryConcepts#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#8)]  
  
## <a name="comparison"></a>Confronto  
 Queste due funzionalità consentono di ottenere una potente combinazione di opzioni: l'esecuzione remota per le raccolte di grandi dimensioni e l'esecuzione locale per le piccole raccolte o dove è necessario disporre della raccolta completa. L'esecuzione remota viene implementata tramite <xref:System.Linq.IQueryable>, mentre l'esecuzione locale viene implementata su una raccolta <xref:System.Collections.Generic.IEnumerable%601> in memoria. Per forzare l'esecuzione locale, ovvero <xref:System.Collections.Generic.IEnumerable%601>, vedere [convertire un tipo in un IEnumerable generico](convert-a-type-to-a-generic-ienumerable.md).  
  
### <a name="queries-against-unordered-sets"></a>Query su set non ordinati  
 Si noti la differenza importante tra una raccolta locale che <xref:System.Collections.Generic.List%601> implementa e una raccolta che fornisce query remote eseguite su *set non ordinati* in un database relazionale. I metodi <xref:System.Collections.Generic.List%601>, ad esempio quelli che usano valori di indice, richiedono la semantica di elenco che in genere non può essere ottenuta tramite una query remota su un set non ordinato. Per questo motivo, tali metodi caricano in modo implicito <xref:System.Data.Linq.EntitySet%601> per consentire l'esecuzione locale.  
  
## <a name="see-also"></a>Vedere anche

- [Concetti relativi alle query](query-concepts.md)
