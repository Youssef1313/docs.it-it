---
title: Funzione CreateInstallReferenceEnum
ms.date: 03/30/2017
api_name:
- CreateInstallReferenceEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateInstallReference
helpviewer_keywords:
- CreateInstallReference function [.NET Framework fusion]
ms.assetid: 80dbbbf8-54fc-4894-b74a-0179d3201083
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d696326ff8861ed8496474f76e9eaf89b4ead3e8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795396"
---
# <a name="createinstallreferenceenum-function"></a><span data-ttu-id="a9ef2-102">Funzione CreateInstallReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="a9ef2-102">CreateInstallReferenceEnum Function</span></span>
<span data-ttu-id="a9ef2-103">Ottiene un puntatore a un'istanza di [IInstallReferenceEnum](iinstallreferenceenum-interface.md) che rappresenta un elenco di riferimenti di un'applicazione all'assembly specificato.</span><span class="sxs-lookup"><span data-stu-id="a9ef2-103">Gets a pointer to an [IInstallReferenceEnum](iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9ef2-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="a9ef2-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateInstallReferenceEnum (  
    [out] IInstallReferenceEnum **ppRefEnum,  
    [in]  IAssemblyName         *pName,  
    [in]  DWORD                 dwFlags,  
    [in]  LPVOID                pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9ef2-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="a9ef2-105">Parameters</span></span>  
 `ppRefEnum`  
 <span data-ttu-id="a9ef2-106">out Puntatore restituito `IInstallReferenceEnum` .</span><span class="sxs-lookup"><span data-stu-id="a9ef2-106">[out] The returned `IInstallReferenceEnum` pointer.</span></span>  
  
 `pName`  
 <span data-ttu-id="a9ef2-107">in [IAssemblyName](iassemblyname-interface.md) che identifica l'assembly per il quale enumerare i riferimenti.</span><span class="sxs-lookup"><span data-stu-id="a9ef2-107">[in] The [IAssemblyName](iassemblyname-interface.md) that identifies the assembly for which to enumerate references.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="a9ef2-108">in Flag che influenzano il comportamento dell'enumeratore.</span><span class="sxs-lookup"><span data-stu-id="a9ef2-108">[in] Flags that influence the enumerator's behavior.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="a9ef2-109">in Riservato per l'estendibilità futura.</span><span class="sxs-lookup"><span data-stu-id="a9ef2-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="a9ef2-110">`pvReserved`deve essere un riferimento null.</span><span class="sxs-lookup"><span data-stu-id="a9ef2-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9ef2-111">Requisiti</span><span class="sxs-lookup"><span data-stu-id="a9ef2-111">Requirements</span></span>  
 <span data-ttu-id="a9ef2-112">**Piattaforme** Vedere [Requisiti di sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9ef2-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9ef2-113">**Intestazione:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="a9ef2-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="a9ef2-114">**Libreria** Fusion. dll e mscorwks. dll.</span><span class="sxs-lookup"><span data-stu-id="a9ef2-114">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="a9ef2-115">Usare Fusion. dll invece di mscorwks. dll per assicurarsi di avere come destinazione la versione corretta del .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a9ef2-115">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="a9ef2-116">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9ef2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9ef2-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a9ef2-117">See also</span></span>

- [<span data-ttu-id="a9ef2-118">Interfaccia IInstallReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="a9ef2-118">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)
- [<span data-ttu-id="a9ef2-119">Interfaccia IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="a9ef2-119">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="a9ef2-120">Funzioni statiche globali Fusion</span><span class="sxs-lookup"><span data-stu-id="a9ef2-120">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
