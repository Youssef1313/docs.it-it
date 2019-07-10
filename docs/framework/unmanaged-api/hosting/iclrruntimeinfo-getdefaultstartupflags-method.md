---
title: Metodo ICLRRuntimeInfo::GetDefaultStartupFlags
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetDefaultStartupFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags method [.NET Framework hosting]
- GetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 35c2173e-3b0b-4b2a-950d-e0a01c6df052
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aeb4c9935d5e9e4063497dd56276edfe6e62752a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765594"
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a><span data-ttu-id="5bde5-102">Metodo ICLRRuntimeInfo::GetDefaultStartupFlags</span><span class="sxs-lookup"><span data-stu-id="5bde5-102">ICLRRuntimeInfo::GetDefaultStartupFlags Method</span></span>
<span data-ttu-id="5bde5-103">Ottiene il flag di avvio e i file di configurazione di host che verrà usato per avviare il runtime.</span><span class="sxs-lookup"><span data-stu-id="5bde5-103">Gets the startup flags and host configuration file that will be used to start the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bde5-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="5bde5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bde5-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="5bde5-105">Parameters</span></span>  
 `pdwStartupFlags`  
 <span data-ttu-id="5bde5-106">[out] Puntatore ai flag di avvio host attualmente impostati.</span><span class="sxs-lookup"><span data-stu-id="5bde5-106">[out] A pointer to the host startup flags that are currently set.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="5bde5-107">[out] Un puntatore al percorso di directory del file di configurazione host corrente.</span><span class="sxs-lookup"><span data-stu-id="5bde5-107">[out] A pointer to the directory path of the current host configuration file.</span></span>  
  
 `pcchHostConfigFile`  
 <span data-ttu-id="5bde5-108">[in, out] In input, le dimensioni di `pwzHostConfigFile`, per evitare i sovraccarichi del buffer.</span><span class="sxs-lookup"><span data-stu-id="5bde5-108">[in, out] On input, the size of `pwzHostConfigFile`, to avoid buffer overruns.</span></span> <span data-ttu-id="5bde5-109">Se `pwzHostConfigFile` è null, il metodo restituisce la dimensione necessaria della `pwzHostConfigFile` per pre-allocazione.</span><span class="sxs-lookup"><span data-stu-id="5bde5-109">If `pwzHostConfigFile` is null, the method returns the required size of `pwzHostConfigFile` for pre-allocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5bde5-110">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="5bde5-110">Return Value</span></span>  
 <span data-ttu-id="5bde5-111">Questo metodo restituisce il valore HRESULT specifico seguente, nonché gli errori HRESULT che indicano un errore di metodo.</span><span class="sxs-lookup"><span data-stu-id="5bde5-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="5bde5-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5bde5-112">HRESULT</span></span>|<span data-ttu-id="5bde5-113">Descrizione</span><span class="sxs-lookup"><span data-stu-id="5bde5-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5bde5-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="5bde5-114">S_OK</span></span>|<span data-ttu-id="5bde5-115">Metodo completato correttamente.</span><span class="sxs-lookup"><span data-stu-id="5bde5-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5bde5-116">Note</span><span class="sxs-lookup"><span data-stu-id="5bde5-116">Remarks</span></span>  
 <span data-ttu-id="5bde5-117">Questo metodo restituisce i valori di flag predefiniti (`STARTUP_CONCURRENT_GC` e `NULL`), o i valori forniti da una precedente chiamata ai [SetDefaultStartupFlags (metodo)](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), o i valori impostati da uno qualsiasi del `CorBind*` metodi se vengono associati a questa versione del runtime.</span><span class="sxs-lookup"><span data-stu-id="5bde5-117">This method returns the default flag values (`STARTUP_CONCURRENT_GC` and `NULL`), or the values provided by a previous call to the [ICLRRuntimeInfo::SetDefaultStartupFlags method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), or the values set by any of the `CorBind*` methods if they are bound to this runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bde5-118">Requisiti</span><span class="sxs-lookup"><span data-stu-id="5bde5-118">Requirements</span></span>  
 <span data-ttu-id="5bde5-119">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5bde5-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bde5-120">**Intestazione:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="5bde5-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5bde5-121">**Libreria:** Inclusa come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="5bde5-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5bde5-122">**Versioni di .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bde5-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bde5-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5bde5-123">See also</span></span>

- [<span data-ttu-id="5bde5-124">Interfaccia ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="5bde5-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="5bde5-125">Interfacce di hosting</span><span class="sxs-lookup"><span data-stu-id="5bde5-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="5bde5-126">Hosting</span><span class="sxs-lookup"><span data-stu-id="5bde5-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
