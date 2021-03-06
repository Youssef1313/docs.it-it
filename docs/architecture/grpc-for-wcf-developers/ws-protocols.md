---
title: Protocolli WS-*-gRPC per sviluppatori WCF
description: Esaminare i protocolli WS-* supportati da WCF e le alternative disponibili con gRPC
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 4e7b80df182fb69cc51e14738e59ad87efaf5dd2
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846037"
---
# <a name="ws--protocols"></a>Protocolli WS-\*

Uno dei vantaggi effettivi dell'utilizzo di Windows Communication Foundation (WCF) era che supportava molti dei protocolli standard _WS-\*_ esistenti. In questa sezione viene illustrato brevemente il modo in cui gRPC gestisce gli stessi protocolli WS-\* e illustra le opzioni disponibili quando non esiste alcuna alternativa.

## <a name="metadata-exchange---ws-policy-ws-discovery-and-so-on"></a>Scambio di metadati-WS-Policy, WS-Discovery e così via

I servizi SOAP espongono documenti di schema Web Services Description Language (WSDL) con informazioni quali formati di dati, operazioni o opzioni di comunicazione. Questo schema può essere utilizzato per generare il codice client.

gRPC funziona in modo ottimale quando i server e i client vengono generati dagli stessi file di `.proto`, ma un'estensione facoltativa di Reflection Server consente di esporre informazioni dinamiche da un server in esecuzione. Per altre informazioni, vedere il pacchetto NuGet [Grpc. Reflection](https://nuget.org/packages/Grpc.Reflection) e l' [articolo C# Reflection server Grpc](https://github.com/grpc/grpc/blob/master/doc/csharp/server_reflection.md) .

Il protocollo WS-Discovery viene utilizzato per individuare i servizi in una rete locale. i servizi gRPC in genere si trovano usando DNS o un registro del servizio, ad esempio Consul o ZooKeeper.

## <a name="security--ws-security-ws-federation-xml-encryption-and-so-on"></a>Sicurezza: WS-Security, WS-Federation, crittografia XML e così via

Sicurezza, autenticazione e autorizzazione sono trattati in modo più dettagliato nel [capitolo 6](security.md). Tuttavia, è importante notare che, a differenza di WCF, gRPC non supporta WS-Security, WS Federation o la crittografia XML. Anche in questo caso, gRPC offre una sicurezza eccellente; tutto il traffico di rete gRPC viene crittografato automaticamente quando si usa HTTP/2 su TLS e i certificati X509 possono essere usati per l'autenticazione reciproca tra client e server.

## <a name="ws-reliablemessaging"></a>WS-ReliableMessaging

gRPC non fornisce un equivalente a WS-ReliableMessaging. La semantica di ripetizione dei tentativi deve essere gestita nel codice, possibilmente con una libreria come [Polly](https://github.com/App-vNext/Polly). Quando è in esecuzione in Kubernetes o in ambienti di orchestrazione simili, i [mesh](service-mesh.md) dei servizi consentono anche di fornire messaggistica affidabile tra i servizi.

## <a name="ws-transaction-ws-coordination"></a>WS-Transaction, WS-Coordination

L'implementazione di transazioni distribuite di WCF utilizza Microsoft Distributed Transaction Coordinator o MSDTC di Windows. Funziona con i gestori di risorse che lo supportano in modo specifico, ad esempio SQL Server, MSMQ o file System Windows. Nel mondo dei microservizi moderni, in parte grazie alla più ampia gamma di tecnologie in uso, non esiste ancora alcun equivalente. Per informazioni sulle transazioni, vedere [appendice a](appendix.md).

>[!div class="step-by-step"]
>[Precedente](error-handling.md)
>[Successivo](migrate-wcf-to-grpc.md)
