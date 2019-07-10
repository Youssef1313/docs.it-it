---
title: Metodo ICLRStrongName::GetHashFromFile
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromFile method [.NET Framework hosting]
- GetHashFromFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 9e50480a-8ada-4044-b2a5-97bb14ed3525
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 87cdf61cfcd0aee661edf9e7d0c053c858f9d854
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748177"
---
# <a name="iclrstrongnamegethashfromfile-method"></a><span data-ttu-id="d6c64-102">Metodo ICLRStrongName::GetHashFromFile</span><span class="sxs-lookup"><span data-stu-id="d6c64-102">ICLRStrongName::GetHashFromFile Method</span></span>
<span data-ttu-id="d6c64-103">Genera un hash basato sul contenuto del file specificato.</span><span class="sxs-lookup"><span data-stu-id="d6c64-103">Generates a hash over the contents of the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6c64-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d6c64-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6c64-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="d6c64-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="d6c64-106">[in] Il nome del file da hash.</span><span class="sxs-lookup"><span data-stu-id="d6c64-106">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="d6c64-107">[in, out] L'algoritmo da utilizzare durante la generazione di hash.</span><span class="sxs-lookup"><span data-stu-id="d6c64-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="d6c64-108">Gli algoritmi validi sono quelli definiti per la funzione CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="d6c64-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="d6c64-109">Se `piHashAlg` è impostato su 0, l'algoritmo predefinito viene utilizzato CALG_SHA-1.</span><span class="sxs-lookup"><span data-stu-id="d6c64-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="d6c64-110">[out] Matrice di byte contenente il valore hash generato.</span><span class="sxs-lookup"><span data-stu-id="d6c64-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="d6c64-111">[in] Le dimensioni massime del buffer che `pbHash` punta a.</span><span class="sxs-lookup"><span data-stu-id="d6c64-111">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="d6c64-112">[out] Le dimensioni, in byte, del valore restituito `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="d6c64-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6c64-113">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="d6c64-113">Return Value</span></span>  
 <span data-ttu-id="d6c64-114">`S_OK` Se il metodo è stata completata correttamente. in caso contrario, un valore HRESULT indicante un errore (vedere [valori HRESULT comuni](https://go.microsoft.com/fwlink/?LinkId=213878) per un elenco).</span><span class="sxs-lookup"><span data-stu-id="d6c64-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6c64-115">Note</span><span class="sxs-lookup"><span data-stu-id="d6c64-115">Remarks</span></span>  
 <span data-ttu-id="d6c64-116">Questo metodo è quello utilizzato per il [GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) metodo, ad eccezione del fatto che il nome del file specifica è ANSI invece di Unicode.</span><span class="sxs-lookup"><span data-stu-id="d6c64-116">This method is the same as the [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) method, except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6c64-117">Requisiti</span><span class="sxs-lookup"><span data-stu-id="d6c64-117">Requirements</span></span>  
 <span data-ttu-id="d6c64-118">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6c64-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6c64-119">**Intestazione:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="d6c64-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d6c64-120">**Libreria:** Inclusa come risorsa in Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="d6c64-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d6c64-121">**Versioni di .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6c64-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6c64-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d6c64-122">See also</span></span>

- [<span data-ttu-id="d6c64-123">Metodo GetHashFromFileW</span><span class="sxs-lookup"><span data-stu-id="d6c64-123">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="d6c64-124">Interfaccia ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="d6c64-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
