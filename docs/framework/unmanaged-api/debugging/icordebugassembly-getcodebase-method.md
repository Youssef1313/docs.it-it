---
title: Metodo ICorDebugAssembly::GetCodeBase
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetCodeBase
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetCodeBase
helpviewer_keywords:
- GetCodeBase method [.NET Framework debugging]
- ICorDebugAssembly::GetCodeBase method [.NET Framework debugging]
ms.assetid: 48adc154-9058-4fef-9c43-e9aad80e4dbf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b08149b2acd766aac428614205401e79246c5b21
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737248"
---
# <a name="icordebugassemblygetcodebase-method"></a><span data-ttu-id="1a31a-102">Metodo ICorDebugAssembly::GetCodeBase</span><span class="sxs-lookup"><span data-stu-id="1a31a-102">ICorDebugAssembly::GetCodeBase Method</span></span>
<span data-ttu-id="1a31a-103">Questo metodo non è implementato nella versione corrente di .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1a31a-103">This method is not implemented in the current version of the .NET Framework.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a31a-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="1a31a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeBase (  
    [in] ULONG32  cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR szName[]  
);  
```
