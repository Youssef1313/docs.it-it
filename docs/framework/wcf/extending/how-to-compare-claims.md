---
title: 'Procedura: Confrontare le attestazioni'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- claims [WCF], comparing
- claims [WCF]
ms.assetid: 0c4ec84d-53df-408f-8953-9bc437f56c28
ms.openlocfilehash: e2d3d33900dd894eea77420aac444ebde0df9a43
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2019
ms.locfileid: "68970771"
---
# <a name="how-to-compare-claims"></a><span data-ttu-id="a7b12-102">Procedura: Confrontare le attestazioni</span><span class="sxs-lookup"><span data-stu-id="a7b12-102">How to: Compare Claims</span></span>

<span data-ttu-id="a7b12-103">L'infrastruttura del modello di identità in Windows Communication Foundation (WCF) viene utilizzata per eseguire il controllo delle autorizzazioni.</span><span class="sxs-lookup"><span data-stu-id="a7b12-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) is used to perform authorization checking.</span></span> <span data-ttu-id="a7b12-104">Un'attività comune consiste quindi nel confrontare le attestazioni presenti nel contesto di autorizzazione con le attestazioni richieste per eseguire l'azione richiesta o accedere alla risorsa richiesta.</span><span class="sxs-lookup"><span data-stu-id="a7b12-104">As such, a common task is to compare claims in the authorization context to the claims required to perform the requested action or access the requested resource.</span></span> <span data-ttu-id="a7b12-105">In questo argomento viene illustrato come confrontare le attestazioni, compresi i tipi di attestazione incorporati e personalizzati.</span><span class="sxs-lookup"><span data-stu-id="a7b12-105">This topic describes how to compare claims, including built-in and custom claim types.</span></span> <span data-ttu-id="a7b12-106">Per ulteriori informazioni sull'infrastruttura del modello di identità, vedere [gestione di attestazioni e autorizzazioni con il modello di identità](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span><span class="sxs-lookup"><span data-stu-id="a7b12-106">For more information about the Identity Model infrastructure, see [Managing Claims and Authorization with the Identity Model](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span></span>

<span data-ttu-id="a7b12-107">Questa operazione implica il confronto delle tre parti di un'attestazione (tipo, diritto e risorsa) con le stesse parti di un'altra attestazione per verificarne la corrispondenza.</span><span class="sxs-lookup"><span data-stu-id="a7b12-107">Claim comparison involves comparing the three parts of a claim (type, right, and resource) against the same parts in another claim to see if they are equal.</span></span> <span data-ttu-id="a7b12-108">Vedere l'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="a7b12-108">See the following example.</span></span>

[!code-csharp[c_CustomClaimComparison#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#9)]
[!code-vb[c_CustomClaimComparison#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#9)]

<span data-ttu-id="a7b12-109">Entrambe le attestazioni dispongono di un tipo <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, un diritto <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> e una risorsa "someone."</span><span class="sxs-lookup"><span data-stu-id="a7b12-109">Both claims have a claim type of <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, a right of <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>, and a resource of the string "someone".</span></span> <span data-ttu-id="a7b12-110">Poiché tutte le tre parti delle attestazioni sono uguali, le attestazioni sono uguali.</span><span class="sxs-lookup"><span data-stu-id="a7b12-110">As all three parts of the claim are equal, the claims themselves are equal.</span></span>

<span data-ttu-id="a7b12-111">I tipi di attestazione incorporati vengono confrontati utilizzando il metodo <xref:System.IdentityModel.Claims.Claim.Equals%2A>.</span><span class="sxs-lookup"><span data-stu-id="a7b12-111">The built-in claim types are compared using the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="a7b12-112">Il codice di confronto specifico dell'attestazione viene utilizzato laddove necessario.</span><span class="sxs-lookup"><span data-stu-id="a7b12-112">Claim-specific comparison code is used where necessary.</span></span> <span data-ttu-id="a7b12-113">Ad esempio, date le due attestazioni del nome dell'entità utente (UPN) seguenti:</span><span class="sxs-lookup"><span data-stu-id="a7b12-113">For example, given the following two user principal name (UPN) claims:</span></span>

[!code-csharp[c_CustomClaimComparison#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#4)]
[!code-vb[c_CustomClaimComparison#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#4)]

<span data-ttu-id="a7b12-114">il codice di confronto nel <xref:System.IdentityModel.Claims.Claim.Equals%2A> metodo restituisce `true`, supponendo `example\someone` che identifichi lo stesso utente disomeone@example.comdominio di "".</span><span class="sxs-lookup"><span data-stu-id="a7b12-114">the comparison code in the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method returns `true`, assuming `example\someone` identifies the same domain user as "someone@example.com".</span></span>

<span data-ttu-id="a7b12-115">Anche i tipi di attestazione personalizzati possono essere confrontati utilizzando il metodo <xref:System.IdentityModel.Claims.Claim.Equals%2A>.</span><span class="sxs-lookup"><span data-stu-id="a7b12-115">Custom claim types can also be compared using the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="a7b12-116">Tuttavia, nei casi in cui il tipo restituito dalla proprietà <xref:System.IdentityModel.Claims.Claim.Resource%2A> dell'attestazione non è un tipo primitivo, il metodo <xref:System.IdentityModel.Claims.Claim.Equals%2A> restituisce `true` solo se i valori restituiti dalle proprietà `Resource` sono uguali in base al metodo <xref:System.IdentityModel.Claims.Claim.Equals%2A>.</span><span class="sxs-lookup"><span data-stu-id="a7b12-116">However, in cases where the type returned by the <xref:System.IdentityModel.Claims.Claim.Resource%2A> property of the claim is something other than a primitive type, the <xref:System.IdentityModel.Claims.Claim.Equals%2A> returns `true` only if the values returned by the `Resource` properties are equal according to the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="a7b12-117">Negli altri casi, il tipo personalizzato restituito dalla proprietà `Resource` deve eseguire l'override dei metodi <xref:System.IdentityModel.Claims.Claim.Equals%2A> e <xref:System.Object.GetHashCode%2A> per eseguire qualsiasi elaborazione personalizzata necessaria.</span><span class="sxs-lookup"><span data-stu-id="a7b12-117">In cases where this is not appropriate, the custom type returned by the `Resource` property should override the <xref:System.IdentityModel.Claims.Claim.Equals%2A> and <xref:System.Object.GetHashCode%2A> methods to perform whatever custom processing is necessary.</span></span>

## <a name="comparing-built-in-claims"></a><span data-ttu-id="a7b12-118">Confronto di attestazioni incorporate</span><span class="sxs-lookup"><span data-stu-id="a7b12-118">Comparing built-in claims</span></span>

1. <span data-ttu-id="a7b12-119">Date due istanze della classe <xref:System.IdentityModel.Claims.Claim>, utilizzare il metodo <xref:System.IdentityModel.Claims.Claim.Equals%2A> per eseguire il confronto, come illustrato nel codice seguente.</span><span class="sxs-lookup"><span data-stu-id="a7b12-119">Given two instances of the <xref:System.IdentityModel.Claims.Claim> class, use the <xref:System.IdentityModel.Claims.Claim.Equals%2A> to make the comparison, as shown in the following code.</span></span>

     [!code-csharp[c_CustomClaimComparison#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#5)]
     [!code-vb[c_CustomClaimComparison#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#5)]

### <a name="comparing-custom-claims-with-primitive-resource-types"></a><span data-ttu-id="a7b12-120">Confronto di attestazioni personalizzate con tipi di risorsa primitivi</span><span class="sxs-lookup"><span data-stu-id="a7b12-120">Comparing custom claims with primitive resource types</span></span>

1. <span data-ttu-id="a7b12-121">Per le attestazioni personalizzate con tipi di risorsa primitivi, è possibile eseguire il confronto come per le attestazioni incorporate, come illustrato nel codice seguente.</span><span class="sxs-lookup"><span data-stu-id="a7b12-121">For custom claims with primitive resource types, comparison can be performed as for built-in claims, as shown in the following code.</span></span>

     [!code-csharp[c_CustomClaimComparison#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#6)]
     [!code-vb[c_CustomClaimComparison#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#6)]

2. <span data-ttu-id="a7b12-122">Per attestazioni personalizzate con tipi di risorsa basati su strutture o su classi, il tipo di risorsa deve eseguire l'override del metodo <xref:System.IdentityModel.Claims.Claim.Equals%2A>.</span><span class="sxs-lookup"><span data-stu-id="a7b12-122">For custom claims with structure or class based resource types, the resource type should override the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span>

3. <span data-ttu-id="a7b12-123">Controllare innanzitutto se il parametro `obj` è `null` e, in caso affermativo, restituire `false`.</span><span class="sxs-lookup"><span data-stu-id="a7b12-123">First check whether the `obj` parameter is `null`, and if so, return `false`.</span></span>

     [!code-csharp[c_CustomClaimComparison#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#7)]
     [!code-vb[c_CustomClaimComparison#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#7)]

4. <span data-ttu-id="a7b12-124">Quindi chiamare il metodo <xref:System.Object.ReferenceEquals%2A> e passare `this` e `obj` come parametri.</span><span class="sxs-lookup"><span data-stu-id="a7b12-124">Next call <xref:System.Object.ReferenceEquals%2A> and pass `this` and `obj` as parameters.</span></span> <span data-ttu-id="a7b12-125">Se viene restituito `true`, restituire `true`.</span><span class="sxs-lookup"><span data-stu-id="a7b12-125">If it returns `true`, then return `true`.</span></span>

     [!code-csharp[c_CustomClaimComparison#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#8)]
     [!code-vb[c_CustomClaimComparison#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#8)]

5. <span data-ttu-id="a7b12-126">Tentare di assegnare il parametro `obj` a una variabile locale del tipo di classe.</span><span class="sxs-lookup"><span data-stu-id="a7b12-126">Next attempt to assign `obj` to a local variable of the class type.</span></span> <span data-ttu-id="a7b12-127">In caso di errore, il riferimento è `null`.</span><span class="sxs-lookup"><span data-stu-id="a7b12-127">If this fails, the reference is `null`.</span></span> <span data-ttu-id="a7b12-128">In tali casi, restituire `false`.</span><span class="sxs-lookup"><span data-stu-id="a7b12-128">In such cases, return `false`.</span></span>

6. <span data-ttu-id="a7b12-129">Eseguire il confronto personalizzato necessario per confrontare correttamente l'attestazione attuale con quella fornita.</span><span class="sxs-lookup"><span data-stu-id="a7b12-129">Perform the custom comparison necessary to correctly compare the current claim to the provided claim.</span></span>

## <a name="example"></a><span data-ttu-id="a7b12-130">Esempio</span><span class="sxs-lookup"><span data-stu-id="a7b12-130">Example</span></span>

<span data-ttu-id="a7b12-131">Nell'esempio seguente viene illustrato un confronto di attestazioni personalizzate in cui la risorsa dell'attestazione è un tipo non primitivo.</span><span class="sxs-lookup"><span data-stu-id="a7b12-131">The following example shows a comparison of custom claims where the claim resource is a non-primitive type.</span></span>

[!code-csharp[c_CustomClaimComparison#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#0)]
[!code-vb[c_CustomClaimComparison#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#0)]

## <a name="see-also"></a><span data-ttu-id="a7b12-132">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a7b12-132">See also</span></span>

- [<span data-ttu-id="a7b12-133">Gestione delle attestazioni e dell'autorizzazione con il modello di identità</span><span class="sxs-lookup"><span data-stu-id="a7b12-133">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [<span data-ttu-id="a7b12-134">Procedura: Creare un'attestazione personalizzata</span><span class="sxs-lookup"><span data-stu-id="a7b12-134">How to: Create a Custom Claim</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)
