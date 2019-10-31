---
title: Metodo ICorDebugProcess::IsTransitionStub
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsTransitionStub
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsTransitionStub
helpviewer_keywords:
- ICorDebugProcess::IsTransitionStub method [.NET Framework debugging]
- IsTransitionStub method [.NET Framework debugging]
ms.assetid: f7653317-7e48-4163-be03-f50f1a4b0f70
topic_type:
- apiref
ms.openlocfilehash: 852c77be0dc8ef91933bacbbd3d6b3f5a69ae8c8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139382"
---
# <a name="icordebugprocessistransitionstub-method"></a><span data-ttu-id="d70ab-102">Metodo ICorDebugProcess::IsTransitionStub</span><span class="sxs-lookup"><span data-stu-id="d70ab-102">ICorDebugProcess::IsTransitionStub Method</span></span>
<span data-ttu-id="d70ab-103">Ottiene un valore che indica se un indirizzo si trova all'interno di uno stub che provocherà una transizione al codice gestito.</span><span class="sxs-lookup"><span data-stu-id="d70ab-103">Gets a value that indicates whether an address is inside a stub that will cause a transition to managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d70ab-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d70ab-104">Syntax</span></span>  
  
```cpp  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d70ab-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="d70ab-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="d70ab-106">in Valore `CORDB_ADDRESS` che specifica l'indirizzo in questione.</span><span class="sxs-lookup"><span data-stu-id="d70ab-106">[in] A `CORDB_ADDRESS` value that specifies the address in question.</span></span>  
  
 `pbTransitionStub`  
 <span data-ttu-id="d70ab-107">out Puntatore a un valore booleano che viene `true` se l'indirizzo specificato si trova all'interno di uno stub che provocherà una transizione al codice gestito; in caso contrario, \*`pbTransitionStub` è `false`.</span><span class="sxs-lookup"><span data-stu-id="d70ab-107">[out] A pointer to a Boolean value that is `true` if the specified address is inside a stub that will cause a transition to managed code; otherwise \*`pbTransitionStub` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d70ab-108">Note</span><span class="sxs-lookup"><span data-stu-id="d70ab-108">Remarks</span></span>  
 <span data-ttu-id="d70ab-109">Il metodo `IsTransitionStub` può essere usato dal codice dell'istruzione non gestita per decidere quando restituire il controllo di avanzamento al gestore di debug gestito.</span><span class="sxs-lookup"><span data-stu-id="d70ab-109">The `IsTransitionStub` method can be used by unmanaged stepping code to decide when to return stepping control to the managed stepper.</span></span>  
  
 <span data-ttu-id="d70ab-110">È anche possibile identificare gli stub di transizione esaminando le informazioni nel file eseguibile di tipo PE.</span><span class="sxs-lookup"><span data-stu-id="d70ab-110">You can also identity transition stubs by looking at information in the portable executable (PE) file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d70ab-111">Requisiti</span><span class="sxs-lookup"><span data-stu-id="d70ab-111">Requirements</span></span>  
 <span data-ttu-id="d70ab-112">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d70ab-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d70ab-113">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d70ab-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d70ab-114">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d70ab-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d70ab-115">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d70ab-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
