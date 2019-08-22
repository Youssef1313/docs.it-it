---
title: <useLegacyJit> Elemento
ms.date: 04/26/2017
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d79479d1836963fcbdaaf8d40bfc3648b88c4a3
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663403"
---
# <a name="uselegacyjit-element"></a><span data-ttu-id="dc7bb-102">Elemento \<useLegacyJit></span><span class="sxs-lookup"><span data-stu-id="dc7bb-102">\<useLegacyJit> Element</span></span>

<span data-ttu-id="dc7bb-103">Determina se Common Language Runtime usa il compilatore JIT a 64 bit legacy per la compilazione JIT.</span><span class="sxs-lookup"><span data-stu-id="dc7bb-103">Determines whether the common language runtime uses the legacy 64-bit JIT compiler for just-in-time compilation.</span></span>  
  
<span data-ttu-id="dc7bb-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="dc7bb-104">\<configuration></span></span>  
<span data-ttu-id="dc7bb-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="dc7bb-105">\<runtime></span></span>  
<span data-ttu-id="dc7bb-106">\<useLegacyJit></span><span class="sxs-lookup"><span data-stu-id="dc7bb-106">\<useLegacyJit></span></span>
  
## <a name="syntax"></a><span data-ttu-id="dc7bb-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="dc7bb-107">Syntax</span></span>  
  
```xml
<useLegacyJit enabled=0|1 />
```

<span data-ttu-id="dc7bb-108">Il nome `useLegacyJit` dell'elemento fa distinzione tra maiuscole e minuscole.</span><span class="sxs-lookup"><span data-stu-id="dc7bb-108">The element name `useLegacyJit` is case-sensitive.</span></span>
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dc7bb-109">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="dc7bb-109">Attributes and elements</span></span>

<span data-ttu-id="dc7bb-110">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="dc7bb-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc7bb-111">Attributi</span><span class="sxs-lookup"><span data-stu-id="dc7bb-111">Attributes</span></span>  
  
| <span data-ttu-id="dc7bb-112">Attributo</span><span class="sxs-lookup"><span data-stu-id="dc7bb-112">Attribute</span></span> | <span data-ttu-id="dc7bb-113">Descrizione</span><span class="sxs-lookup"><span data-stu-id="dc7bb-113">Description</span></span>                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | <span data-ttu-id="dc7bb-114">Attributo obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="dc7bb-114">Required attribute.</span></span><br><br><span data-ttu-id="dc7bb-115">Specifica se il runtime usa il compilatore JIT a 64 bit legacy.</span><span class="sxs-lookup"><span data-stu-id="dc7bb-115">Specifies whether the runtime uses the legacy 64-bit JIT compiler.</span></span> |  
  
### <a name="enabled-attribute"></a><span data-ttu-id="dc7bb-116">attributo enabled</span><span class="sxs-lookup"><span data-stu-id="dc7bb-116">enabled attribute</span></span>  
  
| <span data-ttu-id="dc7bb-117">Value</span><span class="sxs-lookup"><span data-stu-id="dc7bb-117">Value</span></span> | <span data-ttu-id="dc7bb-118">Descrizione</span><span class="sxs-lookup"><span data-stu-id="dc7bb-118">Description</span></span>                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| <span data-ttu-id="dc7bb-119">0</span><span class="sxs-lookup"><span data-stu-id="dc7bb-119">0</span></span>     | <span data-ttu-id="dc7bb-120">Il Common Language Runtime usa il nuovo compilatore JIT a 64 bit incluso in .NET Framework 4,6 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="dc7bb-120">The common language runtime uses the new 64-bit JIT compiler included in the .NET Framework 4.6 and later versions.</span></span> |  
| <span data-ttu-id="dc7bb-121">1</span><span class="sxs-lookup"><span data-stu-id="dc7bb-121">1</span></span>     | <span data-ttu-id="dc7bb-122">Il Common Language Runtime usa il compilatore JIT a 64 bit precedente.</span><span class="sxs-lookup"><span data-stu-id="dc7bb-122">The common language runtime uses the older 64-bit JIT compiler.</span></span>                                                     |  
  
### <a name="child-elements"></a><span data-ttu-id="dc7bb-123">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="dc7bb-123">Child elements</span></span>

<span data-ttu-id="dc7bb-124">Nessuna</span><span class="sxs-lookup"><span data-stu-id="dc7bb-124">None</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="dc7bb-125">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="dc7bb-125">Parent elements</span></span>  
  
