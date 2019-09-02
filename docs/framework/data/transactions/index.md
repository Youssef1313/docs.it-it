---
title: Elaborazione delle transazioni
ms.date: 03/30/2017
ms.assetid: effdc8e6-accf-41eb-98a5-431603ba218b
ms.openlocfilehash: de88247e5916ab6e080c4de361efecee0b193e18
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205916"
---
# <a name="transaction-processing"></a>Elaborazione delle transazioni
Quando si acquista un libro da una libreria online si offre denaro (tramite carta di credito) in cambio di un libro. Se la carta di credito è valida, una serie di operazioni correlate garantisce che l'acquirente riceva il libro e che la libreria riceva il denaro. Se tuttavia durante lo scambio si verifica un errore in una delle operazioni della serie, l'intero scambio ha esito negativo. L'acquirente non riceve il libro e la libreria non riceve il denaro.  
  
 La tecnologia responsabile dell'equità e della prevedibilità dello scambio è detta elaborazione delle transazioni. Le transazioni garantiscono che le risorse orientate ai dati vengano aggiornate in via definitiva solo dopo che tutte le operazioni all'interno dell'unità transazionale siano state completate correttamente. La combinazione di un set di operazioni correlate in un'unità in cui tutte le operazioni hanno lo stesso esito, sia esso positivo o negativo, consente di semplificare il ripristino in caso di errore e di rendere l'applicazione più affidabile.  
  
 I sistemi di elaborazione delle transazioni si basano sull'hosting in componenti hardware e software di un'applicazione orientata alle transazioni che esegue le transazioni di routine necessarie allo svolgimento di attività aziendali. Alcuni esempi di tale applicazione sono i sistemi che gestiscono la registrazione degli ordini di vendita, la prenotazione di biglietti aerei, le retribuzioni, i record degli impiegati, la lavorazione e la spedizione di merci.  
  
 Questa sezione fornisce sia informazioni di carattere generale sull'elaborazione delle transazioni sia informazioni specifiche su come scrivere applicazioni transazionali e gestori di risorse tramite Microsoft .NET Framework.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Nozioni fondamentali sulle transazioni](transaction-fundamentals.md)  
 Introduce i termini e in concetti fondamentali relativi all'elaborazione delle transazioni.  
  
 [Funzionalità offerte da System.Transactions](features-provided-by-system-transactions.md)  
 Descrive come utilizzare le funzionalità di System.Transactions per scrivere un'applicazione transazionale personalizzata.  
  
## <a name="reference"></a>Riferimenti  
 <xref:System.Transactions>  
 Fornisce le classi che consentono al codice di partecipare alle transazioni. Tali classi supportano le transazioni con più partecipanti distribuiti, le notifiche a fase multipla e le integrazioni durevoli.
