---
title: 'Procedura: Ascolto di più richieste di annullamento'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation tokens, joining
- LinkedTokenSource, how to
ms.assetid: 6f4f3804-2ed7-41b4-a97a-6e32b93f6e05
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2684f0fd43f84573933fc0a7107ce4f9035bc092
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913312"
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a>Procedura: Ascolto di più richieste di annullamento
Questo esempio illustra come essere in ascolto di due token di annullamento contemporaneamente, in modo da annullare un'operazione se uno dei due token lo richiede.  
  
> [!NOTE]
> Quando "Just My Code" è abilitato, Visual Studio in alcuni casi si interromperà in corrispondenza della riga che genera l'eccezione e visualizzerà un messaggio di errore simile a "Eccezione non gestita dal codice utente". Questo errore non è grave. È possibile premere F5 per continuare e osservare il comportamento di gestione delle eccezioni illustrato negli esempi seguenti. Per impedire l'interruzione di Visual Studio al primo errore, deselezionare semplicemente la casella di controllo "Just My Code" in **Strumenti, Opzioni, Debug, Generale**.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente il metodo <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> viene usato per unire due token in un token. In questo modo, il token può essere passato ai metodi che accettano un solo token di annullamento come argomento. L'esempio illustra uno scenario comune in cui un metodo deve rilevare sia un token passato dall'esterno della classe che un token generato all'interno della classe.  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 Quando il token collegato genera un'eccezione <xref:System.OperationCanceledException>, il token passato all'eccezione è il token collegato, non uno dei token predecessori. Per determinare quale token è stato annullato, controllare direttamente lo stato dei token predecessori.  
  
 In questo esempio l'eccezione <xref:System.AggregateException> non deve essere mai generata, ma qui viene intercettata perché in scenari reali per le eccezioni diverse da <xref:System.OperationCanceledException> generate da un delegato dell'attività viene eseguito il wrapping in un oggetto <xref:System.AggregateException>.  
  
## <a name="see-also"></a>Vedere anche

- [Annullamento in thread gestiti](../../../docs/standard/threading/cancellation-in-managed-threads.md)
