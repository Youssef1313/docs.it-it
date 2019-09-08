---
title: Operazioni di servizio (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: 583a690a-e60f-4990-8991-d6efce069d76
ms.openlocfilehash: f905eb90b47cb5ab20fd912b1cbcc62947361992
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779767"
---
# <a name="service-operations-wcf-data-services"></a>Operazioni di servizio (WCF Data Services)

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] consente di definire operazioni del servizio in un servizio dati per esporre metodi nel server. Allo stesso modo di altre risorse del servizio dati, le operazioni del servizio vengono indirizzate mediante URI. Le operazioni del servizio consentono di esporre la logica di business in un servizio dati, ad esempio per implementare la logica di convalida, per applicare la sicurezza basata sui ruoli o per esporre funzionalità di query specializzate. Le operazioni del servizio sono metodi aggiunti alla classe del servizio dati che deriva da <xref:System.Data.Services.DataService%601>. Analogamente a tutte le altre risorse del servizio dati, è possibile fornire parametri al metodo dell'operazione del servizio. Ad esempio, l'URI dell'operazione del servizio seguente, basato sul servizio dati di [avvio rapido](quickstart-wcf-data-services.md) , `London` passa il `city` valore al parametro:

```
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'
```

La definizione per questa operazione del servizio è la seguente:

[!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationdef)]
[!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationdef)]

È possibile usare la proprietà <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> dell'oggetto <xref:System.Data.Services.DataService%601> per accedere direttamente all'origine dati usata dal servizio dati. Per altre informazioni, vedere [Procedura: Definire un'operazione](how-to-define-a-service-operation-wcf-data-services.md)del servizio.

Per informazioni su come chiamare un'operazione del servizio da un'applicazione client di .NET Framework, vedere [chiamata di operazioni del servizio](calling-service-operations-wcf-data-services.md).

## <a name="service-operation-requirements"></a>Requisiti delle operazioni del servizio

I requisiti seguenti si applicano in caso di definizione di operazioni del servizio nel servizio dati. Se un metodo non soddisfa questi requisiti, non verrà esposto come operazione del servizio per il servizio dati.

- L'operazione deve essere un metodo di istanza pubblica, ovvero un membro della classe del servizio dati.

- È possibile che il metodo dell'operazione accetti solo parametri di input. L'accesso ai dati inviati nel corpo del messaggio non può essere eseguito dal servizio dati.

- Se sono definiti parametri, il tipo di ogni parametro deve essere primitivo. I dati di un tipo non primitivo devono essere serializzati e passati in un parametro di stringa.

- Il metodo deve restituire uno degli elementi seguenti:

  - `void` (`Nothing` in Visual Basic)

  - <xref:System.Collections.Generic.IEnumerable%601>

  - <xref:System.Linq.IQueryable%601>

  - Un tipo di entità nel modello di dati esposto dal servizio dati.

  - Una classe primitiva, ad esempio Integer o stringa.

- Per supportare opzioni di query di ordinamento, paging e filtro, i metodi delle operazioni del servizio devono restituire <xref:System.Linq.IQueryable%601>. Le richieste a operazioni del servizio che includono opzioni di query vengono rifiutate per le operazioni che restituiscono solo <xref:System.Collections.Generic.IEnumerable%601>.

- Per supportare l'accesso alle entità correlate tramite le proprietà di navigazione, l'operazione del servizio deve restituire <xref:System.Linq.IQueryable%601>.

- Il metodo deve essere annotato con l'attributo `[WebGet]` o `[WebInvoke]`.

  - `[WebGet]` abilita il metodo da richiamare tramite una richiesta GET.

  - `[WebInvoke(Method = "POST")]` abilita il metodo da richiamare tramite una richiesta POST. Altri metodi <xref:System.ServiceModel.Web.WebInvokeAttribute> non sono supportati.

- Un'operazione del servizio può essere annotata con <xref:System.Data.Services.SingleResultAttribute> che specifica che il valore restituito dal metodo è una singola entità anziché una raccolta di entità. Questa distinzione determina la serializzazione della risposta e il modo in cui gli attraversamenti delle proprietà di navigazione aggiuntivi vengono rappresentati nell'URI. Nel caso di utilizzo della serializzazione AtomPub, ad esempio, un'istanza singola del tipo di risorsa viene rappresentata come elemento entry e un set di istanze come elemento feed.

## <a name="addressing-service-operations"></a>Indirizzamento di operazioni di servizio

È possibile indirizzare le operazioni del servizio inserendo il nome del metodo nel primo segmento di percorso di un URI. Ad esempio, l'URI riportato di seguito consente l'accesso a un'operazione `GetOrdersByState` che restituisce una raccolta <xref:System.Linq.IQueryable%601> di oggetti `Orders`.

```
http://localhost:12345/Northwind.svc/GetOrdersByState?state='CA'&includeItems=true
```

Quando si chiama un'operazione del servizio, i parametri vengono forniti come opzioni query. L'operazione del servizio precedente accetta sia un parametro di stringa `state` che un parametro booleano `includeItems` che indicano se includere oggetti `Order_Detail` correlati nella risposta.

Di seguito sono riportati i tipi restituiti validi per un'operazione del servizio:

|Tipi restituiti validi|Regole URI|
|------------------------|---------------|
|`void` (`Nothing` in Visual Basic)<br /><br /> -oppure-<br /><br /> Tipi di entità<br /><br /> -oppure-<br /><br /> Tipi primitivi|L'URI deve essere costituito da un singolo segmento di percorso corrispondente al nome dell'operazione del servizio. Le opzioni di query non sono consentite.|
|<xref:System.Collections.Generic.IEnumerable%601>|L'URI deve essere costituito da un singolo segmento di percorso corrispondente al nome dell'operazione del servizio. Poiché il tipo di risultato non è un tipo <xref:System.Linq.IQueryable%601>, le opzioni di query non sono consentite.|
|<xref:System.Linq.IQueryable%601>|Oltre al percorso corrispondente al nome dell'operazione del servizio, sono consentiti segmenti di percorso di query. Sono consentite anche le opzioni di query.|

A seconda del tipo restituito dell'operazione del servizio, è possibile aggiungere all'URI segmenti di percorso o opzioni di query aggiuntive. Ad esempio, l'URI riportato di seguito consente l'accesso a un'operazione `GetOrdersByCity` che restituisce una raccolta <xref:System.Linq.IQueryable%601> di oggetti `Orders` ordinati in ordine decrescente in base a `RequiredDate` insieme agli oggetti `Order_Details` correlati:

```
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc
```

## <a name="service-operations-access-control"></a>Controllo di accesso alle operazioni del servizio

La visibilità a livello di servizio delle operazioni del servizio viene controllata dal metodo <xref:System.Data.Services.IDataServiceConfiguration.SetServiceOperationAccessRule%2A> sulla classe <xref:System.Data.Services.IDataServiceConfiguration> pressoché nello stesso modo in cui viene controllata la visibilità del set di entità tramite il metodo <xref:System.Data.Services.IDataServiceConfiguration.SetEntitySetAccessRule%2A>. Ad esempio, la riga di codice seguente nella definizione del servizio dati abilita l'accesso all'operazione del servizio `CustomersByCity`.

[!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationconfig)]
[!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationconfig)]

