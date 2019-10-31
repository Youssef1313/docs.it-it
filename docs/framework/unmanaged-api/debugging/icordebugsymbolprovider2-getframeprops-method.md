---
title: 'Metodo ICorDebugSymbolProvider2:: Gettypeprops'
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
ms.openlocfilehash: 39bdb93fcb48da6667d982ca2d511ee5e499ae32
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133637"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="839eb-102">Metodo ICorDebugSymbolProvider2:: Gettypeprops</span><span class="sxs-lookup"><span data-stu-id="839eb-102">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>
<span data-ttu-id="839eb-103">Restituisce l'indirizzo RVA (Relative Virtual Address) iniziale di un metodo e il frame padre in base a un indirizzo virtuale relativo al codice.</span><span class="sxs-lookup"><span data-stu-id="839eb-103">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="839eb-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="839eb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="839eb-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="839eb-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="839eb-106">[in] Indirizzo RVA (Relative Virtual Address)</span><span class="sxs-lookup"><span data-stu-id="839eb-106">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="839eb-107">[out] Puntatore all'indirizzo RVA (Relative Virtual Address) di avvio del metodo.</span><span class="sxs-lookup"><span data-stu-id="839eb-107">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="839eb-108">[out] Puntatore all'indirizzo RVA (Relative Virtual Address) di avvio del frame.</span><span class="sxs-lookup"><span data-stu-id="839eb-108">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="839eb-109">Note</span><span class="sxs-lookup"><span data-stu-id="839eb-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="839eb-110">Questo metodo è disponibile solo con .NET Native.</span><span class="sxs-lookup"><span data-stu-id="839eb-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="839eb-111">Requisiti</span><span class="sxs-lookup"><span data-stu-id="839eb-111">Requirements</span></span>  
 <span data-ttu-id="839eb-112">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="839eb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="839eb-113">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="839eb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="839eb-114">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="839eb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="839eb-115">**Versioni di .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="839eb-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="839eb-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="839eb-116">See also</span></span>

- [<span data-ttu-id="839eb-117">Interfaccia ICorDebugSymbolProvider2</span><span class="sxs-lookup"><span data-stu-id="839eb-117">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="839eb-118">Interfacce di debug</span><span class="sxs-lookup"><span data-stu-id="839eb-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
