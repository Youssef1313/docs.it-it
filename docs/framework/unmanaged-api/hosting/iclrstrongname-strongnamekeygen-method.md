---
title: Metodo ICLRStrongName::StrongNameKeyGen
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyGen method [.NET Framework hosting]
ms.assetid: ac5c1245-9acf-4271-9c08-3d9b7c670df3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c535d3d73b6d3d0165ea2d744ef625a16bd76cd4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747839"
---
# <a name="iclrstrongnamestrongnamekeygen-method"></a><span data-ttu-id="0f8fe-102">Metodo ICLRStrongName::StrongNameKeyGen</span><span class="sxs-lookup"><span data-stu-id="0f8fe-102">ICLRStrongName::StrongNameKeyGen Method</span></span>
<span data-ttu-id="0f8fe-103">Crea una nuova coppia di chiavi pubblica/privata per l'uso come nome sicuro.</span><span class="sxs-lookup"><span data-stu-id="0f8fe-103">Creates a new public/private key pair for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f8fe-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="0f8fe-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f8fe-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="0f8fe-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="0f8fe-106">[in] Il nome di contenitore di chiavi richiesto.</span><span class="sxs-lookup"><span data-stu-id="0f8fe-106">[in] The requested key container name.</span></span> <span data-ttu-id="0f8fe-107">`wszKeyContainer` deve essere una stringa non vuota o null per generare un nome temporaneo.</span><span class="sxs-lookup"><span data-stu-id="0f8fe-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="0f8fe-108">[in] Un valore che specifica se lasciare la chiave di registrazione.</span><span class="sxs-lookup"><span data-stu-id="0f8fe-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="0f8fe-109">Sono supportati i valori seguenti:</span><span class="sxs-lookup"><span data-stu-id="0f8fe-109">The following values are supported:</span></span>  
  
- <span data-ttu-id="0f8fe-110">0x00000000 - utilizzato quando `wszKeyContainer` è null per generare un nome di contenitore di chiavi temporanee.</span><span class="sxs-lookup"><span data-stu-id="0f8fe-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="0f8fe-111">0x00000001 (`SN_LEAVE_KEY`): Specifica che la chiave deve essere registrata a sinistra.</span><span class="sxs-lookup"><span data-stu-id="0f8fe-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="0f8fe-112">[out] La coppia di chiavi pubblica/privata restituita.</span><span class="sxs-lookup"><span data-stu-id="0f8fe-112">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="0f8fe-113">[out] Le dimensioni, in byte, di `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="0f8fe-113">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f8fe-114">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="0f8fe-114">Return Value</span></span>  
 <span data-ttu-id="0f8fe-115">`S_OK` Se il metodo è stata completata correttamente. in caso contrario, un valore HRESULT indicante un errore (vedere [valori HRESULT comuni](https://go.microsoft.com/fwlink/?LinkId=213878) per un elenco).</span><span class="sxs-lookup"><span data-stu-id="0f8fe-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f8fe-116">Note</span><span class="sxs-lookup"><span data-stu-id="0f8fe-116">Remarks</span></span>  
 <span data-ttu-id="0f8fe-117">Il [StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) metodo crea una chiave a 1024 bit.</span><span class="sxs-lookup"><span data-stu-id="0f8fe-117">The [ICLRStrongName::StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) method creates a 1024-bit key.</span></span> <span data-ttu-id="0f8fe-118">Una volta recuperata la chiave, è necessario chiamare il [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metodo per rilasciare la memoria allocata.</span><span class="sxs-lookup"><span data-stu-id="0f8fe-118">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f8fe-119">Requisiti</span><span class="sxs-lookup"><span data-stu-id="0f8fe-119">Requirements</span></span>  
 <span data-ttu-id="0f8fe-120">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f8fe-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f8fe-121">**Intestazione:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="0f8fe-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0f8fe-122">**Libreria:** Inclusa come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="0f8fe-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0f8fe-123">**Versioni di .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f8fe-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f8fe-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0f8fe-124">See also</span></span>

- [<span data-ttu-id="0f8fe-125">Metodo StrongNameKeyGenEx</span><span class="sxs-lookup"><span data-stu-id="0f8fe-125">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="0f8fe-126">Interfaccia ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="0f8fe-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
