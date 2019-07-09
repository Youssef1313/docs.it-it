---
title: Metodo ICorProfilerInfo::SetILInstrumentedCodeMap
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetILInstrumentedCodeMap method [.NET Framework profiling]
ms.assetid: bce1dcf8-b4ec-4e73-a917-f2df1ad49c8a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e41df91ceb9e4b776c2aa1ce864b7e09ec485fd5
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661945"
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a><span data-ttu-id="9128d-102">Metodo ICorProfilerInfo::SetILInstrumentedCodeMap</span><span class="sxs-lookup"><span data-stu-id="9128d-102">ICorProfilerInfo::SetILInstrumentedCodeMap Method</span></span>

<span data-ttu-id="9128d-103">Imposta una mappa codici per la funzione specificata utilizzando voci della mappa specificate Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="9128d-103">Sets a code map for the specified function using the specified Microsoft intermediate language (MSIL) map entries.</span></span>

> [!NOTE]
> <span data-ttu-id="9128d-104">In .NET Framework versione 2.0, la chiamata `SetILInstrumentedCodeMap` su un `FunctionID` che rappresenta una funzione generica in un determinato dominio dell'applicazione influirà su tutte le istanze della funzione nel dominio dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="9128d-104">In the .NET Framework version 2.0, calling `SetILInstrumentedCodeMap` on a `FunctionID` that represents a generic function in a particular application domain will affect all instances of that function in the application domain.</span></span>

## <a name="syntax"></a><span data-ttu-id="9128d-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="9128d-105">Syntax</span></span>

```cpp
HRESULT SetILInstrumentedCodeMap(
    [in]  FunctionID functionId,
    [in]  BOOL       fStartJit,
    [in]  ULONG      cILMapEntries,
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);
```

## <a name="parameters"></a><span data-ttu-id="9128d-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="9128d-106">Parameters</span></span>

`functionId`\
<span data-ttu-id="9128d-107">[in] L'ID della funzione per cui impostare la mappa del codice.</span><span class="sxs-lookup"><span data-stu-id="9128d-107">[in] The ID of the function for which to set the code map.</span></span>

