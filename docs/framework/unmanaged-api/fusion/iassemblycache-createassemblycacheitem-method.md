---
title: Metodo IAssemblyCache::CreateAssemblyCacheItem
ms.date: 03/30/2017
api_name:
- IAssemblyCache.CreateAssemblyCacheItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::CreateAssemblyCacheItem
helpviewer_keywords:
- IAssemblyCache::CreateAssemblyCacheItem method [.NET Framework fusion]
- CreateAssemblyCacheItem method [.NET Framework fusion]
ms.assetid: 017a7ba5-aaaf-44e2-9cbe-ceebef259df0
topic_type:
- apiref
ms.openlocfilehash: e3e50538bde8fe3509b49e3dbcb031875e6863e5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127111"
---
# <a name="iassemblycachecreateassemblycacheitem-method"></a><span data-ttu-id="f160e-102">Metodo IAssemblyCache::CreateAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="f160e-102">IAssemblyCache::CreateAssemblyCacheItem Method</span></span>
<span data-ttu-id="f160e-103">Ottiene un riferimento a un nuovo oggetto [IAssemblyCacheItem](iassemblycacheitem-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="f160e-103">Gets a reference to a new [IAssemblyCacheItem](iassemblycacheitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f160e-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f160e-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyCacheItem (  
    [in]  DWORD dwFlags,  
    [in]  PVOID pvReserved,  
    [out] IAssemblyCacheItem **ppAsmItem,  
    [in, optional] LPCWSTR pszAssemblyName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f160e-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="f160e-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="f160e-106">in Flag definiti in Fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="f160e-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="f160e-107">Sono supportati i valori seguenti:</span><span class="sxs-lookup"><span data-stu-id="f160e-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="f160e-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="f160e-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
- <span data-ttu-id="f160e-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span><span class="sxs-lookup"><span data-stu-id="f160e-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="f160e-110">in Riservato per l'estendibilità futura.</span><span class="sxs-lookup"><span data-stu-id="f160e-110">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="f160e-111">`pvReserved` deve essere un riferimento null.</span><span class="sxs-lookup"><span data-stu-id="f160e-111">`pvReserved` must be a null reference.</span></span>  
  
 `ppAsmItem`  
 <span data-ttu-id="f160e-112">out Puntatore `IAssemblyCacheItem` restituito.</span><span class="sxs-lookup"><span data-stu-id="f160e-112">[out] The returned `IAssemblyCacheItem` pointer.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="f160e-113">[in, facoltativo] Coppie di `name=value` delimitate da virgole.</span><span class="sxs-lookup"><span data-stu-id="f160e-113">[in, optional] Uncanonicalized, comma-separated `name=value` pairs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f160e-114">Requisiti</span><span class="sxs-lookup"><span data-stu-id="f160e-114">Requirements</span></span>  
 <span data-ttu-id="f160e-115">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f160e-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f160e-116">**Intestazione:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="f160e-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f160e-117">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f160e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f160e-118">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f160e-118">See also</span></span>

- [<span data-ttu-id="f160e-119">Interfaccia IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="f160e-119">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="f160e-120">Interfaccia IAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="f160e-120">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
