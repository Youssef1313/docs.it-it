---
title: Panoramica dei client WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], architecture
ms.assetid: f60d9bc5-8ade-4471-8ecf-5a07a936c82d
ms.openlocfilehash: 180de3f571426441155a19b98ab750fcdbb3888e
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73420651"
---
# <a name="wcf-client-overview"></a>Panoramica dei client WCF
In questa sezione vengono descritte le operazioni eseguite dalle applicazioni client, come configurare, creare e utilizzare un client Windows Communication Foundation (WCF) e come proteggere le applicazioni client.  
  
## <a name="using-wcf-client-objects"></a>Uso di oggetti client WCF  
 Un'applicazione client è un'applicazione gestita che utilizza un client WCF per comunicare con un'altra applicazione. Per creare un'applicazione client per un servizio WCF, è necessario eseguire i passaggi seguenti:  
  
1. Ottenere le informazioni relative al contratto di servizio, alle associazioni e all'indirizzo per un endpoint di servizio.  
  
2. Creare un client WCF utilizzando tali informazioni.  
  
3. Chiamare le operazioni.  
  
4. Chiudere l'oggetto client WCF.  
  
 Nelle sezioni seguenti vengono illustrate queste procedure e vengono fornite informazioni introduttive sugli argomenti seguenti:  
  
- Gestione degli errori.  
  
- Configurazione e protezione dei client.  
  
- Creazione di oggetti di callback per i servizi duplex.  
  
- Chiamate ai servizi in modo asincrono.  
  
- Chiamate ai servizi mediante canali client.  
  
## <a name="obtain-the-service-contract-bindings-and-addresses"></a>Ottenere informazioni sul contratto di servizio, sulle associazioni e sugli indirizzi  
 In WCF, i servizi e i client modellano i contratti utilizzando attributi, interfacce e metodi gestiti. Per eseguire la connessione a un servizio in un'applicazione client è necessario ottenere le informazioni sul tipo per il contratto di servizio. Questa operazione viene in genere eseguita utilizzando lo [strumento ServiceModel Metadata Utility Tool (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), che Scarica i metadati dal servizio, li converte in un file di codice sorgente gestito nel linguaggio desiderato e crea un file di configurazione dell'applicazione client. che è possibile usare per configurare l'oggetto client WCF. Se ad esempio si intende creare un oggetto client WCF per richiamare una `MyCalculatorService` e si è certi che i metadati per tale servizio siano pubblicati in `http://computerName/MyCalculatorService/Service.svc?wsdl`, nell'esempio di codice riportato di seguito viene illustrato come utilizzare Svcutil. exe per ottenere un file di `ClientCode.vb` contenente la co-Service ntract nel codice gestito.  
  
```console  
svcutil /language:vb /out:ClientCode.vb /config:app.config http://computerName/MyCalculatorService/Service.svc?wsdl  
```  
  
 È possibile compilare questo codice del contratto nell'applicazione client o in un altro assembly che l'applicazione client può utilizzare per creare un oggetto client WCF. Per configurare l'oggetto client per eseguire la connessione al servizio in modo appropriato, è possibile usare il file di configurazione.  
  
 Per un esempio di questo processo, vedere [How to: Create a client](how-to-create-a-wcf-client.md). Per informazioni più complete sui contratti, vedere [contratti](./feature-details/contracts.md).  
  
## <a name="create-a-wcf-client-object"></a>Creare un oggetto client WCF  
 Un client WCF è un oggetto locale che rappresenta un servizio WCF in un modulo che il client può utilizzare per comunicare con il servizio remoto. I tipi di client WCF implementano il contratto di servizio di destinazione, pertanto quando si crea un oggetto e lo si configura, è possibile usare direttamente l'oggetto client per richiamare le operazioni del servizio. Il runtime di WCF converte le chiamate al metodo in messaggi, le invia al servizio, rimane in attesa della risposta e restituisce tali valori all'oggetto client WCF come valori restituiti o parametri `out` o `ref`.  
  
 È inoltre possibile utilizzare gli oggetti canale client WCF per connettersi e utilizzare i servizi. Per informazioni dettagliate, vedere [architettura client WCF](./feature-details/client-architecture.md).  
  
