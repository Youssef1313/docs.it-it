---
title: Struttura OSINFO
ms.date: 03/30/2017
api_name:
- OSINFO
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- OSINFO
helpviewer_keywords:
- OSINFO structure [.NET Framework metadata]
ms.assetid: fac7b480-7adb-4450-a5e9-690fed81ffae
topic_type:
- apiref
ms.openlocfilehash: 89111bf7eb03d20c2010c7a20c4cd055c2a021e3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430728"
---
# <a name="osinfo-structure"></a>Struttura OSINFO
Contiene informazioni dettagliate sul sistema operativo per un assembly o un modulo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;   
    DWORD   dwOSMinorVersion;   
} OSINFO;  
```  
  
## <a name="members"></a>Members  
  
|Membro|Descrizione|  
|------------|-----------------|  
|`dwOSPlatformId`|Uno dei valori dell'identificatore definito dalla funzione della piattaforma Microsoft Windows `GetVersionEx`. Sono supportati i valori seguenti:<br /><br /> -VER_PLATFORM_WIN32s, o 0x0000, per specificare Microsoft Windows 3,1.<br />-VER_PLATFORM_WIN32_WINDOWS, o 0x0001, per specificare Windows 95, Windows 98 o i sistemi operativi discendenti da essi.<br />-VER_PLATFORM_WIN32_NT, o 0x0010, per specificare Windows NT o i sistemi operativi derivati da esso.|  
|`dwOSMajorVersion`|La versione principale del sistema operativo o un valore NULL per indicare qualsiasi versione.|  
|`dwOSMinorVersion`|La versione secondaria del sistema operativo o un valore NULL per indicare qualsiasi versione.|  
  
## <a name="remarks"></a>Note  
 `OSINFO` è basato sulla struttura di `OSVERSIONINFOEX` utilizzata nelle chiamate alla funzione della piattaforma Microsoft Windows `GetVersionEx`. Questa struttura viene utilizzata dalla struttura ASSEMBLYMETADATA per indicare il relativo supporto del sistema operativo.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** Cor. h  
  
 **Libreria:** Usato come risorsa in MsCorEE. dll  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Strutture di metadati](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [Interfaccia IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
