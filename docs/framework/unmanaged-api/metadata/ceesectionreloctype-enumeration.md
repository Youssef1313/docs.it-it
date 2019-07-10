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
# <a name="ceesectionreloctype-enumeration"></a>Enumerazione CeeSectionRelocType
Fornisce i valori che influenzano il tipo della `reloc` istruzione generato in una chiamata a [ICeeGen:: AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).  
  
## <a name="syntax"></a>Sintassi  
  
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
  
## <a name="members"></a>Membri  
  
|Member|Descrizione|  
|------------|-----------------|  
|`srRelocAbsolute`|Genera solo un relativo alla sezione `reloc`, inviando alcuna informazione in una sezione. reloc.|  
|`srRelocHighLow`|Genera un `reloc` per una località della dimensione del puntatore. Questo viene trasformato in BASED_HIGHLOW o BASED_DIR64 a seconda della piattaforma.|  
|`srRelocHighAdj`|Genera un `reloc` per i primi 16 bit di un numero a 32 bit, in cui sono inclusi la parte inferiore di 16 bit della parola successiva nella tabella reloc.|  
|`srRelocMapToken`|Genera una rilocazione della mappa del token, l'invio di alcuna operazione in una sezione. reloc.|  
|`srRelocRelative`|Indica che il valore è un'indirizzo relativo di correzione.|  
|`srRelocFilePos`|Genera solo un relativo alla sezione `reloc`, inviando alcuna informazione in una sezione. reloc. Ciò `reloc` è relativo alla posizione del file della sezione, non l'indirizzo virtuale.|  
|`srRelocCodeRelative`|Specifica un'indirizzo relativo al codice di correzione.|  
|`srRelocIA64Imm64`|Genera una `reloc` per un indirizzo a 64 bit in un ambiente ia64 `movl` (istruzione).|  
|`srRelocDir64`|Genera un `reloc` per un indirizzo a 64 bit.|  
|`srRelocIA64PcRel25`|Generare una `reloc` per un indirizzo relativo al PC di 25 bit in un ambiente ia64 `br.call` (istruzione).|  
|`srRelocIA64PcRel64`|Genera una `reloc` per un indirizzo relativo al PC a 64 bit in un ambiente ia64 `brl.call` (istruzione).|  
|`srRelocAbsoluteTagged`|Genera un sezione relativo 30 bit `reloc`, usato per i valori di puntatore con tag.|  
|`srRelocSentinel`|Valore di sentinel per garantire che tutte le aggiunte a questa enumerazione vengono riflesse alla classe interna `reloc` matrice nome.|  
|`srNoBaseReloc`|Specifica di non generare una base `reloc`.|  
|`srRelocPtr`|Un valore che indica che il contenuto di pre-correzione della memoria è un puntatore anziché a una sezione di offset.|  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** Cor. h  
  
 **Libreria:** Inclusa come risorsa in Mscoree. dll  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Enumerazioni dei metadati](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [Interfaccia ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [Metodo AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
