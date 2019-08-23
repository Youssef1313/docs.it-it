---
title: <trustedIssuers>
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: 32aad3529ded6d0234b1bcb388ecbbc3b0a11c87
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944265"
---
# <a name="trustedissuers"></a><span data-ttu-id="5ef7f-101">\<> trustedIssuers</span><span class="sxs-lookup"><span data-stu-id="5ef7f-101">\<trustedIssuers></span></span>
<span data-ttu-id="5ef7f-102">Configura l'elenco dei certificati dell'autorità emittente attendibile usati dal registro di sistema del nome dell'autorità emittente<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>basata sulla configurazione ().</span><span class="sxs-lookup"><span data-stu-id="5ef7f-102">Configures the list of trusted issuer certificates used by the configuration-based issuer name registry (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span></span>  
  
 <span data-ttu-id="5ef7f-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="5ef7f-103">\<system.identityModel></span></span>  
<span data-ttu-id="5ef7f-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="5ef7f-104">\<identityConfiguration></span></span>  
<span data-ttu-id="5ef7f-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="5ef7f-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="5ef7f-106">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="5ef7f-106">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="5ef7f-107">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="5ef7f-107">\<issuerNameRegistry></span></span>  
<span data-ttu-id="5ef7f-108">\<> trustedIssuers</span><span class="sxs-lookup"><span data-stu-id="5ef7f-108">\<trustedIssuers></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ef7f-109">Sintassi</span><span class="sxs-lookup"><span data-stu-id="5ef7f-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry>  
          <trustedIssuers>  
            <add thumbprint=xs:string name=xs:string>  
            <clear>  
            <remove thumbprint=xs:string>  
          </trustedIssuers>  
        </issuerNameRegistry>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ef7f-110">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="5ef7f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5ef7f-111">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="5ef7f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ef7f-112">Attributi</span><span class="sxs-lookup"><span data-stu-id="5ef7f-112">Attributes</span></span>  
 <span data-ttu-id="5ef7f-113">Nessuna</span><span class="sxs-lookup"><span data-stu-id="5ef7f-113">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5ef7f-114">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="5ef7f-114">Child Elements</span></span>  
  
|<span data-ttu-id="5ef7f-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="5ef7f-115">Element</span></span>|<span data-ttu-id="5ef7f-116">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="5ef7f-116">Description</span></span>|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|<span data-ttu-id="5ef7f-117">Aggiunge un certificato alla raccolta di autorità emittenti attendibili.</span><span class="sxs-lookup"><span data-stu-id="5ef7f-117">Adds a certificate to the collection of trusted issuers.</span></span> <span data-ttu-id="5ef7f-118">Il certificato viene specificato con l' `thumbprint` attributo.</span><span class="sxs-lookup"><span data-stu-id="5ef7f-118">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="5ef7f-119">Questo attributo è obbligatorio e deve contenere il formato con codifica ASN. 1 dell'identificazione personale del certificato.</span><span class="sxs-lookup"><span data-stu-id="5ef7f-119">This attribute is required and should contain the ASN.1 encoded form of the certificate thumbprint.</span></span> <span data-ttu-id="5ef7f-120">L' `name` attributo è facoltativo e può essere usato per specificare un nome descrittivo per il certificato.</span><span class="sxs-lookup"><span data-stu-id="5ef7f-120">The `name` attribute is optional and can be used to specify a friendly name for the certificate.</span></span>|  
|`<clear>`|<span data-ttu-id="5ef7f-121">Cancella tutti i certificati dalla raccolta di autorità emittenti attendibili.</span><span class="sxs-lookup"><span data-stu-id="5ef7f-121">Clears all certificates from the collection of trusted issuers.</span></span>|  
|`<remove thumbprint=xs:string>`|<span data-ttu-id="5ef7f-122">Rimuove un certificato dalla raccolta di autorità emittenti attendibili.</span><span class="sxs-lookup"><span data-stu-id="5ef7f-122">Removes a certificate from the collection of trusted issuers.</span></span> <span data-ttu-id="5ef7f-123">Il certificato viene specificato con l' `thumbprint` attributo.</span><span class="sxs-lookup"><span data-stu-id="5ef7f-123">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="5ef7f-124">Questo attributo è obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="5ef7f-124">This attribute is required.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5ef7f-125">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="5ef7f-125">Parent Elements</span></span>  
  
