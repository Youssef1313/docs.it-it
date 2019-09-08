---
title: Panoramica di WCF Data Services
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services
- WCF Data Services, about
ms.assetid: 7924cf94-c9a6-4015-afc9-f5d22b1743bb
ms.openlocfilehash: 66dd61210e36210f5444eb05355612eeb75c155a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790233"
---
# <a name="wcf-data-services-overview"></a>Panoramica di WCF Data Services
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]consente la creazione e l' [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]utilizzo di servizi dati per il Web o una Intranet tramite. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]consente di esporre i dati come risorse indirizzabili tramite URI. In questo modo è possibile accedere ai dati e modificarli utilizzando la semantica REST (Representational State Transfer), in particolare i verbi GET, PUT, POST e DELETE standard HTTP. Questo argomento offre cenni preliminari sia sui modelli che sulle pratiche definiti da [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] e fornisce informazioni sulle funzioni disponibili in [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] che consentono di utilizzare [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] nelle applicazioni basate su .NET Framework.  
  
## <a name="address-data-as-resources"></a>Indirizzare i dati come risorse  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] espone i dati come risorse indirizzabili tramite URI. I percorsi delle risorse vengono creati in base alle convenzioni entità-relazione di Entity Data Model. In questo modello le entità rappresentano unità operative di dati in un dominio applicazione, ad esempio clienti, ordini, elementi e prodotti. Per ulteriori informazioni, vedere [Entity Data Model](../adonet/entity-data-model.md).  
  
 In [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] le risorse di entità vengono indirizzate come set di entità contenenti istanze dei tipi di entità. Ad esempio, l'URI `http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders` restituisce tutti gli ordini `Northwind` del servizio dati correlati al cliente con un `CustomerID` valore di`ALFKI.`  
  
 Le espressioni di query consentono di eseguire operazioni di query tradizionali, quali filtro, ordinamento e paging, sulle risorse. L'URI `http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$filter=Freight gt 50` filtra ad esempio le risorse in modo da restituire solo gli ordini con un costo di spedizione superiore a 50 dollari. Per ulteriori informazioni, vedere [accesso alle risorse del servizio dati](accessing-data-service-resources-wcf-data-services.md).  
  
## <a name="interoperable-data-access"></a>Accesso ai dati interoperativo  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]si basa su protocolli Internet standard per rendere interoperabili i servizi dati con applicazioni che non usano la .NET Framework. Poiché è possibile usare gli URI standard per indirizzare i dati, l'applicazione può accedere ai dati e modificarli usando la semantica REST (Representational State Transfer), in particolare i verbi HTTP standard di GET, PUT, POST e DELETE. In questo modo è possibile accedere a questi servizi da qualsiasi client in grado di analizzare e di accedere ai dati trasmessi su protocolli HTTP standard.  
  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] definisce un set di estensioni del protocollo di pubblicazione Atom (AtomPub). Per soddisfare le esigenze di applicazioni e piattaforme client diverse, supporta richieste e risposte HTTP in più formati di dati. Un feed [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] può rappresentare i dati nei formati Atom e JSON (JavaScript Object Notation), nonché come XML semplice. Sebbene Atom sia il formato predefinito, il formato del feed è specificato nell'intestazione della richiesta HTTP. Per ulteriori informazioni, vedere [OData: Formato](https://go.microsoft.com/fwlink/?LinkID=185794) Atom e [OData: Formato](https://go.microsoft.com/fwlink/?LinkID=185795)JSON.  
  
 Quando si pubblicano dati [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] come feed [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] , si basa su altre funzionalità Internet esistenti per operazioni quali la memorizzazione nella cache e l'autenticazione. A tale scopo, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] si integra con i servizi e le applicazioni di hosting esistenti, ad esempio ASP.NET, Windows Communication Foundation (WCF) e Internet Information Services (IIS).  
  
