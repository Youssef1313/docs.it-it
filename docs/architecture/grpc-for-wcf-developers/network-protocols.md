---
title: Protocolli di rete-gRPC per sviluppatori WCF
description: Panoramica dei protocolli di rete gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 5e837738bd345608ca7119d04c9221acb220c276
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971713"
---
# <a name="network-protocols"></a>Protocolli di rete

Diversamente da WCF, gRPC Usa HTTP/2 come base per la rete. Ciò offre vantaggi significativi rispetto a WCF e SOAP, che operano solo su HTTP/1.1. Per gli sviluppatori che vogliono usare gRPC, dato che non esiste alcuna alternativa a HTTP/2, sembrerebbe il momento ideale per esplorare HTTP/2 in modo più dettagliato e identificare i vantaggi aggiuntivi per l'uso di gRPC.

HTTP/2, rilasciato da Internet Engineering Task Force in 2015, è stato derivato dal protocollo sperimentale SPDY, che era già usato da Google. È stato progettato appositamente per essere più efficiente, più veloce e più sicuro rispetto a HTTP/1.1.

## <a name="key-features-of-http2"></a>Funzionalità principali di HTTP/2

Nell'elenco seguente vengono illustrate alcune delle principali funzionalità e vantaggi di HTTP/2:

### <a name="binary-protocol"></a>Protocollo binario

I cicli di richiesta/risposta non necessitano più di comandi di testo. Questo semplifica e velocizza l'implementazione dei comandi. In particolare, l'analisi dei dati è più veloce e usa meno memoria, la latenza di rete è ridotta con evidenti miglioramenti correlati alla velocità e c'è un uso ottimale delle risorse di rete.

### <a name="streams"></a>Flussi

I flussi consentono la creazione di connessioni di lunga durata tra mittente e ricevitore, in cui è possibile inviare più messaggi o frame in modo asincrono. Più flussi possono funzionare in modo indipendente su una singola connessione HTTP/2.

### <a name="request-multiplexing-over-a-single-tcp-connection"></a>Richiedi multiplexing su una singola connessione TCP

Questa funzionalità è una delle innovazioni più importanti di HTTP/2. Consentendo più richieste parallele di dati, è ora possibile scaricare i file Web contemporaneamente da un singolo server. I siti Web vengono caricati più velocemente e la necessità di ottimizzazione è ridotta. Blocco Head-of-line (HOL), in cui le risposte pronte devono attendere l'invio finché non viene completata una richiesta precedente, viene anche attenuato (anche se il blocco di HOL può ancora verificarsi a livello di trasporto TCP).

### <a name="nettcp-like-performance-cross-platform"></a>Prestazioni simili a NetTCP, multipiattaforma

Fondamentalmente, la combinazione di gRPC e HTTP/2 offre agli sviluppatori almeno la velocità e l'efficienza equivalenti delle associazioni NetTCP per WCF e, in alcuni casi, una velocità ed efficienza ancora maggiore. Tuttavia, a differenza di NetTCP, gRPC su HTTP/2 non è vincolato alle applicazioni .NET.

>[!div class="step-by-step"]
>[Precedente](interface-definition-language.md)
>[Successivo](why-grpc.md)
