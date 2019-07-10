---
title: Enumerazione EContextType
ms.date: 03/30/2017
api_name:
- EContextType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EContextType
helpviewer_keywords:
- EContextType enumeration [.NET Framework hosting]
ms.assetid: 92b926a9-b87e-408a-9036-df7b752c9492
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f93f36a78ff5579e131ef4bb3d48f04e806c14de
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779399"
---
# <a name="econtexttype-enumeration"></a><span data-ttu-id="c56f1-102">Enumerazione EContextType</span><span class="sxs-lookup"><span data-stu-id="c56f1-102">EContextType Enumeration</span></span>
<span data-ttu-id="c56f1-103">Descrive il contesto di sicurezza del thread attualmente in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="c56f1-103">Describes the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c56f1-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c56f1-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eCurrentContext    = 0x00,  
    eRestrictedContext = 0x01  
} EContextType;  
```  
  
## <a name="members"></a><span data-ttu-id="c56f1-105">Membri</span><span class="sxs-lookup"><span data-stu-id="c56f1-105">Members</span></span>  
  
|<span data-ttu-id="c56f1-106">Member</span><span class="sxs-lookup"><span data-stu-id="c56f1-106">Member</span></span>|<span data-ttu-id="c56f1-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="c56f1-107">Description</span></span>|  
|------------|-----------------|  
|`eCurrentContext`|<span data-ttu-id="c56f1-108">Indica il contesto sul thread corrente in fase di common language runtime (CLR) chiama il [IHostSecurityManager](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) metodo o il contesto di richiesta da parte di CLR in una chiamata al [ IHostSecurityManager:: SetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md) (metodo).</span><span class="sxs-lookup"><span data-stu-id="c56f1-108">Indicates the context on the current thread at the time the common language runtime (CLR) calls the [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) method, or the context requested by the CLR in a call to the [IHostSecurityManager::SetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md) method.</span></span>|  
|`eRestrictedContext`|<span data-ttu-id="c56f1-109">Indica un contesto in cui l'host dispone di privilegi più bassi, ad esempio il garbage collector, o i costruttori di classe o modulo.</span><span class="sxs-lookup"><span data-stu-id="c56f1-109">Indicates a context over which the host has lower privileges, such as the garbage collector, or class or module constructors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c56f1-110">Note</span><span class="sxs-lookup"><span data-stu-id="c56f1-110">Remarks</span></span>  
 <span data-ttu-id="c56f1-111">CLR fornisce uno dei `EContextType` i valori come un valore di parametro nelle chiamate al `IHostSecurityManager::GetSecurityContext` e `IHostSecurityManager::SetSecurityContext` metodi.</span><span class="sxs-lookup"><span data-stu-id="c56f1-111">The CLR supplies one of the `EContextType` values as a parameter value in calls to the `IHostSecurityManager::GetSecurityContext` and `IHostSecurityManager::SetSecurityContext` methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c56f1-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="c56f1-112">Requirements</span></span>  
 <span data-ttu-id="c56f1-113">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c56f1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c56f1-114">**Intestazione:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c56f1-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c56f1-115">**Libreria:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c56f1-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c56f1-116">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c56f1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c56f1-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c56f1-117">See also</span></span>

- [<span data-ttu-id="c56f1-118">Interfaccia IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="c56f1-118">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="c56f1-119">Interfaccia IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="c56f1-119">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="c56f1-120">Enumerazioni di hosting</span><span class="sxs-lookup"><span data-stu-id="c56f1-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
