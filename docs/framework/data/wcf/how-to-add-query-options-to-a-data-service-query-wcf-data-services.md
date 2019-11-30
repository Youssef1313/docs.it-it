---
title: 'Procedura: aggiungere opzioni di query a una query del servizio dati (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- querying the data service [WCF Data Services]
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: e4258526-557e-4e96-91e1-2175400c7c8f
ms.openlocfilehash: 7b5a9c15f2d46c89abf8fb5bc0f4be99e501a267
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569189"
---
# <a name="how-to-add-query-options-to-a-data-service-query-wcf-data-services"></a>Procedura: aggiungere opzioni di query a una query del servizio dati (WCF Data Services)
WCF Data Services consente di eseguire una query su un servizio dati da un'applicazione client basata su .NET Framework utilizzando le classi del servizio dati client generate. Il modo più semplice per conseguire questo risultato consiste nel creare un 'espressione di query LINQ (Language Integrated Query) con le opzioni query desiderate. È inoltre possibile chiamare una serie di metodi di query LINQ per creare una query equivalente. È infine possibile usare il metodo <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> per aggiungere opzioni query a una query. In ciascuno di questi casi l'URI generato dal client include il set di entità richiesto con le opzioni query selezionate applicate. Per ulteriori informazioni, vedere [esecuzione di query sul servizio dati](querying-the-data-service-wcf-data-services.md).  
  
 Nell'esempio riportato in questo argomento vengono usati il servizio dati Northwind di esempio e le classi del servizio dati client generate automaticamente. Questo servizio e le classi di dati client vengono creati al completamento della [WCF Data Services avvio rapido](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come creare un'espressione di query LINQ che restituisce solo gli ordini con un costo di spedizione maggiore di 30 dollari e ordina i risultati in senso decrescente in base alla data di spedizione.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsLinq](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinq)]
 [!code-vb[Astoria Northwind Client#AddQueryOptionsLinq](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinq)]  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come creare una query LINQ equivalente alla query precedente tramite i metodi di query LINQ.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqExpression](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqexpression)]
 [!code-vb[Astoria Northwind Client#AddQueryOptionsLinqExpression](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqexpression)]  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come usare il metodo <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> per creare un oggetto <xref:System.Data.Services.Client.DataServiceQuery%601> equivalente agli esempi precedenti.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptions)]
 [!code-vb[Astoria Northwind Client#AddQueryOptions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptions)]  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come usare l'opzione query `$orderby` per filtrare e ordinare gli oggetti Orders restituiti in base alla proprietà Freight.  
  
 [!code-csharp[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#orderwithfilter)]
 [!code-vb[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#orderwithfilter)]  
  
## <a name="see-also"></a>Vedere anche

- [Esecuzione di query sul servizio dati](querying-the-data-service-wcf-data-services.md)
- [Procedura: proiettare risultati di query](how-to-project-query-results-wcf-data-services.md)
