---
title: Metodo SetAssemblyFile2
ms.date: 03/30/2017
api_name:
- IALink2.SetAssemblyFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile2
helpviewer_keywords:
- SetAssemblyFile2 method
ms.assetid: eedb9125-1ef1-4000-abfc-7de86e5a1f17
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5d96881ce35dca1ee7a196507ef8d81a565eed82
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741511"
---
# <a name="setassemblyfile2-method"></a><span data-ttu-id="b840a-102">Metodo SetAssemblyFile2</span><span class="sxs-lookup"><span data-stu-id="b840a-102">SetAssemblyFile2 Method</span></span>
<span data-ttu-id="b840a-103">Imposta il nome e le opzioni per un nuovo assembly.</span><span class="sxs-lookup"><span data-stu-id="b840a-103">Sets the name of and options for a new assembly.</span></span> <span data-ttu-id="b840a-104">Non chiamare questo metodo quando si creano moduli non associati.</span><span class="sxs-lookup"><span data-stu-id="b840a-104">Do not call this method when you produce unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b840a-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="b840a-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="b840a-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="b840a-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="b840a-107">Nome del file manifesto.</span><span class="sxs-lookup"><span data-stu-id="b840a-107">Name of manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="b840a-108">[Interfaccia IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interfaccia per questo file.</span><span class="sxs-lookup"><span data-stu-id="b840a-108">[IMetaDataEmit2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interface for this file.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="b840a-109">Opzioni rappresentato da [enumerazione AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="b840a-109">Options represented by [AssemblyFlags Enumeration](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="b840a-110">Riceve l'ID univoco per l'assembly in fase di costruzione.</span><span class="sxs-lookup"><span data-stu-id="b840a-110">Receives unique ID for the assembly being constructed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b840a-111">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="b840a-111">Return Value</span></span>  
 <span data-ttu-id="b840a-112">Restituisce S_OK se il metodo ha esito positivo.</span><span class="sxs-lookup"><span data-stu-id="b840a-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b840a-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="b840a-113">Requirements</span></span>  
 <span data-ttu-id="b840a-114">Richiede alink.h.</span><span class="sxs-lookup"><span data-stu-id="b840a-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b840a-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b840a-115">See also</span></span>

- [<span data-ttu-id="b840a-116">Interfaccia IALink2</span><span class="sxs-lookup"><span data-stu-id="b840a-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="b840a-117">Interfaccia IALink</span><span class="sxs-lookup"><span data-stu-id="b840a-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="b840a-118">Alink (API)</span><span class="sxs-lookup"><span data-stu-id="b840a-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
