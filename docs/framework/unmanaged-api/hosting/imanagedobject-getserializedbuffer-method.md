---
title: Metodo IManagedObject::GetSerializedBuffer
ms.date: 03/30/2017
api_name:
- IManagedObject.GetSerializedBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetSerializedBuffer
helpviewer_keywords:
- IManagedObject::GetSerializedBuffer method [.NET Framework hosting]
- GetSerializedBuffer method [.NET Framework hosting]
ms.assetid: c17105bb-b49f-434e-8f9b-77f8c85b9220
topic_type:
- apiref
ms.openlocfilehash: 4a55ae265230c4da3cc0a19b06a7597be8661beb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73103253"
---
# <a name="imanagedobjectgetserializedbuffer-method"></a><span data-ttu-id="d4b77-102">Metodo IManagedObject::GetSerializedBuffer</span><span class="sxs-lookup"><span data-stu-id="d4b77-102">IManagedObject::GetSerializedBuffer Method</span></span>
<span data-ttu-id="d4b77-103">Ottiene la rappresentazione di stringa di questo oggetto gestito.</span><span class="sxs-lookup"><span data-stu-id="d4b77-103">Gets the string representation of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4b77-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d4b77-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSerializedBuffer (  
    [out] BSTR *pBSTR  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4b77-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="d4b77-105">Parameters</span></span>  
 `pBSTR`  
 <span data-ttu-id="d4b77-106">out Puntatore a una stringa che rappresenta l'oggetto serializzato.</span><span class="sxs-lookup"><span data-stu-id="d4b77-106">[out] A pointer to a string that is the serialized object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4b77-107">Note</span><span class="sxs-lookup"><span data-stu-id="d4b77-107">Remarks</span></span>  
 <span data-ttu-id="d4b77-108">Il metodo `GetSerializedBuffer` serializza l'oggetto in modo che possa essere sottoposto a marshalling nel client.</span><span class="sxs-lookup"><span data-stu-id="d4b77-108">The `GetSerializedBuffer` method serializes the object so it can be marshaled to the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4b77-109">Requisiti</span><span class="sxs-lookup"><span data-stu-id="d4b77-109">Requirements</span></span>  
 <span data-ttu-id="d4b77-110">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4b77-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4b77-111">**Intestazione:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d4b77-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d4b77-112">**Libreria:** Incluso come risorsa in MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d4b77-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d4b77-113">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4b77-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4b77-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d4b77-114">See also</span></span>

- [<span data-ttu-id="d4b77-115">Interfaccia IManagedObject</span><span class="sxs-lookup"><span data-stu-id="d4b77-115">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
