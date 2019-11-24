---
title: Interfaccia ISymUnmanagedDocument
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument
helpviewer_keywords:
- ISymUnmanagedDocument interface [.NET Framework debugging]
ms.assetid: 5c26b366-6e81-467c-9dd0-02dd26fee0a3
topic_type:
- apiref
ms.openlocfilehash: 3fa7b6b19d81e374cdb09b07ec181a7f4249a5eb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449102"
---
# <a name="isymunmanageddocument-interface"></a><span data-ttu-id="33c4f-102">Interfaccia ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="33c4f-102">ISymUnmanagedDocument Interface</span></span>
<span data-ttu-id="33c4f-103">Rappresenta un documento al quale fa riferimento un archivio di simboli.</span><span class="sxs-lookup"><span data-stu-id="33c4f-103">Represents a document referenced by a symbol store.</span></span> <span data-ttu-id="33c4f-104">A document is defined by a uniform resource locator (URL) and a document type GUID.</span><span class="sxs-lookup"><span data-stu-id="33c4f-104">A document is defined by a uniform resource locator (URL) and a document type GUID.</span></span> <span data-ttu-id="33c4f-105">You can locate the document regardless of how it is stored by using the URL and document type GUID.</span><span class="sxs-lookup"><span data-stu-id="33c4f-105">You can locate the document regardless of how it is stored by using the URL and document type GUID.</span></span> <span data-ttu-id="33c4f-106">You can store the document source in the symbol store and retrieve it through this interface.</span><span class="sxs-lookup"><span data-stu-id="33c4f-106">You can store the document source in the symbol store and retrieve it through this interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="33c4f-107">Metodi</span><span class="sxs-lookup"><span data-stu-id="33c4f-107">Methods</span></span>  
  
|<span data-ttu-id="33c4f-108">Metodo</span><span class="sxs-lookup"><span data-stu-id="33c4f-108">Method</span></span>|<span data-ttu-id="33c4f-109">Descrizione</span><span class="sxs-lookup"><span data-stu-id="33c4f-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="33c4f-110">Metodo FindClosestLine</span><span class="sxs-lookup"><span data-stu-id="33c4f-110">FindClosestLine Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-findclosestline-method.md)|<span data-ttu-id="33c4f-111">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span><span class="sxs-lookup"><span data-stu-id="33c4f-111">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>|  
|[<span data-ttu-id="33c4f-112">Metodo GetCheckSum</span><span class="sxs-lookup"><span data-stu-id="33c4f-112">GetCheckSum Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksum-method.md)|<span data-ttu-id="33c4f-113">Ottiene il checksum.</span><span class="sxs-lookup"><span data-stu-id="33c4f-113">Gets the checksum.</span></span>|  
|[<span data-ttu-id="33c4f-114">Metodo GetCheckSumAlgorithmId</span><span class="sxs-lookup"><span data-stu-id="33c4f-114">GetCheckSumAlgorithmId Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksumalgorithmid-method.md)|<span data-ttu-id="33c4f-115">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span><span class="sxs-lookup"><span data-stu-id="33c4f-115">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>|  
|[<span data-ttu-id="33c4f-116">Metodo GetDocumentType</span><span class="sxs-lookup"><span data-stu-id="33c4f-116">GetDocumentType Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getdocumenttype-method.md)|<span data-ttu-id="33c4f-117">Gets the document type of this document.</span><span class="sxs-lookup"><span data-stu-id="33c4f-117">Gets the document type of this document.</span></span>|  
|[<span data-ttu-id="33c4f-118">Metodo GetLanguage</span><span class="sxs-lookup"><span data-stu-id="33c4f-118">GetLanguage Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguage-method.md)|<span data-ttu-id="33c4f-119">Gets the language identifier of this document.</span><span class="sxs-lookup"><span data-stu-id="33c4f-119">Gets the language identifier of this document.</span></span>|  
|[<span data-ttu-id="33c4f-120">Metodo GetLanguageVendor</span><span class="sxs-lookup"><span data-stu-id="33c4f-120">GetLanguageVendor Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguagevendor-method.md)|<span data-ttu-id="33c4f-121">Gets the language vendor of this document.</span><span class="sxs-lookup"><span data-stu-id="33c4f-121">Gets the language vendor of this document.</span></span>|  
|[<span data-ttu-id="33c4f-122">Metodo GetSourceLength</span><span class="sxs-lookup"><span data-stu-id="33c4f-122">GetSourceLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcelength-method.md)|<span data-ttu-id="33c4f-123">Recupera la lunghezza, in byte, dell'origine incorporata.</span><span class="sxs-lookup"><span data-stu-id="33c4f-123">Gets the length, in bytes, of the embedded source.</span></span>|  
|[<span data-ttu-id="33c4f-124">Metodo GetSourceRange</span><span class="sxs-lookup"><span data-stu-id="33c4f-124">GetSourceRange Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcerange-method.md)|<span data-ttu-id="33c4f-125">Returns the specified range of the embedded source into the given buffer.</span><span class="sxs-lookup"><span data-stu-id="33c4f-125">Returns the specified range of the embedded source into the given buffer.</span></span>|  
|[<span data-ttu-id="33c4f-126">Metodo GetURL</span><span class="sxs-lookup"><span data-stu-id="33c4f-126">GetURL Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-geturl-method.md)|<span data-ttu-id="33c4f-127">Returns the URL for this document.</span><span class="sxs-lookup"><span data-stu-id="33c4f-127">Returns the URL for this document.</span></span>|  
|[<span data-ttu-id="33c4f-128">Metodo HasEmbeddedSource</span><span class="sxs-lookup"><span data-stu-id="33c4f-128">HasEmbeddedSource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-hasembeddedsource-method.md)|<span data-ttu-id="33c4f-129">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span><span class="sxs-lookup"><span data-stu-id="33c4f-129">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="33c4f-130">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="33c4f-130">See also</span></span>

- [<span data-ttu-id="33c4f-131">Interfacce dell'archivio simboli di diagnostica</span><span class="sxs-lookup"><span data-stu-id="33c4f-131">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
