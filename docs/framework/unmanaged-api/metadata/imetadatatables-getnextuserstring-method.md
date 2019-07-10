---
title: Metodo IMetaDataTables::GetNextUserString
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextUserString
helpviewer_keywords:
- GetNextUserString method [.NET Framework metadata]
- IMetaDataTables::GetNextUserString method [.NET Framework metadata]
ms.assetid: b7cb40ee-67b7-4f4e-8dcc-ee7ac8bc986b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c50740e59019edb44f6e8c2cee1b823fa047a039
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781431"
---
# <a name="imetadatatablesgetnextuserstring-method"></a><span data-ttu-id="a6603-102">Metodo IMetaDataTables::GetNextUserString</span><span class="sxs-lookup"><span data-stu-id="a6603-102">IMetaDataTables::GetNextUserString Method</span></span>
<span data-ttu-id="a6603-103">Ottiene l'indice della riga che contiene la stringa a livello di codice successiva nella colonna della tabella corrente.</span><span class="sxs-lookup"><span data-stu-id="a6603-103">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6603-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="a6603-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextUserString (  
    [in]  ULONG   ixUserString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6603-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="a6603-105">Parameters</span></span>  
 `ixUserString`  
 <span data-ttu-id="a6603-106">[in] Un valore di indice della colonna stringa corrente.</span><span class="sxs-lookup"><span data-stu-id="a6603-106">[in] An index value from the current string column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="a6603-107">[out] Puntatore all'indice di riga della stringa nella colonna successiva.</span><span class="sxs-lookup"><span data-stu-id="a6603-107">[out] A pointer to the row index of the next string in the column.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6603-108">Note</span><span class="sxs-lookup"><span data-stu-id="a6603-108">Remarks</span></span>  
 <span data-ttu-id="a6603-109">Non è consigliabile l'uso di questo metodo, perché non restituire risultati coerenti.</span><span class="sxs-lookup"><span data-stu-id="a6603-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="a6603-110">Per informazioni sulla tabella di GUID, vedere la documentazione di Common Language Infrastructure (CLI), in particolare "Partition II: Metadata Definition and Semantics".</span><span class="sxs-lookup"><span data-stu-id="a6603-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="a6603-111">La documentazione è disponibile online; vedere [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) (ECMA C# e standard di Common Language Infrastructure) in MSDN e [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) nel sito Web internazionale Ecma.</span><span class="sxs-lookup"><span data-stu-id="a6603-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6603-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="a6603-112">Requirements</span></span>  
 <span data-ttu-id="a6603-113">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6603-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6603-114">**Intestazione:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a6603-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a6603-115">**Libreria:** Usato come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="a6603-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a6603-116">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6603-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6603-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a6603-117">See also</span></span>

- [<span data-ttu-id="a6603-118">Interfaccia IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="a6603-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="a6603-119">Interfaccia IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="a6603-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
