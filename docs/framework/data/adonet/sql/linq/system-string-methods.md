---
title: Metodi System.String
ms.date: 03/30/2017
ms.assetid: ce307f14-87e6-4816-8694-8a4147f6b784
ms.openlocfilehash: 583c0d58562c1605f24b61489d481e19248ebed4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792500"
---
# <a name="systemstring-methods"></a><span data-ttu-id="46376-102">Metodi System.String</span><span class="sxs-lookup"><span data-stu-id="46376-102">System.String Methods</span></span>
<span data-ttu-id="46376-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] non sono supportati i metodi <xref:System.String> riportati di seguito.</span><span class="sxs-lookup"><span data-stu-id="46376-103">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not support the following <xref:System.String> methods.</span></span>  
  
## <a name="unsupported-systemstring-methods-in-general"></a><span data-ttu-id="46376-104">Metodi System.String non supportati in generale</span><span class="sxs-lookup"><span data-stu-id="46376-104">Unsupported System.String Methods in General</span></span>  
 <span data-ttu-id="46376-105">Metodi <xref:System.String> non supportati in generale:</span><span class="sxs-lookup"><span data-stu-id="46376-105">Unsupported <xref:System.String> methods in general:</span></span>  
  
- <span data-ttu-id="46376-106">Overload in grado di riconoscere le impostazioni cultura (metodi che `CultureInfo`accettano un  /   /  `StringComparison` `IFormatProvider`).</span><span class="sxs-lookup"><span data-stu-id="46376-106">Culture-aware overloads (methods that take a `CultureInfo` / `StringComparison` / `IFormatProvider`).</span></span>  
  
- <span data-ttu-id="46376-107">Metodi che accettano o producono una matrice `char`.</span><span class="sxs-lookup"><span data-stu-id="46376-107">Methods that take or produce a `char` array.</span></span>  
  
## <a name="unsupported-systemstring-static-methods"></a><span data-ttu-id="46376-108">Metodi System.String statici non supportati</span><span class="sxs-lookup"><span data-stu-id="46376-108">Unsupported System.String Static Methods</span></span>  
  
|<span data-ttu-id="46376-109">Metodi System.String statici non supportati</span><span class="sxs-lookup"><span data-stu-id="46376-109">Unsupported System.String Static Methods</span></span>|  
|----------------------------------------------|  
|<xref:System.String.Copy%28System.String%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.Boolean%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.CompareOrdinal%28System.String%2CSystem.String%29?displayProperty=nameWithType>|  
|<xref:System.String.CompareOrdinal%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|  
  
## <a name="unsupported-systemstring-non-static-methods"></a><span data-ttu-id="46376-110">Metodi System.String non statici non supportati</span><span class="sxs-lookup"><span data-stu-id="46376-110">Unsupported System.String Non-static Methods</span></span>  
  
|<span data-ttu-id="46376-111">Metodi System.String non statici non supportati</span><span class="sxs-lookup"><span data-stu-id="46376-111">Unsupported System.String Non-static Methods</span></span>|  
|---------------------------------------------------|  
|<xref:System.String.IndexOfAny%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.Split%2A?displayProperty=nameWithType>|  
|<xref:System.String.ToCharArray?displayProperty=nameWithType>|  
|<xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimEnd%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimStart%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
  
## <a name="differences-from-net"></a><span data-ttu-id="46376-112">Differenze rispetto a .NET</span><span class="sxs-lookup"><span data-stu-id="46376-112">Differences from .NET</span></span>  
  
- <span data-ttu-id="46376-113">Nelle query non vengono considerate le regole di confronto di SQL Server eventualmente attive sul server pertanto, per impostazione predefinita, verranno restituite regole di confronto dipendenti dalle impostazioni cultura e senza distinzione fra maiuscole e minuscole.</span><span class="sxs-lookup"><span data-stu-id="46376-113">Queries do not account for SQL Server collations that might be in effect on the server, and therefore will provide culture-sensitive, case-insensitive comparisons by default.</span></span> <span data-ttu-id="46376-114">Questo comportamento differisce dalla semantica predefinita con distinzione tra maiuscole e minuscole di .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="46376-114">This behavior differs from the default, case-sensitive semantics of the .NET Framework.</span></span>  
  
- <span data-ttu-id="46376-115">Quando `LastIndexOf` restituisce 0, la stringa è `NULL` o la posizione trovata è 0.</span><span class="sxs-lookup"><span data-stu-id="46376-115">When `LastIndexOf` returns 0, either the string is `NULL` or the found position is 0.</span></span>  
  
- <span data-ttu-id="46376-116">È possibile che vengano restituiti risultati imprevisti dalla concatenazione o da altre operazioni sulle stringhe a lunghezza fissa (`CHAR`, `NCHAR`), poiché a questi tipi viene applicata automaticamente la spaziatura interna nel database.</span><span class="sxs-lookup"><span data-stu-id="46376-116">Unexpected results might be returned from concatenation or other operations on fixed-length strings (`CHAR`, `NCHAR`), because these types automatically have padding applied in the database.</span></span>  
  
- <span data-ttu-id="46376-117">Poiché molti metodi, ad esempio `Replace`, `ToLower`, `ToUpper` e l'indicizzatore del carattere, non dispongono di una conversione valida per le colonne `TEXT` o `NTEXT` e XML, se vengono convertiti normalmente si verifica un'eccezione `SqlExceptions`.</span><span class="sxs-lookup"><span data-stu-id="46376-117">Because many methods, such as `Replace`, `ToLower`, `ToUpper`, and the character indexer, have no valid translation for `TEXT` or `NTEXT` columns and XML, `SqlExceptions` occur if translated normally.</span></span> <span data-ttu-id="46376-118">Questo comportamento viene considerato accettabile per questi tipi.</span><span class="sxs-lookup"><span data-stu-id="46376-118">This behavior is considered acceptable for these types.</span></span> <span data-ttu-id="46376-119">Tuttavia è necessario che tutte le operazioni stringa corrispondano alla semantica Common Language Runtime (CLR) per `VARCHAR`, `NVARCHAR`, `VARCHAR(max)` e `NVARCHAR(max)`.</span><span class="sxs-lookup"><span data-stu-id="46376-119">However, all string operations must match common language runtime (CLR) semantics for `VARCHAR`, `NVARCHAR`, `VARCHAR(max)`, and `NVARCHAR(max)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46376-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="46376-120">See also</span></span>

- [<span data-ttu-id="46376-121">Tipi di dati e funzioni</span><span class="sxs-lookup"><span data-stu-id="46376-121">Data Types and Functions</span></span>](data-types-and-functions.md)
