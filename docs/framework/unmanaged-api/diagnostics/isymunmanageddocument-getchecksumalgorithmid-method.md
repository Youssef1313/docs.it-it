---
title: Metodo ISymUnmanagedDocument::GetCheckSumAlgorithmId
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetCheckSumAlgorithmId
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetCheckSumAlgorithmId
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSumAlgorithmId method [.NET Framework debugging]
- GetCheckSumAlgorithmId method [.NET Framework debugging]
ms.assetid: c7f941cd-e25b-4b85-b1ce-5f77c9208fa9
topic_type:
- apiref
ms.openlocfilehash: 2bc673d2e331cd32d5317cb20f9418eb3a3b144a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431071"
---
# <a name="isymunmanageddocumentgetchecksumalgorithmid-method"></a><span data-ttu-id="3093f-102">Metodo ISymUnmanagedDocument::GetCheckSumAlgorithmId</span><span class="sxs-lookup"><span data-stu-id="3093f-102">ISymUnmanagedDocument::GetCheckSumAlgorithmId Method</span></span>
<span data-ttu-id="3093f-103">Ottiene l'identificatore dell'algoritmo di checksum oppure restituisce un GUID di tutti gli zeri in assenza di checksum.</span><span class="sxs-lookup"><span data-stu-id="3093f-103">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3093f-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="3093f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCheckSumAlgorithmId(  
    [out, retval] GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3093f-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="3093f-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="3093f-106">out Puntatore a una variabile che riceve l'identificatore dell'algoritmo di checksum.</span><span class="sxs-lookup"><span data-stu-id="3093f-106">[out] A pointer to a variable that receives the checksum algorithm identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3093f-107">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="3093f-107">Return Value</span></span>  
 <span data-ttu-id="3093f-108">S_OK se il metodo ha esito positivo.</span><span class="sxs-lookup"><span data-stu-id="3093f-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3093f-109">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3093f-109">See also</span></span>

- [<span data-ttu-id="3093f-110">Interfaccia ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="3093f-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
