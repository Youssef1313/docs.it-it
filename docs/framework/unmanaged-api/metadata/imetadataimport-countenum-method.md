---
title: Metodo IMetaDataImport::CountEnum
ms.date: 03/30/2017
api_name:
- IMetaDataImport.CountEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::CountEnum
helpviewer_keywords:
- CountEnum method [.NET Framework metadata]
- IMetaDataImport::CountEnum method [.NET Framework metadata]
ms.assetid: d1de53ad-9435-4b5f-9df7-07f21210e5b5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1f657957d42cef1421ab3aa19f297bd04b0cacd8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781337"
---
# <a name="imetadataimportcountenum-method"></a><span data-ttu-id="02f79-102">Metodo IMetaDataImport::CountEnum</span><span class="sxs-lookup"><span data-stu-id="02f79-102">IMetaDataImport::CountEnum Method</span></span>
<span data-ttu-id="02f79-103">Ottiene il numero di elementi nell'enumerazione recuperato dall'enumeratore specificato.</span><span class="sxs-lookup"><span data-stu-id="02f79-103">Gets the number of elements in the enumeration that was retrieved by the specified enumerator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02f79-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="02f79-104">Syntax</span></span>  
  
```cpp  
HRESULT CountEnum (  
   [in]  HCORENUM    hEnum,   
   [out] ULONG       *pulCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02f79-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="02f79-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="02f79-106">[in] L'handle per l'enumeratore.</span><span class="sxs-lookup"><span data-stu-id="02f79-106">[in] The handle for the enumerator.</span></span>  
  
 `pulCount`  
 <span data-ttu-id="02f79-107">[out] Il numero di elementi enumerati.</span><span class="sxs-lookup"><span data-stu-id="02f79-107">[out] The number of elements enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02f79-108">Note</span><span class="sxs-lookup"><span data-stu-id="02f79-108">Remarks</span></span>  
 <span data-ttu-id="02f79-109">L'handle specificato da `hEnum` ottenuto da una precedente `Enum` *nome* chiamare (ad esempio [EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="02f79-109">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02f79-110">Requisiti</span><span class="sxs-lookup"><span data-stu-id="02f79-110">Requirements</span></span>  
 <span data-ttu-id="02f79-111">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02f79-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02f79-112">**Intestazione:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="02f79-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="02f79-113">**Libreria:** Inclusa come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="02f79-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="02f79-114">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02f79-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02f79-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="02f79-115">See also</span></span>

- [<span data-ttu-id="02f79-116">Interfaccia IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="02f79-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="02f79-117">Interfaccia IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="02f79-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
