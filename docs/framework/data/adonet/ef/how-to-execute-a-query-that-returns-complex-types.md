---
title: 'Procedura: Eseguire una query che restituisce tipi complessi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
ms.openlocfilehash: b08b220e969ad1c400413978c85b2f107d64a688
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854647"
---
# <a name="how-to-execute-a-query-that-returns-complex-types"></a><span data-ttu-id="1110c-102">Procedura: Eseguire una query che restituisce tipi complessi</span><span class="sxs-lookup"><span data-stu-id="1110c-102">How to: Execute a Query that Returns Complex Types</span></span>
<span data-ttu-id="1110c-103">In questo argomento viene illustrato come eseguire una query [!INCLUDE[esql](../../../../../includes/esql-md.md)] che restituisce oggetti del tipo di entità contenenti una proprietà di un tipo complesso.</span><span class="sxs-lookup"><span data-stu-id="1110c-103">This topic shows how to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query that returns entity type objects that contain a property of a complex type.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="1110c-104">Per eseguire il codice in questo esempio</span><span class="sxs-lookup"><span data-stu-id="1110c-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="1110c-105">Aggiungere il [modello Sales di AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) al progetto e configurare il progetto per l'utilizzo del Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="1110c-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="1110c-106">Per altre informazioni, vedere [Procedura: Utilizzare la procedura guidata](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))Entity Data Model.</span><span class="sxs-lookup"><span data-stu-id="1110c-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="1110c-107">Nella tabella codici per l'applicazione aggiungere le istruzioni `using` seguenti (`Imports` in Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="1110c-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3. <span data-ttu-id="1110c-108">Fare doppio clic sul file con estensione edmx per visualizzare il modello nella [finestra browser modello](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738483(v=vs.100)) della Entity Designer.</span><span class="sxs-lookup"><span data-stu-id="1110c-108">Double click the .edmx file to display the model in the [Model Browser window](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738483(v=vs.100)) of the Entity Designer.</span></span> <span data-ttu-id="1110c-109">Nell'area di `Email` Entity Designer selezionare le proprietà e `Phone` del tipo di `Contact` entità, quindi fare clic con il pulsante destro del mouse e selezionare **Effettua refactoring nel nuovo tipo complesso**.</span><span class="sxs-lookup"><span data-stu-id="1110c-109">On the Entity Designer surface, select the `Email` and `Phone` properties of the `Contact` entity type, then right-click and select **Refactor into New Complex Type**.</span></span>  
  
4. <span data-ttu-id="1110c-110">Un nuovo tipo complesso con le proprietà `Email` selezionate `Phone` e viene aggiunto a **browser modello**.</span><span class="sxs-lookup"><span data-stu-id="1110c-110">A new complex type with the selected `Email` and `Phone` properties is added to the **Model Browser**.</span></span> <span data-ttu-id="1110c-111">Al tipo complesso viene assegnato un nome predefinito: rinominare il tipo `EmailPhone` in nella finestra **proprietà** .</span><span class="sxs-lookup"><span data-stu-id="1110c-111">The complex type is given a default name: rename the type to `EmailPhone` in the **Properties** window.</span></span> <span data-ttu-id="1110c-112">Viene inoltre aggiunta, una nuova proprietà `ComplexProperty` al tipo di entità `Contact`.</span><span class="sxs-lookup"><span data-stu-id="1110c-112">Also, a new `ComplexProperty` property is added to the `Contact` entity type.</span></span> <span data-ttu-id="1110c-113">Rinominare la proprietà in `EmailPhoneComplexType.`</span><span class="sxs-lookup"><span data-stu-id="1110c-113">Rename the property to `EmailPhoneComplexType.`</span></span>  
  
     <span data-ttu-id="1110c-114">Per informazioni sulla creazione e la modifica di tipi complessi tramite la procedura guidata Entity Data Model [, vedere Procedura: Effettuare il refactoring delle proprietà esistenti in una](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456814(v=vs.100)) proprietà [di tipo complesso e procedura: Creare e modificare tipi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100))complessi.</span><span class="sxs-lookup"><span data-stu-id="1110c-114">For information about creating and modifying complex types by using the Entity Data Model Wizard, see [How to: Refactor Existing Properties into a Complex Type Property](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456814(v=vs.100)) and [How to: Create and Modify Complex Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1110c-115">Esempio</span><span class="sxs-lookup"><span data-stu-id="1110c-115">Example</span></span>  
 <span data-ttu-id="1110c-116">Nell'esempio seguente viene eseguita una query che restituisce una raccolta di `Contact` oggetti e vengono visualizzate due proprietà `Contact` degli oggetti: `ContactID` e i valori del `EmailPhoneComplexType` tipo complesso.</span><span class="sxs-lookup"><span data-stu-id="1110c-116">The following example executes a query that returns a collection of `Contact` objects and displays two properties of the `Contact` objects: `ContactID` and the values of the `EmailPhoneComplexType` complex type.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]
