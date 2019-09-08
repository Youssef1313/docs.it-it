---
title: _AxlRSAKeyValueToPublicKeyToken (funzione)
ms.date: 03/30/2017
api_name:
- _AxlRSAKeyValueToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d60f19fe-7bec-47ba-b60e-ba9ce66abf8c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 690035ffe0724d3987a198c78bf14e668527b98a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787029"
---
# <a name="_axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="93fd3-102">\_AxlRSAKeyValueToPublicKeyToken (funzione)</span><span class="sxs-lookup"><span data-stu-id="93fd3-102">\_AxlRSAKeyValueToPublicKeyToken function</span></span>

<span data-ttu-id="93fd3-103">Converte un elemento Modulus e un elemento Exponent in un token di chiave pubblica con nome sicuro.</span><span class="sxs-lookup"><span data-stu-id="93fd3-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93fd3-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="93fd3-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93fd3-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="93fd3-105">Parameters</span></span>  
 `pModulusBlob`  
 <span data-ttu-id="93fd3-106">in Il BLOB del modulo con codifica Base64 (dall' \<elemento modulo >).</span><span class="sxs-lookup"><span data-stu-id="93fd3-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="93fd3-107">Vedere la struttura [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="93fd3-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="93fd3-108">in BLOB dell'esponente con codifica Base64 (dall'elemento \<> dell'esponente).</span><span class="sxs-lookup"><span data-stu-id="93fd3-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="93fd3-109">Vedere la struttura [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="93fd3-109">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="93fd3-110">[out] Puntatore a WCHAR \* per ricevere il token di chiave pubblica con codifica esadecimale.</span><span class="sxs-lookup"><span data-stu-id="93fd3-110">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="93fd3-111">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="93fd3-111">Return Value</span></span>  
 <span data-ttu-id="93fd3-112">`S_OK` se la funzione ha esito positivo.</span><span class="sxs-lookup"><span data-stu-id="93fd3-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="93fd3-113">In caso contrario, verrà restituito un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="93fd3-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93fd3-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="93fd3-114">See also</span></span>

- [<span data-ttu-id="93fd3-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="93fd3-115">Authenticode</span></span>](index.md)
