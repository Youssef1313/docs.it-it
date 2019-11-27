---
title: Interfaccia ISymUnmanagedSymbolSearchInfo
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo
helpviewer_keywords:
- ISymUnmanagedSymbolSearchInfo interface [.NET Framework debugging]
ms.assetid: 30817373-0a21-49c1-a0c4-8e8daeecb8db
topic_type:
- apiref
ms.openlocfilehash: d7371361b074454e8aa359c49b964193c12f3034
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446142"
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a><span data-ttu-id="1ce3f-102">Interfaccia ISymUnmanagedSymbolSearchInfo</span><span class="sxs-lookup"><span data-stu-id="1ce3f-102">ISymUnmanagedSymbolSearchInfo Interface</span></span>
<span data-ttu-id="1ce3f-103">Fornisce metodi che consentono di ottenere informazioni sul percorso di ricerca.</span><span class="sxs-lookup"><span data-stu-id="1ce3f-103">Provides methods that get information about the search path.</span></span> <span data-ttu-id="1ce3f-104">Ottenere questa interfaccia chiamando `QueryInterface` su un oggetto che implementa l'interfaccia [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="1ce3f-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1ce3f-105">Metodi</span><span class="sxs-lookup"><span data-stu-id="1ce3f-105">Methods</span></span>  
  
|<span data-ttu-id="1ce3f-106">Metodo</span><span class="sxs-lookup"><span data-stu-id="1ce3f-106">Method</span></span>|<span data-ttu-id="1ce3f-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="1ce3f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1ce3f-108">Metodo GetHRESULT</span><span class="sxs-lookup"><span data-stu-id="1ce3f-108">GetHRESULT Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-gethresult-method.md)|<span data-ttu-id="1ce3f-109">Ottiene HRESULT.</span><span class="sxs-lookup"><span data-stu-id="1ce3f-109">Gets the HRESULT.</span></span>|  
|[<span data-ttu-id="1ce3f-110">Metodo GetSearchPath</span><span class="sxs-lookup"><span data-stu-id="1ce3f-110">GetSearchPath Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|<span data-ttu-id="1ce3f-111">Ottiene il percorso di ricerca.</span><span class="sxs-lookup"><span data-stu-id="1ce3f-111">Gets the search path.</span></span>|  
|[<span data-ttu-id="1ce3f-112">Metodo GetSearchPathLength</span><span class="sxs-lookup"><span data-stu-id="1ce3f-112">GetSearchPathLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|<span data-ttu-id="1ce3f-113">Ottiene la lunghezza del percorso di ricerca.</span><span class="sxs-lookup"><span data-stu-id="1ce3f-113">Gets the search path length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1ce3f-114">Requisiti</span><span class="sxs-lookup"><span data-stu-id="1ce3f-114">Requirements</span></span>  
 <span data-ttu-id="1ce3f-115">**Intestazione:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="1ce3f-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ce3f-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1ce3f-116">See also</span></span>

- [<span data-ttu-id="1ce3f-117">Interfacce dell'archivio simboli di diagnostica</span><span class="sxs-lookup"><span data-stu-id="1ce3f-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
