---
title: Contatori delle prestazioni per l'operazione
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: 7a9b35346333f7b910802ff2a1b1769d177f3952
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040323"
---
# <a name="operation-performance-counters"></a><span data-ttu-id="1f88d-102">Contatori delle prestazioni per l'operazione</span><span class="sxs-lookup"><span data-stu-id="1f88d-102">Operation Performance Counters</span></span>
<span data-ttu-id="1f88d-103">I contatori delle prestazioni per l'operazione si trovano nell'oggetto prestazione `ServiceModelOperation 4.0.0.0` in caso di visualizzazione con Performance Monitor (Perfmon.exe).</span><span class="sxs-lookup"><span data-stu-id="1f88d-103">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="1f88d-104">Ogni operazione ha un'istanza singola.</span><span class="sxs-lookup"><span data-stu-id="1f88d-104">Each operation has an individual instance.</span></span> <span data-ttu-id="1f88d-105">Ovvero, se un determinato contratto ha 10 operazioni, ad esso sono associate 10 istanze di contatore per l'operazione.</span><span class="sxs-lookup"><span data-stu-id="1f88d-105">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="1f88d-106">Le istanze di oggetti vengono denominate usando il modello seguente:</span><span class="sxs-lookup"><span data-stu-id="1f88d-106">The object instances are named using the following pattern:</span></span>  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 <span data-ttu-id="1f88d-107">Questo contatore consente di misurare come viene usata la chiamata e le prestazioni dell'operazione.</span><span class="sxs-lookup"><span data-stu-id="1f88d-107">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="1f88d-108">Esiste un limite di lunghezza per il nome dell'istanza di un contatore delle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="1f88d-108">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="1f88d-109">Quando il nome di un'istanza del contatore Windows Communication Foundation (WCF) supera la lunghezza massima, WCF sostituisce una parte del nome dell'istanza con un valore hash.</span><span class="sxs-lookup"><span data-stu-id="1f88d-109">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f88d-110">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1f88d-110">See also</span></span>

- [<span data-ttu-id="1f88d-111">Contatori delle prestazioni</span><span class="sxs-lookup"><span data-stu-id="1f88d-111">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
