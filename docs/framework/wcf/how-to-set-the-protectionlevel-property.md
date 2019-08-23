---
title: 'Procedura: Impostare la proprietà ProtectionLevel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
- ProtectionLevel property
ms.assetid: 3d4e8f80-0f9e-4a26-9899-beb6584e78df
ms.openlocfilehash: 222fda180923cdc7b0d7b7ab413c151c69add259
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950972"
---
# <a name="how-to-set-the-protectionlevel-property"></a><span data-ttu-id="c2148-102">Procedura: Impostare la proprietà ProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="c2148-102">How to: Set the ProtectionLevel Property</span></span>
<span data-ttu-id="c2148-103">È possibile impostare il livello di protezione applicando un attributo appropriato e impostando la proprietà.</span><span class="sxs-lookup"><span data-stu-id="c2148-103">You can set the protection level by applying an appropriate attribute and setting the property.</span></span> <span data-ttu-id="c2148-104">È possibile impostare la protezione a livello di servizio su tutte le parti di ogni messaggio. In alternativa è possibile impostare la protezione a livelli granulari in modo crescente, dai metodi alle parti del messaggio.</span><span class="sxs-lookup"><span data-stu-id="c2148-104">You can set protection at the service level to affect all parts of every message, or you can set protection at increasingly granular levels, from methods to message parts.</span></span> <span data-ttu-id="c2148-105">Per ulteriori informazioni sulla `ProtectionLevel` proprietà, vedere informazioni sul livello di [protezione](../../../docs/framework/wcf/understanding-protection-level.md).</span><span class="sxs-lookup"><span data-stu-id="c2148-105">For more information about the `ProtectionLevel` property, see [Understanding Protection Level](../../../docs/framework/wcf/understanding-protection-level.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c2148-106">È possibile impostare i livelli di protezione solo nel codice, non nella configurazione.</span><span class="sxs-lookup"><span data-stu-id="c2148-106">You can set protection levels only in code, not in configuration.</span></span>  
  
### <a name="to-sign-all-messages-for-a-service"></a><span data-ttu-id="c2148-107">Per firmare tutti i messaggi per un servizio</span><span class="sxs-lookup"><span data-stu-id="c2148-107">To sign all messages for a service</span></span>  
  
1. <span data-ttu-id="c2148-108">Creare un'interfaccia per il servizio.</span><span class="sxs-lookup"><span data-stu-id="c2148-108">Create an interface for the service.</span></span>  
  
2. <span data-ttu-id="c2148-109">Applicare l'attributo <xref:System.ServiceModel.ServiceContractAttribute> al servizio e impostare la proprietà <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> su <xref:System.Net.Security.ProtectionLevel.Sign>, come illustrato nel codice seguente (il livello predefinito è <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>).</span><span class="sxs-lookup"><span data-stu-id="c2148-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the service and set the <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.Sign>, as shown in the following code (the default level is <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>).</span></span>  
  
     [!code-csharp[C_ProtectionLevel#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#1)]
     [!code-vb[C_ProtectionLevel#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#1)]  
  
### <a name="to-sign-all-message-parts-for-an-operation"></a><span data-ttu-id="c2148-110">Per firmare tutte le parti del messaggio per un'operazione</span><span class="sxs-lookup"><span data-stu-id="c2148-110">To sign all message parts for an operation</span></span>  
  
1. <span data-ttu-id="c2148-111">Creare un'interfaccia per il servizio e applicarvi l'attributo <xref:System.ServiceModel.ServiceContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="c2148-111">Create an interface for the service and apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the interface.</span></span>  
  
2. <span data-ttu-id="c2148-112">Aggiungere una dichiarazione di metodo all'interfaccia.</span><span class="sxs-lookup"><span data-stu-id="c2148-112">Add a method declaration to the interface.</span></span>  
  
3. <span data-ttu-id="c2148-113">Applicare l'attributo <xref:System.ServiceModel.OperationContractAttribute> al metodo e impostare la proprietà <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> su <xref:System.Net.Security.ProtectionLevel.Sign>, come illustrato nel codice seguente.</span><span class="sxs-lookup"><span data-stu-id="c2148-113">Apply the <xref:System.ServiceModel.OperationContractAttribute> attribute to the method, and set the <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.Sign>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#2)]
     [!code-vb[C_ProtectionLevel#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#2)]  
  
## <a name="protecting-fault-messages"></a><span data-ttu-id="c2148-114">Protezione dei messaggi di errore</span><span class="sxs-lookup"><span data-stu-id="c2148-114">Protecting Fault Messages</span></span>  
 <span data-ttu-id="c2148-115">È possibile inviare le eccezioni generate in un servizio a un client come errori SOAP.</span><span class="sxs-lookup"><span data-stu-id="c2148-115">Exceptions that are thrown on a service can be sent to a client as SOAP faults.</span></span> <span data-ttu-id="c2148-116">Per ulteriori informazioni sulla creazione di errori fortemente tipizzati, vedere [specifica e gestione di errori in contratti e servizi](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md) e [procedura: Dichiarare gli errori nei contratti](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md)di servizio.</span><span class="sxs-lookup"><span data-stu-id="c2148-116">For more information about creating strongly typed faults, see [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md) and [How to: Declare Faults in Service Contracts](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md).</span></span>  
  
#### <a name="to-protect-a-fault-message"></a><span data-ttu-id="c2148-117">Per proteggere i messaggi di errore</span><span class="sxs-lookup"><span data-stu-id="c2148-117">To protect a fault message</span></span>  
  
1. <span data-ttu-id="c2148-118">Creare un tipo che rappresenta il messaggio di errore.</span><span class="sxs-lookup"><span data-stu-id="c2148-118">Create a type that represents the fault message.</span></span> <span data-ttu-id="c2148-119">Nell'esempio seguente viene creata una classe denominata `MathFault` con due campi.</span><span class="sxs-lookup"><span data-stu-id="c2148-119">The following example creates a class named `MathFault` with two fields.</span></span>  
  
2. <span data-ttu-id="c2148-120">Applicare l'attributo <xref:System.Runtime.Serialization.DataContractAttribute> al tipo e un attributo <xref:System.Runtime.Serialization.DataMemberAttribute> a ogni campo che deve essere serializzato, come illustrato nel codice seguente.</span><span class="sxs-lookup"><span data-stu-id="c2148-120">Apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the type and a <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to each field that should be serialized, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#3)]
     [!code-vb[C_ProtectionLevel#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#3)]  
  
3. <span data-ttu-id="c2148-121">Nell'interfaccia che restituirà l'errore, applicare l'attributo <xref:System.ServiceModel.FaultContractAttribute> al metodo che restituirà l'errore e impostare il parametro `detailType` sul tipo della classe di errore.</span><span class="sxs-lookup"><span data-stu-id="c2148-121">In the interface that will return the fault, apply the <xref:System.ServiceModel.FaultContractAttribute> attribute to the method that will return the fault and set the `detailType` parameter to the type of the fault class.</span></span>  
  
4. <span data-ttu-id="c2148-122">Nel costruttore, inoltre, impostare la proprietà <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> su <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, come illustrato nel codice seguente.</span><span class="sxs-lookup"><span data-stu-id="c2148-122">Also in the constructor, set the <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#4)]
     [!code-vb[C_ProtectionLevel#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#4)]  
  
## <a name="protecting-message-parts"></a><span data-ttu-id="c2148-123">Protezione delle parti del messaggio</span><span class="sxs-lookup"><span data-stu-id="c2148-123">Protecting Message Parts</span></span>  
 <span data-ttu-id="c2148-124">Utilizzare un contratto di messaggio per proteggere le parti di un messaggio.</span><span class="sxs-lookup"><span data-stu-id="c2148-124">Use a message contract to protect parts of a message.</span></span> <span data-ttu-id="c2148-125">Per ulteriori informazioni sui contratti di messaggio, vedere [utilizzo dei contratti di messaggio](../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="c2148-125">For more information about message contracts, see [Using Message Contracts](../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span></span>  
  
#### <a name="to-protect-a-message-body"></a><span data-ttu-id="c2148-126">Per proteggere il corpo del messaggio</span><span class="sxs-lookup"><span data-stu-id="c2148-126">To protect a message body</span></span>  
  
1. <span data-ttu-id="c2148-127">Creare un tipo che rappresenta il messaggio.</span><span class="sxs-lookup"><span data-stu-id="c2148-127">Create a type that represents the message.</span></span> <span data-ttu-id="c2148-128">Nell'esempio seguente viene creata una classe `Company` con due campi, `CompanyName` e `CompanyID`.</span><span class="sxs-lookup"><span data-stu-id="c2148-128">The following example creates a `Company` class with two fields, `CompanyName` and `CompanyID`.</span></span>  
  
2. <span data-ttu-id="c2148-129">Applicare l'attributo <xref:System.ServiceModel.MessageContractAttribute> alla classe e impostare la proprietà <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> su <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span><span class="sxs-lookup"><span data-stu-id="c2148-129">Apply the <xref:System.ServiceModel.MessageContractAttribute> attribute to the class and set the <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
3. <span data-ttu-id="c2148-130">Applicare l'attributo <xref:System.ServiceModel.MessageHeaderAttribute> a un campo che verrà espresso come intestazione del messaggio e impostare la proprietà `ProtectionLevel` su <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span><span class="sxs-lookup"><span data-stu-id="c2148-130">Apply the <xref:System.ServiceModel.MessageHeaderAttribute> attribute to a field that will be expressed as a message header and set the `ProtectionLevel` property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
4. <span data-ttu-id="c2148-131">Applicare a qualsiasi campo che verrà espresso come parte del corpo del messaggio e impostare la `ProtectionLevel` proprietà su <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, come illustrato nell'esempio seguente. <xref:System.ServiceModel.MessageBodyMemberAttribute></span><span class="sxs-lookup"><span data-stu-id="c2148-131">Apply the <xref:System.ServiceModel.MessageBodyMemberAttribute> to any field that will be expressed as part of the message body, and set the `ProtectionLevel` property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, as shown in the following example.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#5)]
     [!code-vb[C_ProtectionLevel#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="c2148-132">Esempio</span><span class="sxs-lookup"><span data-stu-id="c2148-132">Example</span></span>  
 <span data-ttu-id="c2148-133">Nell'esempio seguente viene impostata la proprietà `ProtectionLevel` di diverse classi Attribute in varie posizioni di un servizio.</span><span class="sxs-lookup"><span data-stu-id="c2148-133">The following example sets the `ProtectionLevel` property of several attribute classes at various places in a service.</span></span>  
  
 [!code-csharp[C_ProtectionLevel#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#6)]
 [!code-vb[C_ProtectionLevel#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#6)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c2148-134">Compilazione del codice</span><span class="sxs-lookup"><span data-stu-id="c2148-134">Compiling the Code</span></span>  
 <span data-ttu-id="c2148-135">Nel codice seguente vengono illustrati gli spazi dei nomi necessari per compilare il codice di esempio.</span><span class="sxs-lookup"><span data-stu-id="c2148-135">The following code shows the namespaces required to compile the example code.</span></span>  
  
 [!code-csharp[C_ProtectionLevel#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#0)]
 [!code-vb[C_ProtectionLevel#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="c2148-136">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c2148-136">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.MessageContractAttribute>
- <xref:System.ServiceModel.MessageBodyMemberAttribute>
- [<span data-ttu-id="c2148-137">Informazioni sul livello di protezione</span><span class="sxs-lookup"><span data-stu-id="c2148-137">Understanding Protection Level</span></span>](../../../docs/framework/wcf/understanding-protection-level.md)
