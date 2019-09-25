---
title: 'Procedura: Dichiarare errori nei contratti di servizio'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e8da98e7-d22f-4f60-ac82-3fb0928a353f
ms.openlocfilehash: 2de14a76fd2ce8ad656c2b64f5f9e5b17d81eebc
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216872"
---
# <a name="how-to-declare-faults-in-service-contracts"></a><span data-ttu-id="e08a6-102">Procedura: Dichiarare errori nei contratti di servizio</span><span class="sxs-lookup"><span data-stu-id="e08a6-102">How to: Declare Faults in Service Contracts</span></span>

<span data-ttu-id="e08a6-103">Nel codice gestito, vengono generate eccezioni quando si verificano condizioni di errore.</span><span class="sxs-lookup"><span data-stu-id="e08a6-103">In managed code, exceptions are thrown when error conditions occur.</span></span> <span data-ttu-id="e08a6-104">Nelle applicazioni Windows Communication Foundation (WCF), tuttavia, i contratti di servizio specificano quali informazioni sugli errori vengono restituite ai client dichiarando gli errori SOAP nel contratto di servizio.</span><span class="sxs-lookup"><span data-stu-id="e08a6-104">In Windows Communication Foundation (WCF) applications, however, service contracts specify what error information is returned to clients by declaring SOAP faults in the service contract.</span></span> <span data-ttu-id="e08a6-105">Per una panoramica della relazione tra eccezioni ed errori, vedere [specifica e gestione di errori in contratti e servizi](specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="e08a6-105">For an overview of the relationship between exceptions and faults, see [Specifying and Handling Faults in Contracts and Services](specifying-and-handling-faults-in-contracts-and-services.md).</span></span>

## <a name="create-a-service-contract-that-specifies-a-soap-fault"></a><span data-ttu-id="e08a6-106">Creare un contratto di servizio che specifica un errore SOAP.</span><span class="sxs-lookup"><span data-stu-id="e08a6-106">Create a service contract that specifies a SOAP fault</span></span>

1. <span data-ttu-id="e08a6-107">Creare un contratto di servizio che contiene almeno un'operazione.</span><span class="sxs-lookup"><span data-stu-id="e08a6-107">Create a service contract that contains at least one operation.</span></span> <span data-ttu-id="e08a6-108">Per un esempio, vedere [Procedura: Definire un contratto](how-to-define-a-wcf-service-contract.md)di servizio.</span><span class="sxs-lookup"><span data-stu-id="e08a6-108">For an example, see [How to: Define a Service Contract](how-to-define-a-wcf-service-contract.md).</span></span>

2. <span data-ttu-id="e08a6-109">Selezionare un'operazione che può specificare una condizione di errore in merito alla quale i client prevedono di ricevere una notifica.</span><span class="sxs-lookup"><span data-stu-id="e08a6-109">Select an operation that can specify an error condition about which clients can expect to be notified.</span></span> <span data-ttu-id="e08a6-110">Per decidere quali condizioni di errore giustificano la restituzione di errori SOAP ai client, vedere [specifica e gestione di errori in contratti e servizi](specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="e08a6-110">To decide which error conditions justify returning SOAP faults to clients, see [Specifying and Handling Faults in Contracts and Services](specifying-and-handling-faults-in-contracts-and-services.md).</span></span>

3. <span data-ttu-id="e08a6-111">Applicare una classe <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> all'operazione selezionata e passare un tipo di errore serializzabile al costruttore.</span><span class="sxs-lookup"><span data-stu-id="e08a6-111">Apply a <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> to the selected operation and pass a serializable fault type to the constructor.</span></span> <span data-ttu-id="e08a6-112">Per informazioni dettagliate sulla creazione e sull'uso di tipi serializzabili, vedere [specifica trasferimento dati nei contratti di servizio](./feature-details/specifying-data-transfer-in-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="e08a6-112">For details about creating and using serializable types, see [Specifying Data Transfer in Service Contracts](./feature-details/specifying-data-transfer-in-service-contracts.md).</span></span> <span data-ttu-id="e08a6-113">Nell'esempio seguente viene illustrato come specificare che l'operazione `SampleMethod` può produrre un `GreetingFault`.</span><span class="sxs-lookup"><span data-stu-id="e08a6-113">The following example shows how to specify that the `SampleMethod` operation can result in a `GreetingFault`.</span></span>

     [!code-csharp[FaultContractAttribute#4](~/samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
     [!code-vb[FaultContractAttribute#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]

4. <span data-ttu-id="e08a6-114">Ripetere i passaggi 2 e 3 per tutte le operazioni nel contratto che comunicano condizioni di errore ai client.</span><span class="sxs-lookup"><span data-stu-id="e08a6-114">Repeat steps 2 and 3 for all operations in the contract that communicate error conditions to clients.</span></span>

## <a name="implementing-an-operation-to-return-a-specified-soap-fault"></a><span data-ttu-id="e08a6-115">Implementazione di un'operazione per restituire un errore SOAP specificato</span><span class="sxs-lookup"><span data-stu-id="e08a6-115">Implementing an Operation to Return a Specified SOAP Fault</span></span>
 <span data-ttu-id="e08a6-116">Dopo che un'operazione ha specificato che può essere restituito un determinato errore SOAP (come nella procedura seguente), per comunicare una condizione di errore a un'applicazione chiamante, il passaggio successivo consiste nell'implementare la specifica in questione.</span><span class="sxs-lookup"><span data-stu-id="e08a6-116">Once an operation has specified that a specific SOAP fault can be returned (such as in the preceding procedure) to communicate an error condition to a calling application, the next step is to implement that specification.</span></span>

### <a name="throw-the-specified-soap-fault-in-the-operation"></a><span data-ttu-id="e08a6-117">Generare l'errore SOAP specificato nell'operazione</span><span class="sxs-lookup"><span data-stu-id="e08a6-117">Throw the specified SOAP fault in the operation</span></span>

1. <span data-ttu-id="e08a6-118">Quando in un'operazione si verifica una condizione di errore specificata da <xref:System.ServiceModel.FaultContractAttribute>, generare una nuova eccezione <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> in cui l'errore SOAP specificato è il parametro di tipo.</span><span class="sxs-lookup"><span data-stu-id="e08a6-118">When a <xref:System.ServiceModel.FaultContractAttribute>-specified error condition occurs in an operation, throw a new <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> where the specified SOAP fault is the type parameter.</span></span> <span data-ttu-id="e08a6-119">Nell'esempio seguente viene illustrato come generare il `GreetingFault` nel `SampleMethod` descritto nella procedura precedente e nella sezione Codice seguente.</span><span class="sxs-lookup"><span data-stu-id="e08a6-119">The following example shows how to throw the `GreetingFault` in the `SampleMethod` shown in the preceding procedure and in the following Code section.</span></span>

     [!code-csharp[FaultContractAttribute#5](~/samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
     [!code-vb[FaultContractAttribute#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]

## <a name="example"></a><span data-ttu-id="e08a6-120">Esempio</span><span class="sxs-lookup"><span data-stu-id="e08a6-120">Example</span></span>

<span data-ttu-id="e08a6-121">Nell'esempio di codice seguente viene illustrata un'implementazione di una singola operazione che specifica un `GreetingFault` per l'operazione `SampleMethod`.</span><span class="sxs-lookup"><span data-stu-id="e08a6-121">The following code example shows an implementation of a single operation that specifies a `GreetingFault` for the `SampleMethod` operation.</span></span>

[!code-csharp[FaultContractAttribute#1](~/samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#1)]
[!code-vb[FaultContractAttribute#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#1)]

## <a name="see-also"></a><span data-ttu-id="e08a6-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e08a6-122">See also</span></span>

- <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
