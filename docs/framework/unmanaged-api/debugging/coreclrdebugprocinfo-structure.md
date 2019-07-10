---
title: Struttura CoreClrDebugProcInfo
ms.date: 03/30/2017
api_name:
- CoreClrDebugProcInfo
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CoreClrDebugProcInfo
helpviewer_keywords:
- remote debugging API [Silverlight]
- CoreClrDebugProcInfo structure
- Silverlight, remote debugging
ms.assetid: 4ddc37da-5c94-4beb-b61c-b54071c0e749
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 21fc34add4038d25d60e4728847e0d84914a14e3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739423"
---
# <a name="coreclrdebugprocinfo-structure"></a><span data-ttu-id="73ba8-102">Struttura CoreClrDebugProcInfo</span><span class="sxs-lookup"><span data-stu-id="73ba8-102">CoreClrDebugProcInfo Structure</span></span>
<span data-ttu-id="73ba8-103">Rappresenta un processo in esecuzione in un computer remoto.</span><span class="sxs-lookup"><span data-stu-id="73ba8-103">Represents a process that is running on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73ba8-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="73ba8-104">Syntax</span></span>  
  
```cpp  
struct  CoreClrDebugProcInfo {  
    DWORD m_dwPID;  
    DWORD m_dwInternalID;  
    WCHAR m_wszName[256];  
};  
```  
  
## <a name="members"></a><span data-ttu-id="73ba8-105">Membri</span><span class="sxs-lookup"><span data-stu-id="73ba8-105">Members</span></span>  
  
|<span data-ttu-id="73ba8-106">Member</span><span class="sxs-lookup"><span data-stu-id="73ba8-106">Member</span></span>|<span data-ttu-id="73ba8-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="73ba8-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwPID`|<span data-ttu-id="73ba8-108">Identificatore di processo assegnato dal sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="73ba8-108">OS-assigned process identifier.</span></span>|  
|`m_dwInternalID`|<span data-ttu-id="73ba8-109">Identificatore di processo assegnato dal proxy di debug remoto in esecuzione sul computer di destinazione.</span><span class="sxs-lookup"><span data-stu-id="73ba8-109">Process identifier that is assigned by the remote debugging proxy running on the target machine.</span></span> <span data-ttu-id="73ba8-110">Questo identificatore esegue il riciclo meno frequentemente rispetto all'identificatore del sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="73ba8-110">This identifier recycles less often than the OS identifier.</span></span>|  
|`m_wszName`|<span data-ttu-id="73ba8-111">Riga di comando del processo.</span><span class="sxs-lookup"><span data-stu-id="73ba8-111">Command-line of the process.</span></span> <span data-ttu-id="73ba8-112">Questo membro può essere troncato.</span><span class="sxs-lookup"><span data-stu-id="73ba8-112">This member may be truncated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="73ba8-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="73ba8-113">Requirements</span></span>  
 <span data-ttu-id="73ba8-114">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73ba8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73ba8-115">**Intestazione:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="73ba8-115">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="73ba8-116">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="73ba8-116">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="73ba8-117">**Versioni di .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="73ba8-117">**.NET Framework Versions:** 3.5 SP1</span></span>
