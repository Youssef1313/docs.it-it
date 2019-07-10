---
title: Enumerazione CorMethodAttr
ms.date: 03/30/2017
api_name:
- CorMethodAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodAttr
helpviewer_keywords:
- CorMethodAttr enumeration [.NET Framework metadata]
ms.assetid: 4e0c3521-e54d-43c1-9857-cc76b49b8ffc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ff298f73f02f148fc389f389ba86fd9a550998c7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781780"
---
# <a name="cormethodattr-enumeration"></a><span data-ttu-id="1a52d-102">Enumerazione CorMethodAttr</span><span class="sxs-lookup"><span data-stu-id="1a52d-102">CorMethodAttr Enumeration</span></span>
<span data-ttu-id="1a52d-103">Contiene valori che descrivono le funzionalità di un metodo.</span><span class="sxs-lookup"><span data-stu-id="1a52d-103">Contains values that describe the features of a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a52d-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="1a52d-104">Syntax</span></span>  
  
```cpp  
typedef enum CorMethodAttr {  
  
    mdMemberAccessMask          =   0x0007,  
    mdPrivateScope              =   0x0000,  
    mdPrivate                   =   0x0001,  
    mdFamANDAssem               =   0x0002,  
    mdAssem                     =   0x0003,  
    mdFamily                    =   0x0004,  
    mdFamORAssem                =   0x0005,  
    mdPublic                    =   0x0006,  
  
    mdStatic                    =   0x0010,  
    mdFinal                     =   0x0020,  
    mdVirtual                   =   0x0040,  
    mdHideBySig                 =   0x0080,  
  
    mdVtableLayoutMask          =   0x0100,  
    mdReuseSlot                 =   0x0000,  
    mdNewSlot                   =   0x0100,  
  
    mdCheckAccessOnOverride     =   0x0200,  
    mdAbstract                  =   0x0400,  
    mdSpecialName               =   0x0800,  
  
    mdPinvokeImpl               =   0x2000,  
    mdUnmanagedExport           =   0x0008,  
  
    mdReservedMask              =   0xd000,  
    mdRTSpecialName             =   0x1000,  
    mdHasSecurity               =   0x4000,  
    mdRequireSecObject          =   0x8000,  
  
} CorMethodAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="1a52d-105">Membri</span><span class="sxs-lookup"><span data-stu-id="1a52d-105">Members</span></span>  
  
|<span data-ttu-id="1a52d-106">Member</span><span class="sxs-lookup"><span data-stu-id="1a52d-106">Member</span></span>|<span data-ttu-id="1a52d-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="1a52d-107">Description</span></span>|  
|------------|-----------------|  
|`mdMemberAccessMask`|<span data-ttu-id="1a52d-108">Specifica l'accesso al membro.</span><span class="sxs-lookup"><span data-stu-id="1a52d-108">Specifies member access.</span></span>|  
|`mdPrivateScope`|<span data-ttu-id="1a52d-109">Specifica che il membro non è possibile fare riferimento.</span><span class="sxs-lookup"><span data-stu-id="1a52d-109">Specifies that the member cannot be referenced.</span></span>|  
|`mdPrivate`|<span data-ttu-id="1a52d-110">Specifica che il membro è accessibile solo dal tipo padre.</span><span class="sxs-lookup"><span data-stu-id="1a52d-110">Specifies that the member is accessible only by the parent type.</span></span>|  
|`mdFamANDAssem`|<span data-ttu-id="1a52d-111">Specifica che il membro è accessibile dai sottotipi solo in questo assembly.</span><span class="sxs-lookup"><span data-stu-id="1a52d-111">Specifies that the member is accessible by subtypes only in this assembly.</span></span>|  
|`mdAssem`|<span data-ttu-id="1a52d-112">Specifica che il membro è accessibile da tutti gli utenti nell'assembly.</span><span class="sxs-lookup"><span data-stu-id="1a52d-112">Specifies that the member is accessibly by anyone in the assembly.</span></span>|  
|`mdFamily`|<span data-ttu-id="1a52d-113">Specifica che il membro è accessibile solo dal tipo e sottotipi.</span><span class="sxs-lookup"><span data-stu-id="1a52d-113">Specifies that the member is accessible only by type and subtypes.</span></span>|  
|`mdFamORAssem`|<span data-ttu-id="1a52d-114">Specifica che il membro è accessibile dalle classi derivate e da altri tipi nell'assembly.</span><span class="sxs-lookup"><span data-stu-id="1a52d-114">Specifies that the member is accessible by derived classes and by other types in its assembly.</span></span>|  
|`mdPublic`|<span data-ttu-id="1a52d-115">Specifica che il membro è accessibile da tutti i tipi con accesso all'ambito.</span><span class="sxs-lookup"><span data-stu-id="1a52d-115">Specifies that the member is accessible by all types with access to the scope.</span></span>|  
|`mdStatic`|<span data-ttu-id="1a52d-116">Specifica che il membro è definito come parte del tipo anziché come un membro di un'istanza.</span><span class="sxs-lookup"><span data-stu-id="1a52d-116">Specifies that the member is defined as part of the type rather than as a member of an instance.</span></span>|  
|`mdFinal`|<span data-ttu-id="1a52d-117">Specifica che il metodo non può essere sottoposto a override.</span><span class="sxs-lookup"><span data-stu-id="1a52d-117">Specifies that the method cannot be overridden.</span></span>|  
|`mdVirtual`|<span data-ttu-id="1a52d-118">Specifica che il metodo può essere sottoposto a override.</span><span class="sxs-lookup"><span data-stu-id="1a52d-118">Specifies that the method can be overridden.</span></span>|  
|`mdHideBySig`|<span data-ttu-id="1a52d-119">Specifica che il metodo è nascosto per nome e firma, anziché semplicemente dal nome.</span><span class="sxs-lookup"><span data-stu-id="1a52d-119">Specifies that the method hides by name and signature, rather than just by name.</span></span>|  
|`mdVtableLayoutMask`|<span data-ttu-id="1a52d-120">Specifica il layout di tabella virtuale.</span><span class="sxs-lookup"><span data-stu-id="1a52d-120">Specifies virtual table layout.</span></span>|  
|`mdReuseSlot`|<span data-ttu-id="1a52d-121">Specifica che lo slot usato per questo metodo nella tabella virtuale è possibile riutilizzare.</span><span class="sxs-lookup"><span data-stu-id="1a52d-121">Specifies that the slot used for this method in the virtual table be reused.</span></span> <span data-ttu-id="1a52d-122">Questa è l'impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="1a52d-122">This is the default.</span></span>|  
|`mdNewSlot`|<span data-ttu-id="1a52d-123">Specifica che il metodo ottiene sempre un nuovo slot nella tabella virtuale.</span><span class="sxs-lookup"><span data-stu-id="1a52d-123">Specifies that the method always gets a new slot in the virtual table.</span></span>|  
|`mdCheckAccessOnOverride`|<span data-ttu-id="1a52d-124">Specifica che il metodo può essere sostituito dagli stessi tipi a cui è visibile.</span><span class="sxs-lookup"><span data-stu-id="1a52d-124">Specifies that the method can be overridden by the same types to which it is visible.</span></span>|  
|`mdAbstract`|<span data-ttu-id="1a52d-125">Specifica che il metodo non è implementato.</span><span class="sxs-lookup"><span data-stu-id="1a52d-125">Specifies that the method is not implemented.</span></span>|  
|`mdSpecialName`|<span data-ttu-id="1a52d-126">Specifica che il metodo è speciale e che il relativo nome viene descritto come.</span><span class="sxs-lookup"><span data-stu-id="1a52d-126">Specifies that the method is special, and that its name describes how.</span></span>|  
|`mdPinvokeImpl`|<span data-ttu-id="1a52d-127">Specifica che l'implementazione del metodo è inoltrata tramite PInvoke.</span><span class="sxs-lookup"><span data-stu-id="1a52d-127">Specifies that the method implementation is forwarded using PInvoke.</span></span>|  
|`mdUnmanagedExport`|<span data-ttu-id="1a52d-128">Specifica che il metodo è un metodo gestito esportato in codice non gestito.</span><span class="sxs-lookup"><span data-stu-id="1a52d-128">Specifies that the method is a managed method exported to unmanaged code.</span></span>|  
|`mdReservedMask`|<span data-ttu-id="1a52d-129">Riservato per uso interno da common language runtime.</span><span class="sxs-lookup"><span data-stu-id="1a52d-129">Reserved for internal use by the common language runtime.</span></span>|  
|`mdRTSpecialName`|<span data-ttu-id="1a52d-130">Specifica che common language runtime deve verificare la codifica del nome del metodo.</span><span class="sxs-lookup"><span data-stu-id="1a52d-130">Specifies that the common language runtime should check the encoding of the method name.</span></span>|  
|`mdHasSecurity`|<span data-ttu-id="1a52d-131">Specifica che il metodo è associata una sicurezza.</span><span class="sxs-lookup"><span data-stu-id="1a52d-131">Specifies that the method has security associated with it.</span></span>|  
|`mdRequireSecObject`|<span data-ttu-id="1a52d-132">Specifica che il metodo chiama un altro metodo contenente codice di sicurezza.</span><span class="sxs-lookup"><span data-stu-id="1a52d-132">Specifies that the method calls another method containing security code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1a52d-133">Requisiti</span><span class="sxs-lookup"><span data-stu-id="1a52d-133">Requirements</span></span>  
 <span data-ttu-id="1a52d-134">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a52d-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a52d-135">**Intestazione:** CorHdr. H</span><span class="sxs-lookup"><span data-stu-id="1a52d-135">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="1a52d-136">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a52d-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a52d-137">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1a52d-137">See also</span></span>

- [<span data-ttu-id="1a52d-138">Enumerazioni dei metadati</span><span class="sxs-lookup"><span data-stu-id="1a52d-138">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
