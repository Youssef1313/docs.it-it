---
title: Metodo ICorRuntimeHost::GetDefaultDomain
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.GetDefaultDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::GetDefaultDomain
helpviewer_keywords:
- ICorRuntimeHost::GetDefaultDomain method [.NET Framework hosting]
- GetDefaultDomain method [.NET Framework hosting]
ms.assetid: 5e17a6fc-f335-4aae-9bb0-c3e1271a9426
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fe80050d7b513bce2660b81c5e4faa35b375f22b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780026"
---
# <a name="icorruntimehostgetdefaultdomain-method"></a><span data-ttu-id="98e23-102">Metodo ICorRuntimeHost::GetDefaultDomain</span><span class="sxs-lookup"><span data-stu-id="98e23-102">ICorRuntimeHost::GetDefaultDomain Method</span></span>
<span data-ttu-id="98e23-103">Ottiene un puntatore di interfaccia di tipo <xref:System._AppDomain?displayProperty=nameWithType> che rappresenta il dominio predefinito per il processo corrente.</span><span class="sxs-lookup"><span data-stu-id="98e23-103">Gets an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the default domain for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98e23-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="98e23-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDefaultDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98e23-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="98e23-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="98e23-106">[out] Un puntatore a interfaccia typu <xref:System._AppDomain?displayProperty=nameWithType> per il <xref:System.AppDomain> istanza che rappresenta il dominio applicazione predefinito per il processo.</span><span class="sxs-lookup"><span data-stu-id="98e23-106">[out] An interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> to the <xref:System.AppDomain> instance that represents the default application domain for the process.</span></span>  
  
 <span data-ttu-id="98e23-107">Il puntatore è tipizzato `IUnknown`, in modo che i chiamanti in genere consigliabile chiamare `QueryInterface` per ottenere un puntatore di interfaccia di tipo <xref:System._AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="98e23-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="98e23-108">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="98e23-108">Return Value</span></span>  
  
|<span data-ttu-id="98e23-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="98e23-109">HRESULT</span></span>|<span data-ttu-id="98e23-110">Descrizione</span><span class="sxs-lookup"><span data-stu-id="98e23-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="98e23-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="98e23-111">S_OK</span></span>|<span data-ttu-id="98e23-112">L'operazione è riuscita.</span><span class="sxs-lookup"><span data-stu-id="98e23-112">The operation was successful.</span></span>|  
|<span data-ttu-id="98e23-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="98e23-113">S_FALSE</span></span>|<span data-ttu-id="98e23-114">Impossibile completare l'operazione.</span><span class="sxs-lookup"><span data-stu-id="98e23-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="98e23-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="98e23-115">E_FAIL</span></span>|<span data-ttu-id="98e23-116">Si è verificato un errore irreversibile sconosciuto.</span><span class="sxs-lookup"><span data-stu-id="98e23-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="98e23-117">Se un metodo viene restituito E_FAIL, common language runtime (CLR) non è più utilizzabile nel processo.</span><span class="sxs-lookup"><span data-stu-id="98e23-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="98e23-118">Le chiamate successive a qualsiasi API di hosting restituiranno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="98e23-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="98e23-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="98e23-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="98e23-120">CLR non è stato caricato in un processo oppure si trova in uno stato in cui non può eseguire codice gestito o elaborare correttamente la chiamata.</span><span class="sxs-lookup"><span data-stu-id="98e23-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="98e23-121">Requisiti</span><span class="sxs-lookup"><span data-stu-id="98e23-121">Requirements</span></span>  
 <span data-ttu-id="98e23-122">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98e23-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98e23-123">**Intestazione:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="98e23-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="98e23-124">**Libreria:** Inclusa come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="98e23-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="98e23-125">**Versioni di .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="98e23-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98e23-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="98e23-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="98e23-127">Interfaccia ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="98e23-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
