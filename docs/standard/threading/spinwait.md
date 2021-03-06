---
title: SpinWait
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronization primitives, SpinWait
ms.assetid: 36012f42-34e5-4f86-adf4-973f433ed6c6
ms.openlocfilehash: 91588fc6e9c3c8e85de6a315c0743efb0137ecd5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128993"
---
# <a name="spinwait"></a>SpinWait
<xref:System.Threading.SpinWait?displayProperty=nameWithType> è un tipo di sincronizzazione leggera che è possibile usare in scenari di basso livello per evitare i cambi di contesto dispendiosi e le transizioni del kernel necessarie per gli eventi del kernel. Nei computer multicore, quando non si prevede che una risorsa venga bloccata per lunghi periodi di tempo, per un thread in attesa potrebbe essere più efficiente ruotare in modalità utente per alcune decine o centinaia di cicli e quindi ritentare di acquisire la risorsa. Se la risorsa è disponibile dopo la rotazione, vengono risparmiate diverse migliaia di cicli. Se la risorsa continua a non essere disponibile, sono stati usati solo alcuni cicli ed è possibile attivare un'attesa basata sul kernel. Questa combinazione di rotazione-attesa è talvolta detta un *operazione di attesa a due fasi*.  
  
 <xref:System.Threading.SpinWait> è progettato per essere usato in combinazione con i tipi di .NET Framework che eseguono il wrapping di eventi del kernel, ad esempio <xref:System.Threading.ManualResetEvent>. <xref:System.Threading.SpinWait> può essere usato anche da solo per la funzionalità di rotazione di base in un unico programma.  
  
 <xref:System.Threading.SpinWait> è molto più di un ciclo vuoto. Viene implementato con particolare attenzione per offrire un comportamento di rotazione corretto per usi generali; avvia cambi di contesto in caso di rotazione per una durata sufficiente (approssimativamente l'intervallo di tempo necessario per una transizione del kernel). Ad esempio, nei computer a core singolo, <xref:System.Threading.SpinWait> restituisce subito l'intervallo di tempo del thread perché la rotazione impedisce l'avanzamento per tutti i thread. <xref:System.Threading.SpinWait> restituisce il controllo anche in computer multicore per impedire al thread in attesa di bloccare i thread con priorità superiore o la funzionalità Garbage Collector. Pertanto, se si usa <xref:System.Threading.SpinWait> in un'operazione di attesa a due fasi, è consigliabile richiamare l'attesa del kernel prima che <xref:System.Threading.SpinWait> avvii un cambio di contesto. <xref:System.Threading.SpinWait> fornisce la proprietà <xref:System.Threading.SpinWait.NextSpinWillYield%2A>, che è possibile controllare prima di ogni chiamata a <xref:System.Threading.SpinWait.SpinOnce%2A>. Quando la proprietà restituisce `true`, avviare l'operazione di attesa. Per un esempio, vedere [Procedura: Usare SpinWait per implementare un'operazione di attesa a due fasi](../../../docs/standard/threading/how-to-use-spinwait-to-implement-a-two-phase-wait-operation.md).  
  
 Se non si esegue un'operazione di attesa a due fasi, ma la rotazione continua finché una condizione è vera, è possibile abilitare <xref:System.Threading.SpinWait> per eseguire i relativi cambi di contesto in modo che sia un elemento positivo nell'ambiente del sistema operativo Windows. L'esempio di base seguente illustra un <xref:System.Threading.SpinWait> in uno stack senza blocco. Se è necessario uno stack thread-safe e ad alte prestazioni, è consigliabile usare <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>.  
  
 [!code-csharp[CDS_SpinWait#05](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait.cs#05)]
 [!code-vb[CDS_SpinWait#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/cds_spinwait1.vb#05)]  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.Threading.Thread.SpinWait%2A>
- [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md) (Oggetti e funzionalità del threading)
