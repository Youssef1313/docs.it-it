---
title: Metodo ICorRuntimeHost::CreateEvidence
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateEvidence
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateEvidence
helpviewer_keywords:
- CreateEvidence method [.NET Framework hosting]
- ICorRuntimeHost::CreateEvidence method [.NET Framework hosting]
ms.assetid: e235ea80-b84c-4442-a4c3-fc96c25a8eb9
topic_type:
- apiref
ms.openlocfilehash: 429ce0510162b3256cdf58f4820b04dd80243e29
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139629"
---
# <a name="icorruntimehostcreateevidence-method"></a><span data-ttu-id="225ac-102">Metodo ICorRuntimeHost::CreateEvidence</span><span class="sxs-lookup"><span data-stu-id="225ac-102">ICorRuntimeHost::CreateEvidence Method</span></span>
<span data-ttu-id="225ac-103">Ottiene un puntatore a interfaccia di tipo <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, che consente all'host di creare evidenze di sicurezza da passare al metodo [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) o [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="225ac-103">Gets an interface pointer of type <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, which allows the host to create security evidence to pass to the [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) or [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="225ac-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="225ac-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateEvidence (  
    [out] IUnknown** pEvidence  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="225ac-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="225ac-105">Parameters</span></span>  
 `pEvidence`  
 <span data-ttu-id="225ac-106">out Puntatore a un'interfaccia a un'istanza di <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> utilizzata per creare l'evidenza di sicurezza.</span><span class="sxs-lookup"><span data-stu-id="225ac-106">[out] A interface pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> instance used to create security evidence.</span></span> <span data-ttu-id="225ac-107">Questo puntatore è tipizzato `IUnknown`, quindi i chiamanti devono in genere chiamare `QueryInterface` su questa interfaccia per ottenere un puntatore a un <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="225ac-107">This pointer is typed `IUnknown`, so callers should typically call `QueryInterface` on this interface to obtain a pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="225ac-108">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="225ac-108">Return Value</span></span>  
  
|<span data-ttu-id="225ac-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="225ac-109">HRESULT</span></span>|<span data-ttu-id="225ac-110">Descrizione</span><span class="sxs-lookup"><span data-stu-id="225ac-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="225ac-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="225ac-111">S_OK</span></span>|<span data-ttu-id="225ac-112">Operazione completata.</span><span class="sxs-lookup"><span data-stu-id="225ac-112">The operation was successful.</span></span>|  
|<span data-ttu-id="225ac-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="225ac-113">S_FALSE</span></span>|<span data-ttu-id="225ac-114">Non è stato possibile completare l'operazione.</span><span class="sxs-lookup"><span data-stu-id="225ac-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="225ac-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="225ac-115">E_FAIL</span></span>|<span data-ttu-id="225ac-116">Si è verificato un errore irreversibile sconosciuto.</span><span class="sxs-lookup"><span data-stu-id="225ac-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="225ac-117">Se un metodo restituisce E_FAIL, il Common Language Runtime (CLR) non è più utilizzabile nel processo.</span><span class="sxs-lookup"><span data-stu-id="225ac-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="225ac-118">Le chiamate successive a qualsiasi API di hosting restituiscono HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="225ac-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="225ac-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="225ac-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="225ac-120">CLR non è stato caricato in un processo oppure CLR si trova in uno stato in cui non è possibile eseguire codice gestito o elaborare la chiamata correttamente.</span><span class="sxs-lookup"><span data-stu-id="225ac-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="225ac-121">Note</span><span class="sxs-lookup"><span data-stu-id="225ac-121">Remarks</span></span>  
 <span data-ttu-id="225ac-122">Questo metodo restituisce una raccolta vuota che non può essere popolata dal codice nativo.</span><span class="sxs-lookup"><span data-stu-id="225ac-122">This method returns an empty collection that cannot be populated from native code.</span></span> <span data-ttu-id="225ac-123">Usare invece il metodo <xref:System.Security.Policy.Evidence>.</span><span class="sxs-lookup"><span data-stu-id="225ac-123">You should use the <xref:System.Security.Policy.Evidence> method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="225ac-124">Requisiti</span><span class="sxs-lookup"><span data-stu-id="225ac-124">Requirements</span></span>  
 <span data-ttu-id="225ac-125">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="225ac-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="225ac-126">**Intestazione:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="225ac-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="225ac-127">**Libreria:** Incluso come risorsa in MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="225ac-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="225ac-128">**Versione .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="225ac-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="225ac-129">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="225ac-129">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="225ac-130">Interfaccia ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="225ac-130">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
