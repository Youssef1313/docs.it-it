---
title: Funzione StrongNameFreeBuffer
ms.date: 03/30/2017
api_name:
- StrongNameFreeBuffer
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameFreeBuffer
helpviewer_keywords:
- StrongNameFreeBuffer function [.NET Framework strong naming]
ms.assetid: eda21ecf-4734-4f92-aaba-9f34884385db
topic_type:
- apiref
ms.openlocfilehash: 11821acbeeb04ae09464eb0e032b9bf387914168
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095058"
---
# <a name="strongnamefreebuffer-function"></a>Funzione StrongNameFreeBuffer
Libera la memoria allocata con una precedente chiamata a una funzione con nome sicuro, ad esempio [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md) o [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).  
  
 Questa funzione è stata deprecata. Usare invece il metodo [ICLRStrongName:: StrongNameFreeBuffer](../hosting/iclrstrongname-strongnamefreebuffer-method.md) .  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
VOID StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `pbMemory`  
 in Puntatore alla memoria da liberare.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../get-started/system-requirements.md).  
  
 **Intestazione:** StrongName. h  
  
 **Libreria:** Incluso come risorsa in MsCorEE. dll  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Metodo StrongNameFreeBuffer](../hosting/iclrstrongname-strongnamefreebuffer-method.md)
- [Interfaccia ICLRStrongName](../hosting/iclrstrongname-interface.md)
