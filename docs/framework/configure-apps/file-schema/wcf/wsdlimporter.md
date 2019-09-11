---
title: <wsdlImporter>
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 317921a66fa3b8d1f0026d676ea674b67732b3df
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854766"
---
# <a name="wsdlimporter"></a><span data-ttu-id="8caf0-101">\<> di wsdlImporter</span><span class="sxs-lookup"><span data-stu-id="8caf0-101">\<wsdlImporter></span></span>
<span data-ttu-id="8caf0-102">Specifica tutte le unità di importazione WSDL per l'importazione di metadati Web Services Description Language (WSDL) 1.1 con allegati WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="8caf0-102">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>  
  
<span data-ttu-id="8caf0-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8caf0-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8caf0-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="8caf0-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8caf0-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> client**](client.md)</span><span class="sxs-lookup"><span data-stu-id="8caf0-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="8caf0-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> metadati**](metadata.md)</span><span class="sxs-lookup"><span data-stu-id="8caf0-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<metadata>**](metadata.md)</span></span>\
<span data-ttu-id="8caf0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsdlImporters >** ](wsdlimporters.md)</span><span class="sxs-lookup"><span data-stu-id="8caf0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsdlImporters>**](wsdlimporters.md)</span></span>  
<span data-ttu-id="8caf0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> di wsdlImporter**</span><span class="sxs-lookup"><span data-stu-id="8caf0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsdlImporter>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8caf0-109">Sintassi</span><span class="sxs-lookup"><span data-stu-id="8caf0-109">Syntax</span></span>  
  
```xml  
<metadata>
  <wsdlImporters>
    <wsdlImporter type="string" />
  </wsdlImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8caf0-110">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="8caf0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8caf0-111">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="8caf0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8caf0-112">Attributi</span><span class="sxs-lookup"><span data-stu-id="8caf0-112">Attributes</span></span>  
  
|<span data-ttu-id="8caf0-113">Attributo</span><span class="sxs-lookup"><span data-stu-id="8caf0-113">Attribute</span></span>|<span data-ttu-id="8caf0-114">Descrizione</span><span class="sxs-lookup"><span data-stu-id="8caf0-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="8caf0-115">Tipo di questo elemento.</span><span class="sxs-lookup"><span data-stu-id="8caf0-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8caf0-116">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="8caf0-116">Child Elements</span></span>  
 <span data-ttu-id="8caf0-117">Nessuno.</span><span class="sxs-lookup"><span data-stu-id="8caf0-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8caf0-118">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="8caf0-118">Parent Elements</span></span>  
  
|<span data-ttu-id="8caf0-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="8caf0-119">Element</span></span>|<span data-ttu-id="8caf0-120">Descrizione</span><span class="sxs-lookup"><span data-stu-id="8caf0-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8caf0-121">\<wsdlImporters></span><span class="sxs-lookup"><span data-stu-id="8caf0-121">\<wsdlImporters></span></span>](wsdlimporters.md)|<span data-ttu-id="8caf0-122">Specifica tutte le unità di importazione WSDL per l'importazione di metadati Web Services Description Language (WSDL) 1.1 con allegati WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="8caf0-122">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8caf0-123">Note</span><span class="sxs-lookup"><span data-stu-id="8caf0-123">Remarks</span></span>  
 <span data-ttu-id="8caf0-124">Un'unità di importazione WSDL viene usata per importare metadati e per convertire tali informazioni in diverse classi che rappresentano informazioni di contratto e di endpoint.</span><span class="sxs-lookup"><span data-stu-id="8caf0-124">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="8caf0-125">Può importare selettivamente informazioni di contratto e di endpoint e proprietà che espongono qualsiasi errore di importazione e accettano informazioni sul tipo relative al processo di importazione e di conversione.</span><span class="sxs-lookup"><span data-stu-id="8caf0-125">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="8caf0-126">Supporta inoltre l'importazione di informazioni dell'associazione e proprietà che forniscono accesso a qualsiasi documento di criteri, documento WSDL, estensione WSDL e documento di XML Schema.</span><span class="sxs-lookup"><span data-stu-id="8caf0-126">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8caf0-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8caf0-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.WsdlImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="8caf0-128">Configurazione del client WCF</span><span class="sxs-lookup"><span data-stu-id="8caf0-128">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="8caf0-129">Client</span><span class="sxs-lookup"><span data-stu-id="8caf0-129">Clients</span></span>](../../../wcf/feature-details/clients.md)
