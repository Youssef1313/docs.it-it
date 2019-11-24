---
title: Metodo ExportTypeForwarder
ms.date: 03/30/2017
api_name:
- IALink.ExportTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportTypeForwarder
helpviewer_keywords:
- ExportTypeForwarder method
ms.assetid: 55989fa9-ab43-4f08-8eb6-2eb56fa7ca76
topic_type:
- apiref
ms.openlocfilehash: 36c99477e9faead5e24799d5b0ae8901f1dd13c9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448714"
---
# <a name="exporttypeforwarder-method"></a><span data-ttu-id="88703-102">Metodo ExportTypeForwarder</span><span class="sxs-lookup"><span data-stu-id="88703-102">ExportTypeForwarder Method</span></span>
<span data-ttu-id="88703-103">Adds a type forwarder to the type table of the given assembly.</span><span class="sxs-lookup"><span data-stu-id="88703-103">Adds a type forwarder to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88703-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="88703-104">Syntax</span></span>  
  
```cpp  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="88703-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="88703-105">Parameters</span></span>  
 `tkAssemblyRef`  
 <span data-ttu-id="88703-106">Reference to the assembly to which the type forwarder refers.</span><span class="sxs-lookup"><span data-stu-id="88703-106">Reference to the assembly to which the type forwarder refers.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="88703-107">Fully qualified type name to export.</span><span class="sxs-lookup"><span data-stu-id="88703-107">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="88703-108">`ComType` flags such as `tdPublic` or `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="88703-108">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="88703-109">This value may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="88703-109">This value may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="88703-110">Receives the token of the exported type.</span><span class="sxs-lookup"><span data-stu-id="88703-110">Receives the token of the exported type.</span></span> <span data-ttu-id="88703-111">This is necessary only for emitting nested types.</span><span class="sxs-lookup"><span data-stu-id="88703-111">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="88703-112">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="88703-112">Return Value</span></span>  
 <span data-ttu-id="88703-113">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="88703-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88703-114">Requisiti</span><span class="sxs-lookup"><span data-stu-id="88703-114">Requirements</span></span>  
 <span data-ttu-id="88703-115">Requires alink.h</span><span class="sxs-lookup"><span data-stu-id="88703-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88703-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="88703-116">See also</span></span>

- [<span data-ttu-id="88703-117">Interfaccia IALink</span><span class="sxs-lookup"><span data-stu-id="88703-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="88703-118">Interfaccia IALink2</span><span class="sxs-lookup"><span data-stu-id="88703-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="88703-119">API ALink</span><span class="sxs-lookup"><span data-stu-id="88703-119">ALink API</span></span>](index.md)