> [!NOTE]
> Se un'operazione del servizio dispone di un tipo restituito nascosto mediante limitazione dell'accesso nei set di entità sottostanti, l'operazione del servizio non sarà disponibile alle applicazioni client.

Per altre informazioni, vedere [Procedura: Definire un'operazione](how-to-define-a-service-operation-wcf-data-services.md)del servizio.

## <a name="raising-exceptions"></a>Generazione di eccezioni

È consigliabile usare la classe <xref:System.Data.Services.DataServiceException> quando si genera un'eccezione nell'esecuzione del servizio dati, poiché il runtime del servizio dati è in grado di eseguire il mapping delle proprietà di questo oggetto eccezione al messaggio di risposta HTTP in modo corretto. Quando si genera un oggetto <xref:System.Data.Services.DataServiceException> in un'operazione del servizio, verrà eseguito il wrapping dell'eccezione restituita in un oggetto <xref:System.Reflection.TargetInvocationException>. Per restituire l'oggetto <xref:System.Data.Services.DataServiceException> di base senza includere l'oggetto <xref:System.Reflection.TargetInvocationException>, è necessario eseguire l'override del metodo <xref:System.Data.Services.DataService%601.HandleException%2A> in <xref:System.Data.Services.DataService%601>, estrarre <xref:System.Data.Services.DataServiceException> da <xref:System.Reflection.TargetInvocationException> e restituirlo come errore di livello superiore, come illustrato nell'esempio seguente:

[!code-csharp[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#handleexceptions)]
[!code-vb[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#handleexceptions)]

## <a name="see-also"></a>Vedere anche

- [Intercettori](interceptors-wcf-data-services.md)
