---
title: "Procedura: aggiungere un endpoint ASP.NET AJAX con l'uso della configurazione"
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: 3ccfb34614707c17885da3ed37f545bbab808869
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978259"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a>Procedura: aggiungere un endpoint ASP.NET AJAX con l'uso della configurazione
Windows Communication Foundation (WCF) consente di creare un servizio che rende disponibile un endpoint ASP.NET compatibile con AJAX che può essere chiamato da JavaScript su un sito Web client. Per creare un endpoint di questo tipo, è possibile utilizzare un file di configurazione, come con tutti gli altri endpoint Windows Communication Foundation (WCF), oppure utilizzare un metodo che non richiede elementi di configurazione. In questo argomento viene illustrato l'approccio tramite configurazione.  
  
 La parte della procedura che consente all'endpoint di servizio di diventare ASP.NET AJAX-Enabled consiste nella configurazione dell'endpoint per l'uso del <xref:System.ServiceModel.WebHttpBinding> e per aggiungere il [\<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) comportamento dell'endpoint. Dopo aver configurato l'endpoint, i passaggi per implementare e ospitare il servizio sono simili a quelli utilizzati da qualsiasi servizio WCF. Per un esempio funzionante, vedere il [servizio AJAX che usa http post](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
 Per altre informazioni su come configurare un endpoint ASP.NET AJAX senza usare la configurazione, vedere [procedura: aggiungere un endpoint ASP.NET AJAX senza usare la configurazione](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
## <a name="to-create-a-basic-wcf-service"></a>Per creare un servizio WFC di base  
  
1. Definire un contratto di servizio WCF di base con un'interfaccia contrassegnata con l'attributo <xref:System.ServiceModel.ServiceContractAttribute>. Contrassegnare ogni operazione con <xref:System.ServiceModel.OperationContractAttribute>. Assicurarsi di impostare la proprietà <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A>.  
  
    ```csharp
    [ServiceContract(Namespace = "MyService")]  
    public interface ICalculator  
    {  
        [OperationContract]  
         // This operation returns the sum of d1 and d2.  
        double Add(double n1, double n2);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2. Implementare il contratto di servizio `ICalculator` con `CalculatorService`.  
  
    ```csharp
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }
        // Other operations omitted…
    }
    ```  
  
3. Definire uno spazio dei nomi per le implementazioni `ICalculator` e `CalculatorService` eseguendo il wrapping di queste ultime in un blocco dello spazio dei nomi.  
  
    ```csharp
    namespace Microsoft.Ajax.Samples
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
## <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a>Per creare endpoint ASP.NET AJAX per il servizio.  
  
1. Creare una configurazione di comportamento e specificare il comportamento di [\<> enableWebScript](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) per gli endpoint abilitati per ASP.NET AJAX del servizio.  
  
    ```xml  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="AspNetAjaxBehavior">  
                    <enableWebScript />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
    </system.serviceModel>  
    ```  
  
2. Creare un endpoint per il servizio che utilizza <xref:System.ServiceModel.WebHttpBinding> e il comportamento ASP.NET AJAX definito nel passaggio precedente.  
  
    ```xml  
    <system.serviceModel>  
        <services>  
            <service name="Microsoft.Ajax.Samples.CalculatorService">  
                <endpoint address=""  
                    behaviorConfiguration="AspNetAjaxBehavior"   
                    binding="webHttpBinding"  
                    contract="Microsoft.Ajax.Samples.ICalculator" />  
            </service>  
        </services>  
    </system.serviceModel>   
    ```  
  
## <a name="to-host-the-service-in-iis"></a>Per ospitare il servizio in IIS  
  
1. Per ospitare il servizio in IIS, creare nell'applicazione un nuovo file denominato "service" con estensione svc. Modificare questo file aggiungendo le informazioni della direttiva [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) appropriate per il servizio. Ad esempio, il file del servizio per l'esempio `CalculatorService` contiene le informazioni seguenti:  
  
    ```
    <%@ServiceHost   
    language=c#   
    Debug="true"   
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2. Per ulteriori informazioni sull'hosting in IIS, vedere [procedura: ospitare un servizio WCF in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
## <a name="to-call-the-service"></a>Per chiamare il servizio  
  
1. L'endpoint è configurato in un indirizzo vuoto relativo al file con estensione svc, quindi il servizio è ora disponibile e può essere richiamato inviando richieste all'operazione Service. svc/\<>, ad esempio Service. svc/Add per l'operazione di `Add`. È possibile utilizzarlo immettendo l'URL dell'endpoint nella raccolta degli script del controllo Script Manager ASP.NET AJAX. Per un esempio, vedere il [servizio AJAX che usa http post](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
## <a name="see-also"></a>Vedere anche

- [Creazione di servizi WCF per ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [Procedura: Eseguire la migrazione di servizi Web ASP.NET abilitati AJAX in WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
