---
title: Metodo IMetaDataTables::GetNextBlob
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextBlob
helpviewer_keywords:
- IMetaDataTables::GetNextBlob method [.NET Framework metadata]
- GetNextBlob method [.NET Framework metadata]
ms.assetid: 017c8ab4-4c09-4754-9935-5b0b49cabecb
topic_type:
- apiref
ms.openlocfilehash: 145fdde302e7e942ea77049b3faeabf60894dd94
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448405"
---
# <a name="imetadatatablesgetnextblob-method"></a><span data-ttu-id="17a28-102">Metodo IMetaDataTables::GetNextBlob</span><span class="sxs-lookup"><span data-stu-id="17a28-102">IMetaDataTables::GetNextBlob Method</span></span>
<span data-ttu-id="17a28-103">Ottiene l'indice del BLOB (Binary Large Object) successivo nella tabella.</span><span class="sxs-lookup"><span data-stu-id="17a28-103">Gets the index of the next binary large object (BLOB) in the table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17a28-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="17a28-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextBlob (  
    [in]  ULONG   ixBlob,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17a28-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="17a28-105">Parameters</span></span>  
 `ixBlob`  
 <span data-ttu-id="17a28-106">in Indice, come restituito da una colonna di BLOB.</span><span class="sxs-lookup"><span data-stu-id="17a28-106">[in] The index, as returned from a column of BLOBs.</span></span>  
  
 `pNext`  
 <span data-ttu-id="17a28-107">out Puntatore all'indice del BLOB successivo.</span><span class="sxs-lookup"><span data-stu-id="17a28-107">[out] A pointer to the index of the next BLOB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17a28-108">Requisiti</span><span class="sxs-lookup"><span data-stu-id="17a28-108">Requirements</span></span>  
 <span data-ttu-id="17a28-109">**Piattaforme:** vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17a28-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17a28-110">**Intestazione:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="17a28-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="17a28-111">**Libreria:** Usato come risorsa in MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="17a28-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="17a28-112">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17a28-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17a28-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="17a28-113">See also</span></span>

- [<span data-ttu-id="17a28-114">Interfaccia IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="17a28-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="17a28-115">Interfaccia IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="17a28-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
