---
title: Metodo IMetaDataEmit::DefineMemberRef
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMemberRef
helpviewer_keywords:
- DefineMemberRef method [.NET Framework metadata]
- IMetaDataEmit::DefineMemberRef method [.NET Framework metadata]
ms.assetid: 21b5bcb8-ea75-4962-8acc-ad17584061e5
topic_type:
- apiref
ms.openlocfilehash: 696389b51328e167212fb2292a873c34b9263811
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431828"
---
# <a name="imetadataemitdefinememberref-method"></a>Metodo IMetaDataEmit::DefineMemberRef
Defines a reference to a member of a module outside the current scope, and gets a token to that reference definition.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT DefineMemberRef (   
    [in]  mdToken           tkImport,   
    [in]  LPCWSTR           szName,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [out] mdMemberRef       *pmr   
);  
```  
  
## <a name="parameters"></a>Parametri  
 `tkImport`  
 [in] Token for the target member's class or interface, if the member is not global; if the member is global, the `mdModuleRef` token for that other file.  
  
 `szName`  
 [in] The name of the target member.  
  
 `pvSigBlob`  
 [in] The signature of the target member.  
  
 `cbSigBlob`  
 [in] The count of bytes in `pvSigBlob`.  
  
 `pmr`  
 [out] The `mdMemberRef` token assigned.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** Cor.h  
  
 **Library:** Used as a resource in MSCorEE.dll  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interfaccia IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