| <span data-ttu-id="dc7bb-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="dc7bb-126">Element</span></span>         | <span data-ttu-id="dc7bb-127">Descrizione</span><span class="sxs-lookup"><span data-stu-id="dc7bb-127">Description</span></span>                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | <span data-ttu-id="dc7bb-128">Elemento radice in ciascun file di configurazione usato in Common Language Runtime e nelle applicazioni .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dc7bb-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |  
| `runtime`       | <span data-ttu-id="dc7bb-129">Contiene informazioni sulle opzioni di inizializzazione in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="dc7bb-129">Contains information about runtime initialization options.</span></span>                                                        |  
  
## <a name="remarks"></a><span data-ttu-id="dc7bb-130">Note</span><span class="sxs-lookup"><span data-stu-id="dc7bb-130">Remarks</span></span>  

<span data-ttu-id="dc7bb-131">A partire da .NET Framework 4,6, il Common Language Runtime usa un nuovo compilatore a 64 bit per la compilazione JIT (just-in-Time) per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="dc7bb-131">Starting with the .NET Framework 4.6, the common language runtime uses a new 64-bit compiler for Just-In-Time (JIT) compilation by default.</span></span> <span data-ttu-id="dc7bb-132">In alcuni casi, questo può comportare una differenza nel comportamento del codice dell'applicazione compilato tramite JIT dalla versione precedente del compilatore JIT a 64 bit.</span><span class="sxs-lookup"><span data-stu-id="dc7bb-132">In some cases, this may result in a difference in behavior from application code that was JIT-compiled by the previous version of the 64-bit JIT compiler.</span></span> <span data-ttu-id="dc7bb-133">Impostando l' `enabled` attributo `<useLegacyJit>` dell'elemento su, `1`è possibile disabilitare il nuovo compilatore JIT a 64 bit e compilare l'app usando il compilatore JIT legacy a 64 bit.</span><span class="sxs-lookup"><span data-stu-id="dc7bb-133">By setting the `enabled` attribute of the `<useLegacyJit>` element to `1`, you can disable the new 64-bit JIT compiler and instead compile your app using the legacy 64-bit JIT compiler.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dc7bb-134">L' `<useLegacyJit>` elemento interessa solo la compilazione JIT a 64 bit.</span><span class="sxs-lookup"><span data-stu-id="dc7bb-134">The `<useLegacyJit>` element affects 64-bit JIT compilation only.</span></span> <span data-ttu-id="dc7bb-135">La compilazione con il compilatore JIT a 32 bit non è interessata.</span><span class="sxs-lookup"><span data-stu-id="dc7bb-135">Compilation with the 32-bit JIT compiler is unaffected.</span></span>  
  
<span data-ttu-id="dc7bb-136">Invece di usare un'impostazione del file di configurazione, è possibile abilitare il compilatore JIT a 64 bit legacy in altri due modi:</span><span class="sxs-lookup"><span data-stu-id="dc7bb-136">Instead of using a configuration file setting, you can enable the legacy 64-bit JIT compiler in two other ways:</span></span>  
  
