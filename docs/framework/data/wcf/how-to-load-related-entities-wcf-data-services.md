---
title: 'Procedura: Carica entità correlate (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: 6f143d30-d997-4e6b-bcf0-d5c394ecb108
ms.openlocfilehash: 14b0ba988c96c270610208a4f944083bb333eac5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780023"
---
# <a name="how-to-load-related-entities-wcf-data-services"></a>Procedura: Carica entità correlate (WCF Data Services)
Per caricare entità associate in [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], è possibile usare il metodo <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> sulla classe <xref:System.Data.Services.Client.DataServiceContext>. È anche possibile usare il <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> metodo <xref:System.Data.Services.Client.DataServiceQuery%601> su per richiedere che le entità correlate vengano caricate in modo eager nella stessa risposta alla query.  
  
 Nell'esempio riportato in questo argomento vengono usati il servizio dati Northwind di esempio e le classi del servizio dati client generate automaticamente. Questo servizio e le classi di dati client vengono creati al completamento della [WCF Data Services avvio rapido](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come caricare in modo esplicito l'entità `Customer` correlata a ogni istanza di `Orders` restituita.  
  
 [!code-csharp[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadrelatedordercustomer)]
 [!code-vb[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadrelatedordercustomer)]  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come usare il metodo <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> per restituire le entità `Order Details` che appartengono all'entità `Orders` restituita dalla query.  
  
 [!code-csharp[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#expandorderdetails)]
 [!code-vb[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#expandorderdetails)]  
  
## <a name="see-also"></a>Vedere anche

- [Esecuzione di query sul servizio dati](querying-the-data-service-wcf-data-services.md)
