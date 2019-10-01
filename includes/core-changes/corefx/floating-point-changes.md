---
ms.openlocfilehash: ce4f09908b1025e8e5a0380c9bf035c6b0db479a
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182015"
---
### <a name="floating-point-formatting-and-parsing-behavior-changed"></a><span data-ttu-id="0151c-101">Modifica del comportamento di analisi e formattazione a virgola mobile</span><span class="sxs-lookup"><span data-stu-id="0151c-101">Floating-point formatting and parsing behavior changed</span></span>

<span data-ttu-id="0151c-102">L'analisi a virgola mobile e il comportamento di <xref:System.Double> formattazione <xref:System.Single> (per i tipi e) sono ora conformi a IEEE.</span><span class="sxs-lookup"><span data-stu-id="0151c-102">Floating point parsing and formatting behavior (by the <xref:System.Double> and <xref:System.Single> types) are now IEEE-compliant.</span></span>

#### <a name="change-description"></a><span data-ttu-id="0151c-103">Descrizione della modifica</span><span class="sxs-lookup"><span data-stu-id="0151c-103">Change description</span></span>

<span data-ttu-id="0151c-104">In .NET Core 2,2 e versioni precedenti, la formattazione <xref:System.Double.ToString%2A?displayProperty=nameWithType> con <xref:System.Single.ToString%2A?displayProperty=nameWithType>e e l'analisi con <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>e <xref:System.Single.TryParse%2A?displayProperty=nameWithType> non sono conformi a IEEE.</span><span class="sxs-lookup"><span data-stu-id="0151c-104">In .NET Core 2.2 and earlier versions, formatting with <xref:System.Double.ToString%2A?displayProperty=nameWithType> and <xref:System.Single.ToString%2A?displayProperty=nameWithType>, and parsing with <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> are not IEEE-compliant.</span></span> <span data-ttu-id="0151c-105">Di conseguenza, è impossibile garantire che un valore venga round trip con qualsiasi stringa di formato standard o personalizzata supportata.</span><span class="sxs-lookup"><span data-stu-id="0151c-105">As a result, it is impossible to guarantee that a value will roundtrip with any supported standard or custom format string.</span></span> <span data-ttu-id="0151c-106">Per alcuni input, il tentativo di analizzare un valore formattato può avere esito negativo e, per altri, il valore analizzato non è uguale al valore originale.</span><span class="sxs-lookup"><span data-stu-id="0151c-106">For some inputs, the attempt to parse a formatted value can fail, and for others, the parsed value doesn't equal the original value.</span></span>

<span data-ttu-id="0151c-107">A partire da .NET Core 3,0, le operazioni di analisi e formattazione sono conformi a IEEE 754.</span><span class="sxs-lookup"><span data-stu-id="0151c-107">Starting with .NET Core 3.0, parsing and formatting operations are IEEE 754-compliant.</span></span> <span data-ttu-id="0151c-108">Ciò garantisce che il comportamento dei tipi a virgola mobile in .NET corrisponda a quello di linguaggi conformi C#a IEEE, ad esempio.</span><span class="sxs-lookup"><span data-stu-id="0151c-108">This ensures that the behavior of floating-point types in .NET matches that of IEEE-compliant languages such as C#.</span></span> <span data-ttu-id="0151c-109">Per ulteriori informazioni, vedere la pagina relativa ai miglioramenti apportati all' [analisi e alla formattazione a virgola mobile nel post di Blog di .NET Core 3,0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) .</span><span class="sxs-lookup"><span data-stu-id="0151c-109">For more information, see the [Floating-point parsing and formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0151c-110">Versione introdotta</span><span class="sxs-lookup"><span data-stu-id="0151c-110">Version introduced</span></span>

<span data-ttu-id="0151c-111">3.0</span><span class="sxs-lookup"><span data-stu-id="0151c-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0151c-112">Azione consigliata</span><span class="sxs-lookup"><span data-stu-id="0151c-112">Recommended action</span></span>

<span data-ttu-id="0151c-113">La sezione "impatto potenziale sul codice esistente" dei miglioramenti apportati all' [analisi e alla formattazione a virgola mobile nel](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) post di Blog di .net core 3,0 suggerisce le modifiche al codice se si osserva una modifica del comportamento rispetto alle applicazioni .net core 2,2 in genere. Ciò comporta l'uso di una stringa di formato standard o personalizzata diversa per applicare il comportamento desiderato.</span><span class="sxs-lookup"><span data-stu-id="0151c-113">The "Potential impact to existing code" section of the [Floating-point parsing and formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post suggests changes to your code if you observe a change of behavior when compared to .NET Core 2.2 applications Generally, this involves using a different standard or custom format string to enforce the desired behavior.</span></span> <span data-ttu-id="0151c-114">Alcuni risultati potrebbero non avere una soluzione alternativa se in precedenza non erano corretti.</span><span class="sxs-lookup"><span data-stu-id="0151c-114">Some results may not have a workaround if they were previously incorrect.</span></span>

#### <a name="category"></a><span data-ttu-id="0151c-115">Category</span><span class="sxs-lookup"><span data-stu-id="0151c-115">Category</span></span>

<span data-ttu-id="0151c-116">CoreFx</span><span class="sxs-lookup"><span data-stu-id="0151c-116">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0151c-117">API interessate</span><span class="sxs-lookup"><span data-stu-id="0151c-117">Affected APIs</span></span>

- <xref:System.Double.ToString%2A?displayProperty=nameWithType>
- <xref:System.Single.ToString%2A?displayProperty=nameWithType>
- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `Overload:System.Double.ToString`
- `Overload:System.Single.ToString`
- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->