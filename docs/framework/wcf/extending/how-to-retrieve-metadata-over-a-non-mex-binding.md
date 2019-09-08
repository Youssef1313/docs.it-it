---
title: "Procedura: Recuperare metadati attraverso un'associazione non MEX"
ms.date: 03/30/2017
ms.assetid: 2292e124-81b2-4317-b881-ce9c1ec66ecb
ms.openlocfilehash: 6cd6e0ce5dc287c826179c152b989b5f7842bb6e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795581"
---
# <a name="how-to-retrieve-metadata-over-a-non-mex-binding"></a><span data-ttu-id="67a12-102">Procedura: Recuperare metadati attraverso un'associazione non MEX</span><span class="sxs-lookup"><span data-stu-id="67a12-102">How to: Retrieve Metadata Over a non-MEX Binding</span></span>
<span data-ttu-id="67a12-103">In questo argomento viene illustrato come recuperare metadati da un endpoint MEX attraverso un'associazione non MEX.</span><span class="sxs-lookup"><span data-stu-id="67a12-103">This topic describes how to retrieve metadata from a MEX endpoint over a non-MEX binding.</span></span> <span data-ttu-id="67a12-104">Il codice in questo esempio è basato sull'esempio di [endpoint dei metadati protetti personalizzato](../samples/custom-secure-metadata-endpoint.md) .</span><span class="sxs-lookup"><span data-stu-id="67a12-104">The code in this sample is based on the [Custom Secure Metadata Endpoint](../samples/custom-secure-metadata-endpoint.md) sample.</span></span>  
  
### <a name="to-retrieve-metadata-over-a-non-mex-binding"></a><span data-ttu-id="67a12-105">Per recuperare metadati attraverso un'associazione non MEX</span><span class="sxs-lookup"><span data-stu-id="67a12-105">To retrieve metadata over a non-MEX binding</span></span>  
  
1. <span data-ttu-id="67a12-106">Determinare l'associazione utilizzata dall'endpoint MEX.</span><span class="sxs-lookup"><span data-stu-id="67a12-106">Determine the binding used by the MEX endpoint.</span></span> <span data-ttu-id="67a12-107">Per i servizi Windows Communication Foundation (WCF), è possibile determinare l'associazione MEX accedendo al file di configurazione del servizio.</span><span class="sxs-lookup"><span data-stu-id="67a12-107">For Windows Communication Foundation (WCF) services, you can determine the MEX binding by accessing the service's configuration file.</span></span> <span data-ttu-id="67a12-108">In questo caso, l'associazione MEX è definita nella configurazione del servizio seguente:</span><span class="sxs-lookup"><span data-stu-id="67a12-108">In this case, the MEX binding is defined in the following service configuration.</span></span>  
  
    ```xml  
    <services>  
        <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
                behaviorConfiguration="CalculatorServiceBehavior">  
         <!-- Use the base address provided by the host. -->  
         <endpoint address=""  
           binding="wsHttpBinding"  
           bindingConfiguration="Binding2"  
           contract="Microsoft.ServiceModel.Samples.ICalculator" />  
         <endpoint address="mex"  
           binding="wsHttpBinding"  
           bindingConfiguration="Binding1"  
           contract="IMetadataExchange" />  
         </service>  
     </services>  
     <bindings>  
       <wsHttpBinding>  
         <binding name="Binding1">  
           <security mode="Message">  
             <message clientCredentialType="Certificate" />  
           </security>  
         </binding>  
         <binding name="Binding2">  
           <reliableSession inactivityTimeout="00:01:00" enabled="true" />  
           <security mode="Message">  
             <message clientCredentialType="Certificate" />  
           </security>  
         </binding>  
       </wsHttpBinding>  
     </bindings>  
    ```  
  
