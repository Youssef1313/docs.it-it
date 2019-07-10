---
title: Enumerazione CeeSectionRelocType
ms.date: 03/30/2017
api_name:
- CeeSectionRelocType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionRelocType
helpviewer_keywords:
- CeeSectionRelocType enumeration [.NET Framework metadata]
ms.assetid: 124656f6-0dad-4ceb-9043-d3869ab65cde
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1218ee76a3b7a2f501f87adf1e0bc8133d5329b5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781341"
---
# <a name="ceesectionreloctype-enumeration"></a><span data-ttu-id="2813b-102">Enumerazione CeeSectionRelocType</span><span class="sxs-lookup"><span data-stu-id="2813b-102">CeeSectionRelocType Enumeration</span></span>
<span data-ttu-id="2813b-103">Fornisce i valori che influenzano il tipo della `reloc` istruzione generato in una chiamata a [ICeeGen:: AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).</span><span class="sxs-lookup"><span data-stu-id="2813b-103">Provides values to influence the type of `reloc` instruction emitted in a call to [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2813b-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="2813b-104">Syntax</span></span>  
  
```cpp  
typedef enum  {  
    srRelocAbsolute,  
    srRelocHighLow          = 3,  
    srRelocHighAdj,       
    srRelocMapToken,  
    srRelocRelative,  
    srRelocFilePos,  
    srRelocCodeRelative,  
    srRelocIA64Imm64,  
    srRelocDir64,  
    srRelocIA64PcRel25,  
    srRelocIA64PcRel64,    srRelocAbsoluteTagged,    srRelocSentinel,    srNoBaseReloc       = 0x4000,  
    srRelocPtr          = 0x8000,  
    srRelocAbsolutePtr      = srRelocPtr + srRelocAbsolute,  
    srRelocHighLowPtr       = srRelocPtr + srRelocHighLow,  
    srRelocRelativePtr      = srRelocPtr + srRelocRelative,  
    srRelocIA64Imm64Ptr     = srRelocPtr + srRelocIA64Imm64,  
    srRelocDir64Ptr         = srRelocPtr + srRelocDir64  
    } CeeSectionRelocType;  
```  
  
## <a name="members"></a><span data-ttu-id="2813b-105">Membri</span><span class="sxs-lookup"><span data-stu-id="2813b-105">Members</span></span>  
  
|<span data-ttu-id="2813b-106">Member</span><span class="sxs-lookup"><span data-stu-id="2813b-106">Member</span></span>|<span data-ttu-id="2813b-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="2813b-107">Description</span></span>|  
|------------|-----------------|  
|`srRelocAbsolute`|<span data-ttu-id="2813b-108">Genera solo un relativo alla sezione `reloc`, inviando alcuna informazione in una sezione. reloc.</span><span class="sxs-lookup"><span data-stu-id="2813b-108">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span>|  
|`srRelocHighLow`|<span data-ttu-id="2813b-109">Genera un `reloc` per una località della dimensione del puntatore.</span><span class="sxs-lookup"><span data-stu-id="2813b-109">Generates a `reloc` for a pointer-sized location.</span></span> <span data-ttu-id="2813b-110">Questo viene trasformato in BASED_HIGHLOW o BASED_DIR64 a seconda della piattaforma.</span><span class="sxs-lookup"><span data-stu-id="2813b-110">This is transformed into BASED_HIGHLOW or BASED_DIR64 depending on the platform.</span></span>|  
|`srRelocHighAdj`|<span data-ttu-id="2813b-111">Genera un `reloc` per i primi 16 bit di un numero a 32 bit, in cui sono inclusi la parte inferiore di 16 bit della parola successiva nella tabella reloc.</span><span class="sxs-lookup"><span data-stu-id="2813b-111">Generates a `reloc` for the top 16 bits of a 32-bit number, where the bottom 16 bits are included in the next word in the .reloc table.</span></span>|  
|`srRelocMapToken`|<span data-ttu-id="2813b-112">Genera una rilocazione della mappa del token, l'invio di alcuna operazione in una sezione. reloc.</span><span class="sxs-lookup"><span data-stu-id="2813b-112">Generates a token map relocation, sending nothing into a .reloc section.</span></span>|  
|`srRelocRelative`|<span data-ttu-id="2813b-113">Indica che il valore è un'indirizzo relativo di correzione.</span><span class="sxs-lookup"><span data-stu-id="2813b-113">Indicates that the value is a relative address fixup.</span></span>|  
|`srRelocFilePos`|<span data-ttu-id="2813b-114">Genera solo un relativo alla sezione `reloc`, inviando alcuna informazione in una sezione. reloc.</span><span class="sxs-lookup"><span data-stu-id="2813b-114">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span> <span data-ttu-id="2813b-115">Ciò `reloc` è relativo alla posizione del file della sezione, non l'indirizzo virtuale.</span><span class="sxs-lookup"><span data-stu-id="2813b-115">This `reloc` is relative to the file position of the section, not the section's virtual address.</span></span>|  
|`srRelocCodeRelative`|<span data-ttu-id="2813b-116">Specifica un'indirizzo relativo al codice di correzione.</span><span class="sxs-lookup"><span data-stu-id="2813b-116">Specifies a code-relative address fixup.</span></span>|  
|`srRelocIA64Imm64`|<span data-ttu-id="2813b-117">Genera una `reloc` per un indirizzo a 64 bit in un ambiente ia64 `movl` (istruzione).</span><span class="sxs-lookup"><span data-stu-id="2813b-117">Generates a `reloc` for a 64 bit address in an ia64 `movl` instruction.</span></span>|  
|`srRelocDir64`|<span data-ttu-id="2813b-118">Genera un `reloc` per un indirizzo a 64 bit.</span><span class="sxs-lookup"><span data-stu-id="2813b-118">Generates a `reloc` for a 64-bit address.</span></span>|  
|`srRelocIA64PcRel25`|<span data-ttu-id="2813b-119">Generare una `reloc` per un indirizzo relativo al PC di 25 bit in un ambiente ia64 `br.call` (istruzione).</span><span class="sxs-lookup"><span data-stu-id="2813b-119">Generate a `reloc` for a 25-bit PC-relative address in an ia64 `br.call` instruction.</span></span>|  
|`srRelocIA64PcRel64`|<span data-ttu-id="2813b-120">Genera una `reloc` per un indirizzo relativo al PC a 64 bit in un ambiente ia64 `brl.call` (istruzione).</span><span class="sxs-lookup"><span data-stu-id="2813b-120">Generates a `reloc` for a 64-bit PC-relative address in an ia64 `brl.call` instruction.</span></span>|  
|`srRelocAbsoluteTagged`|<span data-ttu-id="2813b-121">Genera un sezione relativo 30 bit `reloc`, usato per i valori di puntatore con tag.</span><span class="sxs-lookup"><span data-stu-id="2813b-121">Generates a 30-bit section-relative `reloc`, used for tagged pointer values.</span></span>|  
|`srRelocSentinel`|<span data-ttu-id="2813b-122">Valore di sentinel per garantire che tutte le aggiunte a questa enumerazione vengono riflesse alla classe interna `reloc` matrice nome.</span><span class="sxs-lookup"><span data-stu-id="2813b-122">A sentinel value to help ensure any additions to this enum are reflected to the internal `reloc` name array.</span></span>|  
|`srNoBaseReloc`|<span data-ttu-id="2813b-123">Specifica di non generare una base `reloc`.</span><span class="sxs-lookup"><span data-stu-id="2813b-123">Specifies not to emit a base `reloc`.</span></span>|  
|`srRelocPtr`|<span data-ttu-id="2813b-124">Un valore che indica che il contenuto di pre-correzione della memoria è un puntatore anziché a una sezione di offset.</span><span class="sxs-lookup"><span data-stu-id="2813b-124">A value indicating that the pre-fixup contents of memory are a pointer rather than a section offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2813b-125">Requisiti</span><span class="sxs-lookup"><span data-stu-id="2813b-125">Requirements</span></span>  
 <span data-ttu-id="2813b-126">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2813b-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2813b-127">**Intestazione:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2813b-127">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2813b-128">**Libreria:** Inclusa come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="2813b-128">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2813b-129">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2813b-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2813b-130">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2813b-130">See also</span></span>

- [<span data-ttu-id="2813b-131">Enumerazioni dei metadati</span><span class="sxs-lookup"><span data-stu-id="2813b-131">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="2813b-132">Interfaccia ICeeGen</span><span class="sxs-lookup"><span data-stu-id="2813b-132">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [<span data-ttu-id="2813b-133">Metodo AddSectionReloc</span><span class="sxs-lookup"><span data-stu-id="2813b-133">AddSectionReloc Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
