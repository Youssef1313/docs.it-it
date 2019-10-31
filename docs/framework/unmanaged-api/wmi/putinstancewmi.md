---
title: Funzione PutInstanceWmi (riferimenti alle API non gestite)
description: La funzione PutInstanceWmi crea o aggiorna un'istanza di una classe esistente.
ms.date: 11/06/2017
api_name:
- PutInstanceWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutInstanceWmi
helpviewer_keywords:
- PutInstanceWmi function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: b33f31d69c64ce520580c29f1014c058c78d0953
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127346"
---
# <a name="putinstancewmi-function"></a><span data-ttu-id="aadb5-103">PutInstanceWmi (funzione)</span><span class="sxs-lookup"><span data-stu-id="aadb5-103">PutInstanceWmi function</span></span>

<span data-ttu-id="aadb5-104">Crea o aggiorna un'istanza di una classe esistente.</span><span class="sxs-lookup"><span data-stu-id="aadb5-104">Creates or updates an instance of an existing class.</span></span> <span data-ttu-id="aadb5-105">L'istanza viene scritta nel repository WMI.</span><span class="sxs-lookup"><span data-stu-id="aadb5-105">The instance is written to the WMI repository.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="aadb5-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="aadb5-106">Syntax</span></span>

```cpp
HRESULT PutInstanceWmi (
   [in] IWbemClassObject*    pInst,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
);
```

## <a name="parameters"></a><span data-ttu-id="aadb5-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="aadb5-107">Parameters</span></span>

`pInst`\
<span data-ttu-id="aadb5-108">in Puntatore all'istanza da scrivere.</span><span class="sxs-lookup"><span data-stu-id="aadb5-108">[in] A pointer to the instance to be written.</span></span>

`lFlags`\
<span data-ttu-id="aadb5-109">in Combinazione di flag che influiscono sul comportamento di questa funzione.</span><span class="sxs-lookup"><span data-stu-id="aadb5-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="aadb5-110">I valori seguenti vengono definiti nel file di intestazione *WbemCli. h* oppure è possibile definirli come costanti nel codice:</span><span class="sxs-lookup"><span data-stu-id="aadb5-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="aadb5-111">Costante</span><span class="sxs-lookup"><span data-stu-id="aadb5-111">Constant</span></span>  |<span data-ttu-id="aadb5-112">Value</span><span class="sxs-lookup"><span data-stu-id="aadb5-112">Value</span></span>  |<span data-ttu-id="aadb5-113">Descrizione</span><span class="sxs-lookup"><span data-stu-id="aadb5-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="aadb5-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="aadb5-114">0x20000</span></span> | <span data-ttu-id="aadb5-115">Se impostato, WMI non archivia alcun qualificatore con la **versione modificata** .</span><span class="sxs-lookup"><span data-stu-id="aadb5-115">If set, WMI does not store any qualifiers with the **Amended** flavor.</span></span> <br> <span data-ttu-id="aadb5-116">Se non è impostato, si presuppone che l'oggetto non sia localizzato e che tutti i qualificatori siano archiviati con questa istanza.</span><span class="sxs-lookup"><span data-stu-id="aadb5-116">If not set, it is assumed that this object is not localized, and all qualifiers are stored with this instance.</span></span> |
| `WBEM_FLAG_CREATE_OR_UPDATE` | <span data-ttu-id="aadb5-117">0</span><span class="sxs-lookup"><span data-stu-id="aadb5-117">0</span></span> | <span data-ttu-id="aadb5-118">Creare l'istanza, se non esiste, oppure sovrascriverla se esiste già.</span><span class="sxs-lookup"><span data-stu-id="aadb5-118">Create the instance if it does not exist, or overwrite it if it exists already.</span></span> |
| `WBEM_FLAG_UPDATE_ONLY` | <span data-ttu-id="aadb5-119">1</span><span class="sxs-lookup"><span data-stu-id="aadb5-119">1</span></span> | <span data-ttu-id="aadb5-120">Aggiornare l'istanza di.</span><span class="sxs-lookup"><span data-stu-id="aadb5-120">Update the instance.</span></span> <span data-ttu-id="aadb5-121">L'istanza deve esistere affinché la chiamata abbia esito positivo.</span><span class="sxs-lookup"><span data-stu-id="aadb5-121">The instance must exist for the call to be successful.</span></span> |
| `WBEM_FLAG_CREATE_ONLY` | <span data-ttu-id="aadb5-122">2</span><span class="sxs-lookup"><span data-stu-id="aadb5-122">2</span></span> | <span data-ttu-id="aadb5-123">Creare l'istanza di.</span><span class="sxs-lookup"><span data-stu-id="aadb5-123">Create the instance.</span></span> <span data-ttu-id="aadb5-124">La chiamata ha esito negativo se l'istanza esiste già.</span><span class="sxs-lookup"><span data-stu-id="aadb5-124">The call fails if the instance already exists.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="aadb5-125">0x10</span><span class="sxs-lookup"><span data-stu-id="aadb5-125">0x10</span></span> | <span data-ttu-id="aadb5-126">Il flag causa una chiamata semisincrono.</span><span class="sxs-lookup"><span data-stu-id="aadb5-126">The flag causes a semisynchronous call.</span></span> |

