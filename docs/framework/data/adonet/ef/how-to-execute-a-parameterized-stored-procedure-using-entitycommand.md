---
title: 'Procedura: Eseguire una stored procedure con parametri tramite EntityCommand'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4f5639bf-bb7f-4982-bb1d-c7caa4348888
ms.openlocfilehash: a2196be1a5fb6b9c676542ab5bcc74b1824df9cc
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251517"
---
# <a name="how-to-execute-a-parameterized-stored-procedure-using-entitycommand"></a><span data-ttu-id="d6ef6-102">Procedura: Eseguire una stored procedure con parametri tramite EntityCommand</span><span class="sxs-lookup"><span data-stu-id="d6ef6-102">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>
<span data-ttu-id="d6ef6-103">In questo argomento viene mostrato come eseguire una stored procedure con parametri usando la classe <xref:System.Data.EntityClient.EntityCommand>.</span><span class="sxs-lookup"><span data-stu-id="d6ef6-103">This topic shows how to execute a parameterized stored procedure by using the <xref:System.Data.EntityClient.EntityCommand> class.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="d6ef6-104">Per eseguire il codice in questo esempio</span><span class="sxs-lookup"><span data-stu-id="d6ef6-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="d6ef6-105">Aggiungere il [modello School](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) al progetto e configurare il progetto per l' [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]uso di.</span><span class="sxs-lookup"><span data-stu-id="d6ef6-105">Add the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="d6ef6-106">Per altre informazioni, vedere [Procedura: Utilizzare la procedura guidata](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))Entity Data Model.</span><span class="sxs-lookup"><span data-stu-id="d6ef6-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="d6ef6-107">Nella tabella codici per l'applicazione aggiungere le istruzioni `using` seguenti (`Imports` in Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="d6ef6-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3. <span data-ttu-id="d6ef6-108">Importare la stored procedure `GetStudentGrades` e specificare entità `CourseGrade` come tipo restituito.</span><span class="sxs-lookup"><span data-stu-id="d6ef6-108">Import the `GetStudentGrades` stored procedure and specify `CourseGrade` entities as a return type.</span></span> <span data-ttu-id="d6ef6-109">Per informazioni su come importare una stored procedure, vedere [procedura: Importare una stored procedure](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896231(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d6ef6-109">For information on how to import a stored procedure, see [How to: Import a Stored Procedure](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896231(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6ef6-110">Esempio</span><span class="sxs-lookup"><span data-stu-id="d6ef6-110">Example</span></span>  
 <span data-ttu-id="d6ef6-111">Nel codice seguente viene eseguita la stored procedure `GetStudentGrades`, dove `StudentId` è un parametro obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="d6ef6-111">The following code executes the `GetStudentGrades` stored procedure where `StudentId` is a required parameter.</span></span> <span data-ttu-id="d6ef6-112">I risultati vengono quindi letti da <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="d6ef6-112">The results are then read by an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#storedprocwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#storedprocwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="d6ef6-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d6ef6-113">See also</span></span>

- [<span data-ttu-id="d6ef6-114">Provider EntityClient per Entity Framework</span><span class="sxs-lookup"><span data-stu-id="d6ef6-114">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)
