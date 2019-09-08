---
title: 'Procedura dettagliata: Eseguire query tra relazioni (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: a7da43e3-769f-4e07-bcd6-552b8bde66f4
ms.openlocfilehash: 3164656bb183e7773b098cab79d8fe5e0dc5de34
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792151"
---
# <a name="walkthrough-querying-across-relationships-visual-basic"></a><span data-ttu-id="1b2d4-102">Procedura dettagliata: Eseguire query tra relazioni (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b2d4-102">Walkthrough: Querying Across Relationships (Visual Basic)</span></span>
<span data-ttu-id="1b2d4-103">In questa procedura dettagliata viene illustrato [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] l'utilizzo delle *associazioni* per rappresentare relazioni di chiave esterna nel database.</span><span class="sxs-lookup"><span data-stu-id="1b2d4-103">This walkthrough demonstrates the use of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *associations* to represent foreign-key relationships in the database.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="1b2d4-104">Questa procedura dettagliata è stata scritta usando Impostazioni di sviluppo di Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1b2d4-104">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="1b2d4-105">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="1b2d4-105">Prerequisites</span></span>  
 <span data-ttu-id="1b2d4-106">È necessario avere completato [la procedura dettagliata: Modello a oggetti e query semplici (Visual Basic](walkthrough-simple-object-model-and-query-visual-basic.md)).</span><span class="sxs-lookup"><span data-stu-id="1b2d4-106">You must have completed [Walkthrough: Simple Object Model and Query (Visual Basic)](walkthrough-simple-object-model-and-query-visual-basic.md).</span></span> <span data-ttu-id="1b2d4-107">Questa procedura dettagliata si basa su tale procedura dettagliata, inclusa la presenza del file northwnd.mdf in c:\linqtest.</span><span class="sxs-lookup"><span data-stu-id="1b2d4-107">This walkthrough builds on that one, including the presence of the northwnd.mdf file in c:\linqtest.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="1b2d4-108">Panoramica</span><span class="sxs-lookup"><span data-stu-id="1b2d4-108">Overview</span></span>  
 <span data-ttu-id="1b2d4-109">La procedura dettagliata è costituita da tre attività principali:</span><span class="sxs-lookup"><span data-stu-id="1b2d4-109">This walkthrough consists of three main tasks:</span></span>  
  
- <span data-ttu-id="1b2d4-110">Aggiunta di una classe di entità per rappresentare la tabella Orders nel database di esempio Northwind.</span><span class="sxs-lookup"><span data-stu-id="1b2d4-110">Adding an entity class to represent the Orders table in the sample Northwind database.</span></span>  
  
- <span data-ttu-id="1b2d4-111">Completamento delle annotazioni alla classe `Customer` per migliorare la relazione tra le classi `Customer` e `Order`.</span><span class="sxs-lookup"><span data-stu-id="1b2d4-111">Supplementing annotations to the `Customer` class to enhance the relationship between the `Customer` and `Order` classes.</span></span>  
  
- <span data-ttu-id="1b2d4-112">Creazione ed esecuzione di una query per testare il processo per ottenere informazioni su `Order` usando la classe `Customer`.</span><span class="sxs-lookup"><span data-stu-id="1b2d4-112">Creating and running a query to test the process of obtaining `Order` information by using the `Customer` class.</span></span>  
  
