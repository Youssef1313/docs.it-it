---
title: Enumerazione CorGenericParamAttr
ms.date: 03/30/2017
api_name:
- CorGenericParamAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGenericParamAttr
helpviewer_keywords:
- CorGenericParamAttr enumeration [.NET Framework metadata]
ms.assetid: 36c76266-71d8-48dc-bd89-54943fa659c1
topic_type:
- apiref
ms.openlocfilehash: e4abf876681d5b04555c9f030a94b722874e326e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450286"
---
# <a name="corgenericparamattr-enumeration"></a>Enumerazione CorGenericParamAttr
Contains values that describe the <xref:System.Type> parameters for generic types, as used in calls to [IMetaDataEmit2::DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef enum CorGenericParamAttr {  
  
    gpVarianceMask                     =   0x0003,  
    gpNonVariant                       =   0x0000,   
    gpCovariant                        =   0x0001,  
    gpContravariant                    =   0x0002,  
  
    gpSpecialConstraintMask            =   0x001C,  
    gpNoSpecialConstraint              =   0x0000,  
    gpReferenceTypeConstraint          =   0x0004,   
    gpNotNullableValueTypeConstraint   =   0x0008,  
    gpDefaultConstructorConstraint     =   0x0010  
  
} CorGenericParamAttr;  
```  
  
## <a name="members"></a>Members  
  
|Member|Descrizione|  
|------------|-----------------|  
|`gpVarianceMask`|Parameter variance applies only to generic parameters for interfaces and delegates.|  
|`gpNonVariant`|Indicates the absence of variance.|  
|`gpCovariant`|Indicates covariance.|  
|`gpContravariant`|Indicates contravariance.|  
|`gpSpecialConstraintMask`|Special constraints can apply to any <xref:System.Type> parameter.|  
|`gpNoSpecialConstraint`|Indicates that no constraint applies to the <xref:System.Type> parameter.|  
|`gpReferenceTypeConstraint`|Indicates that the <xref:System.Type> parameter must be a reference type.|  
|`gpNotNullableValueTypeConstraint`|Indicates that the <xref:System.Type> parameter must be a value type that cannot be a null value.|  
|`gpDefaultConstructorConstraint`|Indicates that the <xref:System.Type> parameter must have a default public constructor that takes no parameters.|  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorHdr.h  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Enumerazioni dei metadati](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