`pCtx`\
<span data-ttu-id="aadb5-127">in In genere, questo valore è `null`.</span><span class="sxs-lookup"><span data-stu-id="aadb5-127">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="aadb5-128">In caso contrario, è un puntatore a un'istanza di [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) che può essere usata dal provider che fornisce le classi richieste.</span><span class="sxs-lookup"><span data-stu-id="aadb5-128">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span>

`ppCallResult`\
<span data-ttu-id="aadb5-129">out Se `null`, questo parametro è inutilizzato.</span><span class="sxs-lookup"><span data-stu-id="aadb5-129">[out] If `null`, this parameter is unused.</span></span> <span data-ttu-id="aadb5-130">Se `lFlags` contiene `WBEM_FLAG_RETURN_IMMEDIATELY`, la funzione viene restituita immediatamente con `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="aadb5-130">If `lFlags` contains `WBEM_FLAG_RETURN_IMMEDIATELY`, the function returns immediately with `WBEM_S_NO_ERROR`.</span></span> <span data-ttu-id="aadb5-131">Il parametro `ppCallResult` riceve un puntatore a un nuovo oggetto [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) .</span><span class="sxs-lookup"><span data-stu-id="aadb5-131">The `ppCallResult` parameter receives a pointer to a new [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) object.</span></span>

## <a name="return-value"></a><span data-ttu-id="aadb5-132">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="aadb5-132">Return value</span></span>

<span data-ttu-id="aadb5-133">I valori seguenti restituiti da questa funzione sono definiti nel file di intestazione *WbemCli. h* oppure è possibile definirli come costanti nel codice:</span><span class="sxs-lookup"><span data-stu-id="aadb5-133">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="aadb5-134">Costante</span><span class="sxs-lookup"><span data-stu-id="aadb5-134">Constant</span></span>  |<span data-ttu-id="aadb5-135">Value</span><span class="sxs-lookup"><span data-stu-id="aadb5-135">Value</span></span>  |<span data-ttu-id="aadb5-136">Descrizione</span><span class="sxs-lookup"><span data-stu-id="aadb5-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="aadb5-137">0x80041003</span><span class="sxs-lookup"><span data-stu-id="aadb5-137">0x80041003</span></span> | <span data-ttu-id="aadb5-138">L'utente non dispone delle autorizzazioni necessarie per aggiornare un'istanza della classe specificata.</span><span class="sxs-lookup"><span data-stu-id="aadb5-138">The user does not have permission to update an instance of the specified class.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="aadb5-139">0x80041001</span><span class="sxs-lookup"><span data-stu-id="aadb5-139">0x80041001</span></span> | <span data-ttu-id="aadb5-140">Si è verificato un errore non specificato.</span><span class="sxs-lookup"><span data-stu-id="aadb5-140">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="aadb5-141">0x80041010</span><span class="sxs-lookup"><span data-stu-id="aadb5-141">0x80041010</span></span> | <span data-ttu-id="aadb5-142">La classe che supporta questa istanza non è valida.</span><span class="sxs-lookup"><span data-stu-id="aadb5-142">The class supporting this instance is not valid.</span></span> |
| `WBEM_E_ILLEGAL_NULL` | <span data-ttu-id="aadb5-143">0x80041028</span><span class="sxs-lookup"><span data-stu-id="aadb5-143">0x80041028</span></span> | <span data-ttu-id="aadb5-144">è stato specificato un `null` per una proprietà che non può essere `null`, ad esempio uno contrassegnato da un qualificatore **NOT_NULL** o **indicizzato** .</span><span class="sxs-lookup"><span data-stu-id="aadb5-144">a `null` was specified for a property that cannot be `null`, such as one that is marked by an **Indexed** or **Not_Null** qualifier.</span></span> |
| `WBEM_E_INVALID_OBJECT` | <span data-ttu-id="aadb5-145">0x8004100f</span><span class="sxs-lookup"><span data-stu-id="aadb5-145">0x8004100f</span></span> | <span data-ttu-id="aadb5-146">L'istanza specificata non è valida.</span><span class="sxs-lookup"><span data-stu-id="aadb5-146">The specified instance is not valid.</span></span> <span data-ttu-id="aadb5-147">(Ad esempio, la chiamata di `PutInstanceWmi` con una classe restituisce questo valore).</span><span class="sxs-lookup"><span data-stu-id="aadb5-147">(For example, calling `PutInstanceWmi` with a class returns this value.)</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="aadb5-148">0x80041008</span><span class="sxs-lookup"><span data-stu-id="aadb5-148">0x80041008</span></span> | <span data-ttu-id="aadb5-149">Parametro non valido.</span><span class="sxs-lookup"><span data-stu-id="aadb5-149">A parameter is not valid.</span></span> |
| `WBEM_E_ALREADY_EXISTS` | <span data-ttu-id="aadb5-150">0x80041019</span><span class="sxs-lookup"><span data-stu-id="aadb5-150">0x80041019</span></span> | <span data-ttu-id="aadb5-151">Il flag di `WBEM_FLAG_CREATE_ONLY` è stato specificato, ma l'istanza esiste già.</span><span class="sxs-lookup"><span data-stu-id="aadb5-151">The `WBEM_FLAG_CREATE_ONLY` flag was specified, but the instance already exists.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="aadb5-152">0x80041002</span><span class="sxs-lookup"><span data-stu-id="aadb5-152">0x80041002</span></span> | <span data-ttu-id="aadb5-153">`WBEM_FLAG_UPDATE_ONLY` è stato specificato in `lFlags`, ma l'istanza non esiste.</span><span class="sxs-lookup"><span data-stu-id="aadb5-153">`WBEM_FLAG_UPDATE_ONLY` was specified in `lFlags`, but the instance does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="aadb5-154">0x80041006</span><span class="sxs-lookup"><span data-stu-id="aadb5-154">0x80041006</span></span> | <span data-ttu-id="aadb5-155">Memoria insufficiente per completare l'operazione.</span><span class="sxs-lookup"><span data-stu-id="aadb5-155">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="aadb5-156">0x80041033</span><span class="sxs-lookup"><span data-stu-id="aadb5-156">0x80041033</span></span> | <span data-ttu-id="aadb5-157">WMI è stato probabilmente interrotto e riavviato.</span><span class="sxs-lookup"><span data-stu-id="aadb5-157">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="aadb5-158">Chiamare nuovamente [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="aadb5-158">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="aadb5-159">0x80041015</span><span class="sxs-lookup"><span data-stu-id="aadb5-159">0x80041015</span></span> | <span data-ttu-id="aadb5-160">Il collegamento RPC (Remote Procedure Call) tra il processo corrente e WMI non è riuscito.</span><span class="sxs-lookup"><span data-stu-id="aadb5-160">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="aadb5-161">0</span><span class="sxs-lookup"><span data-stu-id="aadb5-161">0</span></span> | <span data-ttu-id="aadb5-162">La chiamata di funzione è stata completata.</span><span class="sxs-lookup"><span data-stu-id="aadb5-162">The function call was successful.</span></span> |

## <a name="remarks"></a><span data-ttu-id="aadb5-163">Note</span><span class="sxs-lookup"><span data-stu-id="aadb5-163">Remarks</span></span>

<span data-ttu-id="aadb5-164">Questa funzione esegue il wrapping di una chiamata al metodo [IWbemServices::P utinstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putinstance) .</span><span class="sxs-lookup"><span data-stu-id="aadb5-164">This function wraps a call to the [IWbemServices::PutInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putinstance) method.</span></span>

<span data-ttu-id="aadb5-165">La funzione `PutInstanceWmi` supporta la creazione di istanze e l'aggiornamento solo delle istanze delle classi esistenti.</span><span class="sxs-lookup"><span data-stu-id="aadb5-165">The `PutInstanceWmi` function supports creating instances and updating instances of existing classes only.</span></span>  <span data-ttu-id="aadb5-166">A seconda del modo in cui viene impostato il parametro `pCtx`, vengono aggiornate alcune o tutte le proprietà dell'istanza.</span><span class="sxs-lookup"><span data-stu-id="aadb5-166">Depending on how the `pCtx` parameter is set, either some or all of the properties of the instance are updated.</span></span>

<span data-ttu-id="aadb5-167">Quando l'istanza a cui punta `pInst` appartiene a una sottoclasse, gestione Windows chiama tutti i provider responsabili delle classi da cui deriva la sottoclasse.</span><span class="sxs-lookup"><span data-stu-id="aadb5-167">When the instance pointed to by `pInst` belongs to a subclass, Windows Management calls all the providers responsible for the classes from which the subclass derives.</span></span> <span data-ttu-id="aadb5-168">Tutti questi provider devono avere esito positivo affinché la richiesta di `PutInstanceWmi` originale abbia esito positivo.</span><span class="sxs-lookup"><span data-stu-id="aadb5-168">All of these providers must succeed for the original `PutInstanceWmi` request to succeed.</span></span> <span data-ttu-id="aadb5-169">Il provider che supporta la classe più in alto nella gerarchia viene chiamato per primo.</span><span class="sxs-lookup"><span data-stu-id="aadb5-169">The provider supporting the topmost class in the hierarchy is called first.</span></span> <span data-ttu-id="aadb5-170">L'ordine di chiamata continua con la sottoclasse della classe superiore e procede dall'alto verso il basso fino a quando gestione Windows non raggiunge il provider per la classe proprietaria dell'istanza a cui fa riferimento `pInst`.</span><span class="sxs-lookup"><span data-stu-id="aadb5-170">The calling order continues with the subclass of the topmost class and proceeds from top to bottom until Windows Management reaches the provider for the class owning the instance pointed to by `pInst`.</span></span>
<span data-ttu-id="aadb5-171">Gestione Windows non chiama i provider per nessuna delle classi figlio di un'istanza.</span><span class="sxs-lookup"><span data-stu-id="aadb5-171">Windows Management does not call the providers for any of the child classes of an instance.</span></span>

<span data-ttu-id="aadb5-172">Quando un'applicazione deve aggiornare un'istanza che appartiene a una gerarchia di classi, il `pInst` parametro deve puntare all'istanza contenente le proprietà da modificare.</span><span class="sxs-lookup"><span data-stu-id="aadb5-172">When an application must update an instance that belongs to a class hierarchy, the `pInst` parameter must point to the instance containing the properties to be modified.</span></span> <span data-ttu-id="aadb5-173">Ovvero, si consideri un'istanza di destinazione che appartiene a **ClassB**.</span><span class="sxs-lookup"><span data-stu-id="aadb5-173">That is, consider a target instance that belongs to **ClassB**.</span></span> <span data-ttu-id="aadb5-174">L'istanza di **ClassB** deriva da **ClassA**e **ClassA** definisce la proprietà **propa**.</span><span class="sxs-lookup"><span data-stu-id="aadb5-174">The **ClassB** instance derives from **ClassA**, and **ClassA** defines the property **PropA**.</span></span> <span data-ttu-id="aadb5-175">Se un'applicazione vuole apportare una modifica al valore di **propa** nell'istanza di **ClassB** , deve impostare `pInst` su tale istanza anziché un'istanza di **ClassA**.</span><span class="sxs-lookup"><span data-stu-id="aadb5-175">If an application wants to make a change to the value of **PropA** in the **ClassB** instance, it must set `pInst` to that instance rather than an instance of **ClassA**.</span></span>

<span data-ttu-id="aadb5-176">La chiamata di `PutInstanceWmi` su un'istanza di una classe astratta non è consentita.</span><span class="sxs-lookup"><span data-stu-id="aadb5-176">Calling `PutInstanceWmi` on an instance of an abstract class is not allowed.</span></span>

<span data-ttu-id="aadb5-177">Se la chiamata di funzione ha esito negativo, è possibile ottenere ulteriori informazioni sull'errore chiamando la funzione [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="aadb5-177">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="aadb5-178">Requisiti</span><span class="sxs-lookup"><span data-stu-id="aadb5-178">Requirements</span></span>

<span data-ttu-id="aadb5-179">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aadb5-179">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="aadb5-180">**Intestazione:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="aadb5-180">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="aadb5-181">**Versioni di .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="aadb5-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="aadb5-182">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="aadb5-182">See also</span></span>

- [<span data-ttu-id="aadb5-183">WMI e contatori delle prestazioni (riferimenti alle API non gestite)</span><span class="sxs-lookup"><span data-stu-id="aadb5-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
