---
title: Metodo IMetaDataTables::GetNextString
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextString
helpviewer_keywords:
- IMetaDataTables::GetNextString method [.NET Framework metadata]
- GetNextString method [.NET Framework metadata]
ms.assetid: d9720428-c353-4f07-a7e8-899e106a1b37
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3c2008556ebf1b1961aef7dc0f24fd0a3161d06e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781455"
---
# <a name="imetadatatablesgetnextstring-method"></a><span data-ttu-id="3892b-102">Metodo IMetaDataTables::GetNextString</span><span class="sxs-lookup"><span data-stu-id="3892b-102">IMetaDataTables::GetNextString Method</span></span>
<span data-ttu-id="3892b-103">Ottiene l'indice della stringa successiva nella colonna della tabella corrente.</span><span class="sxs-lookup"><span data-stu-id="3892b-103">Gets the index of the next string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3892b-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="3892b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextString (   
    [in]  ULONG   ixString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3892b-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="3892b-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="3892b-106">[in] Il valore di indice da una colonna di tabella di stringhe.</span><span class="sxs-lookup"><span data-stu-id="3892b-106">[in] The index value from a string table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="3892b-107">[out] Un puntatore all'indice della stringa nella colonna successiva.</span><span class="sxs-lookup"><span data-stu-id="3892b-107">[out] A pointer to the index of the next string in the column.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3892b-108">Requisiti</span><span class="sxs-lookup"><span data-stu-id="3892b-108">Requirements</span></span>  
 <span data-ttu-id="3892b-109">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3892b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3892b-110">**Intestazione:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3892b-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3892b-111">**Libreria:** Usato come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="3892b-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3892b-112">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3892b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3892b-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3892b-113">See also</span></span>

- [<span data-ttu-id="3892b-114">Interfaccia IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="3892b-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="3892b-115">Interfaccia IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="3892b-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