`fStartJit`\
<span data-ttu-id="9128d-108">[in] Un valore booleano che indica se la chiamata per il `SetILInstrumentedCodeMap` metodo è il primo di una particolare `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="9128d-108">[in] A Boolean value that indicates whether the call to the `SetILInstrumentedCodeMap` method is the first for a particular `FunctionID`.</span></span> <span data-ttu-id="9128d-109">Impostare `fStartJit` al `true` nella prima chiamata a `SetILInstrumentedCodeMap` per un determinato `FunctionID`e a `false` successivamente.</span><span class="sxs-lookup"><span data-stu-id="9128d-109">Set `fStartJit` to `true` in the first call to `SetILInstrumentedCodeMap` for a given `FunctionID`, and to `false` thereafter.</span></span>

`cILMapEntries`\
<span data-ttu-id="9128d-110">[in] Il numero di elementi nel `cILMapEntries` matrice.</span><span class="sxs-lookup"><span data-stu-id="9128d-110">[in] The number of elements in the `cILMapEntries` array.</span></span>

`rgILMapEntries`\
<span data-ttu-id="9128d-111">[in] Matrice di strutture COR_IL_MAP, ognuno dei quali specifica un offset MSIL.</span><span class="sxs-lookup"><span data-stu-id="9128d-111">[in] An array of COR_IL_MAP structures, each of which specifies an MSIL offset.</span></span>

## <a name="remarks"></a><span data-ttu-id="9128d-112">Note</span><span class="sxs-lookup"><span data-stu-id="9128d-112">Remarks</span></span>

<span data-ttu-id="9128d-113">Spesso, un profiler inserisce istruzioni all'interno del codice sorgente di un metodo per instrumentare tale metodo (ad esempio, per inviare una notifica quando viene raggiunta una riga di origine specificato).</span><span class="sxs-lookup"><span data-stu-id="9128d-113">A profiler often inserts statements within the source code of a method in order to instrument that method (for example, to notify when a given source line is reached).</span></span> <span data-ttu-id="9128d-114">`SetILInstrumentedCodeMap` consente a un profiler eseguire il mapping di istruzioni MSIL originale nelle nuove posizioni.</span><span class="sxs-lookup"><span data-stu-id="9128d-114">`SetILInstrumentedCodeMap` enables a profiler to map the original MSIL instructions to their new locations.</span></span> <span data-ttu-id="9128d-115">Un profiler può usare la [ICorProfilerInfo:: GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) metodo per ottenere l'offset MSIL originale per un determinato offset nativi.</span><span class="sxs-lookup"><span data-stu-id="9128d-115">A profiler can use the [ICorProfilerInfo::GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) method to get the original MSIL offset for a given native offset.</span></span>

<span data-ttu-id="9128d-116">Il debugger presuppone che ogni offset precedente fa riferimento a un offset all'interno del codice MSIL originale, non modificato MSIL e che ogni nuovo offset fa riferimento all'offset all'interno del nuovo codice instrumentato MSIL.</span><span class="sxs-lookup"><span data-stu-id="9128d-116">The debugger will assume that each old offset refers to an MSIL offset within the original, unmodified MSIL code, and that each new offset refers to the MSIL offset within the new, instrumented code.</span></span> <span data-ttu-id="9128d-117">La mappa deve essere disposti in ordine crescente.</span><span class="sxs-lookup"><span data-stu-id="9128d-117">The map should be sorted in increasing order.</span></span> <span data-ttu-id="9128d-118">Per l'esecuzione di istruzioni per il corretto funzionamento, seguire queste linee guida:</span><span class="sxs-lookup"><span data-stu-id="9128d-118">For stepping to work properly, follow these guidelines:</span></span>

- <span data-ttu-id="9128d-119">Non riordinano le codice instrumentato MSIL.</span><span class="sxs-lookup"><span data-stu-id="9128d-119">Do not reorder instrumented MSIL code.</span></span>

- <span data-ttu-id="9128d-120">Non rimuovere il codice MSIL originale.</span><span class="sxs-lookup"><span data-stu-id="9128d-120">Do not remove the original MSIL code.</span></span>

- <span data-ttu-id="9128d-121">Includere le voci per tutti i punti di sequenza dal file di database (PDB) di programma nella mappa.</span><span class="sxs-lookup"><span data-stu-id="9128d-121">Include entries for all the sequence points from the program database (PDB) file in the map.</span></span> <span data-ttu-id="9128d-122">La mappa non esegue l'interpolazione voci mancanti.</span><span class="sxs-lookup"><span data-stu-id="9128d-122">The map does not interpolate missing entries.</span></span> <span data-ttu-id="9128d-123">Pertanto, data la mappa seguente:</span><span class="sxs-lookup"><span data-stu-id="9128d-123">So, given the following map:</span></span>

  <span data-ttu-id="9128d-124">(0 precedente, 0 nuovi)</span><span class="sxs-lookup"><span data-stu-id="9128d-124">(0 old, 0 new)</span></span>

  <span data-ttu-id="9128d-125">(5 precedenti, 10 nuovi)</span><span class="sxs-lookup"><span data-stu-id="9128d-125">(5 old, 10 new)</span></span>

  <span data-ttu-id="9128d-126">(9 precedente, 20 nuovi)</span><span class="sxs-lookup"><span data-stu-id="9128d-126">(9 old, 20 new)</span></span>

  - <span data-ttu-id="9128d-127">Verrà eseguito il mapping di un offset 0, 1, 2, 3 o 4 precedente al nuovo offset 0.</span><span class="sxs-lookup"><span data-stu-id="9128d-127">An old offset of 0, 1, 2, 3, or 4 will be mapped to new offset 0.</span></span>

  - <span data-ttu-id="9128d-128">Verrà eseguito il mapping di un offset precedente del 5, 6, 7 o 8 al nuovo offset 10.</span><span class="sxs-lookup"><span data-stu-id="9128d-128">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>

  - <span data-ttu-id="9128d-129">Verrà eseguito il mapping di un offset precedente del 9 o versione successiva al nuovo offset 20.</span><span class="sxs-lookup"><span data-stu-id="9128d-129">An old offset of 9 or higher will be mapped to new offset 20.</span></span>

  - <span data-ttu-id="9128d-130">Verrà eseguito il mapping di un nuovo offset 0, 1, 2, 3, 4, 5, 6, 7, 8 o 9 al vecchio offset 0.</span><span class="sxs-lookup"><span data-stu-id="9128d-130">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>

  - <span data-ttu-id="9128d-131">Verrà eseguito il mapping di un nuovo offset di 10, 11, 12, 13, 14, 15, 16, 17, 18 o 19 al vecchio offset 5.</span><span class="sxs-lookup"><span data-stu-id="9128d-131">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>

  - <span data-ttu-id="9128d-132">Verrà eseguito il mapping di un nuovo offset pari a 20 o superiore al vecchio offset 9.</span><span class="sxs-lookup"><span data-stu-id="9128d-132">A new offset of 20 or higher will be mapped to old offset 9.</span></span>

## <a name="requirements"></a><span data-ttu-id="9128d-133">Requisiti</span><span class="sxs-lookup"><span data-stu-id="9128d-133">Requirements</span></span>

<span data-ttu-id="9128d-134">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9128d-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="9128d-135">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9128d-135">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="9128d-136">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9128d-136">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="9128d-137">**Versioni di .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9128d-137">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="9128d-138">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9128d-138">See also</span></span>

- [<span data-ttu-id="9128d-139">Interfaccia ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="9128d-139">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
