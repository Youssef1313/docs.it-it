---
title: Metodo ICLRDataTarget::WriteVirtual
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.WriteVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::WriteVirtual
helpviewer_keywords:
- ICLRDataTarget::WriteVirtual method [.NET Framework debugging]
- WriteVirtual method [.NET Framework debugging]
ms.assetid: d627e8b7-a605-40ac-b9bb-da9a3f1b66d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a0ad4b7e907412aced911d7869ffce81eb867448
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738514"
---
# <a name="iclrdatatargetwritevirtual-method"></a><span data-ttu-id="90c05-102">Metodo ICLRDataTarget::WriteVirtual</span><span class="sxs-lookup"><span data-stu-id="90c05-102">ICLRDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="90c05-103">Scrive i dati dal buffer specificato per l'indirizzo di memoria virtuale specificato.</span><span class="sxs-lookup"><span data-stu-id="90c05-103">Writes data from the specified buffer to the specified virtual memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90c05-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="90c05-104">Syntax</span></span>  
  
```cpp  
HRESULT WriteVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [in, size_is(bytesRequested)]   
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesWritten  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90c05-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="90c05-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="90c05-106">[in] CLRDATA_ADDRESS che archivia l'indirizzo di memoria virtuale.</span><span class="sxs-lookup"><span data-stu-id="90c05-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="90c05-107">[in] Un puntatore a un buffer che archivia i dati da scrivere.</span><span class="sxs-lookup"><span data-stu-id="90c05-107">[in] A pointer to a buffer that stores the data to be written.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="90c05-108">[in] Il numero di byte da scrivere.</span><span class="sxs-lookup"><span data-stu-id="90c05-108">[in] The number of bytes to be written.</span></span>  
  
 `bytesWritten`  
 <span data-ttu-id="90c05-109">[out] Puntatore al numero effettivo di byte che sono state scritte.</span><span class="sxs-lookup"><span data-stu-id="90c05-109">[out] A pointer to the actual number of bytes that were written.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90c05-110">Requisiti</span><span class="sxs-lookup"><span data-stu-id="90c05-110">Requirements</span></span>  
 <span data-ttu-id="90c05-111">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90c05-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90c05-112">**Intestazione:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="90c05-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="90c05-113">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90c05-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90c05-114">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90c05-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90c05-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="90c05-115">See also</span></span>

- [<span data-ttu-id="90c05-116">Interfaccia ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="90c05-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
