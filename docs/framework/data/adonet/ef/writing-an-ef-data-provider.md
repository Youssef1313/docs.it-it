---
title: Scrittura di un provider di dati Entity Framework
ms.date: 03/30/2017
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
ms.openlocfilehash: 6c5e6e2859b48db6c982862381d223a4c9deb2c5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248184"
---
# <a name="writing-an-entity-framework-data-provider"></a><span data-ttu-id="4a7af-102">Scrittura di un provider di dati Entity Framework</span><span class="sxs-lookup"><span data-stu-id="4a7af-102">Writing an Entity Framework Data Provider</span></span>
<span data-ttu-id="4a7af-103">In questa sezione viene illustrato come scrivere [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] un provider per supportare un'origine dati diversa da SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4a7af-103">This section discusses how to write an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider to support a data source other than SQL Server.</span></span> <span data-ttu-id="4a7af-104">In [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] è incluso un provider che supporta SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4a7af-104">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] includes a provider that supports SQL Server.</span></span>  
  
## <a name="introducing-the-entity-framework-provider-model"></a><span data-ttu-id="4a7af-105">Introduzione al modello di provider Entity Framework</span><span class="sxs-lookup"><span data-stu-id="4a7af-105">Introducing the Entity Framework Provider Model</span></span>  
 <span data-ttu-id="4a7af-106">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] è indipendente dal database ed è possibile scrivere un provider usando il modello di provider ADO.NET per connettersi a un set di origini dati differente.</span><span class="sxs-lookup"><span data-stu-id="4a7af-106">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] is database independent, and you can write a provider by using the ADO.NET Provider Model to connect to a diverse set of data sources.</span></span>  
  
 <span data-ttu-id="4a7af-107">Il provider di dati Entity Framework, compilato usando il modello di provider di dati ADO.NET, consente di eseguire le funzioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="4a7af-107">The Entity Framework data provider (built using the ADO.NET Data Provider model) performs the following functions:</span></span>  
  
- <span data-ttu-id="4a7af-108">Mapping dei tipi primitivi EDM (Entity Data Model) ai tipi di provider.</span><span class="sxs-lookup"><span data-stu-id="4a7af-108">Maps Entity Data Model (EDM) primitive types to provider types.</span></span>  
  
- <span data-ttu-id="4a7af-109">Esposizione delle funzioni specifiche del provider.</span><span class="sxs-lookup"><span data-stu-id="4a7af-109">Exposes provider-specific functions.</span></span>  
  
- <span data-ttu-id="4a7af-110">Generazione di comandi specifici del provider per un determinato DbQueryCommandTree per supportare le query [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4a7af-110">Generates provider-specific commands for a given DbQueryCommandTree to support [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] queries.</span></span>  
  
- <span data-ttu-id="4a7af-111">Generazione di comandi di aggiornamento specifici del provider per un determinato DbModificationCommandTree per supportare gli aggiornamenti mediante [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4a7af-111">Generates provider-specific update commands for a given DbModificationCommandTree to support updates through the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  
  
- <span data-ttu-id="4a7af-112">Esposizione di file di mapping per la definizione dello schema di archiviazione per supportare la generazione di un modello basato su un database.</span><span class="sxs-lookup"><span data-stu-id="4a7af-112">Exposes mapping files for the store schema definition, to support generation of a model based on a database.</span></span>  
  
- <span data-ttu-id="4a7af-113">Esposizione di metadati, ad esempio tabelle e visualizzazioni, mediante un modello concettuale.</span><span class="sxs-lookup"><span data-stu-id="4a7af-113">Exposes metadata (tables and views, for example) via a conceptual model.</span></span>  
  
 <span data-ttu-id="4a7af-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](./media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span><span class="sxs-lookup"><span data-stu-id="4a7af-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](./media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span></span>  
  
## <a name="sample"></a><span data-ttu-id="4a7af-115">Esempio</span><span class="sxs-lookup"><span data-stu-id="4a7af-115">Sample</span></span>  
 <span data-ttu-id="4a7af-116">Vedere il [provider di esempio Entity Framework](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) per un esempio di [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider che supporta un'origine dati diversa da SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4a7af-116">See the [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) for a sample of an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider that supports a data source other than SQL Server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4a7af-117">In questa sezione</span><span class="sxs-lookup"><span data-stu-id="4a7af-117">In This Section</span></span>  
 [<span data-ttu-id="4a7af-118">Generazione SQL</span><span class="sxs-lookup"><span data-stu-id="4a7af-118">SQL Generation</span></span>](sql-generation.md)  
  
 [<span data-ttu-id="4a7af-119">Generazione di comandi SQL di modifica</span><span class="sxs-lookup"><span data-stu-id="4a7af-119">Modification SQL Generation</span></span>](modification-sql-generation.md)  
  
 [<span data-ttu-id="4a7af-120">Specifica del manifesto del provider</span><span class="sxs-lookup"><span data-stu-id="4a7af-120">Provider Manifest Specification</span></span>](provider-manifest-specification.md)  
  
## <a name="see-also"></a><span data-ttu-id="4a7af-121">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4a7af-121">See also</span></span>

- [<span data-ttu-id="4a7af-122">Uso di provider di dati</span><span class="sxs-lookup"><span data-stu-id="4a7af-122">Working with Data Providers</span></span>](working-with-data-providers.md)