#### <a name="creating-a-new-wcf-object"></a>Creazione di un nuovo oggetto WCF  
 Per illustrare l'uso di una classe <xref:System.ServiceModel.ClientBase%601>, si supponga che il contratto di servizio seguente sia stato generato da un'applicazione di servizio.  
  
> [!NOTE]
> Se si utilizza Visual Studio per creare il client WCF, gli oggetti vengono caricati automaticamente nel Visualizzatore oggetti quando si aggiunge un riferimento al servizio al progetto.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Se non si usa Visual Studio, esaminare il codice del contratto generato per trovare il tipo che estende <xref:System.ServiceModel.ClientBase%601> e l'interfaccia del contratto di servizio `ISampleService`. In questo caso il tipo ha l'aspetto del codice seguente:  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 Questa classe può essere creata come un oggetto locale usando uno dei costruttori, configurata e quindi usata per la connessione a un servizio del tipo `ISampleService`.  
  
 È consigliabile creare prima l'oggetto client WCF e quindi usarlo e chiuderlo all'interno di un singolo blocco try/catch. Non usare l'istruzione `using` (`Using` in Visual Basic) perché potrebbe mascherare eccezioni in determinate modalità di errore. Per ulteriori informazioni, vedere le sezioni seguenti, nonché [utilizzare Close e Abort per rilasciare le risorse client WCF](./samples/use-close-abort-release-wcf-client-resources.md).  
  
