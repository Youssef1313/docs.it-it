---
title: Metodo SetPEKind
ms.date: 03/30/2017
api_name:
- IALink2.SetPEKind
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetPEKind
helpviewer_keywords:
- SetPEKind method
ms.assetid: 050e77ee-3014-45c0-9e29-2ebe29347b0d
topic_type:
- apiref
ms.openlocfilehash: dfbc10bdbe633450dee2e27524c29ead21fb739e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445543"
---
# <a name="setpekind-method"></a><span data-ttu-id="81768-102">Metodo SetPEKind</span><span class="sxs-lookup"><span data-stu-id="81768-102">SetPEKind Method</span></span>
<span data-ttu-id="81768-103">Determines the portable executable type, either machine-specific or machine-agnostic.</span><span class="sxs-lookup"><span data-stu-id="81768-103">Determines the portable executable type, either machine-specific or machine-agnostic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81768-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="81768-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;   
```  
  
## <a name="parameters"></a><span data-ttu-id="81768-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="81768-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="81768-106">ID of the assembly.</span><span class="sxs-lookup"><span data-stu-id="81768-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="81768-107">Token of file for which the PE type is to be set.</span><span class="sxs-lookup"><span data-stu-id="81768-107">Token of file for which the PE type is to be set.</span></span> <span data-ttu-id="81768-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span><span class="sxs-lookup"><span data-stu-id="81768-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `dwPEKind`  
 <span data-ttu-id="81768-109">The type of PE, as indicated by the [CorPEKind Enumeration](../metadata/corpekind-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="81768-109">The type of PE, as indicated by the [CorPEKind Enumeration](../metadata/corpekind-enumeration.md).</span></span>  
  
 `dwMachine`  
 <span data-ttu-id="81768-110">The target machine architecture, as indicated in the NT header.</span><span class="sxs-lookup"><span data-stu-id="81768-110">The target machine architecture, as indicated in the NT header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81768-111">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="81768-111">Return Value</span></span>  
 <span data-ttu-id="81768-112">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="81768-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81768-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="81768-113">Requirements</span></span>  
 <span data-ttu-id="81768-114">Requires alink.h.</span><span class="sxs-lookup"><span data-stu-id="81768-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81768-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="81768-115">See also</span></span>

- [<span data-ttu-id="81768-116">Metodo GetPEKind</span><span class="sxs-lookup"><span data-stu-id="81768-116">GetPEKind Method</span></span>](../metadata/imetadataimport2-getpekind-method.md)
- [<span data-ttu-id="81768-117">Interfaccia IALink2</span><span class="sxs-lookup"><span data-stu-id="81768-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="81768-118">Interfaccia IALink</span><span class="sxs-lookup"><span data-stu-id="81768-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="81768-119">API ALink</span><span class="sxs-lookup"><span data-stu-id="81768-119">ALink API</span></span>](index.md)
