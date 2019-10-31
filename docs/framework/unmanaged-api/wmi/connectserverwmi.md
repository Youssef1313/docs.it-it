---
title: Funzione ConnectServerWmi (riferimenti alle API non gestite)
description: La funzione ConnectServerWmi utilizza DCOM per creare una connessione a uno spazio dei nomi WMI.
ms.date: 11/06/2017
api_name:
- ConnectServerWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ConnectServerWmi
helpviewer_keywords:
- ConnectServerWmi function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 25a73060ed242fd0e77042cd0ea9618b9b27250f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128688"
---
# <a name="connectserverwmi-function"></a><span data-ttu-id="43af1-103">ConnectServerWmi (funzione)</span><span class="sxs-lookup"><span data-stu-id="43af1-103">ConnectServerWmi function</span></span>

<span data-ttu-id="43af1-104">Crea una connessione tramite DCOM a uno spazio dei nomi WMI in un computer specifico.</span><span class="sxs-lookup"><span data-stu-id="43af1-104">Creates a connection through DCOM to a WMI namespace on a specified computer.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="43af1-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="43af1-105">Syntax</span></span>

```cpp
HRESULT ConnectServerWmi (
   [in] BSTR               strNetworkResource,
   [in] BSTR               strUser,
   [in] BSTR               strPassword,
   [in] BSTR               strLocale,
   [in] long               lSecurityFlags,
   [in] BSTR               strAuthority,
   [in] IWbemContext*      pCtx,
   [out] IWbemServices**   ppNamespace,
   [in] DWORD              impLevel,
   [in] DWORD              authLevel
);
```

## <a name="parameters"></a><span data-ttu-id="43af1-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="43af1-106">Parameters</span></span>

`strNetworkResource`\
<span data-ttu-id="43af1-107">in Puntatore a un `BSTR` valido che contiene il percorso dell'oggetto dello spazio dei nomi WMI corretto.</span><span class="sxs-lookup"><span data-stu-id="43af1-107">[in] Pointer to a valid `BSTR` that contains the object path of the correct WMI namespace.</span></span> <span data-ttu-id="43af1-108">Per ulteriori informazioni, vedere la sezione [osservazioni](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="43af1-108">See the [Remarks](#remarks) section for more information.</span></span>

`strUser`\
<span data-ttu-id="43af1-109">in Puntatore a un `BSTR` valido che contiene il nome utente.</span><span class="sxs-lookup"><span data-stu-id="43af1-109">[in] A pointer to a valid `BSTR` that contains the user name.</span></span> <span data-ttu-id="43af1-110">Valore `null` indica il contesto di sicurezza corrente.</span><span class="sxs-lookup"><span data-stu-id="43af1-110">A `null` value indicates the current security context.</span></span> <span data-ttu-id="43af1-111">Se l'utente si trova in un dominio diverso da quello corrente, `strUser` può contenere anche il dominio e il nome utente separati da una barra rovesciata.</span><span class="sxs-lookup"><span data-stu-id="43af1-111">If the user is from a different domain than the current one, `strUser` can also contain the domain and user name separated by a backslash.</span></span> <span data-ttu-id="43af1-112">`strUser` possono essere presenti anche in formato UPN (User Principal Name), ad esempio `userName@domainName`.</span><span class="sxs-lookup"><span data-stu-id="43af1-112">`strUser` can also be in user principal name (UPN) format, such as `userName@domainName`.</span></span> <span data-ttu-id="43af1-113">Per ulteriori informazioni, vedere la sezione [osservazioni](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="43af1-113">See the [Remarks](#remarks) section for more information.</span></span>

`strPassword`\
<span data-ttu-id="43af1-114">in Puntatore a un `BSTR` valido che contiene la password.</span><span class="sxs-lookup"><span data-stu-id="43af1-114">[in] A pointer to a valid `BSTR` that contains the password.</span></span> <span data-ttu-id="43af1-115">Un `null` indica il contesto di sicurezza corrente.</span><span class="sxs-lookup"><span data-stu-id="43af1-115">A `null` indicates the current security context.</span></span> <span data-ttu-id="43af1-116">Una stringa vuota ("") indica una password di lunghezza zero valida.</span><span class="sxs-lookup"><span data-stu-id="43af1-116">An empty string ("") indicates a valid zero-length password.</span></span>

