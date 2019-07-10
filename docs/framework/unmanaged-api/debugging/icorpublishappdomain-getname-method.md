---
title: Metodo ICorPublishAppDomain::GetName
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomain.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomain::GetName
helpviewer_keywords:
- GetName method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetName method [.NET Framework debugging]
ms.assetid: 6ef8ac9b-9803-4b65-8b13-25f3e0b1bc6b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b518a3be939c70b207a71d79a3d362dba26fd3d0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774194"
---
# <a name="icorpublishappdomaingetname-method"></a><span data-ttu-id="0de95-102">Metodo ICorPublishAppDomain::GetName</span><span class="sxs-lookup"><span data-stu-id="0de95-102">ICorPublishAppDomain::GetName Method</span></span>
<span data-ttu-id="0de95-103">Ottiene il nome del dominio dell'applicazione che è rappresentato da questo [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="0de95-103">Gets the name of the application domain that is represented by this [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0de95-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="0de95-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32   cchName,   
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR       *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0de95-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="0de95-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="0de95-106">[in] Dimensione della matrice `szName`.</span><span class="sxs-lookup"><span data-stu-id="0de95-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="0de95-107">[out] Un puntatore al numero di caratteri "wide", incluso il carattere null, restituito nel `szName` matrice.</span><span class="sxs-lookup"><span data-stu-id="0de95-107">[out] A pointer to the number of wide characters, including the null character, returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="0de95-108">[out] Matrice in cui archiviare il nome.</span><span class="sxs-lookup"><span data-stu-id="0de95-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0de95-109">Note</span><span class="sxs-lookup"><span data-stu-id="0de95-109">Remarks</span></span>  
 <span data-ttu-id="0de95-110">Se `szName` è diverso da null, il `GetName` metodo copia fino a `cchName` caratteri (incluso il carattere di terminazione null) in `szName`.</span><span class="sxs-lookup"><span data-stu-id="0de95-110">If `szName` is non-null, the `GetName` method copies up to `cchName` characters (including the null terminator) into `szName`.</span></span> <span data-ttu-id="0de95-111">Se non null viene restituito in `pcchName`, il numero effettivo di caratteri del nome (incluso il carattere di terminazione null) verrà archiviato nel `szName` matrice.</span><span class="sxs-lookup"><span data-stu-id="0de95-111">If a non-null is returned in `pcchName`, the actual number of characters in the name (including the null terminator) is stored in the `szName` array.</span></span>  
  
 <span data-ttu-id="0de95-112">Il `GetName` metodo restituisce un HRESULT S_OK indipendentemente dal numero di caratteri sono stato copiato.</span><span class="sxs-lookup"><span data-stu-id="0de95-112">The `GetName` method returns an S_OK HRESULT regardless of how many characters were copied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0de95-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="0de95-113">Requirements</span></span>  
 <span data-ttu-id="0de95-114">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0de95-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0de95-115">**Intestazione:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="0de95-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="0de95-116">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0de95-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0de95-117">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0de95-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0de95-118">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0de95-118">See also</span></span>

- [<span data-ttu-id="0de95-119">Interfaccia ICorPublishAppDomain</span><span class="sxs-lookup"><span data-stu-id="0de95-119">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)
