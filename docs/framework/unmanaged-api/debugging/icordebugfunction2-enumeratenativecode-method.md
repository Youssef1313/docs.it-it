---
title: Metodo ICorDebugFunction2::EnumerateNativeCode
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.EnumerateNativeCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::EnumerateNativeCode
helpviewer_keywords:
- ICorDebugFunction2::EnumerateNativeCode method [.NET Framework debugging]
- EnumerateNativeCode method [.NET Framework debugging]
ms.assetid: d383f5cc-1144-4b6d-b57a-db34d9134ab2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb7e2ed7b076cfa20064902b3592c8f958efc0ee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917043"
---
# <a name="icordebugfunction2enumeratenativecode-method"></a><span data-ttu-id="3e4f2-102">Metodo ICorDebugFunction2::EnumerateNativeCode</span><span class="sxs-lookup"><span data-stu-id="3e4f2-102">ICorDebugFunction2::EnumerateNativeCode Method</span></span>
<span data-ttu-id="3e4f2-103">Ottiene un puntatore a interfaccia a un oggetto ICorDebugCodeEnum che contiene le istruzioni di codice nativo nella funzione a cui fa riferimento questo oggetto ICorDebugFunction2.</span><span class="sxs-lookup"><span data-stu-id="3e4f2-103">Gets an interface pointer to an ICorDebugCodeEnum object that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3e4f2-104">`EnumerateNativeCode`non è implementato nella versione corrente del .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3e4f2-104">`EnumerateNativeCode` is not implemented in the current version of the .NET Framework.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e4f2-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="3e4f2-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateNativeCode (  
    [out] ICorDebugCodeEnum   **ppCodeEnum  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="3e4f2-106">Requisiti</span><span class="sxs-lookup"><span data-stu-id="3e4f2-106">Requirements</span></span>  
 <span data-ttu-id="3e4f2-107">**Intestazione:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3e4f2-107">**Header:** CorDebug.idl, CorDebug.h</span></span>
