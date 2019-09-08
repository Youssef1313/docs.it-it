---
title: Pool di connessioni
ms.date: 03/30/2017
ms.assetid: 955c057f-aea8-4ba8-aa6d-e3dfa18ba8d5
ms.openlocfilehash: c431011cf57fd9ef79c2f0a099ab1080116c571f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786716"
---
# <a name="connection-pooling"></a><span data-ttu-id="7998f-102">Pool di connessioni</span><span class="sxs-lookup"><span data-stu-id="7998f-102">Connection Pooling</span></span>
<span data-ttu-id="7998f-103">La connessione a un'origine dati può richiedere molto tempo.</span><span class="sxs-lookup"><span data-stu-id="7998f-103">Connecting to a data source can be time consuming.</span></span> <span data-ttu-id="7998f-104">Per ridurre al minimo il costo dell'apertura delle connessioni, ADO.NET usa una tecnica di ottimizzazione denominata *pool*di connessioni, che riduce al minimo il costo di apertura e chiusura ripetute delle connessioni.</span><span class="sxs-lookup"><span data-stu-id="7998f-104">To minimize the cost of opening connections, ADO.NET uses an optimization technique called *connection pooling*, which minimizes the cost of repeatedly opening and closing connections.</span></span> <span data-ttu-id="7998f-105">Per i provider di dati .NET Framework il pool di connessioni viene gestito in modo diverso.</span><span class="sxs-lookup"><span data-stu-id="7998f-105">Connection pooling is handled differently for the .NET Framework data providers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7998f-106">In questa sezione</span><span class="sxs-lookup"><span data-stu-id="7998f-106">In This Section</span></span>  
 [<span data-ttu-id="7998f-107">Pool di connessioni SQL Server (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="7998f-107">SQL Server Connection Pooling (ADO.NET)</span></span>](sql-server-connection-pooling.md)  
 <span data-ttu-id="7998f-108">Viene fornita una panoramica del pool di connessioni e viene descritto il funzionamento del pool di connessioni in SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7998f-108">Provides an overview of connection pooling and describes how connection pooling works in SQL Server.</span></span>  
  
 [<span data-ttu-id="7998f-109">Pool di connessioni OLE DB, ODBC e Oracle</span><span class="sxs-lookup"><span data-stu-id="7998f-109">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](ole-db-odbc-and-oracle-connection-pooling.md)  
 <span data-ttu-id="7998f-110">Viene descritto l'uso del pool di connessioni con i provider di dati .NET Framework per OLE DB, ODBC e Oracle.</span><span class="sxs-lookup"><span data-stu-id="7998f-110">Describes connection pooling for the .NET Framework Data Provider for OLE DB, the .NET Framework Data Provider for ODBC, and the .NET Framework Data Provider for Oracle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7998f-111">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7998f-111">See also</span></span>

- [<span data-ttu-id="7998f-112">Recupero e modifica di dati in ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7998f-112">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="7998f-113">Panoramica di ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7998f-113">ADO.NET Overview</span></span>](ado-net-overview.md)