## <a name="mapping-relationships-across-tables"></a><span data-ttu-id="1b2d4-113">Esecuzione del mapping delle relazioni tra tabelle</span><span class="sxs-lookup"><span data-stu-id="1b2d4-113">Mapping Relationships across Tables</span></span>  
 <span data-ttu-id="1b2d4-114">Dopo la definizione della classe `Customer`, creare la definizione della classe di entità `Order` includendo il codice seguente per indicare che `Orders.Customer` è correlata come chiave esterna a `Customers.CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="1b2d4-114">After the `Customer` class definition, create the `Order` entity class definition that includes the following code, which indicates that `Orders.Customer` relates as a foreign key to `Customers.CustomerID`.</span></span>  
  
#### <a name="to-add-the-order-entity-class"></a><span data-ttu-id="1b2d4-115">Per aggiungere la classe di entità Order</span><span class="sxs-lookup"><span data-stu-id="1b2d4-115">To add the Order entity class</span></span>  
  
- <span data-ttu-id="1b2d4-116">Digitare o incollare il codice seguente dopo la classe `Customer`:</span><span class="sxs-lookup"><span data-stu-id="1b2d4-116">Type or paste the following code after the `Customer` class:</span></span>  
  
     [!code-vb[DLinqWalk2VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#1)]  
  
## <a name="annotating-the-customer-class"></a><span data-ttu-id="1b2d4-117">Annotazione della classe Customer</span><span class="sxs-lookup"><span data-stu-id="1b2d4-117">Annotating the Customer Class</span></span>  
 <span data-ttu-id="1b2d4-118">In questo passaggio vengono aggiunte annotazioni alla classe `Customer` per indicare la relazione alla classe `Order`.</span><span class="sxs-lookup"><span data-stu-id="1b2d4-118">In this step, you annotate the `Customer` class to indicate its relationship to the `Order` class.</span></span> <span data-ttu-id="1b2d4-119">Questa aggiunta non è strettamente necessaria, in quanto la definizione della relazione in una direzione è sufficiente per creare il collegamento.</span><span class="sxs-lookup"><span data-stu-id="1b2d4-119">(This addition is not strictly necessary, because defining the relationship in either direction is sufficient to create the link.</span></span> <span data-ttu-id="1b2d4-120">Tuttavia aggiungendo l'annotazione sarà possibile spostarsi facilmente tra gli oggetti in entrambe le direzioni.</span><span class="sxs-lookup"><span data-stu-id="1b2d4-120">But adding this annotation does enable you to easily navigate objects in either direction.)</span></span>  
  
#### <a name="to-annotate-the-customer-class"></a><span data-ttu-id="1b2d4-121">Per annotare la classe Customer</span><span class="sxs-lookup"><span data-stu-id="1b2d4-121">To annotate the Customer class</span></span>  
  
- <span data-ttu-id="1b2d4-122">Digitare o incollare il codice seguente nella classe `Customer`:</span><span class="sxs-lookup"><span data-stu-id="1b2d4-122">Type or paste the following code into the `Customer` class:</span></span>  
  
     [!code-vb[DLinqWalk2VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a><span data-ttu-id="1b2d4-123">Creazione ed esecuzione di un query sulla relazione Customer-Order</span><span class="sxs-lookup"><span data-stu-id="1b2d4-123">Creating and Running a Query across the Customer-Order Relationship</span></span>  
 <span data-ttu-id="1b2d4-124">A questo punto è possibile accedere direttamente agli oggetti `Order` dagli oggetti `Customer` o viceversa.</span><span class="sxs-lookup"><span data-stu-id="1b2d4-124">You can now access `Order` objects directly from the `Customer` objects, or in the opposite order.</span></span> <span data-ttu-id="1b2d4-125">Non è necessario un *join* esplicito tra clienti e ordini.</span><span class="sxs-lookup"><span data-stu-id="1b2d4-125">You do not need an explicit *join* between customers and orders.</span></span>  
  
#### <a name="to-access-order-objects-by-using-customer-objects"></a><span data-ttu-id="1b2d4-126">Per accedere agli oggetti Order usando oggetti Customer</span><span class="sxs-lookup"><span data-stu-id="1b2d4-126">To access Order objects by using Customer objects</span></span>  
  
1. <span data-ttu-id="1b2d4-127">Modificare il metodo `Sub Main` digitando o incollando il codice seguente nel metodo stesso:</span><span class="sxs-lookup"><span data-stu-id="1b2d4-127">Modify the `Sub Main` method by typing or pasting the following code into the method:</span></span>  
  
     [!code-vb[DLinqWalk2VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#3)]  
  
2. <span data-ttu-id="1b2d4-128">Premere F5 per eseguire il debug dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="1b2d4-128">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="1b2d4-129">Nella finestra di messaggio vengono visualizzati due nomi, mentre nella finestra della console viene riportato il codice SQL generato.</span><span class="sxs-lookup"><span data-stu-id="1b2d4-129">Two names appear in the message box, and the Console window shows the generated SQL code.</span></span>  
  
3. <span data-ttu-id="1b2d4-130">Chiudere la finestra di messaggio per interrompere il debug.</span><span class="sxs-lookup"><span data-stu-id="1b2d4-130">Close the message box to stop debugging.</span></span>  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a><span data-ttu-id="1b2d4-131">Creazione di una visualizzazione fortemente tipizzata del database</span><span class="sxs-lookup"><span data-stu-id="1b2d4-131">Creating a Strongly Typed View of Your Database</span></span>  
 <span data-ttu-id="1b2d4-132">È molto più facile iniziare con una visualizzazione fortemente tipizzata del database.</span><span class="sxs-lookup"><span data-stu-id="1b2d4-132">It is much easier to start with a strongly typed view of your database.</span></span> <span data-ttu-id="1b2d4-133">Applicando la tipizzazione forte all'oggetto <xref:System.Data.Linq.DataContext>, si eviterà di eseguire chiamate a <xref:System.Data.Linq.DataContext.GetTable%2A>.</span><span class="sxs-lookup"><span data-stu-id="1b2d4-133">By strongly typing the <xref:System.Data.Linq.DataContext> object, you do not need calls to <xref:System.Data.Linq.DataContext.GetTable%2A>.</span></span> <span data-ttu-id="1b2d4-134">Quando si usa l'oggetto fortemente tipizzato <xref:System.Data.Linq.DataContext>, è possibile usare tabelle fortemente tipizzate in tutte le query.</span><span class="sxs-lookup"><span data-stu-id="1b2d4-134">You can use strongly typed tables in all your queries when you use the strongly typed <xref:System.Data.Linq.DataContext> object.</span></span>  
  
 <span data-ttu-id="1b2d4-135">Nei passaggi seguenti si creerà `Customers` come tabella fortemente tipizzata mappata alla tabella Customers nel database.</span><span class="sxs-lookup"><span data-stu-id="1b2d4-135">In the following steps, you will create `Customers` as a strongly typed table that maps to the Customers table in the database.</span></span>  
  
#### <a name="to-strongly-type-the-datacontext-object"></a><span data-ttu-id="1b2d4-136">Per tipizzare fortemente l'oggetto DataContext</span><span class="sxs-lookup"><span data-stu-id="1b2d4-136">To strongly type the DataContext object</span></span>  
  
1. <span data-ttu-id="1b2d4-137">Aggiungere il codice riportato di seguito sopra la dichiarazione della classe `Customer`.</span><span class="sxs-lookup"><span data-stu-id="1b2d4-137">Add the following code above the `Customer` class declaration.</span></span>  
  
     [!code-vb[DLinqWalk2VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#4)]  
  
2. <span data-ttu-id="1b2d4-138">Modificare `Sub Main` per usare l'oggetto fortemente tipizzato <xref:System.Data.Linq.DataContext> come segue:</span><span class="sxs-lookup"><span data-stu-id="1b2d4-138">Modify `Sub Main` to use the strongly typed <xref:System.Data.Linq.DataContext> as follows:</span></span>  
  
     [!code-vb[DLinqWalk2VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#5)]  
  
3. <span data-ttu-id="1b2d4-139">Premere F5 per eseguire il debug dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="1b2d4-139">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="1b2d4-140">L'output nella finestra della console sarà:</span><span class="sxs-lookup"><span data-stu-id="1b2d4-140">The Console window output is:</span></span>  
  
     `ID=WHITC`  
  
4. <span data-ttu-id="1b2d4-141">Premere INVIO nella finestra Console per chiudere l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="1b2d4-141">Press Enter in the Console window to close the application.</span></span>  
  
5. <span data-ttu-id="1b2d4-142">Scegliere **Salva tutto** dal menu **file** se si desidera salvare l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="1b2d4-142">On the **File** menu, click **Save All** if you want to save this application.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="1b2d4-143">Fasi successive</span><span class="sxs-lookup"><span data-stu-id="1b2d4-143">Next Steps</span></span>  
 <span data-ttu-id="1b2d4-144">Procedura dettagliata successiva ([procedura dettagliata: La manipolazione dei dati (Visual Basic](walkthrough-manipulating-data-visual-basic.md))) illustra come modificare i dati.</span><span class="sxs-lookup"><span data-stu-id="1b2d4-144">The next walkthrough ([Walkthrough: Manipulating Data (Visual Basic)](walkthrough-manipulating-data-visual-basic.md)) demonstrates how to manipulate data.</span></span> <span data-ttu-id="1b2d4-145">Per tale procedura dettagliata non è necessario avere salvato le due procedure dettagliate di questa serie già completate.</span><span class="sxs-lookup"><span data-stu-id="1b2d4-145">That walkthrough does not require that you save the two walkthroughs in this series that you have already completed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b2d4-146">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1b2d4-146">See also</span></span>

- [<span data-ttu-id="1b2d4-147">Apprendimento tramite procedure dettagliate</span><span class="sxs-lookup"><span data-stu-id="1b2d4-147">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