## <a name="storage-independence"></a>Indipendenza dall'archiviazione  
 Sebbene le risorse vengano indirizzate in base a un modello entità-relazione, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] espone i feed [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] indipendentemente dall'origine dati sottostante. Quando [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] accetta una richiesta HTTP per una risorsa identificata da un URI, la richiesta viene deserializzata e una rappresentazione di tale richiesta viene passata a un provider di [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Questo provider traduce la richiesta in un formato specifico dell'origine dati ed esegue la richiesta sull'origine dati sottostante. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] realizza l'indipendenza di archiviazione separando il modello concettuale per l'indirizzamento delle risorse previste da [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] dallo schema specifico dell'origine dati sottostante.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] si integra con ADO.NET Entity Framework per consentire la creazione di servizi dati che espongono dati relazionali. È possibile usare gli strumenti di Entity Data Model per creare un modello di dati contenente risorse indirizzabili come entità e definire contemporaneamente il mapping tra questo modello e le tabelle nel database sottostante. Per ulteriori informazioni, vedere [Provider Entity Framework](entity-framework-provider-wcf-data-services.md).  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]consente inoltre di creare servizi dati che espongono strutture di dati che restituiscono un'implementazione dell' <xref:System.Linq.IQueryable%601> interfaccia. In questo modo è possibile creare servizi dati che espongono dati di tipi di .NET Framework. Le operazioni di creazione, aggiornamento ed eliminazione sono supportate quando si implementa anche l'interfaccia <xref:System.Data.Services.IUpdatable>. Per ulteriori informazioni, vedere [provider di Reflection](reflection-provider-wcf-data-services.md).  
  
 Per un'illustrazione di come [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] si integra con questi provider di dati, vedere il diagramma dell'architettura più avanti in questo argomento.  
  
## <a name="custom-business-logic"></a>Logica di business personalizzata  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]semplifica l'aggiunta di logica di business personalizzata a un servizio dati tramite operazioni del servizio e intercettori. Le operazioni del servizio sono metodi definiti nel server che possono essere indirizzati tramite URI allo stesso modo delle risorse di dati. Le operazioni del servizio possono inoltre utilizzare la sintassi delle espressioni di query per filtrare e ordinare i dati restituiti da un'operazione ed eseguirne il paging. L'URI `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$orderby=OrderDate&$top=10&$skip=10` rappresenta ad esempio una chiamata a un'operazione del servizio denominata `GetOrdersByCity` nel servizio dati Northwind che restituisce gli ordini dei clienti residenti a Londra, con i risultati di paging ordinati per `OrderDate`. Per altre informazioni, vedere [operazioni del servizio](service-operations-wcf-data-services.md).  
  
 Gli intercettori consentono l'integrazione della logica delle applicazioni personalizzata nell'elaborazione dei messaggi di richiesta o di risposta da parte di un servizio dati. Gli intercettori vengono chiamati quando si verifica un'azione di query, inserimento, aggiornamento o eliminazione nel set di entità specificato. Un intercettore può modificare i dati, applicare criteri di autorizzazione o anche terminare l'operazione. I metodi dell'intercettore devono essere registrati in modo esplicito per un determinato set di entità esposto da un servizio dati. Per ulteriori informazioni, vedere [intercettori](interceptors-wcf-data-services.md).  
  
## <a name="client-libraries"></a>Librerie client  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]definisce un set di modelli uniformi per l'interazione con i servizi dati. Questo consente di creare componenti riutilizzabili basati su questi servizi, ad esempio librerie sul lato client che semplificano l'utilizzo dei servizi dati.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] include librerie client sia per le applicazioni client basate su .NET Framework che su Silverlight. Queste librerie client consentono di interagire con i servizi dati usando oggetti di .NET Framework. Supportano inoltre query basate su oggetto e query LINQ, caricamento di oggetti correlati, rilevamento di modifiche e risoluzione di identità. Per ulteriori informazioni, vedere [WCF Data Services libreria client](wcf-data-services-client-library.md).  
  
 Oltre alle [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] librerie client incluse nel .NET Framework e con Silverlight, sono disponibili altre librerie client che consentono di utilizzare un [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed nelle applicazioni client, ad esempio le applicazioni PHP, Ajax e Java. Per ulteriori informazioni, vedere [OData SDK](https://go.microsoft.com/fwlink/?LinkID=185796).  
  
## <a name="architecture-overview"></a>Panoramica dell'architettura  
 Il diagramma seguente illustra l'architettura [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] per [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] esporre i feed e usare questi feed nelle [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]librerie client abilitate:  
  
 ![Screenshot che illustra un diagramma dell'architettura WCF Data Services.](./media/wcf-data-services-overview/windows-communication-foundation-data-services-architecture.gif)  
  
## <a name="see-also"></a>Vedere anche

- [WCF Data Services 4.5](index.md)
- [Introduzione](getting-started-with-wcf-data-services.md)
- [Definizione di WCF Data Services](defining-wcf-data-services.md)
- [Accesso alle risorse del servizio dati (WCF Data Services)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd728283(v=vs.100))
- [Libreria client WCF Data Services](wcf-data-services-client-library.md)
- [REST (Representational State Transfer)](https://go.microsoft.com/fwlink/?LinkId=113919)
