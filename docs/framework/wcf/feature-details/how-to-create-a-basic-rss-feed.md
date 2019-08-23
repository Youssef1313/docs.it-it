---
title: 'Procedura: Creare un feed RSS di base'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 431879b8-a5f8-4947-ad1e-4768c726aca8
ms.openlocfilehash: 9a07754e8fdad700bd5488f392f80b5c5f907f6e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968449"
---
# <a name="how-to-create-a-basic-rss-feed"></a>Procedura: Creare un feed RSS di base
Windows Communication Foundation (WCF) consente di creare un servizio che espone un feed di diffusione. In questo argomento viene illustrato come creare un servizio di diffusione che espone un feed di diffusione RSS.  
  
### <a name="to-create-a-basic-syndication-service"></a>Per creare un servizio di diffusione di base  
  
1. Definire un contratto di servizio usando un'interfaccia contrassegnata con l'attributo <xref:System.ServiceModel.Web.WebGetAttribute>. Ogni operazione esposta come feed di diffusione deve restituire un oggetto <xref:System.ServiceModel.Syndication.Rss20FeedFormatter>.  
  
     [!code-csharp[htRssBasic#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#0)]
     [!code-vb[htRssBasic#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#0)]  
  
    > [!NOTE]
    > Tutte le operazioni del servizio che applicano l'attributo <xref:System.ServiceModel.Web.WebGetAttribute> vengono mappate alle richieste HTTP GET. Per eseguire il mapping dell'operazione a un metodo HTTP diverso, utilizzare invece <xref:System.ServiceModel.Web.WebInvokeAttribute>. Per altre informazioni, vedere [Procedura: Creare un servizio](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)http Web WCF di base.  
  
2. Implementare il contratto di servizio  
  
     [!code-csharp[htRssBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#1)]
     [!code-vb[htRssBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#1)]  
  
3. Creare un oggetto <xref:System.ServiceModel.Syndication.SyndicationFeed> e aggiungere un autore, una categoria e una descrizione.  
  
     [!code-csharp[htRssBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#2)]
     [!code-vb[htRssBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#2)]  
  
4. Creare diversi oggetti <xref:System.ServiceModel.Syndication.SyndicationItem>.  
  
     [!code-csharp[htRssBasic#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#3)]
     [!code-vb[htRssBasic#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#3)]  
  
5. Aggiungere <xref:System.ServiceModel.Syndication.SyndicationItem> al feed.  
  
     [!code-csharp[htRssBasic#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#4)]
     [!code-vb[htRssBasic#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#4)]  
  
6. Restituire il feed.  
  
     [!code-csharp[htRssBasic#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#5)]
     [!code-vb[htRssBasic#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#5)]  
  
### <a name="to-host-a-service"></a>Per ospitare un servizio  
  
1. Creare un oggetto <xref:System.ServiceModel.Web.WebServiceHost>.  
  
     [!code-csharp[htRssBasic#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#6)]
     [!code-vb[htRssBasic#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#6)]  
  
2. Aprire l'host del servizio e attendere finché l'utente non preme INVIO.  
  
     [!code-csharp[htRssBasic#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#8)]
     [!code-vb[htRssBasic#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a>Per chiamare GetBlog() con un HTTP GET  
  
1. Aprire Internet Explorer, digitare l'URL seguente e premere INVIO: `http://localhost:8000/BlogService/GetBlog`. L'URL contiene l'indirizzo di base del servizio (`http://localhost:8000/BlogService`), l'indirizzo relativo dell'endpoint e l'operazione del servizio da chiamare.  
  
### <a name="to-call-getblog-from-code"></a>Per chiamare GetBlog() dal codice  
  
1. Creare un <xref:System.Xml.XmlReader> con l'indirizzo di base e il metodo che si sta chiamando.  
  
     [!code-csharp[htRssBasic#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#9)]
     [!code-vb[htRssBasic#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#9)]  
  
2. Chiamare il metodo statico <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> passando l'oggetto <xref:System.Xml.XmlReader> appena creato.  
  
     [!code-csharp[htRssBasic#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#10)]
     [!code-vb[htRssBasic#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#10)]  
  
     Verrà in tal modo richiamata l'operazione del servizio e verrà popolato un nuovo <xref:System.ServiceModel.Syndication.SyndicationFeed> con il formattatore restituito dall'operazione del servizio.  
  
3. Accedere all'oggetto feed.  
  
     [!code-csharp[htRssBasic#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/snippets.cs#11)]
     [!code-vb[htRssBasic#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/snippets.vb#11)]  
  
## <a name="example"></a>Esempio  
 Di seguito è riportato il codice completo per questo esempio.  
  
 [!code-csharp[htRssBasic#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htrssbasic/cs/program.cs#12)]
 [!code-vb[htRssBasic#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htrssbasic/vb/program.vb#12)]  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 Durante la compilazione del codice precedente, fare riferimento a System.ServiceModel.dll e a System.ServiceModel.Web.dll.  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