|<span data-ttu-id="5ef7f-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="5ef7f-126">Element</span></span>|<span data-ttu-id="5ef7f-127">Descrizione</span><span class="sxs-lookup"><span data-stu-id="5ef7f-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ef7f-128">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="5ef7f-128">\<issuerNameRegistry></span></span>](issuernameregistry.md)|<span data-ttu-id="5ef7f-129">Configura il registro dei nomi delle autorità emittenti.</span><span class="sxs-lookup"><span data-stu-id="5ef7f-129">Configures the issuer name registry.</span></span> <span data-ttu-id="5ef7f-130">**Importante:**  L' `type` attributo <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> `<trustedIssuers>` dell'elemento deve fare riferimento alla classe affinché l'elemento sia valido. `<issuerNameRegistry>`</span><span class="sxs-lookup"><span data-stu-id="5ef7f-130">**Important:**  The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ef7f-131">Note</span><span class="sxs-lookup"><span data-stu-id="5ef7f-131">Remarks</span></span>  
 <span data-ttu-id="5ef7f-132">Windows Identity Foundation (WIF) fornisce una singola implementazione della <xref:System.IdentityModel.Tokens.IssuerNameRegistry> classe predefinita, la <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> classe.</span><span class="sxs-lookup"><span data-stu-id="5ef7f-132">Windows Identity Foundation (WIF) provides a single implementation of the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="5ef7f-133">Il registro dei nomi delle autorità emittenti di configurazione mantiene un elenco di autorità emittenti attendibili caricate dalla configurazione.</span><span class="sxs-lookup"><span data-stu-id="5ef7f-133">The configuration issuer name registry maintains a list of trusted issuers that is loaded from configuration.</span></span> <span data-ttu-id="5ef7f-134">L'elenco associa ogni nome dell'autorità emittente al certificato X. 509 necessario per verificare la firma dei token prodotti dall'autorità emittente.</span><span class="sxs-lookup"><span data-stu-id="5ef7f-134">The list associates each issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by the issuer.</span></span> <span data-ttu-id="5ef7f-135">L'elenco dei certificati dell'autorità emittente attendibile viene specificato `<trustedIssuers>` nell'elemento.</span><span class="sxs-lookup"><span data-stu-id="5ef7f-135">The list of trusted issuer certificates is specified under the `<trustedIssuers>` element.</span></span> <span data-ttu-id="5ef7f-136">Ogni elemento nell'elenco associa il nome di un emittente mnemonico al certificato X. 509 necessario per verificare la firma dei token prodotti dall'emittente.</span><span class="sxs-lookup"><span data-stu-id="5ef7f-136">Each element in the list associates a mnemonic issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by that issuer.</span></span> <span data-ttu-id="5ef7f-137">I certificati attendibili vengono specificati utilizzando il formato con codifica ASN. 1 dell'identificazione personale del certificato e vengono aggiunti alla raccolta `<add>` tramite l'elemento.</span><span class="sxs-lookup"><span data-stu-id="5ef7f-137">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added the collection by using `<add>` element.</span></span> <span data-ttu-id="5ef7f-138">È possibile cancellare o rimuovere autorità emittenti (certificati) dall'elenco usando gli `<clear>` elementi e. `<remove>`</span><span class="sxs-lookup"><span data-stu-id="5ef7f-138">You can clear or remove issuers (certificates) from the list by using the `<clear>` and `<remove>` elements.</span></span>  
  
 <span data-ttu-id="5ef7f-139">L' `type` attributo <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> `<trustedIssuers>` dell'elemento deve fare riferimento alla classe affinché l'elemento sia valido. `<issuerNameRegistry>`</span><span class="sxs-lookup"><span data-stu-id="5ef7f-139">The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ef7f-140">Esempio</span><span class="sxs-lookup"><span data-stu-id="5ef7f-140">Example</span></span>  
 <span data-ttu-id="5ef7f-141">Nel codice XML seguente viene illustrato come specificare il registro dei nomi delle autorità emittenti basato sulla configurazione.</span><span class="sxs-lookup"><span data-stu-id="5ef7f-141">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5ef7f-142">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5ef7f-142">See also</span></span>

- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
