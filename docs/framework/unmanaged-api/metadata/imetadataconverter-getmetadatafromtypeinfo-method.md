---
title: Metodo IMetaDataConverter::GetMetaDataFromTypeInfo
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetMetaDataFromTypeInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetMetaDataFromTypeInfo
helpviewer_keywords:
- GetMetaDataFromTypeInfo method [.NET Framework metadata]
- IMetaDataConverter::GetMetaDataFromTypeInfo method [.NET Framework metadata]
ms.assetid: d44484bb-23a3-49c3-9e46-69d0d9ab4f0f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 906ab3603d9a4926642848b547a793f129f949ce
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782039"
---
# <a name="imetadataconvertergetmetadatafromtypeinfo-method"></a><span data-ttu-id="93a77-102">Metodo IMetaDataConverter::GetMetaDataFromTypeInfo</span><span class="sxs-lookup"><span data-stu-id="93a77-102">IMetaDataConverter::GetMetaDataFromTypeInfo Method</span></span>
<span data-ttu-id="93a77-103">Ottiene un puntatore a un [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) istanza che rappresenta la firma dei metadati della libreria dei tipi a cui fa riferimento l'oggetto specificato `ITypeInfo` istanza.</span><span class="sxs-lookup"><span data-stu-id="93a77-103">Gets a pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature of the type library referenced by the specified `ITypeInfo` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93a77-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="93a77-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataFromTypeInfo (  
    [in]  ITypeInfo         *pITI,  
    [out] IMetaDataImport   **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93a77-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="93a77-105">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="93a77-106">[in] Un puntatore a un `ITypeInfo` oggetto che fa riferimento alla libreria dei tipi.</span><span class="sxs-lookup"><span data-stu-id="93a77-106">[in] A pointer to an `ITypeInfo` object that refers to the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="93a77-107">[out] Un puntatore a una posizione che riceve l'indirizzo del `IMetaDataImport` istanza che rappresenta la firma dei metadati.</span><span class="sxs-lookup"><span data-stu-id="93a77-107">[out] A pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93a77-108">Requisiti</span><span class="sxs-lookup"><span data-stu-id="93a77-108">Requirements</span></span>  
 <span data-ttu-id="93a77-109">**Piattaforma:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93a77-109">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93a77-110">**Intestazione:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="93a77-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="93a77-111">**Libreria:** Usato come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="93a77-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="93a77-112">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93a77-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93a77-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="93a77-113">See also</span></span>

- [<span data-ttu-id="93a77-114">Interfaccia IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="93a77-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="93a77-115">Interfaccia IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="93a77-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
