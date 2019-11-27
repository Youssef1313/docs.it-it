---
title: Enumerazione CorOpenFlags
ms.date: 03/30/2017
api_name:
- CorOpenFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorOpenFlags
helpviewer_keywords:
- CorOpenFlags enumeration [.NET Framework metadata]
ms.assetid: e27a83b5-2698-4996-9032-1e0fed8b91ca
topic_type:
- apiref
ms.openlocfilehash: ad582fc2fd1bd1d2fc9d5a0d483fdb3a51309a10
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436500"
---
# <a name="coropenflags-enumeration"></a><span data-ttu-id="76716-102">Enumerazione CorOpenFlags</span><span class="sxs-lookup"><span data-stu-id="76716-102">CorOpenFlags Enumeration</span></span>
<span data-ttu-id="76716-103">Contiene valori di flag che controllano il comportamento dei metadati all'apertura di file manifesto.</span><span class="sxs-lookup"><span data-stu-id="76716-103">Contains flag values that control metadata behavior upon opening manifest files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76716-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="76716-104">Syntax</span></span>  
  
```cpp  
typedef enum CorOpenFlags  
{  
    ofRead              =   0x00000000,  
    ofWrite             =   0x00000001,  
    ofReadWriteMask     =   0x00000001,  
    ofCopyMemory        =   0x00000002,  
    ofCacheImage        =   0x00000004,  
    ofManifestMetadata  =   0x00000008,  
    ofReadOnly          =   0x00000010,  
    ofTakeOwnership     =   0x00000020,  
    ofCacheImage        =   0x00000004,  
    ofNoTypeLib         =   0x00000080,  
    ofNoTransform       =   0x00001000,  
    ofReserved1         =   0x00000100,  
    ofReserved2         =   0x00000200,  
    ofReserved          =   0xffffff40  
} CorOpenFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="76716-105">Members</span><span class="sxs-lookup"><span data-stu-id="76716-105">Members</span></span>  
  
|<span data-ttu-id="76716-106">Membro</span><span class="sxs-lookup"><span data-stu-id="76716-106">Member</span></span>|<span data-ttu-id="76716-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="76716-107">Description</span></span>|  
|------------|-----------------|  
|`ofRead`|<span data-ttu-id="76716-108">Indica che il file deve essere aperto in sola lettura.</span><span class="sxs-lookup"><span data-stu-id="76716-108">Indicates that the file should be opened for reading only.</span></span>|  
|`ofWrite`|<span data-ttu-id="76716-109">Indica che il file deve essere aperto in scrittura.</span><span class="sxs-lookup"><span data-stu-id="76716-109">Indicates that the file should be opened for writing.</span></span><br /><br /> <span data-ttu-id="76716-110">Se si usa il flag `ofWrite` quando si apre un file con estensione winmd, è anche necessario passare il flag `ofNoTransform`.</span><span class="sxs-lookup"><span data-stu-id="76716-110">If you are using the `ofWrite` flag when opening a .winmd file, you should also pass the `ofNoTransform` flag.</span></span>|  
|`ofReadWriteMask`|<span data-ttu-id="76716-111">Maschera per la lettura e la scrittura.</span><span class="sxs-lookup"><span data-stu-id="76716-111">A mask for reading and writing.</span></span>|  
|`ofCopyMemory`|<span data-ttu-id="76716-112">Indica che il file deve essere letto in memoria.</span><span class="sxs-lookup"><span data-stu-id="76716-112">Indicates that the file should be read into memory.</span></span> <span data-ttu-id="76716-113">I metadati devono mantenere la propria copia.</span><span class="sxs-lookup"><span data-stu-id="76716-113">Metadata should maintain its own copy.</span></span>|  
|`ofCacheImage`|<span data-ttu-id="76716-114">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="76716-114">Obsolete.</span></span> <span data-ttu-id="76716-115">Questo flag viene ignorato.</span><span class="sxs-lookup"><span data-stu-id="76716-115">This flag is ignored.</span></span>|  
|`ofManifestMetadata`|<span data-ttu-id="76716-116">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="76716-116">Obsolete.</span></span> <span data-ttu-id="76716-117">Questo flag viene ignorato.</span><span class="sxs-lookup"><span data-stu-id="76716-117">This flag is ignored.</span></span>|  
|`ofReadOnly`|<span data-ttu-id="76716-118">Indica che il file deve essere aperto per la lettura e che non è possibile effettuare una chiamata a `QueryInterface` per un oggetto [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="76716-118">Indicates that the file should be opened for reading, and that a call to `QueryInterface` for an [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) cannot be made.</span></span>|  
|`ofTakeOwnership`|<span data-ttu-id="76716-119">Indica che la memoria è stata allocata utilizzando una chiamata a [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) e verrà liberata dai metadati.</span><span class="sxs-lookup"><span data-stu-id="76716-119">Indicates that the memory was allocated using a call to [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) and will be freed by the metadata.</span></span>|  
|`ofNoTypeLib`|<span data-ttu-id="76716-120">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="76716-120">Obsolete.</span></span> <span data-ttu-id="76716-121">Questo flag viene ignorato.</span><span class="sxs-lookup"><span data-stu-id="76716-121">This flag is ignored.</span></span>|  
|`ofNoTransform`|<span data-ttu-id="76716-122">Indica che le trasformazioni automatiche dei file con estensione winmd devono essere disabilitate.</span><span class="sxs-lookup"><span data-stu-id="76716-122">Indicates that automatic transforms of .winmd files should be disabled.</span></span> <span data-ttu-id="76716-123">In altre parole, la proiezione di un tipo di Windows Runtime in un tipo di .NET Framework deve essere disabilitata.</span><span class="sxs-lookup"><span data-stu-id="76716-123">In other words, the projection of a Windows Runtime type to a .NET Framework type should be disabled.</span></span> <span data-ttu-id="76716-124">Per ulteriori informazioni, vedere [Windows Runtime e CLR-sotto la cappa con .NET e il Windows Runtime](https://docs.microsoft.com/archive/msdn-magazine/2012/windows-8-special-issue/windows-runtime-and-the-clr-underneath-the-hood-with-net-and-the-windows-runtime).</span><span class="sxs-lookup"><span data-stu-id="76716-124">For more information, see [Windows Runtime and the CLR - Underneath the Hood with .NET and the Windows Runtime](https://docs.microsoft.com/archive/msdn-magazine/2012/windows-8-special-issue/windows-runtime-and-the-clr-underneath-the-hood-with-net-and-the-windows-runtime).</span></span>|  
|`ofReserved1`|<span data-ttu-id="76716-125">Riservato a un uso interno.</span><span class="sxs-lookup"><span data-stu-id="76716-125">Reserved for internal use.</span></span>|  
|`ofReserved2`|<span data-ttu-id="76716-126">Riservato a un uso interno.</span><span class="sxs-lookup"><span data-stu-id="76716-126">Reserved for internal use.</span></span>|  
|`ofReserved`|<span data-ttu-id="76716-127">Riservato a un uso interno.</span><span class="sxs-lookup"><span data-stu-id="76716-127">Reserved for internal use.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="76716-128">Requisiti</span><span class="sxs-lookup"><span data-stu-id="76716-128">Requirements</span></span>  
 <span data-ttu-id="76716-129">**Piattaforme:** vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76716-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76716-130">**Intestazione:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="76716-130">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="76716-131">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76716-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76716-132">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="76716-132">See also</span></span>

- [<span data-ttu-id="76716-133">Enumerazioni dei metadati</span><span class="sxs-lookup"><span data-stu-id="76716-133">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
