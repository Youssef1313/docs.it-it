---
title: '#pragma - Riferimenti per C#'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 65ca38ff6993117b6ed9f716d4ac93ba2d4a9ddf
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605660"
---
# <a name="pragma-c-reference"></a><span data-ttu-id="a4a9e-102">#pragma (Riferimenti per C#)</span><span class="sxs-lookup"><span data-stu-id="a4a9e-102">#pragma (C# Reference)</span></span>
<span data-ttu-id="a4a9e-103">`#pragma` fornisce al compilatore istruzioni speciali per la compilazione del file in cui si trova.</span><span class="sxs-lookup"><span data-stu-id="a4a9e-103">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="a4a9e-104">Le istruzioni devono essere supportate dal compilatore.</span><span class="sxs-lookup"><span data-stu-id="a4a9e-104">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="a4a9e-105">In altre parole, non è possibile usare `#pragma` per creare istruzioni di pre-elaborazione personalizzate.</span><span class="sxs-lookup"><span data-stu-id="a4a9e-105">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="a4a9e-106">Il compilatore Microsoft C# supporta le due istruzioni `#pragma` seguenti:</span><span class="sxs-lookup"><span data-stu-id="a4a9e-106">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="a4a9e-107">avviso #pragma</span><span class="sxs-lookup"><span data-stu-id="a4a9e-107">#pragma warning</span></span>](./preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="a4a9e-108">checksum #pragma</span><span class="sxs-lookup"><span data-stu-id="a4a9e-108">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="a4a9e-109">Sintassi</span><span class="sxs-lookup"><span data-stu-id="a4a9e-109">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4a9e-110">Parametri</span><span class="sxs-lookup"><span data-stu-id="a4a9e-110">Parameters</span></span>  
 `pragma-name`  
 <span data-ttu-id="a4a9e-111">Nome di un pragma riconosciuto.</span><span class="sxs-lookup"><span data-stu-id="a4a9e-111">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="a4a9e-112">Argomenti specifici del pragma.</span><span class="sxs-lookup"><span data-stu-id="a4a9e-112">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4a9e-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a4a9e-113">See also</span></span>

- [<span data-ttu-id="a4a9e-114">Riferimenti per C#</span><span class="sxs-lookup"><span data-stu-id="a4a9e-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a4a9e-115">Guida per programmatori C#</span><span class="sxs-lookup"><span data-stu-id="a4a9e-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a4a9e-116">Direttive per il preprocessore C#</span><span class="sxs-lookup"><span data-stu-id="a4a9e-116">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="a4a9e-117">avviso #pragma</span><span class="sxs-lookup"><span data-stu-id="a4a9e-117">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="a4a9e-118">checksum #pragma</span><span class="sxs-lookup"><span data-stu-id="a4a9e-118">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)
