---
title: Metodo ICorDebugSymbolProvider::GetMethodProps
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95610bc527b8f5b90df906b6260eb636d61dbcd8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957314"
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a>Metodo ICorDebugSymbolProvider::GetMethodProps
Restituisce informazioni sulle proprietà del metodo, ad esempio il token di metadati del metodo e informazioni sui relativi parametri generici, da un indirizzo RVA (Relative Virtual Address) fornito in tale metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetMethodProps(  
   [in]  ULONG32 codeRva,  
   [out] mdToken *pMethodToken,  
   [out] ULONG32 *pcGenericParams,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `codeRVA`  
 [in] Indirizzo virtuale relativo del metodo sul quale recuperare informazioni.  
  
 `pMethodToken`  
 [out] Puntatore al token di metadati del metodo.  
  
 `pcGenericParams`  
 [out] Puntatore al numero di parametri generici associati al metodo.  
  
 `cbSignature`  
 [in] Dimensione della matrice `signature`. Vedere la sezione Osservazioni.  
  
 `pcbSignature`  
 [out] Puntatore alla dimensione della matrice `signature` restituita.  
  
 `signature`  
 [out] Buffer contenente le firme typespec di tutti i parametri generici.  
  
## <a name="remarks"></a>Note  
 Per ottenere `signature` le dimensioni richieste della matrice del metodo, impostare l' `cbSignature` argomento su 0 e `signature` su **null**. Quando il metodo viene restituito, `pcbSignature` conterrà il numero di byte necessari per la matrice `signature`.  
  
> [!NOTE]
> Questo metodo è disponibile solo con .NET Native.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorDebug. idl, CorDebug. h  
  
 **Libreria** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Metodo GetTypeProps](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)
- [Interfaccia ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [Interfacce di debug](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
