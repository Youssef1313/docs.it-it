---
title: SqlClient per Entity Framework
ms.date: 03/30/2017
ms.assetid: 9a5d6d39-d955-43a5-a5c2-931c239398f1
ms.openlocfilehash: e8933a975c075407066bff97672f1b82f125bb47
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662113"
---
# <a name="sqlclient-for-the-entity-framework"></a><span data-ttu-id="c9f12-102">SqlClient per Entity Framework</span><span class="sxs-lookup"><span data-stu-id="c9f12-102">SqlClient for the Entity Framework</span></span>
<span data-ttu-id="c9f12-103">Contenuto della sezione viene descritto il provider di dati .NET Framework per SQL Server (SqlClient), che consente a Entity Framework di funzionare su Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c9f12-103">This section describes the .NET Framework Data Provider for SQL Server (SqlClient), which enables the Entity Framework to work over Microsoft SQL Server.</span></span>  
  
## <a name="provider-schema-attribute"></a><span data-ttu-id="c9f12-104">Attributo Provider dell'elemento Schema</span><span class="sxs-lookup"><span data-stu-id="c9f12-104">Provider Schema Attribute</span></span>  
 <span data-ttu-id="c9f12-105">`Provider` è un attributo dell'elemento `Schema` in SSDL (Store Schema Definition Language).</span><span class="sxs-lookup"><span data-stu-id="c9f12-105">`Provider` is an attribute of the `Schema` element in store schema definition language (SSDL).</span></span>  
  
 <span data-ttu-id="c9f12-106">Per usare SqlClient, assegnare la stringa "System.Data.SqlClient" all'attributo `Provider` dell'elemento `Schema`.</span><span class="sxs-lookup"><span data-stu-id="c9f12-106">To use SqlClient, assign the string "System.Data.SqlClient" to the `Provider` attribute of the `Schema` element.</span></span>  
  
