---
title: Esposizione di componenti .NET Framework a COM
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: e42a65f7-1e61-411f-b09a-aca1bbce24c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1879f5b5aa2fbe6b0e51f9b38fca3af1f4c0cedf
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971766"
---
# <a name="exposing-net-framework-components-to-com"></a><span data-ttu-id="ba64b-102">Esposizione di componenti .NET Framework a COM</span><span class="sxs-lookup"><span data-stu-id="ba64b-102">Exposing .NET Framework Components to COM</span></span>

<span data-ttu-id="ba64b-103">La scrittura di un tipo .NET e l'utilizzo di tale tipo dal codice non gestito sono attività distinte per gli sviluppatori.</span><span class="sxs-lookup"><span data-stu-id="ba64b-103">Writing a .NET type and consuming that type from unmanaged code are distinct activities for developers.</span></span> <span data-ttu-id="ba64b-104">Questa sezione offre diversi suggerimenti per la scrittura di un codice gestito che interagisce con i client COM:</span><span class="sxs-lookup"><span data-stu-id="ba64b-104">This section describes several tips for writing managed code that interoperates with COM clients:</span></span>

- <span data-ttu-id="ba64b-105">[Qualificazione di tipi .NET per l'interoperabilità](../../../docs/standard/native-interop/qualify-net-types-for-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="ba64b-105">[Qualifying .NET types for interoperation](../../../docs/standard/native-interop/qualify-net-types-for-interoperation.md).</span></span>

     <span data-ttu-id="ba64b-106">Tutti i tipi gestiti, i metodi, le proprietà, i campi e gli eventi che si vuole esporre a COM devono essere pubblici.</span><span class="sxs-lookup"><span data-stu-id="ba64b-106">All managed types, methods, properties, fields, and events that you want to expose to COM must be public.</span></span> <span data-ttu-id="ba64b-107">I tipi devono avere un costruttore senza parametri pubblico, che è l'unico costruttore a poter essere richiamato tramite COM.</span><span class="sxs-lookup"><span data-stu-id="ba64b-107">Types must have a public parameterless constructor, which is the only constructor that can be invoked through COM.</span></span>

- <span data-ttu-id="ba64b-108">[Applicazione di attributi di interoperabilità](../../../docs/standard/native-interop/apply-interop-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="ba64b-108">[Applying interop attributes](../../../docs/standard/native-interop/apply-interop-attributes.md).</span></span>

     <span data-ttu-id="ba64b-109">Gli attributi personalizzati nel codice gestito possono migliorare l'interoperabilità di un componente.</span><span class="sxs-lookup"><span data-stu-id="ba64b-109">Custom attributes within managed code can enhance the interoperability of a component.</span></span>

- <span data-ttu-id="ba64b-110">[Preparazione di un assembly per COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span><span class="sxs-lookup"><span data-stu-id="ba64b-110">[Packaging an assembly for COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span></span>

     <span data-ttu-id="ba64b-111">Gli sviluppatori COM potrebbero richiedere di riepilogare i passaggi previsti per fare riferimento agli assembly e distribuirli.</span><span class="sxs-lookup"><span data-stu-id="ba64b-111">COM developers might require that you summarize the steps involved in referencing and deploying your assemblies.</span></span>

 <span data-ttu-id="ba64b-112">Questa sezione indica anche le attività relative all'utilizzo di un tipo gestito da un client COM.</span><span class="sxs-lookup"><span data-stu-id="ba64b-112">Additionally, this section identifies the tasks related to consuming a managed type from a COM client.</span></span>

## <a name="to-consume-a-managed-type-from-com"></a><span data-ttu-id="ba64b-113">Per utilizzare un tipo gestito da COM</span><span class="sxs-lookup"><span data-stu-id="ba64b-113">To consume a managed type from COM</span></span>

1. <span data-ttu-id="ba64b-114">[Registrare gli assembly con COM](../../../docs/framework/interop/registering-assemblies-with-com.md).</span><span class="sxs-lookup"><span data-stu-id="ba64b-114">[Register assemblies with COM](../../../docs/framework/interop/registering-assemblies-with-com.md).</span></span>

     <span data-ttu-id="ba64b-115">I tipi in un assembly (e le librerie dei tipi) devono essere registrati in fase di progettazione.</span><span class="sxs-lookup"><span data-stu-id="ba64b-115">Types in an assembly (and type libraries) must be registered at design time.</span></span> <span data-ttu-id="ba64b-116">Se un programma di installazione non registra l'assembly, comunicare agli sviluppatori COM di usare Regasm.exe.</span><span class="sxs-lookup"><span data-stu-id="ba64b-116">If an installer does not register the assembly, instruct COM developers to use Regasm.exe.</span></span>

2. <span data-ttu-id="ba64b-117">[Fare riferimento a tipi .NET da COM](../../../docs/framework/interop/how-to-reference-net-types-from-com.md).</span><span class="sxs-lookup"><span data-stu-id="ba64b-117">[Reference .NET types from COM](../../../docs/framework/interop/how-to-reference-net-types-from-com.md).</span></span>

     <span data-ttu-id="ba64b-118">Gli sviluppatori COM possono fare riferimento ai tipi in un assembly usando gli strumenti e le tecniche abituali.</span><span class="sxs-lookup"><span data-stu-id="ba64b-118">COM developers can reference types in an assembly using the same tools and techniques they use today.</span></span>

3. <span data-ttu-id="ba64b-119">[Chiamare un oggetto .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ba64b-119">[Call a .NET object](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100)).</span></span>

     <span data-ttu-id="ba64b-120">Gli sviluppatori COM possono chiamare i metodi sull'oggetto .NET nello stesso modo in cui chiamano i metodi sui tipi non gestiti.</span><span class="sxs-lookup"><span data-stu-id="ba64b-120">COM developers can call methods on the .NET object the same way they call methods on any unmanaged type.</span></span> <span data-ttu-id="ba64b-121">Ad esempio, l'API **CoCreateInstance** COM attiva gli oggetti .NET.</span><span class="sxs-lookup"><span data-stu-id="ba64b-121">For example, the COM **CoCreateInstance** API activates .NET objects.</span></span>

4. <span data-ttu-id="ba64b-122">[Distribuire un'applicazione per l'accesso COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ba64b-122">[Deploy an application for COM access](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100)).</span></span>

     <span data-ttu-id="ba64b-123">Un assembly con nome sicuro può essere installato nella Global Assembly Cache e richiede una firma dall'entità di pubblicazione.</span><span class="sxs-lookup"><span data-stu-id="ba64b-123">A strong-named assembly can be installed in the global assembly cache and requires a signature from its publisher.</span></span> <span data-ttu-id="ba64b-124">Gli assembly privi di nome sicuro devono essere installati nella directory dell'applicazione del client.</span><span class="sxs-lookup"><span data-stu-id="ba64b-124">Assemblies that are not strong named must be installed in the application directory of the client.</span></span>

## <a name="see-also"></a><span data-ttu-id="ba64b-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ba64b-125">See also</span></span>

- [<span data-ttu-id="ba64b-126">Interoperabilità con codice non gestito</span><span class="sxs-lookup"><span data-stu-id="ba64b-126">Interoperating with Unmanaged Code</span></span>](../../../docs/framework/interop/index.md)
- [<span data-ttu-id="ba64b-127">Esempio di interoperabilità COM: client COM e server .NET</span><span class="sxs-lookup"><span data-stu-id="ba64b-127">COM Interop Sample: COM Client and .NET Server</span></span>](../../../docs/framework/interop/com-interop-sample-com-client-and-net-server.md)
