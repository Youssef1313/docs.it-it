---
title: Metodo ICeeGen::AddSectionReloc
ms.date: 03/30/2017
api_name:
- ICeeGen.AddSectionReloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::AddSectionReloc
helpviewer_keywords:
- AddSectionReloc method [.NET Framework metadata]
- ICeeGen::AddSectionReloc method [.NET Framework metadata]
ms.assetid: b500a260-1d57-4953-95e1-c27063f7c8da
topic_type:
- apiref
ms.openlocfilehash: e5940f229e86b46bb8c5d5b2f9920a8261359f65
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436416"
---
# <a name="iceegenaddsectionreloc-method"></a>Metodo ICeeGen::AddSectionReloc
Adds a .reloc instruction to the code base.  
  
 This method is obsolete and should not be used.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,   
   [in] CeeSectionRelocType    relocType  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `section`  
 [in] The section of in-memory code to which to add a .reloc instruction.  
  
 `offset`  
 [in] The offset of the section.  
  
 `relativeTo`  
 [in] The section to which `offset` refers.  
  
 `relocType`  
 [in] One of the [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) values, indicating the kind of .reloc instruction to add.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** Cor.h  
  
 **Library:** Used as a resource in MsCorEE.dll  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
