---
title: 'Procedura: Eseguire la conversione tra stringhe esadecimali e tipi numerici - Guida per programmatori C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
ms.openlocfilehash: a7109945192fe1577cd1b96c8b4d6c05270d54e8
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588379"
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a><span data-ttu-id="bb7ad-102">Procedura: Eseguire la conversione tra stringhe esadecimali e tipi numerici (Guida per programmatori C#)</span><span class="sxs-lookup"><span data-stu-id="bb7ad-102">How to: Convert Between Hexadecimal Strings and Numeric Types (C# Programming Guide)</span></span>
<span data-ttu-id="bb7ad-103">In questi esempi viene mostrato come effettuare le seguenti attività:</span><span class="sxs-lookup"><span data-stu-id="bb7ad-103">These examples show you how to perform the following tasks:</span></span>  
  
- <span data-ttu-id="bb7ad-104">Ottenere il valore esadecimale di ogni carattere in un oggetto [string](../../language-reference/keywords/string.md).</span><span class="sxs-lookup"><span data-stu-id="bb7ad-104">Obtain the hexadecimal value of each character in a [string](../../language-reference/keywords/string.md).</span></span>  
  
- <span data-ttu-id="bb7ad-105">Ottenere l'oggetto [char](../../language-reference/keywords/char.md) che corrisponde a ogni valore in una stringa esadecimale.</span><span class="sxs-lookup"><span data-stu-id="bb7ad-105">Obtain the [char](../../language-reference/keywords/char.md) that corresponds to each value in a hexadecimal string.</span></span>  
  
- <span data-ttu-id="bb7ad-106">Convertire un oggetto `string` esadecimale in un oggetto [int](../../language-reference/builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="bb7ad-106">Convert a hexadecimal `string` to an [int](../../language-reference/builtin-types/integral-numeric-types.md).</span></span>  
  
- <span data-ttu-id="bb7ad-107">Convertire un oggetto `string` esadecimale in un oggetto [float](../../language-reference/builtin-types/floating-point-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="bb7ad-107">Convert a hexadecimal `string` to a [float](../../language-reference/builtin-types/floating-point-numeric-types.md).</span></span>  
  
- <span data-ttu-id="bb7ad-108">Convertire una matrice di [byte](../../language-reference/builtin-types/integral-numeric-types.md) in un oggetto `string` esadecimale.</span><span class="sxs-lookup"><span data-stu-id="bb7ad-108">Convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal `string`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb7ad-109">Esempio</span><span class="sxs-lookup"><span data-stu-id="bb7ad-109">Example</span></span>  
 <span data-ttu-id="bb7ad-110">Questo esempio restituisce il valore esadecimale di ogni carattere in un oggetto `string`.</span><span class="sxs-lookup"><span data-stu-id="bb7ad-110">This example outputs the hexadecimal value of each character in a `string`.</span></span> <span data-ttu-id="bb7ad-111">Prima viene analizzato l'oggetto `string` in una matrice di caratteri.</span><span class="sxs-lookup"><span data-stu-id="bb7ad-111">First it parses the `string` to an array of characters.</span></span> <span data-ttu-id="bb7ad-112">Poi viene chiamato <xref:System.Convert.ToInt32%28System.Char%29> in ogni carattere per ottenere il rispettivo valore numerico.</span><span class="sxs-lookup"><span data-stu-id="bb7ad-112">Then it calls <xref:System.Convert.ToInt32%28System.Char%29> on each character to obtain its numeric value.</span></span> <span data-ttu-id="bb7ad-113">Il numero viene infine formattato come esadecimale in un oggetto `string`.</span><span class="sxs-lookup"><span data-stu-id="bb7ad-113">Finally, it formats the number as its hexadecimal representation in a `string`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#30)]  
  
## <a name="example"></a><span data-ttu-id="bb7ad-114">Esempio</span><span class="sxs-lookup"><span data-stu-id="bb7ad-114">Example</span></span>  
 <span data-ttu-id="bb7ad-115">Questo esempio analizza un oggetto `string` di valori esadecimali e restituisce il carattere corrispondente a ogni valore esadecimale.</span><span class="sxs-lookup"><span data-stu-id="bb7ad-115">This example parses a `string` of hexadecimal values and outputs the character corresponding to each hexadecimal value.</span></span> <span data-ttu-id="bb7ad-116">Prima viene chiamato il metodo [Split(Char\[\])](xref:System.String.Split(System.Char[])) per ottenere ogni valore esadecimale come singolo oggetto `string` in una matrice.</span><span class="sxs-lookup"><span data-stu-id="bb7ad-116">First it calls the [Split(Char\[\])](xref:System.String.Split(System.Char[])) method to obtain each hexadecimal value as an individual `string` in an array.</span></span> <span data-ttu-id="bb7ad-117">Poi viene chiamato <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> per convertire il valore esadecimale in un valore decimale rappresentato come [int](../../language-reference/builtin-types/integral-numeric-types.md). Per ottenere il carattere corrispondente al codice di tale carattere vengono illustrate due modalità diverse.</span><span class="sxs-lookup"><span data-stu-id="bb7ad-117">Then it calls <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> to convert the hexadecimal value to a decimal value represented as an [int](../../language-reference/builtin-types/integral-numeric-types.md). It shows two different ways to obtain the character corresponding to that character code.</span></span> <span data-ttu-id="bb7ad-118">La prima tecnica usa `string` che restituisce il carattere corrispondente all'argomento Integer come <xref:System.Char.ConvertFromUtf32%28System.Int32%29>.</span><span class="sxs-lookup"><span data-stu-id="bb7ad-118">The first technique uses <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, which returns the character corresponding to the integer argument as a `string`.</span></span> <span data-ttu-id="bb7ad-119">La seconda tecnica esegue il cast in modo esplicito del valore `int` a un valore [char](../../language-reference/keywords/char.md).</span><span class="sxs-lookup"><span data-stu-id="bb7ad-119">The second technique explicitly casts the `int` to a [char](../../language-reference/keywords/char.md).</span></span>  
  
 [!code-csharp[csProgGuideTypes#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#31)]  
  
## <a name="example"></a><span data-ttu-id="bb7ad-120">Esempio</span><span class="sxs-lookup"><span data-stu-id="bb7ad-120">Example</span></span>  
 <span data-ttu-id="bb7ad-121">Questo esempio illustra un altro modo per convertire un valore esadecimale `string` in un Integer, chiamando il metodo <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29>.</span><span class="sxs-lookup"><span data-stu-id="bb7ad-121">This example shows another way to convert a hexadecimal `string` to an integer, by calling the <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#32)]  
  
## <a name="example"></a><span data-ttu-id="bb7ad-122">Esempio</span><span class="sxs-lookup"><span data-stu-id="bb7ad-122">Example</span></span>  
 <span data-ttu-id="bb7ad-123">L'esempio seguente illustra come convertire un tipo `string` esadecimale in [float](../../language-reference/builtin-types/floating-point-numeric-types.md) usando la classe <xref:System.BitConverter?displayProperty=nameWithType> e il metodo <xref:System.UInt32.Parse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bb7ad-123">The following example shows how to convert a hexadecimal `string` to a [float](../../language-reference/builtin-types/floating-point-numeric-types.md) by using the <xref:System.BitConverter?displayProperty=nameWithType> class and the <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#39)]  
  
## <a name="example"></a><span data-ttu-id="bb7ad-124">Esempio</span><span class="sxs-lookup"><span data-stu-id="bb7ad-124">Example</span></span>  
 <span data-ttu-id="bb7ad-125">L'esempio seguente illustra come convertire una matrice [byte](../../language-reference/builtin-types/integral-numeric-types.md) in una stringa esadecimale tramite la classe <xref:System.BitConverter?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bb7ad-125">The following example shows how to convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal string by using the <xref:System.BitConverter?displayProperty=nameWithType> class.</span></span>  
  
 [!code-csharp[csProgGuideTypes#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="bb7ad-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="bb7ad-126">See also</span></span>

- [<span data-ttu-id="bb7ad-127">Standard Numeric Format Strings</span><span class="sxs-lookup"><span data-stu-id="bb7ad-127">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="bb7ad-128">Tipi</span><span class="sxs-lookup"><span data-stu-id="bb7ad-128">Types</span></span>](./index.md)
- [<span data-ttu-id="bb7ad-129">Procedura: Determinare se una stringa rappresenta un valore numerico</span><span class="sxs-lookup"><span data-stu-id="bb7ad-129">How to: Determine Whether a String Represents a Numeric Value</span></span>](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
