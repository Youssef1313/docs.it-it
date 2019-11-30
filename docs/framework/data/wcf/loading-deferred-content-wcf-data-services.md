---
title: Caricamento di contenuto posticipato (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: 32f9b588-c832-44c4-a7e0-fcce635df59a
ms.openlocfilehash: 811118755c4688bd0ea8cb9ba37b2101ab6c52cf
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568949"
---
# <a name="loading-deferred-content-wcf-data-services"></a>Caricamento di contenuto posticipato (WCF Data Services)
Per impostazione predefinita, WCF Data Services limita la quantità di dati restituiti da una query. Se necessario, dal servizio dati è tuttavia possibile caricare in modo esplicito dati aggiuntivi, tra cui entità correlate, dati di risposta di paging e flussi di dati binari. In questo argomento viene descritto come caricare questo tipo di contenuto posticipato nell'applicazione.  
  
## <a name="related-entities"></a>Entità correlate  
 Quando si esegue una query, vengono restituite solo le entità incluse nel set di entità indirizzato. Ad esempio, quando una query eseguita sul servizio dati Northwind restituisce le entità `Customers`, per impostazione predefinita non vengono restituite le entità `Orders` correlate, anche se esiste una relazione tra `Customers` e `Orders`. Inoltre, quando nel servizio dati è abilitato il paging, è necessario caricare in modo esplicito le pagine di dati successive dal servizio. Per caricare le entità correlate è possibile usare due modi:  
  
- **Caricamento eager**: è possibile utilizzare l'opzione query `$expand` per richiedere che la query restituisca entità correlate da un'associazione al set di entità richiesto dalla query. Usare il metodo <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> su <xref:System.Data.Services.Client.DataServiceQuery%601> per aggiungere l'opzione `$expand` alla query inviata al servizio dati. È possibile richiedere più set di entità correlati separandoli con una virgola, come illustrato nell'esempio seguente. Tutte le entità richieste dalla query vengono restituite in un'unica risposta. Nell'esempio seguente vengono restituiti `Order_Details` e `Customers` insieme al set di entità `Orders`:  
  
     [!code-csharp[Astoria Northwind Client#ExpandOrderDetailsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#expandorderdetailsspecific)]
     [!code-vb[Astoria Northwind Client#ExpandOrderDetailsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#expandorderdetailsspecific)]  
  
     WCF Data Services limite a 12 il numero di set di entità che è possibile includere in una singola query utilizzando l'opzione di query `$expand`.  
  
- **Caricamento esplicito**: è possibile chiamare il metodo <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> sull'istanza <xref:System.Data.Services.Client.DataServiceContext> per caricare in modo esplicito le entità correlate. Ogni chiamata del metodo <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> determina la creazione di una richiesta distinta al servizio dati. Nell'esempio seguente viene caricato in modo esplicito `Order_Details` per un'entità `Orders`.  
  
     [!code-csharp[Astoria Northwind Client#LoadRelatedOrderDetailsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadrelatedorderdetailsspecific)]
     [!code-vb[Astoria Northwind Client#LoadRelatedOrderDetailsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadrelatedorderdetailsspecific)]  
  
 Nella scelta dell'opzione da usare tener presente che è possibile un compromesso tra il numero di richieste per il servizio dati e la quantità di dati restituiti in una singola risposta. Usare il caricamento eager quando l'applicazione richiede oggetti associati e si desidera evitare la latenza aggiunta per le richieste supplementari necessaria per il loro recupero in modo esplicito. Tuttavia, se vi sono casi in cui l'applicazione necessita solo dei dati per le istanze di entità correlate specifiche, considerare la possibilità di caricare in modo esplicito tali entità chiamando il metodo <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A>. Per altre informazioni, vedere [procedura: caricare entità correlate](how-to-load-related-entities-wcf-data-services.md).  
  
## <a name="paged-content"></a>Contenuto di paging  
 Quando nel servizio dati è abilitato il paging, il numero di voci incluse nel feed restituito dal servizio dati è limitato dalla configurazione del servizio dati. È possibile impostare i limiti di paging separatamente per ogni set di entità. Per ulteriori informazioni, vedere [configurazione del servizio dati](configuring-the-data-service-wcf-data-services.md). Quando il paging è abilitato, la voce finale nel feed contiene un collegamento alla pagina di dati successiva. Questo collegamento è incluso in un oggetto <xref:System.Data.Services.Client.DataServiceQueryContinuation%601>. È possibile ottenere l'URI della pagina successiva di dati chiamando il metodo <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> sull'oggetto <xref:System.Data.Services.Client.QueryOperationResponse%601> restituito durante l'esecuzione di <xref:System.Data.Services.Client.DataServiceQuery%601>. L'oggetto <xref:System.Data.Services.Client.DataServiceQueryContinuation%601> restituito viene quindi usato per caricare la pagina di risultati successiva. Prima di chiamare il metodo <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A>, è necessario enumerare i risultati della query. Considerare la possibilità di usare un ciclo `do…while` per enumerare innanzitutto i risultati della query e verificare quindi se il valore del collegamento successivo corrisponde a `non-null`. Quando il metodo <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> restituisce `null` (`Nothing` in Visual Basic), significa che per la query originale non sono disponibili pagine di risultati aggiuntive. Nell'esempio seguente viene illustrato un ciclo `do…while` che carica i dati dei clienti di cui è stato eseguito il paging dal servizio dati Northwind di esempio.  
  
 [!code-csharp[Astoria Northwind Client#LoadNextLink](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadnextlink)]
 [!code-vb[Astoria Northwind Client#LoadNextLink](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadnextlink)]  
  
 Quando una query richiede che le entità correlate vengano restituite in un'unica risposta insieme al set di entità richiesto, è possibile che i limiti di paging abbiano effetto sui feed annidati inclusi inline con la risposta. Ad esempio, quando un limite di paging viene impostato nel servizio dati Northwind di esempio per il set di entità `Customers`, è inoltre possibile impostare un limite di paging indipendente per il set di entità `Orders` correlato, come illustrato nell'esempio seguente relativo al file Northwind.svc.cs che definisce il servizio dati Northwind di esempio.  
  
 [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigpaging)]
 [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
 In questo caso, sarà necessario implementare il paging per i feed dell'entità `Customers` di primo livello e feed dell'entità `Orders` annidati. Nell'esempio seguente viene illustrato il ciclo `while` usato per caricare pagine di entità `Orders` correlate a un'entità `Customers` selezionata.  
  
 [!code-csharp[Astoria Northwind Client#LoadNextOrdersLink](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadnextorderslink)]
 [!code-vb[Astoria Northwind Client#LoadNextOrdersLink](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadnextorderslink)]  
  
 Per altre informazioni, vedere [procedura: caricare risultati di paging](how-to-load-paged-results-wcf-data-services.md).  
  
## <a name="binary-data-streams"></a>Flussi di dati binari  
 WCF Data Services consente di accedere ai dati BLOB (Binary Large Object) come flusso di dati. Il flusso posticipa il caricamento dei dati binari fino al momento opportuno per consentire al client di elaborare i dati in maniera più efficiente. Per trarre vantaggio da questa funzionalità, il servizio dati deve implementare il provider <xref:System.Data.Services.Providers.IDataServiceStreamProvider>. Per ulteriori informazioni, vedere [provider di flussi](streaming-provider-wcf-data-services.md). Quando il flusso è abilitato, i tipi di entità vengono restituiti senza i dati binari correlati. In questo caso, è necessario utilizzare il metodo <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> della classe <xref:System.Data.Services.Client.DataServiceContext> per accedere al flusso di dati per i dati binari dal servizio. In modo analogo, usare il metodo <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> per aggiungere o modificare i dati binari di un'entità come flusso. Per ulteriori informazioni, vedere [utilizzo di dati binari](working-with-binary-data-wcf-data-services.md).  
  
## <a name="see-also"></a>Vedere anche

- [Libreria client WCF Data Services](wcf-data-services-client-library.md)
- [Esecuzione di query sul servizio dati](querying-the-data-service-wcf-data-services.md)
