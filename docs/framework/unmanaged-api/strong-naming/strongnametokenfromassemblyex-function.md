---
title: Funzione StrongNameTokenFromAssemblyEx
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromAssemblyEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx function [.NET Framework strong naming]
ms.assetid: 67a8a9f2-dee3-44b2-a1c0-f307a3bdf90f
topic_type:
- apiref
ms.openlocfilehash: 8b7866b92be3195b0a767a823a0d7fb1c0aa4918
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73104240"
---
# <a name="strongnametokenfromassemblyex-function"></a><span data-ttu-id="b635e-102">Funzione StrongNameTokenFromAssemblyEx</span><span class="sxs-lookup"><span data-stu-id="b635e-102">StrongNameTokenFromAssemblyEx Function</span></span>
<span data-ttu-id="b635e-103">Crea un token con nome sicuro dal file di assembly specificato e restituisce la chiave pubblica rappresentata dal token.</span><span class="sxs-lookup"><span data-stu-id="b635e-103">Creates a strong name token from the specified assembly file, and returns the public key that the token represents.</span></span>  
  
 <span data-ttu-id="b635e-104">Questa funzione è stata deprecata.</span><span class="sxs-lookup"><span data-stu-id="b635e-104">This function has been deprecated.</span></span> <span data-ttu-id="b635e-105">Usare invece il metodo [ICLRStrongName:: StrongNameTokenFromAssemblyEx](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b635e-105">Use the [ICLRStrongName::StrongNameTokenFromAssemblyEx](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b635e-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="b635e-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b635e-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="b635e-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="b635e-108">in Percorso del file eseguibile di tipo PE per l'assembly.</span><span class="sxs-lookup"><span data-stu-id="b635e-108">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="b635e-109">out Token del nome sicuro restituito.</span><span class="sxs-lookup"><span data-stu-id="b635e-109">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="b635e-110">out Dimensione, in byte, del token del nome sicuro.</span><span class="sxs-lookup"><span data-stu-id="b635e-110">[out] The size, in bytes, of the strong name token.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="b635e-111">out Chiave pubblica restituita.</span><span class="sxs-lookup"><span data-stu-id="b635e-111">[out] The returned public key.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="b635e-112">out Dimensione, in byte, della chiave pubblica.</span><span class="sxs-lookup"><span data-stu-id="b635e-112">[out] The size, in bytes, of the public key.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b635e-113">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="b635e-113">Return Value</span></span>  
 <span data-ttu-id="b635e-114">`true` al completamento; in caso contrario, `false`.</span><span class="sxs-lookup"><span data-stu-id="b635e-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b635e-115">Note</span><span class="sxs-lookup"><span data-stu-id="b635e-115">Remarks</span></span>  
 <span data-ttu-id="b635e-116">Un token di nome sicuro è il formato abbreviato di una chiave pubblica.</span><span class="sxs-lookup"><span data-stu-id="b635e-116">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="b635e-117">Il token è un hash a 64 bit creato dalla chiave pubblica usata per firmare l'assembly.</span><span class="sxs-lookup"><span data-stu-id="b635e-117">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="b635e-118">Il token fa parte del nome sicuro dell'assembly e può essere letto dai metadati dell'assembly.</span><span class="sxs-lookup"><span data-stu-id="b635e-118">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="b635e-119">Dopo che la chiave è stata recuperata e il token è stato creato, è necessario chiamare la funzione [StrongNameFreeBuffer](strongnamefreebuffer-function.md) per rilasciare la memoria allocata.</span><span class="sxs-lookup"><span data-stu-id="b635e-119">After the key is retrieved and the token is created, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="b635e-120">Se la funzione `StrongNameTokenFromAssemblyEx` non viene completata correttamente, chiamare la funzione [StrongNameErrorInfo](strongnameerrorinfo-function.md) per recuperare l'ultimo errore generato.</span><span class="sxs-lookup"><span data-stu-id="b635e-120">If the `StrongNameTokenFromAssemblyEx` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b635e-121">Requisiti</span><span class="sxs-lookup"><span data-stu-id="b635e-121">Requirements</span></span>  
 <span data-ttu-id="b635e-122">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b635e-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b635e-123">**Intestazione:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="b635e-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="b635e-124">**Libreria:** Incluso come risorsa in mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="b635e-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="b635e-125">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b635e-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b635e-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b635e-126">See also</span></span>

- [<span data-ttu-id="b635e-127">Metodo StrongNameTokenFromAssemblyEx</span><span class="sxs-lookup"><span data-stu-id="b635e-127">StrongNameTokenFromAssemblyEx Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="b635e-128">Metodo StrongNameTokenFromAssembly</span><span class="sxs-lookup"><span data-stu-id="b635e-128">StrongNameTokenFromAssembly Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="b635e-129">Interfaccia ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="b635e-129">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