`strLocale`\
<span data-ttu-id="43af1-117">in Puntatore a un `BSTR` valido che indica le impostazioni locali corrette per il recupero delle informazioni.</span><span class="sxs-lookup"><span data-stu-id="43af1-117">[in] A pointer to a valid `BSTR` that indicates the correct locale for information retrieval.</span></span> <span data-ttu-id="43af1-118">Per gli identificatori delle impostazioni locali Microsoft, il formato della stringa è "MS\_*xxx*", dove *xxx* è una stringa in formato esadecimale che indica l'identificatore delle impostazioni locali (LCID).</span><span class="sxs-lookup"><span data-stu-id="43af1-118">For Microsoft locale identifiers, the format of the string is "MS\_*xxx*", where *xxx* is a string in hexadecimal form that indicates the locale identifier (LCID).</span></span> <span data-ttu-id="43af1-119">Se si specificano impostazioni locali non valide, il metodo restituisce `WBEM_E_INVALID_PARAMETER` ad eccezione di Windows 7, in cui vengono invece utilizzate le impostazioni locali predefinite del server.</span><span class="sxs-lookup"><span data-stu-id="43af1-119">If an invalid locale is specified, the method returns `WBEM_E_INVALID_PARAMETER` except on Windows 7, where the default locale of the server is used instead.</span></span> <span data-ttu-id="43af1-120">Se ' NULL1, vengono usate le impostazioni locali correnti.</span><span class="sxs-lookup"><span data-stu-id="43af1-120">If \`null1, the current locale is used.</span></span>

`lSecurityFlags`\
<span data-ttu-id="43af1-121">in Flag da passare al metodo `ConnectServerWmi`.</span><span class="sxs-lookup"><span data-stu-id="43af1-121">[in] Flags to pass to the `ConnectServerWmi` method.</span></span> <span data-ttu-id="43af1-122">Il valore zero (0) per questo parametro determina la chiamata a `ConnectServerWmi` la restituzione solo dopo che è stata stabilita una connessione al server.</span><span class="sxs-lookup"><span data-stu-id="43af1-122">A value of zero (0) for this parameter results in the call to `ConnectServerWmi` returning only after a connection to the server is established.</span></span> <span data-ttu-id="43af1-123">Questo potrebbe comportare un'applicazione che non risponde a tempo indefinito se il server è danneggiato.</span><span class="sxs-lookup"><span data-stu-id="43af1-123">This could result in an application not responding indefinitely if the server is broken.</span></span> <span data-ttu-id="43af1-124">Gli altri valori validi sono:</span><span class="sxs-lookup"><span data-stu-id="43af1-124">The other valid values are:</span></span>

| <span data-ttu-id="43af1-125">Costante</span><span class="sxs-lookup"><span data-stu-id="43af1-125">Constant</span></span>  | <span data-ttu-id="43af1-126">Value</span><span class="sxs-lookup"><span data-stu-id="43af1-126">Value</span></span>  | <span data-ttu-id="43af1-127">Descrizione</span><span class="sxs-lookup"><span data-stu-id="43af1-127">Description</span></span>  |
|---------|---------|---------|
| `CONNECT_REPOSITORY_ONLY` | <span data-ttu-id="43af1-128">0x40</span><span class="sxs-lookup"><span data-stu-id="43af1-128">0x40</span></span> | <span data-ttu-id="43af1-129">Riservato per uso interno.</span><span class="sxs-lookup"><span data-stu-id="43af1-129">Reserved for internal use.</span></span> <span data-ttu-id="43af1-130">Non usare.</span><span class="sxs-lookup"><span data-stu-id="43af1-130">Do not use.</span></span> |
| `WBEM_FLAG_CONNECT_USE_MAX_WAIT` | <span data-ttu-id="43af1-131">0x80</span><span class="sxs-lookup"><span data-stu-id="43af1-131">0x80</span></span> | <span data-ttu-id="43af1-132">`ConnectServerWmi` restituisce almeno due minuti.</span><span class="sxs-lookup"><span data-stu-id="43af1-132">`ConnectServerWmi` returns in two minutes or less.</span></span> |

`strAuthority`\
<span data-ttu-id="43af1-133">in Nome di dominio dell'utente.</span><span class="sxs-lookup"><span data-stu-id="43af1-133">[in] The domain name of the user.</span></span> <span data-ttu-id="43af1-134">Se son presenti i seguenti valori:</span><span class="sxs-lookup"><span data-stu-id="43af1-134">It can have the following values:</span></span>

| <span data-ttu-id="43af1-135">Value</span><span class="sxs-lookup"><span data-stu-id="43af1-135">Value</span></span> | <span data-ttu-id="43af1-136">Descrizione</span><span class="sxs-lookup"><span data-stu-id="43af1-136">Description</span></span> |
|---------|---------|
| <span data-ttu-id="43af1-137">blank</span><span class="sxs-lookup"><span data-stu-id="43af1-137">blank</span></span> | <span data-ttu-id="43af1-138">Viene utilizzata l'autenticazione NTLM e viene utilizzato il dominio NTLM dell'utente corrente.</span><span class="sxs-lookup"><span data-stu-id="43af1-138">NTLM authentication is used, and the NTLM domain of the current user is used.</span></span> <span data-ttu-id="43af1-139">Se `strUser` specifica il dominio (percorso consigliato), non deve essere specificato qui.</span><span class="sxs-lookup"><span data-stu-id="43af1-139">If `strUser` specifies the domain (the recommended location), it must not be specified here.</span></span> <span data-ttu-id="43af1-140">La funzione restituisce `WBEM_E_INVALID_PARAMETER` se si specifica il dominio in entrambi i parametri.</span><span class="sxs-lookup"><span data-stu-id="43af1-140">The function returns `WBEM_E_INVALID_PARAMETER` if you specify the domain in both parameters.</span></span> |
| <span data-ttu-id="43af1-141">Kerberos:*nome entità*</span><span class="sxs-lookup"><span data-stu-id="43af1-141">Kerberos:*principal name*</span></span> | <span data-ttu-id="43af1-142">Viene utilizzata l'autenticazione Kerberos e questo parametro contiene il nome di un'entità Kerberos.</span><span class="sxs-lookup"><span data-stu-id="43af1-142">Kerberos authentication is used, and this parameter contains a Kerberos principal name.</span></span> |
| <span data-ttu-id="43af1-143">NTLMDOMAIN:*nome di dominio*</span><span class="sxs-lookup"><span data-stu-id="43af1-143">NTLMDOMAIN:*domain name*</span></span> | <span data-ttu-id="43af1-144">Viene utilizzata l'autenticazione NT LAN Manager e questo parametro contiene un nome di dominio NTLM.</span><span class="sxs-lookup"><span data-stu-id="43af1-144">NT LAN Manager authentication is used, and this parameter contains an NTLM domain name.</span></span> |

`pCtx`\
<span data-ttu-id="43af1-145">in In genere, questo parametro è `null`.</span><span class="sxs-lookup"><span data-stu-id="43af1-145">[in] Typically, this parameter is `null`.</span></span> <span data-ttu-id="43af1-146">In caso contrario, è un puntatore a un oggetto [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) richiesto da uno o più provider di classi dinamici.</span><span class="sxs-lookup"><span data-stu-id="43af1-146">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) object required by one or more dynamic class providers.</span></span>

`ppNamespace`\
<span data-ttu-id="43af1-147">out Quando la funzione restituisce un risultato, riceve un puntatore a un oggetto [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) associato allo spazio dei nomi specificato.</span><span class="sxs-lookup"><span data-stu-id="43af1-147">[out] When the function returns, receives a pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object bound to the specified namespace.</span></span> <span data-ttu-id="43af1-148">Viene impostato in modo da puntare a `null` quando si verifica un errore.</span><span class="sxs-lookup"><span data-stu-id="43af1-148">It is set to point to `null` when there is an error.</span></span>

`impLevel`\
<span data-ttu-id="43af1-149">in Livello di rappresentazione.</span><span class="sxs-lookup"><span data-stu-id="43af1-149">[in] The impersonation level.</span></span>

`authLevel`\
<span data-ttu-id="43af1-150">in Livello di autorizzazione.</span><span class="sxs-lookup"><span data-stu-id="43af1-150">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="43af1-151">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="43af1-151">Return value</span></span>

<span data-ttu-id="43af1-152">I valori seguenti restituiti da questa funzione sono definiti nel file di intestazione *WbemCli. h* oppure è possibile definirli come costanti nel codice:</span><span class="sxs-lookup"><span data-stu-id="43af1-152">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="43af1-153">Costante</span><span class="sxs-lookup"><span data-stu-id="43af1-153">Constant</span></span>  |<span data-ttu-id="43af1-154">Value</span><span class="sxs-lookup"><span data-stu-id="43af1-154">Value</span></span>  |<span data-ttu-id="43af1-155">Descrizione</span><span class="sxs-lookup"><span data-stu-id="43af1-155">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="43af1-156">0x80041001</span><span class="sxs-lookup"><span data-stu-id="43af1-156">0x80041001</span></span> | <span data-ttu-id="43af1-157">Si è verificato un errore generale.</span><span class="sxs-lookup"><span data-stu-id="43af1-157">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="43af1-158">0x80041008</span><span class="sxs-lookup"><span data-stu-id="43af1-158">0x80041008</span></span> | <span data-ttu-id="43af1-159">Parametro non valido.</span><span class="sxs-lookup"><span data-stu-id="43af1-159">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="43af1-160">0x80041006</span><span class="sxs-lookup"><span data-stu-id="43af1-160">0x80041006</span></span> | <span data-ttu-id="43af1-161">Memoria insufficiente per completare l'operazione.</span><span class="sxs-lookup"><span data-stu-id="43af1-161">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="43af1-162">0</span><span class="sxs-lookup"><span data-stu-id="43af1-162">0</span></span> | <span data-ttu-id="43af1-163">La chiamata di funzione è stata completata.</span><span class="sxs-lookup"><span data-stu-id="43af1-163">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="43af1-164">Note</span><span class="sxs-lookup"><span data-stu-id="43af1-164">Remarks</span></span>

<span data-ttu-id="43af1-165">Questa funzione esegue il wrapping di una chiamata al metodo [IWbemLocator:: ConnectServer](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemlocator-connectserver) .</span><span class="sxs-lookup"><span data-stu-id="43af1-165">This function wraps a call to the [IWbemLocator::ConnectServer](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemlocator-connectserver) method.</span></span>

<span data-ttu-id="43af1-166">Per l'accesso locale allo spazio dei nomi predefinito, `strNetworkResource` può essere un percorso di oggetto semplice: "root\default" o "\\.\root\default".</span><span class="sxs-lookup"><span data-stu-id="43af1-166">For local access to the default namespace, `strNetworkResource` can be a simple object path: "root\default" or "\\.\root\default".</span></span> <span data-ttu-id="43af1-167">Per accedere allo spazio dei nomi predefinito in un computer remoto utilizzando la rete COM o compatibile con Microsoft, includere il nome del computer: "\\myserver\root\default".</span><span class="sxs-lookup"><span data-stu-id="43af1-167">For access to the default namespace on a remote computer using COM or Microsoft-compatible networking, include the computer name: "\\myserver\root\default".</span></span> <span data-ttu-id="43af1-168">Il nome del computer può anche essere un nome DNS o un indirizzo IP.</span><span class="sxs-lookup"><span data-stu-id="43af1-168">The computer name also can be a DNS name or IP address.</span></span> <span data-ttu-id="43af1-169">La funzione `ConnectServerWmi` può inoltre connettersi a computer che eseguono IPv6 utilizzando un indirizzo IPv6.</span><span class="sxs-lookup"><span data-stu-id="43af1-169">The `ConnectServerWmi` function can also connect with computers running IPv6 using an IPv6 address.</span></span>

<span data-ttu-id="43af1-170">`strUser` non può essere una stringa vuota.</span><span class="sxs-lookup"><span data-stu-id="43af1-170">`strUser` cannot be an empty string.</span></span> <span data-ttu-id="43af1-171">Se il dominio viene specificato in `strAuthority`, non deve essere incluso anche nel `strUser`oppure la funzione restituisce `WBEM_E_INVALID_PARAMETER`.</span><span class="sxs-lookup"><span data-stu-id="43af1-171">If the domain is specified in `strAuthority`, it must not also be included in `strUser`, or the function returns `WBEM_E_INVALID_PARAMETER`.</span></span>

## <a name="requirements"></a><span data-ttu-id="43af1-172">Requisiti</span><span class="sxs-lookup"><span data-stu-id="43af1-172">Requirements</span></span>

 <span data-ttu-id="43af1-173">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43af1-173">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="43af1-174">**Intestazione:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="43af1-174">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="43af1-175">**Versioni di .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="43af1-175">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="43af1-176">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="43af1-176">See also</span></span>

- [<span data-ttu-id="43af1-177">WMI e contatori delle prestazioni (riferimenti alle API non gestite)</span><span class="sxs-lookup"><span data-stu-id="43af1-177">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
