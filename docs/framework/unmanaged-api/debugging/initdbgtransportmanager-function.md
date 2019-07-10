---
title: Funzione InitDbgTransportManager
ms.date: 03/30/2017
api_name:
- InitDbgTransportManager
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- InitDbgTransportManager
helpviewer_keywords:
- remote debugging API [Silverlight]
- InitDbgTransportManager function
- Silverlight, remote debugging
ms.assetid: a30102ff-c52e-48c9-b3a9-aa14286a42b2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 948e97064d12dc5b2044faf35aa374e5ba5f2592
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764778"
---
# <a name="initdbgtransportmanager-function"></a><span data-ttu-id="ccea4-102">Funzione InitDbgTransportManager</span><span class="sxs-lookup"><span data-stu-id="ccea4-102">InitDbgTransportManager Function</span></span>
<span data-ttu-id="ccea4-103">Inizializza il gestore trasporto per connettersi a una destinazione remota per l'enumerazione del runtime e dei processi.</span><span class="sxs-lookup"><span data-stu-id="ccea4-103">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccea4-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ccea4-104">Syntax</span></span>  
  
```cpp  
HRESULT InitDbgTransportManager ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ccea4-105">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="ccea4-105">Return Value</span></span>  
 <span data-ttu-id="ccea4-106">S_OK</span><span class="sxs-lookup"><span data-stu-id="ccea4-106">S_OK</span></span>  
 <span data-ttu-id="ccea4-107">Operazione completata.</span><span class="sxs-lookup"><span data-stu-id="ccea4-107">Success.</span></span>  
  
 <span data-ttu-id="ccea4-108">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="ccea4-108">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="ccea4-109">La funzione non è riuscita ad allocare memoria per un gestore trasporto.</span><span class="sxs-lookup"><span data-stu-id="ccea4-109">The function was unable to allocate memory for a transport manager.</span></span>  
  
 <span data-ttu-id="ccea4-110">E_FAIL (o altri codici E_ restituiti)</span><span class="sxs-lookup"><span data-stu-id="ccea4-110">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="ccea4-111">Altri errori.</span><span class="sxs-lookup"><span data-stu-id="ccea4-111">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccea4-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="ccea4-112">Requirements</span></span>  
 <span data-ttu-id="ccea4-113">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ccea4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccea4-114">**Intestazione:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="ccea4-114">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="ccea4-115">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="ccea4-115">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="ccea4-116">**Versioni di .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="ccea4-116">**.NET Framework Versions:** 3.5 SP1</span></span>