- <span data-ttu-id="dc7bb-137">Impostazione di una variabile di ambiente</span><span class="sxs-lookup"><span data-stu-id="dc7bb-137">Setting an environment variable</span></span>

  <span data-ttu-id="dc7bb-138">Impostare la `COMPLUS_useLegacyJit` variabile `0` di ambiente su (usare il nuovo compilatore JIT a 64 bit) o `1` (usare il compilatore JIT a 64 bit precedente):</span><span class="sxs-lookup"><span data-stu-id="dc7bb-138">Set the `COMPLUS_useLegacyJit` environment variable to either `0` (use the new 64-bit JIT compiler) or `1` (use the older 64-bit JIT compiler):</span></span>
  
  ```  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  <span data-ttu-id="dc7bb-139">La variabile di ambiente ha *ambito globale*, il che significa che ha effetto su tutte le applicazioni eseguite nel computer.</span><span class="sxs-lookup"><span data-stu-id="dc7bb-139">The environment variable has *global scope*, which means that it affects all applications run on the machine.</span></span> <span data-ttu-id="dc7bb-140">Se impostato, è possibile eseguire l'override dell'impostazione del file di configurazione dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="dc7bb-140">If set, it can be overridden by the application configuration file setting.</span></span> <span data-ttu-id="dc7bb-141">Il nome della variabile di ambiente non distingue tra maiuscole e minuscole.</span><span class="sxs-lookup"><span data-stu-id="dc7bb-141">The environment variable name is not case-sensitive.</span></span>
  
- <span data-ttu-id="dc7bb-142">Aggiunta di una chiave del registro di sistema</span><span class="sxs-lookup"><span data-stu-id="dc7bb-142">Adding a registry key</span></span>

  <span data-ttu-id="dc7bb-143">È possibile abilitare il compilatore JIT a 64 bit legacy aggiungendo un `REG_DWORD` valore alla `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` chiave o `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` nel registro di sistema.</span><span class="sxs-lookup"><span data-stu-id="dc7bb-143">You can enable the legacy 64-bit JIT compiler by adding a `REG_DWORD` value to either the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` or `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key in the registry.</span></span> <span data-ttu-id="dc7bb-144">Il valore è denominato `useLegacyJit`.</span><span class="sxs-lookup"><span data-stu-id="dc7bb-144">The value is named `useLegacyJit`.</span></span> <span data-ttu-id="dc7bb-145">Se il valore è 0, viene utilizzato il nuovo compilatore.</span><span class="sxs-lookup"><span data-stu-id="dc7bb-145">If the value is 0, the new compiler is used.</span></span> <span data-ttu-id="dc7bb-146">Se il valore è 1, il compilatore JIT a 64 bit legacy è abilitato.</span><span class="sxs-lookup"><span data-stu-id="dc7bb-146">If the value is 1, the legacy 64-bit JIT compiler is enabled.</span></span> <span data-ttu-id="dc7bb-147">Il nome del valore del registro di sistema non distingue tra maiuscole e minuscole.</span><span class="sxs-lookup"><span data-stu-id="dc7bb-147">The registry value name is not case-sensitive.</span></span>
  
  <span data-ttu-id="dc7bb-148">L'aggiunta del valore alla `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` chiave influiscono su tutte le app in esecuzione nel computer.</span><span class="sxs-lookup"><span data-stu-id="dc7bb-148">Adding the value to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key affects all apps running on the machine.</span></span> <span data-ttu-id="dc7bb-149">L'aggiunta del valore alla `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` chiave influiscono su tutte le app eseguite dall'utente corrente.</span><span class="sxs-lookup"><span data-stu-id="dc7bb-149">Adding the value to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key affects all apps run by the current user.</span></span> <span data-ttu-id="dc7bb-150">Se un computer è configurato con più account utente, vengono interessate solo le app eseguite dall'utente corrente, a meno che il valore non venga aggiunto anche alle chiavi del registro di sistema per altri utenti.</span><span class="sxs-lookup"><span data-stu-id="dc7bb-150">If a machine is configured with multiple user accounts, only apps run by the current user are affected, unless the value is added to the registry keys for other users as well.</span></span> <span data-ttu-id="dc7bb-151">L'aggiunta `<useLegacyJit>` dell'elemento a un file di configurazione sostituisce le impostazioni del registro di sistema, se presenti.</span><span class="sxs-lookup"><span data-stu-id="dc7bb-151">Adding the `<useLegacyJit>` element to a configuration file overrides the registry settings, if they're present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc7bb-152">Esempio</span><span class="sxs-lookup"><span data-stu-id="dc7bb-152">Example</span></span>  

<span data-ttu-id="dc7bb-153">Il file di configurazione seguente disabilita la compilazione con il nuovo compilatore JIT a 64 bit e usa invece il compilatore JIT legacy a 64 bit.</span><span class="sxs-lookup"><span data-stu-id="dc7bb-153">The following configuration file disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dc7bb-154">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="dc7bb-154">See also</span></span>

- [<span data-ttu-id="dc7bb-155">\<Elemento runtime ></span><span class="sxs-lookup"><span data-stu-id="dc7bb-155">\<runtime> Element</span></span>](runtime-element.md)
- [<span data-ttu-id="dc7bb-156">Elemento \<configuration></span><span class="sxs-lookup"><span data-stu-id="dc7bb-156">\<configuration> Element</span></span>](../configuration-element.md)
- [<span data-ttu-id="dc7bb-157">Mitigazione Nuovo compilatore JIT a 64 bit</span><span class="sxs-lookup"><span data-stu-id="dc7bb-157">Mitigation: New 64-bit JIT Compiler</span></span>](../../../migration-guide/mitigation-new-64-bit-jit-compiler.md)
