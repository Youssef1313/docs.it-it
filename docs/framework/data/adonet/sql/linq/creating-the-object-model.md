---
title: Creazione del modello a oggetti
ms.date: 03/30/2017
ms.assetid: 27afce86-9b1d-45fb-8e0b-636bf671a236
ms.openlocfilehash: 0f1a0d035f2b11f33a9899ededd876155d45de3c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743584"
---
# <a name="creating-the-object-model"></a><span data-ttu-id="63b37-102">Creazione del modello a oggetti</span><span class="sxs-lookup"><span data-stu-id="63b37-102">Creating the Object Model</span></span>
<span data-ttu-id="63b37-103">È possibile creare un modello a oggetti da un database esistente e usare il modello nello stato predefinito.</span><span class="sxs-lookup"><span data-stu-id="63b37-103">You can create your object model from an existing database and use the model in its default state.</span></span> <span data-ttu-id="63b37-104">È anche possibile personalizzare molti aspetti del modello e il relativo comportamento.</span><span class="sxs-lookup"><span data-stu-id="63b37-104">You can also customize many aspects of the model and its behavior.</span></span>  
  
 <span data-ttu-id="63b37-105">Se si usa Visual Studio, è possibile utilizzare Object Relational Designer per creare il modello a oggetti.</span><span class="sxs-lookup"><span data-stu-id="63b37-105">If you are using Visual Studio, you can use the Object Relational Designer to create your object model.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="63b37-106">In questa sezione</span><span class="sxs-lookup"><span data-stu-id="63b37-106">In This Section</span></span>  
 [<span data-ttu-id="63b37-107">Procedura: Generare il modello a oggetti in Visual Basic o C#</span><span class="sxs-lookup"><span data-stu-id="63b37-107">How to: Generate the Object Model in Visual Basic or C#</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)  
 <span data-ttu-id="63b37-108">Viene descritto come usare lo strumento SQLMetal dalla riga di comando.</span><span class="sxs-lookup"><span data-stu-id="63b37-108">Describes how to use the SQLMetal command-line tool.</span></span> <span data-ttu-id="63b37-109">Include anche un collegamento a Object Relational Designer per gli utenti di Visual Studio</span><span class="sxs-lookup"><span data-stu-id="63b37-109">Also provides a link to the Object Relational Designer for Visual Studio users</span></span>  
  
 [<span data-ttu-id="63b37-110">Procedura: Generare il modello a oggetti come File esterno</span><span class="sxs-lookup"><span data-stu-id="63b37-110">How to: Generate the Object Model as an External File</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-as-an-external-file.md)  
 <span data-ttu-id="63b37-111">Viene descritto come generare un file di mapping esterno anziché usare il mapping basato su attributi.</span><span class="sxs-lookup"><span data-stu-id="63b37-111">Describes how to generate an external mapping file instead of using attribute-based mapping.</span></span>  
  
 [<span data-ttu-id="63b37-112">Procedura: Generare codice personalizzato modificando un File DBML</span><span class="sxs-lookup"><span data-stu-id="63b37-112">How to: Generate Customized Code by Modifying a DBML File</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-customized-code-by-modifying-a-dbml-file.md)  
 <span data-ttu-id="63b37-113">Viene descritto come generare Visual Basic o C# codice da un file di metadati DBML.</span><span class="sxs-lookup"><span data-stu-id="63b37-113">Describes how to generate Visual Basic or C# code from a DBML metadata file.</span></span>  
  
 [<span data-ttu-id="63b37-114">Procedura: Convalidare i file di Mapping esterni e DBML</span><span class="sxs-lookup"><span data-stu-id="63b37-114">How to: Validate DBML and External Mapping Files</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md)  
 <span data-ttu-id="63b37-115">Viene descritto come convalidare file di mapping modificati (funzionalità avanzate).</span><span class="sxs-lookup"><span data-stu-id="63b37-115">Describes how to validate mapping files that you have modified (advanced).</span></span>  
  
 [<span data-ttu-id="63b37-116">Procedura: Rendere serializzabili le entità</span><span class="sxs-lookup"><span data-stu-id="63b37-116">How to: Make Entities Serializable</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md)  
 <span data-ttu-id="63b37-117">Viene descritto come aggiungere attributi appropriati per creare entità serializzabili.</span><span class="sxs-lookup"><span data-stu-id="63b37-117">Describes how to add appropriate attributes to make entities serializable.</span></span>  
  
 [<span data-ttu-id="63b37-118">Procedura: Personalizzare le classi di entità usando l'Editor di codice</span><span class="sxs-lookup"><span data-stu-id="63b37-118">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)  
 <span data-ttu-id="63b37-119">Viene descritto come usare l'editor di codice per scrivere codice di mapping o per personalizzare il codice generato.</span><span class="sxs-lookup"><span data-stu-id="63b37-119">Describes how to use the code editor to write your own mapping code, or customize code that has been autogenerated.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="63b37-120">Sezioni correlate</span><span class="sxs-lookup"><span data-stu-id="63b37-120">Related Sections</span></span>  
 [<span data-ttu-id="63b37-121">Modello a oggetti LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="63b37-121">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 <span data-ttu-id="63b37-122">Vengono forniti dettagli sul [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] modello a oggetti.</span><span class="sxs-lookup"><span data-stu-id="63b37-122">Provides details about the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span>  
  
 [<span data-ttu-id="63b37-123">Passaggi tipici per l'utilizzo di LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="63b37-123">Typical Steps for Using LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/typical-steps-for-using-linq-to-sql.md)  
 <span data-ttu-id="63b37-124">Vengono illustrati i passaggi tipici che è necessario seguire per implementare un'applicazione [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63b37-124">Explains the typical steps that you follow to implement a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] application.</span></span>
