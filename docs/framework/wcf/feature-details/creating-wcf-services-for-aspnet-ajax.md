---
title: Creazione di servizi WCF per ASP.NET AJAX
ms.date: 03/30/2017
ms.assetid: 04c0402c-e617-4ba5-aedf-d17692234776
ms.openlocfilehash: 64be5c8ec0d3ee105e026794912a9820bd7892d0
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045960"
---
# <a name="creating-wcf-services-for-aspnet-ajax"></a>Creazione di servizi WCF per ASP.NET AJAX

Microsoft ASP.NET AJAX consente di creare rapidamente pagine Web caratterizzate da un'esperienza utente più soddisfacente con i classici elementi dell'interfaccia utente di elevata reattività. ASP.NET AJAX fornisce librerie di script client in cui sono incorporate tecnologie multibrowser ECMAScript (JavaScript) e DHTML (HTML dinamico), nonché l'integrazione con la piattaforma di sviluppo basata su server ASP.NET 2.0. Con ASP.NET AJAX è possibile migliorare l'esperienza utente e l'efficienza delle applicazioni Web.

ASP.NET AJAX è costituito da librerie di script client e da componenti server integrati per fornire un framework di sviluppo affidabile. Per accedere a un servizio da una pagina ASP.NET: dopo l'aggiunta dell'URL del servizio al controllo Script Manager di ASP.NET nella pagina, è possibile richiamare le operazioni del servizio utilizzando codice JavaScript che assomiglia esattamente a una normale chiamata alla funzione JavaScript. Vedere [informazioni su ASP.NET AJAX](https://go.microsoft.com/fwlink/?LinkId=186475) sull'uso dei servizi Web all'interno del framework AJAX.

La maggior parte dei servizi di Windows Communication Foundation (WCF) può essere esposta come un servizio compatibile con ASP.NET AJAX aggiungendo un endpoint ASP.NET AJAX appropriato.

Se si utilizza Visual Studio, è possibile utilizzare un modello predefinito per i servizi WCF abilitati per AJAX, disponibile nella finestra di dialogo **Aggiungi nuovo elemento** quando si utilizzano siti Web o applicazioni Web ASP.NET.

Se non si stanno utilizzando i modelli di Visual Studio, esistono due modalità per creare un endpoint ASP.NET AJAX:

- Creare l'endpoint utilizzando l'attivazione dinamica dell'host senza utilizzare alcuna configurazione. Questo è l'approccio più elementare se non si conosce il sistema di configurazione WCF. Per altre informazioni, vedere [Procedura: Aggiungere un endpoint ASP.NET AJAX senza usare la](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)configurazione.

- Aggiungere un endpoint abilitato per AJAX a un servizio WCF utilizzando la configurazione. Per altre informazioni, vedere [Procedura: Usare la configurazione per aggiungere un endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)ASP.NET AJAX.

Il modello di programmazione Web descritto nella [Panoramica del modello di programmazione HTTP Web WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md) può essere utilizzato con i servizi ASP.NET AJAX. In particolare:

- È possibile utilizzare gli attributi <xref:System.ServiceModel.Web.WebGetAttribute> e <xref:System.ServiceModel.Web.WebInvokeAttribute> per selezionare tra i verbi HTTP GET e HTTP POST. Se utilizzati correttamente, possono migliorare notevolmente le prestazioni dell'applicazione. Per altre informazioni, vedere [Procedura: Scegliere tra le richieste HTTP POST e HTTP GET per gli endpoint](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md)ASP.NET AJAX.

- È possibile utilizzare le proprietà <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> e <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> affinché il servizio restituisca dati XML anziché la notazione JSON (JavaScript Object Notation) predefinita. L'utilizzo di questo approccio con il framework ASP.NET AJAX fa sì che il client JavaScript riceva un oggetto XML DOM.

  > [!WARNING]
  > Per funzionare, l'operazione deve impostare il tipo di contenuto su Text/XML. In caso contrario, il client JavaScript riceverà una stringa che contiene XML anziché un oggetto XML DOM.

    Di seguito viene riportato l'esempio di un'operazione che restituisce dati XML con il tipo di contenuto impostato in modo appropriato:

  ```csharp
  [OperationContract, WebGet(ResponseFormat=WebMessageFormat.Xml)]
  public XElement GetData()
  {
      XElement x;
      //Get some data here...

      WebOperationContext.Current.OutgoingResponse.ContentType = "text/xml";
      return x;
  }
  ```

- Se è richiesta la compatibilità con ASP.NET AJAX, non è possibile modificare nessun'altra proprietà negli attributi <xref:System.ServiceModel.Web.WebGetAttribute> e <xref:System.ServiceModel.Web.WebInvokeAttribute>. Gli altri aspetti del modello di programmazione Web possono essere utilizzati a condizione che non vengano violate le convenzioni di chiamata ASP.NET AJAX.

 Per gli scenari più avanzati è necessario comprendere alcuni dettagli aggiuntivi del supporto AJAX in WCF:

- Per informazioni sulla modalità di trasferimento dei dati tra un client di pagine AJAX e un servizio WCF tramite JavaScript e per informazioni dettagliate sulla modalità di mapping dei tipi .NET Framework ai tipi JavaScript, vedere [supporto per JSON e altri formati di trasferimento dati](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md).

- Per sfruttare le funzionalità di ASP.NET, ad esempio, l'autenticazione basata su URL e l'accesso alle informazioni della sessione ASP.NET, è consigliabile abilitare la modalità di compatibilità ASP.NET tramite la configurazione.

Gli endpoint AJAX in WCF possono anche essere utilizzati senza il framework ASP.NET AJAX. In questo modo è necessario comprendere l'architettura di supporto del supporto AJAX in WCF. Per informazioni su questa architettura, vedere [modello a oggetti di programmazione HTTP Web di WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md). Per un esempio di codice che illustra questo approccio, vedere il [servizio AJAX con JSON e XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).

## <a name="see-also"></a>Vedere anche

- [Modello di programmazione HTTP Web di WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [Procedura: Aggiungere un endpoint ASP.NET AJAX senza usare la configurazione](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)
- [Procedura: Usare la configurazione per aggiungere un endpoint ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
- [Procedura: Scegliere tra le richieste HTTP POST e HTTP GET per gli endpoint ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md)
