---
title: Funzione GetVersionFromProcess
ms.date: 03/30/2017
api_name:
- GetVersionFromProcess
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetVersionFromProcess
helpviewer_keywords:
- GetVersionFromProcess function [.NET Framework hosting]
ms.assetid: a9f7f824-64a1-408d-8607-91c7f19d21fe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4015ecec38466650488a653641f5af93c4680f22
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779587"
---
# <a name="getversionfromprocess-function"></a><span data-ttu-id="bedb1-102">Funzione GetVersionFromProcess</span><span class="sxs-lookup"><span data-stu-id="bedb1-102">GetVersionFromProcess Function</span></span>
<span data-ttu-id="bedb1-103">Ottiene il numero di versione di common language runtime (CLR) che viene associato all'handle del processo specificato.</span><span class="sxs-lookup"><span data-stu-id="bedb1-103">Gets the version number of the common language runtime (CLR) that is associated with the specified process handle.</span></span>  
  
 <span data-ttu-id="bedb1-104">Questa funzione è stata deprecata in .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="bedb1-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bedb1-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="bedb1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bedb1-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="bedb1-106">Parameters</span></span>  
 `hProcess`  
 <span data-ttu-id="bedb1-107">[in] Handle per un processo.</span><span class="sxs-lookup"><span data-stu-id="bedb1-107">[in] A handle to a process.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="bedb1-108">[out] Un buffer che contiene la stringa del numero di versione al completamento del metodo.</span><span class="sxs-lookup"><span data-stu-id="bedb1-108">[out] A buffer that contains the version number string upon successful completion of the method.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="bedb1-109">[in] La lunghezza del buffer della versione.</span><span class="sxs-lookup"><span data-stu-id="bedb1-109">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="bedb1-110">[out] Puntatore alla lunghezza della stringa di numeri di versione.</span><span class="sxs-lookup"><span data-stu-id="bedb1-110">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bedb1-111">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="bedb1-111">Return Value</span></span>  
 <span data-ttu-id="bedb1-112">Questo metodo restituisce codici di errore standard modello COM (Component Object), come definito nel file Winerror. H, oltre ai valori seguenti.</span><span class="sxs-lookup"><span data-stu-id="bedb1-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="bedb1-113">Codice restituito</span><span class="sxs-lookup"><span data-stu-id="bedb1-113">Return code</span></span>|<span data-ttu-id="bedb1-114">Descrizione</span><span class="sxs-lookup"><span data-stu-id="bedb1-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="bedb1-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="bedb1-115">S_OK</span></span>|<span data-ttu-id="bedb1-116">Metodo completato correttamente.</span><span class="sxs-lookup"><span data-stu-id="bedb1-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="bedb1-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="bedb1-117">E_INVALIDARG</span></span>|<span data-ttu-id="bedb1-118">`pVersion` è null e `cchBuffer` non è null, o viceversa.</span><span class="sxs-lookup"><span data-stu-id="bedb1-118">`pVersion` is null and `cchBuffer` is not null, or vice versa.</span></span><br /><br /> <span data-ttu-id="bedb1-119">-oppure-</span><span class="sxs-lookup"><span data-stu-id="bedb1-119">-or-</span></span><br /><br /> <span data-ttu-id="bedb1-120">`hProcess` non è un handle valido a un processo.</span><span class="sxs-lookup"><span data-stu-id="bedb1-120">`hProcess` is not a valid handle to a process.</span></span><br /><br /> <span data-ttu-id="bedb1-121">-oppure-</span><span class="sxs-lookup"><span data-stu-id="bedb1-121">-or-</span></span><br /><br /> <span data-ttu-id="bedb1-122">CLR non è caricato.</span><span class="sxs-lookup"><span data-stu-id="bedb1-122">The CLR is not loaded.</span></span>|  
|<span data-ttu-id="bedb1-123">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="bedb1-123">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="bedb1-124">`cchBuffer` è null o minore della lunghezza della stringa di versione.</span><span class="sxs-lookup"><span data-stu-id="bedb1-124">`cchBuffer` is null or less than the length of the version string.</span></span>|  
|<span data-ttu-id="bedb1-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="bedb1-125">E_NOTIMPL</span></span>|<span data-ttu-id="bedb1-126">Questo metodo non è disponibile nel sistema operativo Microsoft Windows 95, Microsoft Windows 98 o Microsoft Windows Millennium Edition.</span><span class="sxs-lookup"><span data-stu-id="bedb1-126">This method is not available on the Microsoft Windows 95, Microsoft Windows 98, or Microsoft Windows Millennium Edition operating system.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bedb1-127">Requisiti</span><span class="sxs-lookup"><span data-stu-id="bedb1-127">Requirements</span></span>  
 <span data-ttu-id="bedb1-128">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bedb1-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bedb1-129">**Intestazione:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bedb1-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bedb1-130">**Libreria:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bedb1-130">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bedb1-131">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bedb1-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bedb1-132">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="bedb1-132">See also</span></span>

- [<span data-ttu-id="bedb1-133">Funzione GetRequestedRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="bedb1-133">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="bedb1-134">Funzione GetRequestedRuntimeVersion</span><span class="sxs-lookup"><span data-stu-id="bedb1-134">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [<span data-ttu-id="bedb1-135">Funzioni di hosting CLR deprecate</span><span class="sxs-lookup"><span data-stu-id="bedb1-135">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