### <a name="contracts-bindings-and-addresses"></a>Contratti, associazioni e indirizzi.  
 Prima di poter creare un oggetto client WCF, è necessario configurare l'oggetto client. In particolare, deve disporre di un *endpoint* di servizio da usare. Un endpoint è la combinazione di un contratto di servizio, un'associazione e un indirizzo. Per ulteriori informazioni sugli endpoint, vedere [endpoint: indirizzi, associazioni e contratti](./feature-details/endpoints-addresses-bindings-and-contracts.md). In genere, queste informazioni si trovano nell'elemento [\<endpoint >](../configure-apps/file-schema/wcf/endpoint-of-client.md) in un file di configurazione dell'applicazione client, ad esempio quello generato dallo strumento Svcutil. exe, e vengono caricate automaticamente quando si crea l'oggetto client. Entrambi i tipi di client WCF dispongono inoltre di overload che consentono di specificare a livello di codice queste informazioni.  
  
 Ad esempio, un file di configurazione generato per un servizio `ISampleService` usato negli esempi precedenti contiene le informazioni sull'endpoint riportate di seguito.  
  
 [!code-xml[C_GeneratedCodeFiles#19](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/common/client.exe.config#19)]  
  
 Questo file di configurazione specifica un endpoint di destinazione nell'elemento `<client>`. Per ulteriori informazioni sull'utilizzo di più endpoint di destinazione, vedere il <xref:System.ServiceModel.ClientBase%601.%23ctor%2A?displayProperty=nameWithType> o i costruttori di <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A?displayProperty=nameWithType>.  
  
## <a name="calling-operations"></a>Chiamate alle operazioni  
 Una volta creato e configurato un oggetto client, creare un blocco try/catch, chiamare le operazioni nello stesso modo in cui si otterrebbe se l'oggetto fosse locale e chiudere l'oggetto client WCF. Quando l'applicazione client chiama la prima operazione, WCF apre automaticamente il canale sottostante e il canale sottostante viene chiuso quando l'oggetto viene riciclato. In alternativa, è possibile aprire e chiudere il canale in modo esplicito prima o dopo la chiamata ad altre operazioni.  
  
 Si supponga, ad esempio, di disporre del contratto di servizio seguente:  
  
```csharp  
namespace Microsoft.ServiceModel.Samples  
{  
    using System;  
    using System.ServiceModel;  
  
    [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
    public interface ICalculator  
   {  
        [OperationContract]  
        double Add(double n1, double n2);  
        [OperationContract]  
        double Subtract(double n1, double n2);  
        [OperationContract]  
        double Multiply(double n1, double n2);  
        [OperationContract]  
        double Divide(double n1, double n2);  
    }  
}  
```  
  
```vb  
Namespace Microsoft.ServiceModel.Samples  
  
    Imports System  
    Imports System.ServiceModel  
  
    <ServiceContract(Namespace:= _  
    "http://Microsoft.ServiceModel.Samples")> _   
   Public Interface ICalculator  
        <OperationContract> _   
        Function Add(n1 As Double, n2 As Double) As Double  
        <OperationContract> _   
        Function Subtract(n1 As Double, n2 As Double) As Double  
        <OperationContract> _   
        Function Multiply(n1 As Double, n2 As Double) As Double  
        <OperationContract> _   
     Function Divide(n1 As Double, n2 As Double) As Double  
End Interface  
```  
  
 È possibile chiamare le operazioni creando un oggetto client WCF e chiamandone i metodi, come illustrato nell'esempio di codice seguente. Si noti che l'apertura, la chiamata e la chiusura dell'oggetto client WCF si verificano all'interno di un singolo blocco try/catch. Per ulteriori informazioni, vedere [accesso ai servizi tramite un client WCF](./feature-details/accessing-services-using-a-client.md) e [utilizzare Close e Abort per rilasciare le risorse client WCF](./samples/use-close-abort-release-wcf-client-resources.md).  
  
 [!code-csharp[C_GeneratedCodeFiles#20](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#20)]  
  
## <a name="handling-errors"></a>Gestione degli errori  
 In un'applicazione client possono verificarsi eccezioni quando si apre il canale client sottostante (sia in modo esplicito che automaticamente chiamando un'operazione), quando si usa l'oggetto client o l'oggetto canale per chiamare operazioni o quando si chiude il canale client sottostante. Oltre a gestire qualsiasi oggetto <xref:System.TimeoutException?displayProperty=nameWithType> generato come risultato di errori SOAP restituiti dalle operazioni, le applicazioni dovrebbero essere configurate per gestire almeno possibili eccezioni <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType> e <xref:System.ServiceModel.FaultException?displayProperty=nameWithType>. Gli errori SOAP specificati nel contratto dell'operazione vengono generati nelle applicazioni client come oggetto <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> dove il parametro di tipo è il tipo di dettaglio dell'errore SOAP. Per ulteriori informazioni sulla gestione delle condizioni di errore in un'applicazione client, vedere [invio e ricezione di errori](sending-and-receiving-faults.md). Per un esempio completo, Mostra come gestire gli errori in un client, vedere le [eccezioni previste](./samples/expected-exceptions.md).  
  
## <a name="configuring-and-securing-clients"></a>Configurazione e protezione dei client  
 La configurazione di un client inizia con il caricamento obbligatorio di informazioni sull'endpoint di destinazione per il client o per l'oggetto del canale, generalmente da un file di configurazione, sebbene sia possibile caricare queste informazioni anche a livello di programmazione usando i costruttori e le proprietà del client. Per attivare determinati comportamenti del client e per numerosi scenari di sicurezza sono tuttavia necessarie operazioni di configurazione aggiuntive.  
  
 I requisiti di sicurezza per i contratti di servizio, ad esempio, vengono dichiarati nell'interfaccia del contratto di servizio e se lo strumento Svcutil.exe ha creato un file di configurazione, questo file contiene in genere un'associazione in grado di supportare i requisiti di sicurezza del servizio. In alcuni casi può essere però necessaria un'ulteriore configurazione della protezione, ad esempio la configurazione di credenziali client. Per informazioni complete sulla configurazione della sicurezza per i client WCF, vedere [protezione dei client](securing-clients.md).  
  
 Nelle applicazioni client possono essere inoltre abilitate alcune modifiche personalizzate, ad esempio comportamenti personalizzati nella fase di esecuzione. Per ulteriori informazioni su come configurare un comportamento client personalizzato, vedere [configurazione dei comportamenti client](configuring-client-behaviors.md).  
  
## <a name="creating-callback-objects-for-duplex-services"></a>Creazione di oggetti di callback per i servizi duplex  
 I servizi duplex specificano un contratto di callback che l'applicazione client deve implementare per fornire un oggetto di callback affinché il servizio esegua la chiamata in base ai requisiti del contratto. Sebbene gli oggetti di callback non siano servizi completi (ad esempio, non è possibile avviare un canale con un oggetto di callback), ai fini dell'implementazione e della configurazione possono essere considerati come una specie di servizio.  
  
 I client di servizi duplex devono:  
  
- Implementare una classe di contratto di callback.  
  
- Creare un'istanza della classe di implementazione del contratto di callback e usarla per creare l'oggetto <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> passato al costruttore client WCF.  
  
- Richiamare operazioni e gestire callback di operazioni.  
  
 Gli oggetti client WCF Duplex funzionano come le controparti non duplex, ad eccezione del fatto che espongono la funzionalità necessaria per supportare i callback, inclusa la configurazione del servizio di callback.  
  
 È possibile controllare, ad esempio, i vari aspetti del comportamento degli oggetti di callback in fase di esecuzione usando proprietà dell'attributo <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType> nella classe di callback. Un altro esempio è l'uso della classe <xref:System.ServiceModel.Description.CallbackDebugBehavior?displayProperty=nameWithType> per attivare la restituzione di informazioni sull'eccezione ai servizi che chiamano l'oggetto di callback. Per ulteriori informazioni, vedere [servizi duplex](./feature-details/duplex-services.md). Per un esempio completo, vedere [duplex](./samples/duplex.md).  
  
 Nei computer Windows XP che eseguono Internet Information Services (IIS) 5.1, i client duplex devono specificare un indirizzo client di base usando la classe <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>. In caso contrario verrà generata un'eccezione. Nel codice di esempio seguente viene illustrato come eseguire questa procedura nel codice.  
  
 [!code-csharp[S_DualHttp#8](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#8)]
 [!code-vb[S_DualHttp#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_dualhttp/vb/module1.vb#8)]  
  
 Il codice seguente mostra come eseguire la procedura in un file di configurazione.  
  
 [!code-csharp[S_DualHttp#134](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#134)]  
  
## <a name="calling-services-asynchronously"></a>Chiamate ai servizi in modo asincrono  
 La modalità in cui vengono chiamate le operazioni dipende interamente dallo sviluppatore client. Ciò è dovuto al fatto che i messaggi che costituiscono un'operazione possono essere mappati a metodi sincroni o asincroni quando vengono espressi in codice gestito. Pertanto, se si desidera compilare un client che chiama operazioni in modo asincrono, è possibile usare Svcutil.exe per generare codice client asincrono usando l'opzione `/async`. Per altre informazioni, vedere [procedura: chiamare operazioni del servizio in modo asincrono](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).  
  
## <a name="calling-services-using-wcf-client-channels"></a>Chiamate ai servizi mediante canali client di WCF  
 I tipi di client WCF estendono <xref:System.ServiceModel.ClientBase%601>, che a sua volta deriva dall'interfaccia <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> per esporre il sistema di canali sottostante. È possibile richiamare servizi usando il contratto di servizio di destinazione con la classe <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>. Per informazioni dettagliate, vedere [architettura client WCF](./feature-details/client-architecture.md).  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>
