---
title: 'Procedura: mettersi in ascolto di richieste di annullamento con handle di attesa'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, waiting with wait handles
ms.assetid: 6e2aa49b-fc84-4bcf-962b-17db98b7edcb
ms.openlocfilehash: 43ca52359a48d3ac5a27933fcc8ce56c07159cac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137985"
---
# <a name="how-to-listen-for-cancellation-requests-that-have-wait-handles"></a>Procedura: mettersi in ascolto di richieste di annullamento con handle di attesa
Se un metodo è bloccato mentre è in attesa che un evento venga segnalato, non può controllare il valore del token di annullamento e rispondere in modo tempestivo. Il primo esempio illustra come risolvere questo problema quando si usano eventi come <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> che non supportano in modo nativo il framework di annullamento unificato. Il secondo esempio illustra un approccio più semplice che usa <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, che supporta l'annullamento unificato.  
  
> [!NOTE]
> Quando "Just My Code" è abilitato, Visual Studio in alcuni casi si interromperà in corrispondenza della riga che genera l'eccezione e visualizzerà un messaggio di errore simile a "Eccezione non gestita dal codice utente". Questo errore non è grave. È possibile premere F5 per continuare e osservare il comportamento di gestione delle eccezioni illustrato negli esempi seguenti. Per impedire l'interruzione di Visual Studio al primo errore, deselezionare semplicemente la casella di controllo "Just My Code" in **Strumenti, Opzioni, Debug, Generale**.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente usa un oggetto <xref:System.Threading.ManualResetEvent> per illustrare come sbloccare gli handle di attesa che non supportano l'annullamento unificato.  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## <a name="example"></a>Esempio  
 L'esempio seguente usa un oggetto <xref:System.Threading.ManualResetEventSlim> per illustrare come sbloccare le primitive di coordinamento che supportano l'annullamento unificato. Lo stesso approccio può essere usato con altre primitive di coordinamento leggere, ad esempio <xref:System.Threading.Semaphore>`Slim` e <xref:System.Threading.CountdownEvent>.  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## <a name="see-also"></a>Vedere anche

- [Annullamento in thread gestiti](../../../docs/standard/threading/cancellation-in-managed-threads.md)
