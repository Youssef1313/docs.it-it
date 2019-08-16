---
title: Wrapper COM
ms.date: 03/30/2017
helpviewer_keywords:
- wrapper classes
- COM interop, COM wrappers
- COM wrappers
- COM, wrappers
- interoperation with unmanaged code, COM wrappers
- COM callable wrappers
ms.assetid: e56c485b-6b67-4345-8e66-fd21835a6092
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af9b87e83def5578ea38e94a4f69c657ac5f7c99
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631435"
---
# <a name="com-wrappers"></a><span data-ttu-id="51d59-102">Wrapper COM</span><span class="sxs-lookup"><span data-stu-id="51d59-102">COM Wrappers</span></span>
<span data-ttu-id="51d59-103">COM è diverso dal modello a oggetti del runtime .NET per diversi aspetti importanti:</span><span class="sxs-lookup"><span data-stu-id="51d59-103">COM differs from the .NET runtime object model in several important ways:</span></span>  
  
- <span data-ttu-id="51d59-104">I client di oggetti COM devono gestire la durata di tali oggetti. Common Language Runtime gestisce la durata degli oggetti nel proprio ambiente.</span><span class="sxs-lookup"><span data-stu-id="51d59-104">Clients of COM objects must manage the lifetime of those objects; the common language runtime manages the lifetime of objects in its environment.</span></span>  
  
- <span data-ttu-id="51d59-105">I client di oggetti COM individuano la disponibilità di un servizio inviando una richiesta a un'interfaccia che offre il servizio in questione e, se il servizio è disponibile, ricevendo un puntatore all'interfaccia.</span><span class="sxs-lookup"><span data-stu-id="51d59-105">Clients of COM objects discover whether a service is available by requesting an interface that provides that service and getting back an interface pointer, or not.</span></span> <span data-ttu-id="51d59-106">I client di oggetti .NET possono ottenere una descrizione della funzionalità di un oggetto tramite reflection.</span><span class="sxs-lookup"><span data-stu-id="51d59-106">Clients of .NET objects can obtain a description of an object's functionality using reflection.</span></span>  
  
- <span data-ttu-id="51d59-107">Gli oggetti .NET risiedono nella memoria gestita dall'ambiente di esecuzione del runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="51d59-107">NET objects reside in memory managed by the .NET runtime execution environment.</span></span> <span data-ttu-id="51d59-108">L'ambiente di esecuzione può spostare gli oggetti in posizioni diverse all'interno della memoria per motivi di prestazioni e aggiornare tutti i riferimenti agli oggetti spostati.</span><span class="sxs-lookup"><span data-stu-id="51d59-108">The execution environment can move objects around in memory for performance reasons and update all references to the objects it moves.</span></span> <span data-ttu-id="51d59-109">I client non gestiti, dopo aver ottenuto un puntatore a un oggetto, per rimanere nella stessa posizione si basano sull'oggetto stesso.</span><span class="sxs-lookup"><span data-stu-id="51d59-109">Unmanaged clients, having obtained a pointer to an object, rely on the object to remain at the same location.</span></span> <span data-ttu-id="51d59-110">Questi client non hanno alcun meccanismo di gestione di oggetti il cui percorso non sia fisso.</span><span class="sxs-lookup"><span data-stu-id="51d59-110">These clients have no mechanism for dealing with an object whose location is not fixed.</span></span>  
  
 <span data-ttu-id="51d59-111">Per superare queste differenze, il runtime mette a disposizione classi wrapper. Tramite tali classi, sia ai client gestiti che ai client non gestiti le chiamate agli oggetti risultano eseguite all'interno dell'ambiente del client.</span><span class="sxs-lookup"><span data-stu-id="51d59-111">To overcome these differences, the runtime provides wrapper classes to make both managed and unmanaged clients think they are calling objects within their respective environment.</span></span> <span data-ttu-id="51d59-112">Ogni volta che il client gestito chiama un metodo per un oggetto COM, il runtime crea un [Runtime Callable Wrapper](runtime-callable-wrapper.md) (RCW).</span><span class="sxs-lookup"><span data-stu-id="51d59-112">Whenever your managed client calls a method on a COM object, the runtime creates a [runtime callable wrapper](runtime-callable-wrapper.md) (RCW).</span></span> <span data-ttu-id="51d59-113">Una delle funzioni degli RCW è nascondere le differenze tra meccanismi di riferimento gestiti e non gestiti.</span><span class="sxs-lookup"><span data-stu-id="51d59-113">RCWs abstract the differences between managed and unmanaged reference mechanisms, among other things.</span></span> <span data-ttu-id="51d59-114">Il runtime crea anche un [COM Callable Wrapper](com-callable-wrapper.md) (CCW) per invertire il processo, consentendo a un client COM di chiamare facilmente un metodo per un oggetto .NET.</span><span class="sxs-lookup"><span data-stu-id="51d59-114">The runtime also creates a [COM callable wrapper](com-callable-wrapper.md) (CCW) to reverse the process, enabling a COM client to seamlessly call a method on a .NET object.</span></span> <span data-ttu-id="51d59-115">Come illustrato nella figura seguente, la prospettiva del codice chiamante determina la classe wrapper creata dal runtime.</span><span class="sxs-lookup"><span data-stu-id="51d59-115">As the following illustration shows, the perspective of the calling code determines which wrapper class the runtime creates.</span></span>  
  
 ![Cenni preliminari sul wrapper COM](./media/com-wrappers/bidirectional-com-overview.gif)  
  
 <span data-ttu-id="51d59-117">Nella maggior parte dei casi, l'oggetto CCW o RCW standard generato dal runtime effettua un marshalling adeguato per le chiamate che superano il limite tra COM e il runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="51d59-117">In most cases, the standard RCW or CCW generated by the runtime provides adequate marshaling for calls that cross the boundary between COM and the .NET runtime.</span></span> <span data-ttu-id="51d59-118">Usando attributi personalizzati, è possibile, facoltativamente, impostare il modo in cui il runtime rappresenta il codice gestito e non gestito.</span><span class="sxs-lookup"><span data-stu-id="51d59-118">Using custom attributes, you can optionally adjust the way the runtime represents managed and unmanaged code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51d59-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="51d59-119">See also</span></span>

- <span data-ttu-id="51d59-120">[Interoperabilità COM avanzata in .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="51d59-120">[Advanced COM Interoperability in .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>
- [<span data-ttu-id="51d59-121">Runtime Callable Wrapper</span><span class="sxs-lookup"><span data-stu-id="51d59-121">Runtime Callable Wrapper</span></span>](runtime-callable-wrapper.md)
- [<span data-ttu-id="51d59-122">COM Callable Wrapper</span><span class="sxs-lookup"><span data-stu-id="51d59-122">COM Callable Wrapper</span></span>](com-callable-wrapper.md)
- <span data-ttu-id="51d59-123">[Personalizzazione di wrapper standard in .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="51d59-123">[Customizing Standard Wrappers in .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))</span></span>
- <span data-ttu-id="51d59-124">[Procedura: Personalizzare Runtime Callable Wrapper in .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/56kh4hy7(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="51d59-124">[How to: Customize Runtime Callable Wrappers in .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/56kh4hy7(v=vs.100))</span></span>