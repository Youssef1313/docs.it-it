---
title: Metodo IMetaDataEmit::DefinePermissionSet
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefinePermissionSet
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefinePermissionSet
helpviewer_keywords:
- DefinePermissionSet method [.NET Framework metadata]
- IMetaDataEmit::DefinePermissionSet method [.NET Framework metadata]
ms.assetid: 36cffbf7-82ca-4cf9-bf60-50ab491ac2d9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 16675e8bfde74c1f9c30ac9d52f8eeb919d22477
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777533"
---
# <a name="imetadataemitdefinepermissionset-method"></a><span data-ttu-id="4ec36-102">Metodo IMetaDataEmit::DefinePermissionSet</span><span class="sxs-lookup"><span data-stu-id="4ec36-102">IMetaDataEmit::DefinePermissionSet Method</span></span>
<span data-ttu-id="4ec36-103">Crea una definizione per un set di autorizzazioni con la firma dei metadati specificati e ottiene un token per tale definizione del set di autorizzazioni.</span><span class="sxs-lookup"><span data-stu-id="4ec36-103">Creates a definition for a permission set with the specified metadata signature, and gets a token to that permission set definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ec36-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="4ec36-104">Syntax</span></span>  
  
```cpp  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,   
    [in]  DWORD          dwAction,   
    [in]  void const     *pvPermission,   
    [in]  ULONG          cbPermission,   
    [out] mdPermission   *ppm   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ec36-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="4ec36-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="4ec36-106">[in] Oggetto da essere decorata.</span><span class="sxs-lookup"><span data-stu-id="4ec36-106">[in] The object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="4ec36-107">[in] Oggetto [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) valore che specifica il tipo di sicurezza dichiarativa da usare.</span><span class="sxs-lookup"><span data-stu-id="4ec36-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="4ec36-108">[in] L'autorizzazione di BLOB.</span><span class="sxs-lookup"><span data-stu-id="4ec36-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="4ec36-109">[in] Le dimensioni, in byte, di `pvPermission`.</span><span class="sxs-lookup"><span data-stu-id="4ec36-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="4ec36-110">[out] Il token di autorizzazione restituito.</span><span class="sxs-lookup"><span data-stu-id="4ec36-110">[out] The returned permission token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ec36-111">Requisiti</span><span class="sxs-lookup"><span data-stu-id="4ec36-111">Requirements</span></span>  
 <span data-ttu-id="4ec36-112">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ec36-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ec36-113">**Intestazione:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4ec36-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4ec36-114">**Libreria:** Usato come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="4ec36-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4ec36-115">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ec36-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ec36-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4ec36-116">See also</span></span>

- [<span data-ttu-id="4ec36-117">Interfaccia IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="4ec36-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="4ec36-118">Interfaccia IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="4ec36-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
