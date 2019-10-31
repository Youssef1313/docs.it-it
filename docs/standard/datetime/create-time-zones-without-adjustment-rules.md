---
title: 'Procedura: creare fusi orari senza regole di regolazione'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], adjustment rule
- time zones [.NET Framework], creating
- adjustment rule [.NET Framework]
ms.assetid: a6af8647-7893-4f29-95a9-d94c65a6e8dd
ms.openlocfilehash: 344d8307318d5a2e50eddb39ef488cd8c5f2fdac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129111"
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a><span data-ttu-id="c73df-102">Procedura: creare fusi orari senza regole di regolazione</span><span class="sxs-lookup"><span data-stu-id="c73df-102">How to: Create time zones without adjustment rules</span></span>

<span data-ttu-id="c73df-103">Le informazioni esatte sul fuso orario richieste da un'applicazione potrebbero non essere presenti in un sistema specifico per diversi motivi:</span><span class="sxs-lookup"><span data-stu-id="c73df-103">The precise time zone information that is required by an application may not be present on a particular system for several reasons:</span></span>

- <span data-ttu-id="c73df-104">Il fuso orario non è mai stato definito nel registro di sistema del sistema locale.</span><span class="sxs-lookup"><span data-stu-id="c73df-104">The time zone has never been defined in the local system's registry.</span></span>

- <span data-ttu-id="c73df-105">I dati relativi al fuso orario sono stati modificati o rimossi dal registro di sistema.</span><span class="sxs-lookup"><span data-stu-id="c73df-105">Data about the time zone has been modified or removed from the registry.</span></span>

- <span data-ttu-id="c73df-106">Il fuso orario esiste ma non dispone di informazioni accurate sulle regolazioni del fuso orario per un determinato periodo cronologico.</span><span class="sxs-lookup"><span data-stu-id="c73df-106">The time zone exists but does not have accurate information about time zone adjustments for a particular historic period.</span></span>

