---
title: Metodo ICLRDataTarget3::GetExceptionRecord
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetExceptionRecord
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6643c2af-2ee6-4789-aa25-1d8eaf500c94
topic_type:
- apiref
ms.openlocfilehash: d5e7841844c8fa500935eb9cba06f4e2fe95d2d5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73111989"
---
# <a name="iclrdatatarget3getexceptionrecord-method"></a><span data-ttu-id="2cdca-102">Metodo ICLRDataTarget3::GetExceptionRecord</span><span class="sxs-lookup"><span data-stu-id="2cdca-102">ICLRDataTarget3::GetExceptionRecord Method</span></span>
<span data-ttu-id="2cdca-103">Chiamato dai servizi di accesso ai dati di Common Language Runtime (CLR) per recuperare il record di eccezione associato al processo destinazione.</span><span class="sxs-lookup"><span data-stu-id="2cdca-103">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span> <span data-ttu-id="2cdca-104">Ad esempio, per una destinazione del dump, questo sarebbe equivalente al record di eccezione passato tramite l'argomento `ExceptionParam` alla funzione [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) nella libreria della Guida di debug di Windows (dbghelp).</span><span class="sxs-lookup"><span data-stu-id="2cdca-104">For example, for a dump target, this would be equivalent to the exception record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cdca-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="2cdca-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize] BYTE* buffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2cdca-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="2cdca-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="2cdca-107">[in] La dimensione del buffer di input, in byte.</span><span class="sxs-lookup"><span data-stu-id="2cdca-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="2cdca-108">Deve essere uguale a `sizeof(`[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception)`)`.</span><span class="sxs-lookup"><span data-stu-id="2cdca-108">This must be equal to `sizeof(`[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception)`)`.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="2cdca-109">[out] Un puntatore a un tipo `ULONG32` che riceve il numero di byte effettivamente scritti nel buffer.</span><span class="sxs-lookup"><span data-stu-id="2cdca-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="2cdca-110">[out] Un puntatore a un buffer di memoria che riceve una copia del record di eccezione.</span><span class="sxs-lookup"><span data-stu-id="2cdca-110">[out] A pointer to a memory buffer that receives a copy of the exception record.</span></span> <span data-ttu-id="2cdca-111">Il record di eccezione viene restituito come tipo [MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) .</span><span class="sxs-lookup"><span data-stu-id="2cdca-111">The exception record is returned as a [MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2cdca-112">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="2cdca-112">Return Value</span></span>  
 <span data-ttu-id="2cdca-113">Il valore restituito è `S_OK` in caso di esito positivo o un codice di errore `HRESULT` in caso di esito negativo.</span><span class="sxs-lookup"><span data-stu-id="2cdca-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="2cdca-114">I codici `HRESULT` possono includere, ma non sono limitati a, quanto segue:</span><span class="sxs-lookup"><span data-stu-id="2cdca-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="2cdca-115">Codice restituito</span><span class="sxs-lookup"><span data-stu-id="2cdca-115">Return code</span></span>|<span data-ttu-id="2cdca-116">Descrizione</span><span class="sxs-lookup"><span data-stu-id="2cdca-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="2cdca-117">Il metodo è riuscito.</span><span class="sxs-lookup"><span data-stu-id="2cdca-117">Method succeeded.</span></span> <span data-ttu-id="2cdca-118">Il record di eccezione è stato copiato nel buffer di output.</span><span class="sxs-lookup"><span data-stu-id="2cdca-118">The exception record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="2cdca-119">Nessun record di eccezione è associato alla destinazione.</span><span class="sxs-lookup"><span data-stu-id="2cdca-119">No exception record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="2cdca-120">La dimensione del buffer di input non è uguale a `sizeof(MINIDUMP_EXCEPTION)`.</span><span class="sxs-lookup"><span data-stu-id="2cdca-120">The input buffer size is not equal to `sizeof(MINIDUMP_EXCEPTION)`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2cdca-121">Note</span><span class="sxs-lookup"><span data-stu-id="2cdca-121">Remarks</span></span>  
 <span data-ttu-id="2cdca-122">[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) è una struttura definita in dbghelp. h e Imagehlp. h nella Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="2cdca-122">[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) is a structure defined in dbghelp.h and imagehlp.h in the Windows SDK.</span></span>  
  
 <span data-ttu-id="2cdca-123">Questo metodo è implementato dal writer dell'applicazione di debug.</span><span class="sxs-lookup"><span data-stu-id="2cdca-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cdca-124">Requisiti</span><span class="sxs-lookup"><span data-stu-id="2cdca-124">Requirements</span></span>  
 <span data-ttu-id="2cdca-125">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2cdca-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cdca-126">**Intestazione:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="2cdca-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="2cdca-127">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2cdca-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2cdca-128">**Versioni di .NET Framework:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2cdca-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cdca-129">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2cdca-129">See also</span></span>

- [<span data-ttu-id="2cdca-130">Interfaccia ICLRDataTarget3</span><span class="sxs-lookup"><span data-stu-id="2cdca-130">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)
- [<span data-ttu-id="2cdca-131">Metodo GetExceptionContextRecord</span><span class="sxs-lookup"><span data-stu-id="2cdca-131">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)
- [<span data-ttu-id="2cdca-132">Metodo GetExceptionThreadID</span><span class="sxs-lookup"><span data-stu-id="2cdca-132">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
