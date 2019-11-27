---
title: Enumerazione CorFileMapping
ms.date: 03/30/2017
api_name:
- CorFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFileMapping
helpviewer_keywords:
- CorFileMapping enumeration [.NET Framework metadata]
ms.assetid: 3ca41592-b8da-475a-8032-a15627730003
topic_type:
- apiref
ms.openlocfilehash: f85a36c810df52f871ecc75b92a3b4440455c66b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450290"
---
# <a name="corfilemapping-enumeration"></a><span data-ttu-id="39716-102">Enumerazione CorFileMapping</span><span class="sxs-lookup"><span data-stu-id="39716-102">CorFileMapping Enumeration</span></span>
<span data-ttu-id="39716-103">Contiene valori che descrivono il tipo di mapping di file restituito da una chiamata al metodo [IMetaDataInfo:: GetFileMapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) .</span><span class="sxs-lookup"><span data-stu-id="39716-103">Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39716-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="39716-104">Syntax</span></span>  
  
```cpp  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="39716-105">Members</span><span class="sxs-lookup"><span data-stu-id="39716-105">Members</span></span>  
  
|<span data-ttu-id="39716-106">Membro</span><span class="sxs-lookup"><span data-stu-id="39716-106">Member</span></span>|<span data-ttu-id="39716-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="39716-107">Description</span></span>|  
|------------|-----------------|  
|`fmFlat`|<span data-ttu-id="39716-108">Il file viene mappato come file di dati.</span><span class="sxs-lookup"><span data-stu-id="39716-108">The file is mapped as a data file.</span></span> <span data-ttu-id="39716-109">Ovvero, il flag di `SEC_IMAGE` non è stato passato alla funzione Microsoft Win32 `CreateFileMapping`.</span><span class="sxs-lookup"><span data-stu-id="39716-109">That is, the `SEC_IMAGE` flag was not passed to the Microsoft Win32 `CreateFileMapping` function.</span></span>|  
|`fmExecutableImage`|<span data-ttu-id="39716-110">Per eseguire il mapping del file, è possibile usare la funzione `LoadLibrary` o la funzione `CreateFileMapping` con il flag `SEC_IMAGE`.</span><span class="sxs-lookup"><span data-stu-id="39716-110">The file is mapped for execution, by using either the `LoadLibrary` function or the `CreateFileMapping` function with the `SEC_IMAGE` flag.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="39716-111">Requisiti</span><span class="sxs-lookup"><span data-stu-id="39716-111">Requirements</span></span>  
 <span data-ttu-id="39716-112">**Piattaforme:** vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39716-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39716-113">**Intestazione:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="39716-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="39716-114">**Versioni di .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39716-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39716-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="39716-115">See also</span></span>

- [<span data-ttu-id="39716-116">Enumerazioni dei metadati</span><span class="sxs-lookup"><span data-stu-id="39716-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="39716-117">Metodo GetFileMapping</span><span class="sxs-lookup"><span data-stu-id="39716-117">GetFileMapping Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md)