<span data-ttu-id="c73df-107">In questi casi, è possibile chiamare il metodo <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> per definire il fuso orario richiesto dall'applicazione.</span><span class="sxs-lookup"><span data-stu-id="c73df-107">In these cases, you can call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method to define the time zone required by your application.</span></span> <span data-ttu-id="c73df-108">È possibile usare gli overload di questo metodo per creare un fuso orario con o senza regole di regolazione.</span><span class="sxs-lookup"><span data-stu-id="c73df-108">You can use the overloads of this method to create a time zone with or without adjustment rules.</span></span> <span data-ttu-id="c73df-109">Se il fuso orario supporta l'ora legale, è possibile definire le regolazioni con regole di rettifica fisse o mobili.</span><span class="sxs-lookup"><span data-stu-id="c73df-109">If the time zone supports daylight saving time, you can define adjustments with either fixed or floating adjustment rules.</span></span> <span data-ttu-id="c73df-110">Per le definizioni di questi termini, vedere la sezione "terminologia del fuso orario" nella [Panoramica del fuso orario](../../../docs/standard/datetime/time-zone-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c73df-110">(For definitions of these terms, see the "Time Zone Terminology" section in [Time zone overview](../../../docs/standard/datetime/time-zone-overview.md).)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c73df-111">I fusi orari personalizzati creati chiamando il metodo <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> non vengono aggiunti al registro di sistema.</span><span class="sxs-lookup"><span data-stu-id="c73df-111">Custom time zones created by calling the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method are not added to the registry.</span></span> <span data-ttu-id="c73df-112">Al contrario, è possibile accedervi solo tramite il riferimento all'oggetto restituito dalla chiamata al metodo <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>.</span><span class="sxs-lookup"><span data-stu-id="c73df-112">Instead, they can be accessed only through the object reference returned by the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method call.</span></span>

<span data-ttu-id="c73df-113">In questo argomento viene illustrato come creare un fuso orario senza regole di rettifica.</span><span class="sxs-lookup"><span data-stu-id="c73df-113">This topic shows how to create a time zone without adjustment rules.</span></span> <span data-ttu-id="c73df-114">Per creare un fuso orario che supporta le regole di regolazione dell'ora legale, vedere [procedura: creare fusi orari con regole di rettifica](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span><span class="sxs-lookup"><span data-stu-id="c73df-114">To create a time zone that supports daylight saving time adjustment rules, see [How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span></span>

### <a name="to-create-a-time-zone-without-adjustment-rules"></a><span data-ttu-id="c73df-115">Per creare un fuso orario senza regole di rettifica</span><span class="sxs-lookup"><span data-stu-id="c73df-115">To create a time zone without adjustment rules</span></span>

1. <span data-ttu-id="c73df-116">Definire il nome visualizzato del fuso orario.</span><span class="sxs-lookup"><span data-stu-id="c73df-116">Define the time zone's display name.</span></span>

   <span data-ttu-id="c73df-117">Il nome visualizzato segue un formato abbastanza standard in cui l'offset del fuso orario rispetto all'ora UTC (Coordinated Universal Time) è racchiuso tra parentesi ed è seguito da una stringa che identifica il fuso orario, una o più città nel fuso orario o una o più delle condizioni ntries o aree del fuso orario.</span><span class="sxs-lookup"><span data-stu-id="c73df-117">The display name follows a fairly standard format in which the time zone's offset from Coordinated Universal Time (UTC) is enclosed in parentheses and is followed by a string that identifies the time zone, one or more of the cities in the time zone, or one or more of the countries or regions in the time zone.</span></span>

2. <span data-ttu-id="c73df-118">Definire il nome dell'ora solare del fuso orario.</span><span class="sxs-lookup"><span data-stu-id="c73df-118">Define the name of the time zone's standard time.</span></span> <span data-ttu-id="c73df-119">In genere, questa stringa viene usata anche come identificatore del fuso orario.</span><span class="sxs-lookup"><span data-stu-id="c73df-119">Typically, this string is also used as the time zone's identifier.</span></span>

3. <span data-ttu-id="c73df-120">Se si vuole usare un identificatore diverso dal nome standard del fuso orario, definire l'identificatore del fuso orario.</span><span class="sxs-lookup"><span data-stu-id="c73df-120">If you want to use a different identifier than the time zone's standard name, define the time zone identifier.</span></span>

4. <span data-ttu-id="c73df-121">Creare un'istanza di un oggetto <xref:System.TimeSpan> che definisce l'offset del fuso orario rispetto all'ora UTC.</span><span class="sxs-lookup"><span data-stu-id="c73df-121">Instantiate a <xref:System.TimeSpan> object that defines the time zone's offset from UTC.</span></span> <span data-ttu-id="c73df-122">I fusi orari con tempi successivi all'ora UTC hanno un offset positivo.</span><span class="sxs-lookup"><span data-stu-id="c73df-122">Time zones with times that are later than UTC have a positive offset.</span></span> <span data-ttu-id="c73df-123">I fusi orari con tempi precedenti all'ora UTC hanno un offset negativo.</span><span class="sxs-lookup"><span data-stu-id="c73df-123">Time zones with times that are earlier than UTC have a negative offset.</span></span>

5. <span data-ttu-id="c73df-124">Chiamare il metodo <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> per creare un'istanza del nuovo fuso orario.</span><span class="sxs-lookup"><span data-stu-id="c73df-124">Call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> method to instantiate the new time zone.</span></span>

## <a name="example"></a><span data-ttu-id="c73df-125">Esempio</span><span class="sxs-lookup"><span data-stu-id="c73df-125">Example</span></span>

<span data-ttu-id="c73df-126">Nell'esempio seguente viene definito un fuso orario personalizzato per Mawson, Antartide, che non dispone di regole di rettifica.</span><span class="sxs-lookup"><span data-stu-id="c73df-126">The following example defines a custom time zone for Mawson, Antarctica, which has no adjustment rules.</span></span>

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

<span data-ttu-id="c73df-127">La stringa assegnata alla proprietà <xref:System.TimeZoneInfo.DisplayName%2A> segue un formato standard in cui l'offset del fuso orario rispetto all'ora UTC è seguito da una descrizione descrittiva del fuso orario.</span><span class="sxs-lookup"><span data-stu-id="c73df-127">The string assigned to the <xref:System.TimeZoneInfo.DisplayName%2A> property follows a standard format in which the time zone's offset from UTC is followed by a friendly description of the time zone.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="c73df-128">Compilazione del codice</span><span class="sxs-lookup"><span data-stu-id="c73df-128">Compiling the code</span></span>

<span data-ttu-id="c73df-129">L'esempio presenta i requisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="c73df-129">This example requires:</span></span>

- <span data-ttu-id="c73df-130">Che vengano importati gli spazi dei nomi seguenti:</span><span class="sxs-lookup"><span data-stu-id="c73df-130">That the following namespaces be imported:</span></span>

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a><span data-ttu-id="c73df-131">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c73df-131">See also</span></span>

- [<span data-ttu-id="c73df-132">Date, ore e fusi orari</span><span class="sxs-lookup"><span data-stu-id="c73df-132">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="c73df-133">Panoramica sui fusi orari</span><span class="sxs-lookup"><span data-stu-id="c73df-133">Time zone overview</span></span>](../../../docs/standard/datetime/time-zone-overview.md)
- [<span data-ttu-id="c73df-134">Procedura: Creare fusi orari con regole di regolazione</span><span class="sxs-lookup"><span data-stu-id="c73df-134">How to: Create time zones with adjustment rules</span></span>](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)
