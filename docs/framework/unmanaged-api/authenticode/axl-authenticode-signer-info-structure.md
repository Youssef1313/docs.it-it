---
title: Struttura AXL_AUTHENTICODE_SIGNER_INFO
ms.date: 03/30/2017
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9aaa0258b53b6b39874c8c99c71ecf53cbdb8f97
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787074"
---
# <a name="axl_authenticode_signer_info-structure"></a><span data-ttu-id="66441-102">Struttura AXL_AUTHENTICODE_SIGNER_INFO</span><span class="sxs-lookup"><span data-stu-id="66441-102">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>
<span data-ttu-id="66441-103">Definisce le informazioni su chi ha apposto la firma Authenticode.</span><span class="sxs-lookup"><span data-stu-id="66441-103">Defines the Authenticode signer information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66441-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="66441-104">Syntax</span></span>  
  
```cpp  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    LPCWSTR pwszHash  
    LPCWSTR pwszDescription;  
    LPCWSTR pwszDescriptionUrl;  
    PCCERT_CHAIN_CONTEXT pChainContext  
} AXL_AUTHENTICODE_SIGNER_INFO, * PAXL_AUTHENTICODE_SIGNER_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="66441-105">Members</span><span class="sxs-lookup"><span data-stu-id="66441-105">Members</span></span>  
  
|<span data-ttu-id="66441-106">Member</span><span class="sxs-lookup"><span data-stu-id="66441-106">Member</span></span>|<span data-ttu-id="66441-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="66441-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="66441-108">Dimensione della struttura.</span><span class="sxs-lookup"><span data-stu-id="66441-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="66441-109">Codice di errore.</span><span class="sxs-lookup"><span data-stu-id="66441-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="66441-110">Algoritmo hash.</span><span class="sxs-lookup"><span data-stu-id="66441-110">The hash algorithm.</span></span>|  
|`pwszHash`|<span data-ttu-id="66441-111">Hash.</span><span class="sxs-lookup"><span data-stu-id="66441-111">The hash.</span></span>|  
|`pwszDescription`|<span data-ttu-id="66441-112">Descrizione.</span><span class="sxs-lookup"><span data-stu-id="66441-112">The description.</span></span>|  
|`pwszDescriptionUrl`|<span data-ttu-id="66441-113">URL della descrizione.</span><span class="sxs-lookup"><span data-stu-id="66441-113">The URL of the description.</span></span>|  
|`pChainContext`|<span data-ttu-id="66441-114">Contesto della catena del firmatario.</span><span class="sxs-lookup"><span data-stu-id="66441-114">The chain context of the signer.</span></span> <span data-ttu-id="66441-115">Vedere la struttura [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) .</span><span class="sxs-lookup"><span data-stu-id="66441-115">See the [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="66441-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="66441-116">See also</span></span>

- [<span data-ttu-id="66441-117">Authenticode</span><span class="sxs-lookup"><span data-stu-id="66441-117">Authenticode</span></span>](index.md)
