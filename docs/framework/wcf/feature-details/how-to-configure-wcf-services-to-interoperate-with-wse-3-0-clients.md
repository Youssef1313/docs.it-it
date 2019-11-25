---
title: 'Procedura: configurare i servizi WCF per interagire con i client WSE 3.0'
ms.date: 03/30/2017
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
ms.openlocfilehash: bd9f2bec94ca45f76590f64366428a00edd5d6ea
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141739"
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a><span data-ttu-id="baa43-102">Procedura: configurare i servizi WCF per interagire con i client WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="baa43-102">How to: Configure WCF Services to Interoperate with WSE 3.0 Clients</span></span>

<span data-ttu-id="baa43-103">I servizi Windows Communication Foundation (WCF) sono compatibili a livello di rete con i miglioramenti dei servizi Web 3,0 per i client di Microsoft .NET (WSE) quando i servizi WCF sono configurati per l'utilizzo della versione agosto 2004 della specifica WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="baa43-103">Windows Communication Foundation (WCF) services are wire-level compatible with Web Services Enhancements 3.0 for Microsoft .NET (WSE) clients when WCF services are configured to use the August 2004 version of the WS-Addressing specification.</span></span>

### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a><span data-ttu-id="baa43-104">Per consentire a un servizio WCF di interagire con i client WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="baa43-104">To enable a WCF service to interoperate with WSE 3.0 clients</span></span>

1. <span data-ttu-id="baa43-105">Definire un'associazione personalizzata per il servizio WCF.</span><span class="sxs-lookup"><span data-stu-id="baa43-105">Define a custom binding for the WCF service.</span></span>

    <span data-ttu-id="baa43-106">Per specificare l'utilizzo della versione dell'agosto 2004 della specifica WS-Addressing per la codifica dei messaggi, è necessario creare un'associazione personalizzata.</span><span class="sxs-lookup"><span data-stu-id="baa43-106">To specify that the August 2004 version of the WS-Addressing specification is used for message encoding, a custom binding must be created.</span></span>

    1. <span data-ttu-id="baa43-107">Aggiungere un elemento figlio [\<custombinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) al [\<associazioni >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) del file di configurazione del servizio.</span><span class="sxs-lookup"><span data-stu-id="baa43-107">Add a child [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) to the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) of the service's configuration file.</span></span>

    2. <span data-ttu-id="baa43-108">Specificare un nome per l'associazione, aggiungendo un' [associazione\<](../../configure-apps/file-schema/wcf/bindings.md) al [\<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) e impostando l'attributo `name`.</span><span class="sxs-lookup"><span data-stu-id="baa43-108">Specify a name for the binding, by adding a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) and setting the `name` attribute.</span></span>

    3. <span data-ttu-id="baa43-109">Specificare una modalità di autenticazione e la versione delle specifiche WS-Security utilizzate per proteggere i messaggi compatibili con WSE 3,0, aggiungendo una [> di sicurezza\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) figlio al [Binding\<](../../configure-apps/file-schema/wcf/bindings.md).</span><span class="sxs-lookup"><span data-stu-id="baa43-109">Specify an authentication mode and the version of the WS-Security specifications that are used to secure messages that are compatible with WSE 3.0, by adding a child [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) to the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md).</span></span>

        <span data-ttu-id="baa43-110">Per impostare la modalità di autenticazione, impostare l'attributo `authenticationMode` del [> di sicurezza\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="baa43-110">To set the authentication mode, set the `authenticationMode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span> <span data-ttu-id="baa43-111">Una modalità di autenticazione è più o meno equivalente a un'asserzione di sicurezza turnkey in WSE 3.0.</span><span class="sxs-lookup"><span data-stu-id="baa43-111">An authentication mode is roughly equivalent to a turnkey security assertion in WSE 3.0.</span></span> <span data-ttu-id="baa43-112">Nella tabella seguente viene eseguito il mapping delle modalità di autenticazione in WCF alle asserzioni di sicurezza chiavi in mano in WSE 3,0.</span><span class="sxs-lookup"><span data-stu-id="baa43-112">The following table maps authentication modes in WCF to turnkey security assertions in WSE 3.0.</span></span>

        |<span data-ttu-id="baa43-113">Modalità di autenticazione WCF</span><span class="sxs-lookup"><span data-stu-id="baa43-113">WCF Authentication Mode</span></span>|<span data-ttu-id="baa43-114">Asserzione di sicurezza turnkey WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="baa43-114">WSE 3.0 turnkey security assertion</span></span>|
        |-----------------------------|----------------------------------------|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|

        <span data-ttu-id="baa43-115">\* una delle principali differenze tra le asserzioni di sicurezza `mutualCertificate10Security` e `mutualCertificate11Security` chiavi in mano è la versione della specifica WS-Security utilizzata da WSE per proteggere i messaggi SOAP.</span><span class="sxs-lookup"><span data-stu-id="baa43-115">\* One of the primary differences between the `mutualCertificate10Security` and `mutualCertificate11Security` turnkey security assertions is the version of the WS-Security specification that WSE uses to secure the SOAP messages.</span></span> <span data-ttu-id="baa43-116">Per `mutualCertificate10Security` viene utilizzata la versione WS-Security 1.0, mentre per `mutualCertificate11Security` viene utilizzata la versione WS-Security 1.1.</span><span class="sxs-lookup"><span data-stu-id="baa43-116">For `mutualCertificate10Security`, WS-Security 1.0 is used, whereas WS-Security 1.1 is used for `mutualCertificate11Security`.</span></span> <span data-ttu-id="baa43-117">Per WCF, la versione della specifica WS-Security viene specificata nell'attributo `messageSecurityVersion` del [> di sicurezza\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="baa43-117">For WCF, the version of the WS-Security specification is specified in the `messageSecurityVersion` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span>

        <span data-ttu-id="baa43-118">Per impostare la versione della specifica WS-Security utilizzata per proteggere i messaggi SOAP, impostare l'attributo `messageSecurityVersion` del [> di sicurezza\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="baa43-118">To set the version of the WS-Security specification that is used to secure SOAP messages, set the `messageSecurityVersion` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span> <span data-ttu-id="baa43-119">Per interagire con WSE 3.0, impostare il valore dell'attributo `messageSecurityVersion` su <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.</span><span class="sxs-lookup"><span data-stu-id="baa43-119">To interoperate with WSE 3.0, set the value of the `messageSecurityVersion` attribute to <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.</span></span>

    4. <span data-ttu-id="baa43-120">Specificare che la versione agosto 2004 della specifica WS-Addressing viene utilizzata da WCF aggiungendo un [\<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md) e impostare il `messageVersion` sul relativo valore su <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.</span><span class="sxs-lookup"><span data-stu-id="baa43-120">Specify that the August 2004 version of the WS-Addressing specification is used by WCF by adding a [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md) and set the `messageVersion` to its value to <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.</span></span>

        > [!NOTE]
        > <span data-ttu-id="baa43-121">Quando si utilizza SOAP 1.2, impostare l'attributo `messageVersion` su <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.</span><span class="sxs-lookup"><span data-stu-id="baa43-121">When you are using SOAP 1.2, set the `messageVersion` attribute to <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.</span></span>

