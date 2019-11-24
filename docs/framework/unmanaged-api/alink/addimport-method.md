---
title: Metodo AddImport
ms.date: 03/30/2017
api_name:
- AddImport
- IALink.AddImport
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddImport
helpviewer_keywords:
- AddImport method
ms.assetid: 4fedf8a0-08c8-43d0-aa00-20f2a521c991
topic_type:
- apiref
ms.openlocfilehash: 52e52ac62e2dcfeb182da3014a863409f640274e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446651"
---
# <a name="addimport-method"></a><span data-ttu-id="07004-102">Metodo AddImport</span><span class="sxs-lookup"><span data-stu-id="07004-102">AddImport Method</span></span>
<span data-ttu-id="07004-103">Adds imports to the assembly.</span><span class="sxs-lookup"><span data-stu-id="07004-103">Adds imports to the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07004-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="07004-104">Syntax</span></span>  
  
```cpp  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="07004-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="07004-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="07004-106">Unique ID of assembly to be augmented.</span><span class="sxs-lookup"><span data-stu-id="07004-106">Unique ID of assembly to be augmented.</span></span>  
  
 `ImportToken`  
 <span data-ttu-id="07004-107">Unique ID, retrieved from [ImportFile Method](importfile-method.md), of file to be imported.</span><span class="sxs-lookup"><span data-stu-id="07004-107">Unique ID, retrieved from [ImportFile Method](importfile-method.md), of file to be imported.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="07004-108">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="07004-108">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="07004-109">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="07004-109">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="07004-110">Pointer to token that receives the ID for the resulting file.</span><span class="sxs-lookup"><span data-stu-id="07004-110">Pointer to token that receives the ID for the resulting file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="07004-111">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="07004-111">Return Value</span></span>  
 <span data-ttu-id="07004-112">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="07004-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07004-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="07004-113">Requirements</span></span>  
 <span data-ttu-id="07004-114">Requires alink.h</span><span class="sxs-lookup"><span data-stu-id="07004-114">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07004-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="07004-115">See also</span></span>

- [<span data-ttu-id="07004-116">Interfaccia IALink</span><span class="sxs-lookup"><span data-stu-id="07004-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="07004-117">Interfaccia IALink2</span><span class="sxs-lookup"><span data-stu-id="07004-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="07004-118">API ALink</span><span class="sxs-lookup"><span data-stu-id="07004-118">ALink API</span></span>](index.md)
