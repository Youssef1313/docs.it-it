---
title: Impostazioni di configurazione della compilazione
description: Informazioni sulle impostazioni della fase di esecuzione che configurano il funzionamento del compilatore JIT per le app .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: bcc445b6edc48d9432ee614b0b19c9c25621f4a0
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802820"
---
# <a name="run-time-configuration-options-for-compilation"></a><span data-ttu-id="5b585-103">Opzioni di configurazione della fase di esecuzione per la compilazione</span><span class="sxs-lookup"><span data-stu-id="5b585-103">Run-time configuration options for compilation</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="5b585-104">Compilazione a livelli</span><span class="sxs-lookup"><span data-stu-id="5b585-104">Tiered compilation</span></span>

- <span data-ttu-id="5b585-105">Configura se il compilatore JIT utilizza la [compilazione a livelli](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="5b585-105">Configures whether the JIT compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span>
- <span data-ttu-id="5b585-106">In .NET Core 3,0 e versioni successive la compilazione a più livelli è abilitata per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="5b585-106">In .NET Core 3.0 and later, tiered compilation is enabled by default.</span></span>
- <span data-ttu-id="5b585-107">In .NET Core 2,1 e 2,2 la compilazione a più livelli è disabilitata per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="5b585-107">In .NET Core 2.1 and 2.2, tiered compilation is disabled by default.</span></span>

| | <span data-ttu-id="5b585-108">Nome impostazione</span><span class="sxs-lookup"><span data-stu-id="5b585-108">Setting name</span></span> | <span data-ttu-id="5b585-109">Valori</span><span class="sxs-lookup"><span data-stu-id="5b585-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="5b585-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="5b585-110">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation` | <span data-ttu-id="5b585-111">Abilitazione di `true`</span><span class="sxs-lookup"><span data-stu-id="5b585-111">`true` - enabled</span></span><br/><span data-ttu-id="5b585-112">`false` disabilitato</span><span class="sxs-lookup"><span data-stu-id="5b585-112">`false` - disabled</span></span> |
| <span data-ttu-id="5b585-113">**Variabile di ambiente**</span><span class="sxs-lookup"><span data-stu-id="5b585-113">**Environment variable**</span></span> | `COMPlus_TieredCompilation` | <span data-ttu-id="5b585-114">Abilitazione di `1`</span><span class="sxs-lookup"><span data-stu-id="5b585-114">`1` - enabled</span></span><br/><span data-ttu-id="5b585-115">`0` disabilitato</span><span class="sxs-lookup"><span data-stu-id="5b585-115">`0` - disabled</span></span> |
