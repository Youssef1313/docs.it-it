---
title: Schema delle sezioni di configurazione
ms.date: 05/02/2017
helpviewer_keywords:
- configuration settings [.NET Framework], custom
- schema configuration settings
- configuration sections [.NET Framework]
- custom elements
- configuration schema [.NET Framework], custom settings in configuration files
- elements [.NET Framework], custom settings in configuration files
ms.assetid: 6e4cc793-c526-4007-b4e9-37d56295f2cb
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a17d30af9d7abc3eea6b87d5e8768ac49a7c05ab
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73118926"
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="9ff2d-102">Schema delle sezioni di configurazione</span><span class="sxs-lookup"><span data-stu-id="9ff2d-102">Configuration sections schema</span></span>

<span data-ttu-id="9ff2d-103">Lo schema delle sezioni di configurazione contiene elementi che definiscono impostazioni personalizzate nei file di configurazione.</span><span class="sxs-lookup"><span data-stu-id="9ff2d-103">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="9ff2d-104">Per informazioni generali sui file di configurazione e sugli schemi, vedere [schema dei file di configurazione per il .NET Framework](index.md).</span><span class="sxs-lookup"><span data-stu-id="9ff2d-104">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](index.md).</span></span>

<span data-ttu-id="9ff2d-105">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="9ff2d-105">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="9ff2d-106">[ **\<configSections>** ](configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="9ff2d-106">[**\<configSections>**](configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="9ff2d-107">[ **\<clear>** ](clear-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="9ff2d-107">[**\<clear>**](clear-element-for-configsections.md) </span></span>  
<span data-ttu-id="9ff2d-108">[ **\<remove>** ](remove-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="9ff2d-108">[**\<remove>**](remove-element-for-configsections.md) </span></span>  
<span data-ttu-id="9ff2d-109">[ **\<> sezione**](section-element.md) </span><span class="sxs-lookup"><span data-stu-id="9ff2d-109">[**\<section>**](section-element.md) </span></span>  
[<span data-ttu-id="9ff2d-110"> **\<sectionGroup>** </span><span class="sxs-lookup"><span data-stu-id="9ff2d-110">**\<sectionGroup>**</span></span>](sectiongroup-element-for-configsections.md)

|     | <span data-ttu-id="9ff2d-111">description</span><span class="sxs-lookup"><span data-stu-id="9ff2d-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="9ff2d-112"> **\<deselezionare >** per **\<configSections >** </span><span class="sxs-lookup"><span data-stu-id="9ff2d-112">**\<clear>** for **\<configSections>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="9ff2d-113">Cancella tutte le sezioni e i gruppi di sezioni definiti in precedenza.</span><span class="sxs-lookup"><span data-stu-id="9ff2d-113">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="9ff2d-114"> **\<clear>** </span><span class="sxs-lookup"><span data-stu-id="9ff2d-114">**\<clear>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="9ff2d-115">Cancella tutte le sezioni e i gruppi di sezioni definiti in precedenza.</span><span class="sxs-lookup"><span data-stu-id="9ff2d-115">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="9ff2d-116"> **\<configSections>** </span><span class="sxs-lookup"><span data-stu-id="9ff2d-116">**\<configSections>**</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="9ff2d-117">Contiene la sezione di configurazione e le dichiarazioni dello spazio dei nomi.</span><span class="sxs-lookup"><span data-stu-id="9ff2d-117">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="9ff2d-118"> **\<rimuovere >** per **\<configSections >** </span><span class="sxs-lookup"><span data-stu-id="9ff2d-118">**\<remove>** for **\<configSections>**</span></span>](remove-element-for-configsections.md) | <span data-ttu-id="9ff2d-119">Rimuove una sezione o un gruppo di sezioni predefinito.</span><span class="sxs-lookup"><span data-stu-id="9ff2d-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="9ff2d-120"> **\<sezione >** per **\<configSections >** e **\<sectionGroup >** </span><span class="sxs-lookup"><span data-stu-id="9ff2d-120">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](section-element.md) | <span data-ttu-id="9ff2d-121">Contiene una dichiarazione della sezione di configurazione.</span><span class="sxs-lookup"><span data-stu-id="9ff2d-121">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="9ff2d-122"> **\<> sectionGroup** per **\<configSections >** </span><span class="sxs-lookup"><span data-stu-id="9ff2d-122">**\<sectionGroup>** for **\<configSections>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="9ff2d-123">Definisce uno spazio dei nomi per le sezioni di configurazione.</span><span class="sxs-lookup"><span data-stu-id="9ff2d-123">Defines a namespace for configuration sections.</span></span> |
