---
title: Metodo ICorDebugProcess2::GetDesiredNGENCompilerFlags
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetDesiredNGENCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags method [.NET Framework debugging]
- GetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: fc834580-3a90-4315-95d2-349b6bb7d059
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ee186604529a3e77a0217c5688df5b62ff8b28c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736991"
---
# <a name="icordebugprocess2getdesiredngencompilerflags-method"></a><span data-ttu-id="e1393-102">Metodo ICorDebugProcess2::GetDesiredNGENCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="e1393-102">ICorDebugProcess2::GetDesiredNGENCompilerFlags Method</span></span>
<span data-ttu-id="e1393-103">Ottiene le impostazioni dell'indicatore che usa common language runtime (CLR) per selezionare i valori corretti precompilati o meno il compilatore corrente (vale a dire, native) immagine da caricare in questo processo.</span><span class="sxs-lookup"><span data-stu-id="e1393-103">Gets the current compiler flag settings that the common language runtime (CLR) uses to select the correct precompiled (that is, native) image to be loaded into this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1393-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e1393-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDesiredNGENCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1393-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="e1393-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="e1393-106">[out] Un puntatore a una combinazione bit per bit del [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) valori di enumerazione che vengono usati per selezionare l'immagine corretta precompilata da caricare.</span><span class="sxs-lookup"><span data-stu-id="e1393-106">[out] A pointer to a bitwise combination of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration values that are used to select the correct precompiled image to be loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1393-107">Note</span><span class="sxs-lookup"><span data-stu-id="e1393-107">Remarks</span></span>  
 <span data-ttu-id="e1393-108">Usare la [ICorDebugProcess2::SetDesiredNGENCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md) metodo per impostare il flag che CLR verranno utilizzati per selezionare l'immagine corretta pre-compilata da caricare.</span><span class="sxs-lookup"><span data-stu-id="e1393-108">Use the [ICorDebugProcess2::SetDesiredNGENCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md) method to set the flags that the CLR will use to select the correct pre-compiled image to load.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1393-109">Requisiti</span><span class="sxs-lookup"><span data-stu-id="e1393-109">Requirements</span></span>  
 <span data-ttu-id="e1393-110">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1393-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1393-111">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e1393-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e1393-112">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1393-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1393-113">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1393-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