2. <span data-ttu-id="baa43-122">Specificare l'utilizzo dell'associazione personalizzata da parte del servizio.</span><span class="sxs-lookup"><span data-stu-id="baa43-122">Specify that the service uses the custom binding.</span></span>

    1. <span data-ttu-id="baa43-123">Impostare l'attributo `binding` dell'elemento [\<endpoint](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) su `customBinding`.</span><span class="sxs-lookup"><span data-stu-id="baa43-123">Set the `binding` attribute of the [\<endpoint>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element to `customBinding`.</span></span>

    2. <span data-ttu-id="baa43-124">Impostare l'attributo `bindingConfiguration` dell'elemento [\<endpoint](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) sul valore specificato nell'attributo `name` del [\<di associazione >](../../configure-apps/file-schema/wcf/bindings.md) per l'associazione personalizzata.</span><span class="sxs-lookup"><span data-stu-id="baa43-124">Set the `bindingConfiguration` attribute of the [\<endpoint>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element to the value specified in the `name` attribute of the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) for the custom binding.</span></span>

## <a name="example"></a><span data-ttu-id="baa43-125">Esempio</span><span class="sxs-lookup"><span data-stu-id="baa43-125">Example</span></span>

<span data-ttu-id="baa43-126">Nell'esempio di codice seguente viene specificato che `Service.HelloWorldService` utilizza un'associazione personalizzata per interagire con i client WSE 3.0.</span><span class="sxs-lookup"><span data-stu-id="baa43-126">The following code example specifies that the `Service.HelloWorldService` uses a custom binding to interoperate with WSE 3.0 clients.</span></span> <span data-ttu-id="baa43-127">L'associazione personalizzata specifica che per la codifica dei messaggi scambiati viene utilizzata la versione dell'agosto 2004 del set di specifiche WS-Addressing e WS-Security 1.1.</span><span class="sxs-lookup"><span data-stu-id="baa43-127">The custom binding specifies that the August 2004 version of the WS-Addressing and the WS-Security 1.1 set of specifications are used to encode the exchanged messages.</span></span> <span data-ttu-id="baa43-128">I messaggi vengono protetti utilizzando la modalità di autenticazione <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>.</span><span class="sxs-lookup"><span data-stu-id="baa43-128">The messages are secured using the <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> authentication mode.</span></span>

```xml
<configuration>
  <system.serviceModel>
    <services>
      <service
        behaviorConfiguration="ServiceBehavior"
        name="Service.HelloWorldService">
        <endpoint binding="customBinding" address=""
          bindingConfiguration="ServiceBinding"
          contract="Service.IHelloWorld"></endpoint>
      </service>
    </services>

    <bindings>
      <customBinding>
        <binding name="ServiceBinding">
          <security authenticationMode="AnonymousForCertificate"
                  messageProtectionOrder="SignBeforeEncrypt"
                  messageSecurityVersion="WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10"
                  requireDerivedKeys="false">
          </security>
          <textMessageEncoding messageVersion ="Soap11WSAddressingAugust2004"></textMessageEncoding>
          <httpTransport/>
        </binding>
      </customBinding>
    </bindings>
    <behaviors>
      <behavior name="ServiceBehavior" returnUnknownExceptionsAsFaults="true">
        <serviceCredentials>
          <serviceCertificate findValue="CN=WCFQuickstartServer" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName"/>
        </serviceCredentials>
      </behavior>
    </behaviors>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="baa43-129">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="baa43-129">See also</span></span>

- [<span data-ttu-id="baa43-130">Procedura: Personalizzare un'associazione specificata dal sistema</span><span class="sxs-lookup"><span data-stu-id="baa43-130">How to: Customize a System-Provided Binding</span></span>](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)