2. <span data-ttu-id="67a12-109">Nel file di configurazione client, configurare la stessa associazione personalizzata.</span><span class="sxs-lookup"><span data-stu-id="67a12-109">In the client configuration file, configure the same custom binding.</span></span> <span data-ttu-id="67a12-110">Qui il client definisce anche un comportamento `clientCredentials` per fornire un certificato da utilizzare per l'autenticazione al servizio quando vengono richiesti metadati dall'endpoint MEX.</span><span class="sxs-lookup"><span data-stu-id="67a12-110">Here the client also defines a `clientCredentials` behavior to provide a certificate to use to authenticate to the service when requesting metadata from the MEX endpoint.</span></span> <span data-ttu-id="67a12-111">Quando si utilizza Svcutil.exe per richiedere metadati su un'associazione personalizzata, è necessario aggiungere la configurazione dell'endpoint MEX al file di configurazione per Svcutil.exe (Svcutil.exe.config) e il nome della configurazione dell'endpoint deve corrispondere allo schema URI dell'indirizzo dell'endpoint MEX, come illustrato nel codice seguente:</span><span class="sxs-lookup"><span data-stu-id="67a12-111">When using Svcutil.exe to request metadata over a custom binding, you should add the MEX endpoint configuration to the configuration file for Svcutil.exe (Svcutil.exe.config), and the name of the endpoint configuration should match the URI scheme of the address of the MEX endpoint, as shown in the following code.</span></span>  
  
    ```xml  
    <system.serviceModel>  
      <client>  
        <endpoint name="http"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  behaviorConfiguration="ClientCertificateBehavior"  
                  contract="IMetadataExchange" />  
      </client>  
      <bindings>  
        <wsHttpBinding>  
          <binding name="Binding1">  
            <security mode="Message">  
              <message clientCredentialType="Certificate"/>  
            </security>  
          </binding>  
        </wsHttpBinding>  
      </bindings>  
      <behaviors>  
        <endpointBehaviors>  
          <behavior name="ClientCertificateBehavior">  
            <clientCredentials>  
              <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName" />  
              <serviceCertificate>  
                <authentication certificateValidationMode="PeerOrChainTrust" />  
              </serviceCertificate>  
            </clientCredentials>  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>    
    </system.serviceModel>  
    ```  
  
3. <span data-ttu-id="67a12-112">Creare un `MetadataExchangeClient` e chiamare `GetMetadata`.</span><span class="sxs-lookup"><span data-stu-id="67a12-112">Create a `MetadataExchangeClient` and call `GetMetadata`.</span></span> <span data-ttu-id="67a12-113">Per eseguire questa operazione, è possibile specificare l'associazione personalizzata nella configurazione oppure nel codice:</span><span class="sxs-lookup"><span data-stu-id="67a12-113">There are two ways to do this: you can specify the custom binding in configuration, or you can specify the custom binding in code, as shown in the following example.</span></span>  
  
    ```  
    // The custom binding is specified in configuration.  
    EndpointAddress mexAddress = new EndpointAddress("http://localhost:8000/ServiceModelSamples/Service/mex");  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("http");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mexSet = mexClient.GetMetadata(mexAddress);  
  
    // The custom binding is specified in code.  
    // Specify the Metadata Exchange binding and its security mode.  
    WSHttpBinding mexBinding = new WSHttpBinding(SecurityMode.Message);  
    mexBinding.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
    // Create a MetadataExchangeClient and set the certificate details.  
    MetadataExchangeClient mexClient = new MetadataExchangeClient(mexBinding);  
    mexClient.SoapCredentials.ClientCertificate.SetCertificate(  
        StoreLocation.CurrentUser, StoreName.My,  
        X509FindType.FindBySubjectName, "client.com");  
    mexClient.SoapCredentials.ServiceCertificate.Authentication.  
        CertificateValidationMode =  
        X509CertificateValidationMode.PeerOrChainTrust;  
    mexClient.SoapCredentials.ServiceCertificate.SetDefaultCertificate(  
        StoreLocation.CurrentUser, StoreName.TrustedPeople,  
        X509FindType.FindBySubjectName, "localhost");  
    MetadataExchangeClient mexClient2 = new MetadataExchangeClient(customBinding);  
    mexClient2.ResolveMetadataReferences = true;  
    MetadataSet mexSet2 = mexClient2.GetMetadata(mexAddress);  
    ```  
  
4. <span data-ttu-id="67a12-114">Creare `WsdlImporter` e chiamare `ImportAllEndpoints`, come illustrato nel codice seguente.</span><span class="sxs-lookup"><span data-stu-id="67a12-114">Create a `WsdlImporter` and call `ImportAllEndpoints`, as shown in the following code.</span></span>  
  
    ```  
    WsdlImporter importer = new WsdlImporter(mexSet);  
    ServiceEndpointCollection endpoints = importer.ImportAllEndpoints();  
    ```  
  
5. <span data-ttu-id="67a12-115">A questo punto, si ha una raccolta di endpoint del servizio.</span><span class="sxs-lookup"><span data-stu-id="67a12-115">At this point, you have a collection of service endpoints.</span></span> <span data-ttu-id="67a12-116">Per ulteriori informazioni sull'importazione di metadati, [vedere Procedura: Importa i metadati in endpoint](../feature-details/how-to-import-metadata-into-service-endpoints.md)di servizio.</span><span class="sxs-lookup"><span data-stu-id="67a12-116">For more information about importing metadata, see [How to: Import Metadata into Service Endpoints](../feature-details/how-to-import-metadata-into-service-endpoints.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67a12-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="67a12-117">See also</span></span>

- [<span data-ttu-id="67a12-118">Metadati</span><span class="sxs-lookup"><span data-stu-id="67a12-118">Metadata</span></span>](../feature-details/metadata.md)
