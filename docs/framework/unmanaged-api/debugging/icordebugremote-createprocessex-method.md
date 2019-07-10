---
title: Metodo ICorDebugRemote::CreateProcessEx
ms.date: 03/30/2017
api_name:
- ICorDebugRemote.CreateProcessEx
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::CreateProcessEx
helpviewer_keywords:
- CreateProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
- ICorDebugRemote::CreateProcessEx method [.NET Framework debugging]
ms.assetid: 41af93c7-e448-4251-8d4d-413d38c635f2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d05384af8201fae8cf81650d38c99a5c44e6bd16
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744781"
---
# <a name="icordebugremotecreateprocessex-method"></a><span data-ttu-id="74a09-102">Metodo ICorDebugRemote::CreateProcessEx</span><span class="sxs-lookup"><span data-stu-id="74a09-102">ICorDebugRemote::CreateProcessEx Method</span></span>
<span data-ttu-id="74a09-103">Avvia un processo in un computer remoto all'interno del debugger.</span><span class="sxs-lookup"><span data-stu-id="74a09-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74a09-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="74a09-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateProcessEx (  
    [in]  ICorDebugRemoteTarget*      pRemoteTarget,  
    [in]  LPCWSTR                     lpApplicationName,  
    [in]  LPWSTR                      lpCommandLine,  
    [in]  LPSECURITY_ATTRIBUTES       lpProcessAttributes,  
    [in]  LPSECURITY_ATTRIBUTES       lpThreadAttributes,  
    [in]  BOOL                        bInheritHandles,  
    [in]  DWORD                       dwCreationFlags,  
    [in]  PVOID                       lpEnvironment,  
    [in]  LPCWSTR                     lpCurrentDirectory,  
    [in]  LPSTARTUPINFOW              lpStartupInfo,  
    [in]  LPPROCESS_INFORMATION       lpProcessInformation,  
    [in]  CorDebugCreateProcessFlags  debuggingFlags,  
    [out] ICorDebugProcess**          ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74a09-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="74a09-105">Parameters</span></span>  
 `pRemoteTarget`  
 <span data-ttu-id="74a09-106">[in] Puntatore a un [interfaccia ICorDebugRemoteTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span><span class="sxs-lookup"><span data-stu-id="74a09-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="74a09-107">Utilizzato per determinare il computer remoto in cui verrà avviato il processo.</span><span class="sxs-lookup"><span data-stu-id="74a09-107">Used to determine the remote machine on which the process will be launched.</span></span>  
  
 `lpApplicationName`  
 <span data-ttu-id="74a09-108">[in] Puntatore a una stringa con terminazione null che specifica il modulo deve essere eseguito dal processo avviato.</span><span class="sxs-lookup"><span data-stu-id="74a09-108">[in] Pointer to a null-terminated string that specifies the module to be executed by the launched process.</span></span> <span data-ttu-id="74a09-109">Il modulo viene eseguito nel contesto di sicurezza del processo chiamante.</span><span class="sxs-lookup"><span data-stu-id="74a09-109">The module is executed in the security context of the calling process.</span></span>  
  
 `lpCommandLine`  
 <span data-ttu-id="74a09-110">[in] Puntatore a una stringa con terminazione null che specifica la riga di comando deve essere eseguito dal processo avviato.</span><span class="sxs-lookup"><span data-stu-id="74a09-110">[in] Pointer to a null-terminated string that specifies the command line to be executed by the launched process.</span></span>  
  
 `lpProcessAttributes`  
 <span data-ttu-id="74a09-111">[in] Non utilizzato per il debug remoto.</span><span class="sxs-lookup"><span data-stu-id="74a09-111">[in] Unused for remote debugging.</span></span>  
  
 `lpThreadAttributes`  
 <span data-ttu-id="74a09-112">[in] Non utilizzato per il debug remoto.</span><span class="sxs-lookup"><span data-stu-id="74a09-112">[in] Unused for remote debugging.</span></span>  
  
 `bInheritHandles`  
 <span data-ttu-id="74a09-113">[in] Non utilizzato per il debug remoto.</span><span class="sxs-lookup"><span data-stu-id="74a09-113">[in] Unused for remote debugging.</span></span>  
  
 `dwCreationFlags`  
 <span data-ttu-id="74a09-114">[in] Non utilizzato per il debug remoto.</span><span class="sxs-lookup"><span data-stu-id="74a09-114">[in] Unused for remote debugging.</span></span>  
  
 `lpEnvironment`  
 <span data-ttu-id="74a09-115">[in] Puntatore a un blocco di ambiente per il nuovo processo.</span><span class="sxs-lookup"><span data-stu-id="74a09-115">[in] Pointer to an environment block for the new process.</span></span>  
  
 `lpCurrentDirectory`  
 <span data-ttu-id="74a09-116">[in] Puntatore a una stringa con terminazione null che specifica il percorso completo per directory corrente per il processo.</span><span class="sxs-lookup"><span data-stu-id="74a09-116">[in] Pointer to a null-terminated string that specifies the full path to the current directory for the process.</span></span> <span data-ttu-id="74a09-117">Se questo parametro è null, il nuovo processo avrà la stessa unità e directory corrente del processo chiamante.</span><span class="sxs-lookup"><span data-stu-id="74a09-117">If this parameter is null, the new process will have the same current drive and directory as the calling process.</span></span>  
  
 `lpStartupInfo`  
 <span data-ttu-id="74a09-118">[in] Non utilizzato per il debug remoto.</span><span class="sxs-lookup"><span data-stu-id="74a09-118">[in] Unused for remote debugging.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="74a09-119">[in] Non utilizzato per il debug remoto.</span><span class="sxs-lookup"><span data-stu-id="74a09-119">[in] Unused for remote debugging.</span></span>  
  
 `debuggingFlags`  
 <span data-ttu-id="74a09-120">[in] Non utilizzato per il debug remoto.</span><span class="sxs-lookup"><span data-stu-id="74a09-120">[in] Unused for remote debugging.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="74a09-121">[out] Un puntatore all'indirizzo di un oggetto "ICorDebugProcess (interfaccia)" che rappresenta il processo.</span><span class="sxs-lookup"><span data-stu-id="74a09-121">[out] A pointer to the address of a"ICorDebugProcess Interface" object that represents the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="74a09-122">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="74a09-122">Return Value</span></span>  
 <span data-ttu-id="74a09-123">S_OK</span><span class="sxs-lookup"><span data-stu-id="74a09-123">S_OK</span></span>  
 <span data-ttu-id="74a09-124">È stato avviato il processo nel computer remoto e restituita un' "interfaccia ICorDebugProcess" per il debug.</span><span class="sxs-lookup"><span data-stu-id="74a09-124">Successfully launched the process on the remote machine and returned an "ICorDebugProcess Interface" for debugging.</span></span>  
  
 <span data-ttu-id="74a09-125">E_FAIL (o altri codici E_ restituiti)</span><span class="sxs-lookup"><span data-stu-id="74a09-125">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="74a09-126">Impossibile avviare il processo nel computer remoto e restituire un' "interfaccia ICorDebugProcess" per il debug.</span><span class="sxs-lookup"><span data-stu-id="74a09-126">Unable to launch the process on the remote machine and return an "ICorDebugProcess Interface" for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74a09-127">Note</span><span class="sxs-lookup"><span data-stu-id="74a09-127">Remarks</span></span>  
 <span data-ttu-id="74a09-128">Debug in modalità mista non è supportato in Silverlight.</span><span class="sxs-lookup"><span data-stu-id="74a09-128">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74a09-129">Requisiti</span><span class="sxs-lookup"><span data-stu-id="74a09-129">Requirements</span></span>  
 <span data-ttu-id="74a09-130">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74a09-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74a09-131">**Intestazione:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="74a09-131">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="74a09-132">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74a09-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74a09-133">**Versioni di .NET framework:** 4.5, 4, 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="74a09-133">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74a09-134">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="74a09-134">See also</span></span>

- [<span data-ttu-id="74a09-135">Interfaccia ICorDebugRemote</span><span class="sxs-lookup"><span data-stu-id="74a09-135">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [<span data-ttu-id="74a09-136">Interfaccia ICorDebug</span><span class="sxs-lookup"><span data-stu-id="74a09-136">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="74a09-137">Interfacce di debug</span><span class="sxs-lookup"><span data-stu-id="74a09-137">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