## <a name="providermanifesttoken-schema-attribute"></a><span data-ttu-id="c9f12-107">Attributo ProviderManifestToken dell'elemento Schema</span><span class="sxs-lookup"><span data-stu-id="c9f12-107">ProviderManifestToken Schema Attribute</span></span>  
 <span data-ttu-id="c9f12-108">`ProviderManifestToken` è un attributo obbligatorio dell'elemento `Schema` in SSDL.</span><span class="sxs-lookup"><span data-stu-id="c9f12-108">`ProviderManifestToken` is a required attribute of the `Schema` element in SSDL.</span></span> <span data-ttu-id="c9f12-109">Questo token è usato per caricare il manifesto del provider per gli scenari non in linea.</span><span class="sxs-lookup"><span data-stu-id="c9f12-109">This token is used to load the provider manifest for offline scenarios.</span></span> <span data-ttu-id="c9f12-110">Per altre informazioni sulle `ProviderManifestToken` dell'attributo, vedere [elemento Schema (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl).</span><span class="sxs-lookup"><span data-stu-id="c9f12-110">For more information about `ProviderManifestToken` attribute, see [Schema Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl).</span></span>  
  
 <span data-ttu-id="c9f12-111">SqlClient può essere usato come provider di dati per versioni diverse di SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c9f12-111">SqlClient can be used as a data provider for different versions of SQL Server.</span></span> <span data-ttu-id="c9f12-112">Queste versioni dispongono di funzionalità diverse.</span><span class="sxs-lookup"><span data-stu-id="c9f12-112">These versions have different capabilities.</span></span> <span data-ttu-id="c9f12-113">Ad esempio, SQL Server 2000 non supporta `varchar(max)` e `nvarchar(max)` tipi che sono stati introdotti con SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="c9f12-113">For example, SQL Server 2000 does not support `varchar(max)` and `nvarchar(max)` types that were introduced with SQL Server 2005.</span></span>  
  
 <span data-ttu-id="c9f12-114">SqlClient produce e accetta i token del manifesto del provider seguenti per versioni diverse di SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c9f12-114">SqlClient produces and accepts the following provider manifest tokens for different versions of SQL Server.</span></span>  
  
|<span data-ttu-id="c9f12-115">SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="c9f12-115">SQL Server 2000</span></span>|<span data-ttu-id="c9f12-116">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="c9f12-116">SQL Server 2005</span></span>|<span data-ttu-id="c9f12-117">SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="c9f12-117">SQL Server 2008</span></span>|  
|-|-|-|  
|<span data-ttu-id="c9f12-118">2000</span><span class="sxs-lookup"><span data-stu-id="c9f12-118">2000</span></span>|<span data-ttu-id="c9f12-119">2005</span><span class="sxs-lookup"><span data-stu-id="c9f12-119">2005</span></span>|<span data-ttu-id="c9f12-120">2008</span><span class="sxs-lookup"><span data-stu-id="c9f12-120">2008</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="c9f12-121">A partire da Visual Studio 2010, il [ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) non supportano SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="c9f12-121">Starting with Visual Studio 2010, the [ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) do not support SQL Server 2000.</span></span>  
  
## <a name="provider-namespace-name"></a><span data-ttu-id="c9f12-122">Nome dello spazio dei nomi del provider</span><span class="sxs-lookup"><span data-stu-id="c9f12-122">Provider Namespace Name</span></span>  
 <span data-ttu-id="c9f12-123">Tutti i provider devono specificare uno spazio dei nomi.</span><span class="sxs-lookup"><span data-stu-id="c9f12-123">All providers must specify a namespace.</span></span> <span data-ttu-id="c9f12-124">Questa proprietà consente a Entity Framework di individuare quale prefisso viene usato dal provider per costrutti specifici, ad esempio tipi e funzioni.</span><span class="sxs-lookup"><span data-stu-id="c9f12-124">This property tells the Entity Framework which prefix is used by the provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="c9f12-125">Lo spazio dei nomi per i manifesti del provider SqlClient è `SqlServer`.</span><span class="sxs-lookup"><span data-stu-id="c9f12-125">The namespace for SqlClient provider manifests is `SqlServer`.</span></span> <span data-ttu-id="c9f12-126">Per altre informazioni sugli spazi dei nomi, vedere [spazi dei nomi](../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="c9f12-126">For more information about namespaces, see [Namespaces](../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md).</span></span>  
  
## <a name="types"></a><span data-ttu-id="c9f12-127">Tipi</span><span class="sxs-lookup"><span data-stu-id="c9f12-127">Types</span></span>  
 <span data-ttu-id="c9f12-128">Il provider SqlClient per Entity Framework fornisce informazioni di mapping tra i tipi del modello concettuale e i tipi SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c9f12-128">The SqlClient provider for the Entity Framework provides mapping information between conceptual model types and SQL Server types.</span></span> <span data-ttu-id="c9f12-129">Per altre informazioni, vedere [SqlClient per tipi Entity FrameworkTypes](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).</span><span class="sxs-lookup"><span data-stu-id="c9f12-129">For more information, see [SqlClient for Entity FrameworkTypes](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).</span></span>  
  
## <a name="functions"></a><span data-ttu-id="c9f12-130">Funzioni</span><span class="sxs-lookup"><span data-stu-id="c9f12-130">Functions</span></span>  
 <span data-ttu-id="c9f12-131">Nel provider SqlClient per Entity Framework viene definito l'elenco di funzioni supportate dal provider.</span><span class="sxs-lookup"><span data-stu-id="c9f12-131">The SqlClient provider for the Entity Framework defines the list of functions supported by the provider.</span></span> <span data-ttu-id="c9f12-132">Per un elenco delle funzioni supportate, vedere [SqlClient per funzioni Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="c9f12-132">For a list of the supported functions, see [SqlClient for Entity Framework Functions](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c9f12-133">In questa sezione</span><span class="sxs-lookup"><span data-stu-id="c9f12-133">In This Section</span></span>  
 [<span data-ttu-id="c9f12-134">SqlClient per funzioni Entity Framework</span><span class="sxs-lookup"><span data-stu-id="c9f12-134">SqlClient for Entity Framework Functions</span></span>](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)  
  
 [<span data-ttu-id="c9f12-135">SqlClient per tipi Entity FrameworkTypes</span><span class="sxs-lookup"><span data-stu-id="c9f12-135">SqlClient for Entity FrameworkTypes</span></span>](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md)  
  
 [<span data-ttu-id="c9f12-136">Problemi noti in SqlClient per Entity Framework</span><span class="sxs-lookup"><span data-stu-id="c9f12-136">Known Issues in SqlClient for Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/known-issues-in-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="c9f12-137">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c9f12-137">See also</span></span>

- [<span data-ttu-id="c9f12-138">Linguaggio Entity SQL</span><span class="sxs-lookup"><span data-stu-id="c9f12-138">Entity SQL Language</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
- [<span data-ttu-id="c9f12-139">Riferimenti per il linguaggio</span><span class="sxs-lookup"><span data-stu-id="c9f12-139">Language Reference</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
- [<span data-ttu-id="c9f12-140">Problemi noti di Provider SqlClient per Entity Framework</span><span class="sxs-lookup"><span data-stu-id="c9f12-140">Known Issues in SqlClient Provider for Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)
