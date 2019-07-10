---
title: Funzione CreateALink
ms.date: 03/30/2017
api_name:
- CreateALink
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- CreateALink
helpviewer_keywords:
- CreateALink function
- Alink API, CreateALink function
ms.assetid: fc73bcb9-6af6-44d8-bc39-2f4400325dae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 993848711f41c9e03b969a3c611982a5c8bc860d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742213"
---
# <a name="createalink-function"></a><span data-ttu-id="ed0b2-102">Funzione CreateALink</span><span class="sxs-lookup"><span data-stu-id="ed0b2-102">CreateALink Function</span></span>
<span data-ttu-id="ed0b2-103">Crea un'istanza dell'Assembly Linker e imposta un puntatore all'interfaccia specificata.</span><span class="sxs-lookup"><span data-stu-id="ed0b2-103">Creates an instance of the Assembly Linker and sets a pointer to the specified interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed0b2-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ed0b2-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed0b2-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="ed0b2-105">Parameters</span></span>  
  
|<span data-ttu-id="ed0b2-106">Parametro</span><span class="sxs-lookup"><span data-stu-id="ed0b2-106">Parameter</span></span>|<span data-ttu-id="ed0b2-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="ed0b2-107">Description</span></span>|  
|---------------|-----------------|  
|`riid`|<span data-ttu-id="ed0b2-108">Il nome fisico di una delle interfacce Assembly Linker.</span><span class="sxs-lookup"><span data-stu-id="ed0b2-108">The physical name of one of the Assembly Linker interfaces.</span></span>|  
|`ppInterface`|<span data-ttu-id="ed0b2-109">Il percorso che, al termine dell'esecuzione, contiene un puntatore al `riid` interfaccia.</span><span class="sxs-lookup"><span data-stu-id="ed0b2-109">The location that on successful completion contains a pointer to the `riid` interface.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ed0b2-110">Requisiti</span><span class="sxs-lookup"><span data-stu-id="ed0b2-110">Requirements</span></span>  
 <span data-ttu-id="ed0b2-111">**Libreria**: ALink. dll</span><span class="sxs-lookup"><span data-stu-id="ed0b2-111">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed0b2-112">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ed0b2-112">See also</span></span>

- [<span data-ttu-id="ed0b2-113">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="ed0b2-113">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
