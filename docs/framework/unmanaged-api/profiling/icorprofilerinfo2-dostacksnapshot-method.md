---
title: Metodo ICorProfilerInfo2::DoStackSnapshot
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.DoStackSnapshot
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::DoStackSnapshot
helpviewer_keywords:
- ICorProfilerInfo2::DoStackSnapshot method [.NET Framework profiling]
- DoStackSnapshot method [.NET Framework profiling]
ms.assetid: 287b11e9-7c52-4a13-ba97-751203fa97f4
topic_type:
- apiref
ms.openlocfilehash: 64bcf6ee58d743a26e31c49a425f36cc808b5080
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426834"
---
# <a name="icorprofilerinfo2dostacksnapshot-method"></a>Metodo ICorProfilerInfo2::DoStackSnapshot
Esamina i frame gestiti nello stack per il thread specificato e invia le informazioni al profiler tramite un callback.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT DoStackSnapshot(  
    [in] ThreadID thread,  
    [in] StackSnapshotCallback *callback,  
    [in] ULONG32 infoFlags,  
    [in] void *clientData,  
    [in, size_is(contextSize), length_is(contextSize)] BYTE context[],  
    [in] ULONG32 contextSize);  
```  
  
## <a name="parameters"></a>Parametri  
 `thread`  
 in ID del thread di destinazione.  
  
 Il passaggio di un valore null in `thread` restituisce uno snapshot del thread corrente. Se viene passato un `ThreadID` di un thread diverso, il Common Language Runtime (CLR) sospende il thread, esegue lo snapshot e riprende.  
  
 `callback`  
 in Puntatore all'implementazione del metodo [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) , che viene chiamato da CLR per fornire al profiler informazioni su ogni frame gestito e ogni esecuzione di frame non gestiti.  
  
 Il `StackSnapshotCallback` metodo viene implementato dal writer del profiler.  
  
 `infoFlags`  
 in Valore dell'enumerazione [COR_PRF_SNAPSHOT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md) , che specifica la quantità di dati da restituire per ogni frame da `StackSnapshotCallback`.  
  
 `clientData`  
 in Puntatore ai dati client, che viene passato direttamente alla funzione di callback `StackSnapshotCallback`.  
  
 `context`  
 in Puntatore a una struttura `CONTEXT` Win32 utilizzata per il seeding del percorso dello stack. La struttura di `CONTEXT` Win32 contiene i valori dei registri della CPU e rappresenta lo stato della CPU in un determinato momento.  
  
 Il valore di inizializzazione consente a CLR di determinare dove iniziare il percorso dello stack, se la parte superiore dello stack è codice di supporto non gestito; in caso contrario, il valore di inizializzazione viene ignorato. È necessario specificare un valore di inizializzazione per un percorso asincrono. Se si sta eseguendo un percorso sincrono, non è necessario alcun valore di inizializzazione.  
  
 Il parametro `context` è valido solo se il flag COR_PRF_SNAPSHOT_CONTEXT è stato passato nel parametro `infoFlags`.  
  
 `contextSize`  
 in Dimensioni della struttura di `CONTEXT`, a cui fa riferimento il parametro di `context`.  
  
## <a name="remarks"></a>Osservazioni  
 Il passaggio di null per `thread` restituisce uno snapshot del thread corrente. Gli snapshot possono essere presi da altri thread solo se il thread di destinazione è sospeso al momento.  
  
 Quando il profiler vuole esaminare lo stack, chiama `DoStackSnapshot`. Prima che CLR torni da tale chiamata, chiama il `StackSnapshotCallback` più volte, una volta per ogni frame gestito (o per l'esecuzione di frame non gestiti) nello stack. Quando vengono rilevati frame non gestiti, è necessario eseguirli manualmente.  
  
 L'ordine in cui viene camminato lo stack è il contrario rispetto alla modalità di push dei frame nello stack: primo fotogramma (ultimo push), principale (primo push).  
  
 Per altre informazioni su come programmare il profiler per l'analisi degli stack gestiti, vedere [analisi dello stack del profiler nella .NET Framework 2,0: Nozioni di base e oltre](https://go.microsoft.com/fwlink/?LinkId=73638).  
  
 Un percorso stack può essere sincrono o asincrono, come illustrato nelle sezioni seguenti.  
  
## <a name="synchronous-stack-walk"></a>Percorso stack sincrono  
 Un percorso stack sincrono prevede l'analisi dello stack del thread corrente in risposta a un callback. Non richiede il seeding o la sospensione.  
  
 Si esegue una chiamata sincrona quando, in risposta a CLR che chiama uno dei metodi [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) (o [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) del profiler, si chiama `DoStackSnapshot` per scorrere lo stack del thread corrente. Questa operazione è utile quando si desidera visualizzare l'aspetto dello stack in una notifica, ad esempio [ICorProfilerCallback:: ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md). È sufficiente chiamare `DoStackSnapshot` dall'interno del metodo `ICorProfilerCallback`, passando null nei parametri `context` e `thread`.  
  
## <a name="asynchronous-stack-walk"></a>Percorso stack asincrono  
 Un percorso stack asincrono comporta l'analisi dello stack di un thread diverso o l'analisi dello stack del thread corrente, non in risposta a un callback, ma il hijack del puntatore all'istruzione del thread corrente. Un percorso asincrono richiede un valore di inizializzazione se il primo dello stack è codice non gestito che non fa parte di una chiamata a platform invoke (PInvoke) o COM, ma codice di supporto in CLR stesso. Ad esempio, il codice che esegue la compilazione JIT (just-in-Time) o Garbage Collection è codice helper.  
  
 Si ottiene un valore di inizializzazione sospendendo direttamente il thread di destinazione e spostando il relativo stack fino a trovare il frame gestito in primo piano. Dopo la sospensione del thread di destinazione, ottenere il contesto di registro corrente del thread di destinazione. Determinare quindi se il contesto del registro punta a codice non gestito chiamando [ICorProfilerInfo:: GetFunctionFromIP](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md) , se restituisce un `FunctionID` uguale a zero, il frame è codice non gestito. A questo punto, scorrere lo stack fino a raggiungere il primo frame gestito, quindi calcolare il contesto di inizializzazione in base al contesto di registro per il frame.  
  
 Chiamare `DoStackSnapshot` con il contesto di inizializzazione per avviare il percorso dello stack asincrono. Se non si specifica un valore di inizializzazione, `DoStackSnapshot` possibile ignorare i frame gestiti nella parte superiore dello stack e, di conseguenza, fornirà un percorso stack incompleto. Se si fornisce un valore di inizializzazione, deve puntare al codice generato con compilazione JIT o Native Image Generator (Ngen. exe); in caso contrario, `DoStackSnapshot` restituisce il codice di errore, CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX.  
  
 I percorsi di stack asincroni possono causare facilmente deadlock o violazioni di accesso, a meno che non si seguano le seguenti linee guida:  
  
- Quando si sospendono direttamente i thread, tenere presente che solo un thread che non esegue mai codice gestito può sospendere un altro thread.  
  
- Blocca sempre nel callback [ICorProfilerCallback:: ThreadDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md) fino al completamento del percorso stack del thread.  
  
- Non mantenere un blocco quando il profiler chiama una funzione CLR che può attivare un Garbage Collection. Ovvero, non mantenere un blocco se il thread proprietario può effettuare una chiamata che attiva un Garbage Collection.  
  
 Esiste anche il rischio che si verifichi un deadlock se si chiama `DoStackSnapshot` da un thread creato dal profiler per poter scorrere lo stack di un thread di destinazione separato. La prima volta che il thread creato immette determinati metodi di `ICorProfilerInfo*` (incluso `DoStackSnapshot`), il CLR eseguirà l'inizializzazione specifica di CLR per thread su tale thread. Se il profiler ha sospeso il thread di destinazione il cui stack si sta tentando di esaminare e se il thread di destinazione è proprietario di un blocco necessario per eseguire questa inizializzazione per thread, si verificherà un deadlock. Per evitare questo deadlock, effettuare una chiamata iniziale in `DoStackSnapshot` dal thread creato dal profiler per esaminare un thread di destinazione separato, ma non sospendere prima il thread di destinazione. Questa chiamata iniziale garantisce che l'inizializzazione per thread possa essere completata senza deadlock. Se `DoStackSnapshot` ha esito positivo e segnala almeno un frame, dopo tale punto sarà sicuro per il thread creato dal profiler sospendere qualsiasi thread di destinazione e chiamare `DoStackSnapshot` per esaminare lo stack del thread di destinazione.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorProf.idl, CorProf.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interfaccia ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
