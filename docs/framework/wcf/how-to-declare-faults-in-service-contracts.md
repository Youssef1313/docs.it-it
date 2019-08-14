---
title: 'Procedura: Dichiarare errori nei contratti di servizio'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e8da98e7-d22f-4f60-ac82-3fb0928a353f
ms.openlocfilehash: 6f08ef6eb62b31b0969779d51d0a068145a23fc0
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971974"
---
# <a name="how-to-declare-faults-in-service-contracts"></a>Procedura: Dichiarare errori nei contratti di servizio

Nel codice gestito, vengono generate eccezioni quando si verificano condizioni di errore. Nelle applicazioni Windows Communication Foundation (WCF), tuttavia, i contratti di servizio specificano quali informazioni sugli errori vengono restituite ai client dichiarando gli errori SOAP nel contratto di servizio. Per una panoramica della relazione tra eccezioni ed errori, vedere [specifica e gestione di errori in contratti e servizi](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).

## <a name="create-a-service-contract-that-specifies-a-soap-fault"></a>Creare un contratto di servizio che specifica un errore SOAP.

1. Creare un contratto di servizio che contiene almeno un'operazione. Per un esempio, vedere [Procedura: Definire un contratto](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)di servizio.

2. Selezionare un'operazione che può specificare una condizione di errore in merito alla quale i client prevedono di ricevere una notifica. Per decidere quali condizioni di errore giustificano la restituzione di errori SOAP ai client, vedere [specifica e gestione di errori in contratti e servizi](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).

3. Applicare una classe <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> all'operazione selezionata e passare un tipo di errore serializzabile al costruttore. Per informazioni dettagliate sulla creazione e sull'uso di tipi serializzabili, vedere [specifica trasferimento dati nei contratti di servizio](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). Nell'esempio seguente viene illustrato come specificare che l'operazione `SampleMethod` può produrre un `GreetingFault`.

     [!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
     [!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]

4. Ripetere i passaggi 2 e 3 per tutte le operazioni nel contratto che comunicano condizioni di errore ai client.

## <a name="implementing-an-operation-to-return-a-specified-soap-fault"></a>Implementazione di un'operazione per restituire un errore SOAP specificato
 Dopo che un'operazione ha specificato che può essere restituito un determinato errore SOAP (come nella procedura seguente), per comunicare una condizione di errore a un'applicazione chiamante, il passaggio successivo consiste nell'implementare la specifica in questione.

### <a name="throw-the-specified-soap-fault-in-the-operation"></a>Generare l'errore SOAP specificato nell'operazione

1. Quando in un'operazione si verifica una condizione di errore specificata da <xref:System.ServiceModel.FaultContractAttribute>, generare una nuova eccezione <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> in cui l'errore SOAP specificato è il parametro di tipo. Nell'esempio seguente viene illustrato come generare il `GreetingFault` nel `SampleMethod` descritto nella procedura precedente e nella sezione Codice seguente.

     [!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
     [!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]

## <a name="example"></a>Esempio

Nell'esempio di codice seguente viene illustrata un'implementazione di una singola operazione che specifica un `GreetingFault` per l'operazione `SampleMethod`.

[!code-csharp[FaultContractAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#1)]
[!code-vb[FaultContractAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#1)]

## <a name="see-also"></a>Vedere anche

- <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
