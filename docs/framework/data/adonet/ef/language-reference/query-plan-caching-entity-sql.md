---
title: Memorizzazione nella cache di piani di query (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 90b0c685-5ef2-461b-98b4-c3c0a2b253c7
ms.openlocfilehash: ca95f3aed5c092247a97bbfe5b0237a45b95ae16
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249294"
---
# <a name="query-plan-caching-entity-sql"></a><span data-ttu-id="d712f-102">Memorizzazione nella cache di piani di query (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d712f-102">Query Plan Caching (Entity SQL)</span></span>
<span data-ttu-id="d712f-103">Ogni volta che viene fatto un tentativo di eseguire una query, la pipeline di query analizza il proprio piano di query per verificare se la query esatta è già stata compilata ed è disponibile.</span><span class="sxs-lookup"><span data-stu-id="d712f-103">Whenever an attempt to execute a query is made, the query pipeline looks up its query plan cache to see whether the exact query is already compiled and available.</span></span> <span data-ttu-id="d712f-104">In caso affermativo, viene riutilizzato il piano memorizzato nella cache anziché compilarne un nuovo.</span><span class="sxs-lookup"><span data-stu-id="d712f-104">If so, it reuses the cached plan rather than building a new one.</span></span> <span data-ttu-id="d712f-105">Se non viene individuata una corrispondenza nella cache dei piani di query, la query viene compilata e memorizzata nella cache.</span><span class="sxs-lookup"><span data-stu-id="d712f-105">If a match is not found in the query plan cache, the query is compiled and cached.</span></span> <span data-ttu-id="d712f-106">Una query è identificata dal testo [!INCLUDE[esql](../../../../../../includes/esql-md.md)] e dalla raccolta di parametri (nomi e tipi).</span><span class="sxs-lookup"><span data-stu-id="d712f-106">A query is identified by its [!INCLUDE[esql](../../../../../../includes/esql-md.md)] text and parameter collection (names and types).</span></span> <span data-ttu-id="d712f-107">In tutti i confronti di testo viene fatta distinzione tra maiuscole e minuscole.</span><span class="sxs-lookup"><span data-stu-id="d712f-107">All text comparisons are case-sensitive.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="d712f-108">Configurazione</span><span class="sxs-lookup"><span data-stu-id="d712f-108">Configuration</span></span>  
 <span data-ttu-id="d712f-109">La memorizzazione nella cache del piano di query può essere configurata tramite <xref:System.Data.EntityClient.EntityCommand>.</span><span class="sxs-lookup"><span data-stu-id="d712f-109">Query plan caching is configurable through the <xref:System.Data.EntityClient.EntityCommand>.</span></span>  
  
 <span data-ttu-id="d712f-110">Per abilitare o disabilitare la memorizzazione nella cache del piano di query tramite <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, impostare questa proprietà su `true` o su `false`.</span><span class="sxs-lookup"><span data-stu-id="d712f-110">To enable or disable query plan caching through <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, set this property to `true` or `false`.</span></span> <span data-ttu-id="d712f-111">Disattivando la memorizzazione nella cache del piano di query per singole query dinamiche che non verranno probabilmente usate più di una volta è possibile migliorare le prestazioni.</span><span class="sxs-lookup"><span data-stu-id="d712f-111">Disabling plan caching for individual dynamic queries that are unlikely to be used more then once improves performance.</span></span>  
  
 <span data-ttu-id="d712f-112">È possibile abilitare la memorizzazione nella cache del piano di query tramite <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.</span><span class="sxs-lookup"><span data-stu-id="d712f-112">You can enable query plan caching through <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.</span></span>  
  
## <a name="recommended-practice"></a><span data-ttu-id="d712f-113">Procedure consigliate</span><span class="sxs-lookup"><span data-stu-id="d712f-113">Recommended Practice</span></span>  
 <span data-ttu-id="d712f-114">In genere, è consigliabile evitare le query dinamiche.</span><span class="sxs-lookup"><span data-stu-id="d712f-114">Dynamic queries should be avoided, in general.</span></span> <span data-ttu-id="d712f-115">L'esempio di query dinamica seguente è vulnerabile ad attacchi SQL injection, in quanto usa direttamente l'input dell'utente senza alcuna convalida.</span><span class="sxs-lookup"><span data-stu-id="d712f-115">The following dynamic query example is vulnerable to SQL injection attacks, because it takes user input directly without any validation.</span></span>  
  
 `"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp WHERE sp.EmployeeID = " + employeeTextBox.Text;`  
  
 <span data-ttu-id="d712f-116">Se si usano query dinamicamente generate, disabilitare la memorizzazione nella cache del piano di query per evitare un consumo di memoria non necessario per le voci della cache con poche probabilità di riutilizzo.</span><span class="sxs-lookup"><span data-stu-id="d712f-116">If you do use dynamically generated queries, consider disabling query plan caching to avoid unnecessary memory consumption for cache entries that are unlikely to be reused.</span></span>  
  
 <span data-ttu-id="d712f-117">La memorizzazione nella cache del piano di query per le query statiche e con parametri può offrire vantaggi a livello di prestazioni.</span><span class="sxs-lookup"><span data-stu-id="d712f-117">Query plan caching on static queries and parameterized queries can provide performance benefits.</span></span> <span data-ttu-id="d712f-118">Di seguito è riportato un esempio di query statica:</span><span class="sxs-lookup"><span data-stu-id="d712f-118">The following is an example of a static query:</span></span>  
  
```  
"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp";  
```  
  
 <span data-ttu-id="d712f-119">Per garantire una corretta individuazione della corrispondenza delle query con la cache dei piani di query, è necessario che le query siano conformi ai requisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="d712f-119">For queries to be matched properly by the query plan cache, they should comply with the following requirements:</span></span>  
  
- <span data-ttu-id="d712f-120">Il testo delle query deve essere un modello costante, preferibilmente una risorsa o una stringa costante.</span><span class="sxs-lookup"><span data-stu-id="d712f-120">Query text should be a constant pattern, preferably a constant string or a resource.</span></span>  
  
- <span data-ttu-id="d712f-121">È necessario usare <xref:System.Data.EntityClient.EntityParameter> o <xref:System.Data.Objects.ObjectParameter> in ogni situazione in cui deve essere passato un valore fornito dall'utente.</span><span class="sxs-lookup"><span data-stu-id="d712f-121"><xref:System.Data.EntityClient.EntityParameter> or <xref:System.Data.Objects.ObjectParameter> should be used wherever a user-supplied value must be passed.</span></span>  
  
 <span data-ttu-id="d712f-122">È necessario evitare i modelli di query seguenti, che usano inutilmente slot nella cache dei piani di query:</span><span class="sxs-lookup"><span data-stu-id="d712f-122">You should avoid the following query patterns, which unnecessarily consume slots in the query plan cache:</span></span>  
  
- <span data-ttu-id="d712f-123">Conversione di caratteri maiuscoli in minuscoli o viceversa nel testo.</span><span class="sxs-lookup"><span data-stu-id="d712f-123">Changes to letter case in the text.</span></span>  
  
- <span data-ttu-id="d712f-124">Modifiche degli spazi vuoti.</span><span class="sxs-lookup"><span data-stu-id="d712f-124">Changes to white space.</span></span>  
  
- <span data-ttu-id="d712f-125">Modifiche dei valori letterali.</span><span class="sxs-lookup"><span data-stu-id="d712f-125">Changes to literal values.</span></span>  
  
- <span data-ttu-id="d712f-126">Modifiche del testo nei commenti.</span><span class="sxs-lookup"><span data-stu-id="d712f-126">Changes to text inside comments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d712f-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d712f-127">See also</span></span>

- [<span data-ttu-id="d712f-128">Panoramica di Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d712f-128">Entity SQL Overview</span></span>](entity-sql-overview.md)
