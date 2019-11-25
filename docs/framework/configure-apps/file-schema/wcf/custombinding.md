---
title: <customBinding>
ms.date: 03/30/2017
ms.assetid: 9da4f960-f64e-4d8a-894d-2b09eba5ce4b
ms.openlocfilehash: cdaaacf0dfa75209d001f6e8d6ac7175816048aa
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2019
ms.locfileid: "74140800"
---
# <a name="custombinding"></a><span data-ttu-id="f6aa4-101">\<CustomBinding ></span><span class="sxs-lookup"><span data-stu-id="f6aa4-101">\<customBinding></span></span>

<span data-ttu-id="f6aa4-102">Fornisce il controllo completo dello stack di messaggistica per l'utente.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-102">Provides full control over the messaging stack for the user.</span></span>

<span data-ttu-id="f6aa4-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f6aa4-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f6aa4-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f6aa4-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f6aa4-105">&nbsp;&nbsp;&nbsp;&nbsp;[**Binding**](bindings.md)\<</span><span class="sxs-lookup"><span data-stu-id="f6aa4-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\</span></span>
<span data-ttu-id="f6aa4-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**customBinding**\<</span><span class="sxs-lookup"><span data-stu-id="f6aa4-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customBinding>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="f6aa4-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f6aa4-107">Syntax</span></span>

```xml
<customBinding>
  <binding name="String"
           closeTimeout="TimeSpan"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
    <compositeDuplex clientBaseAddress="Uri" />
    <reliableSession acknowledgementInterval="TimeSpan"
                     advancedFlowControl="Boolean"
                     bufferedMessagesQuota="Integer"
                     inactivityTimeout="TimeSpan"
                     maxPendingChannels="Integer"
                     maxRetryCount="Integer"
                     ordered="Boolean" />
    <pnrpPeerResolver />
    <windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
    <sslStreamSecurity requireClientCertificate="Boolean" />
    <transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
    <security defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
              authenticationMode="UserNameForAnonymous"
              contextMode="Cookie"
              defaultProtectionLevel="Sign"
              enableKeyDerivation="false"
              keyEntropyMode="ClientEntropy"
              messageProtectionOrder="SignBeforeEncryptAndEncryptSignature"
              securityVersion="WSSecurityXXX2005">
      <localClientSettings cacheCookies="false"
                           detectReplays="false"
                           maxCookieCachingTime="00:07:24" />
      <localServiceSettings replayCacheSize="9"
                            maxClockSkew="00:00:03"
                            replayWindow="00:07:22.2190000" />
    </security>
    <binaryMessageEncoding maxReadPoolSize="Integer"
                           maxWritePoolSize="Integer"
                           maxSessionSize="Integer" />
    <httpsTransport manualAddressing="Boolean"
                    maxMessageSize="Integer"
                    authenticationScheme="Negotiate"
                    bypassProxyOnLocal="Boolean"
                    hostNameComparisonMode="Exact"
                    mapAddressingHeadersToHttpHeaders="Boolean"
                    proxyaddress="Uri"
                    realm="String"
                    requireClientCertificate="Boolean" />
    <peerTransport manualAddressing="false"
                   maxMessageSize="20002"
                   listenIPAddress="202.10.1.9"
                   messageAuthentication="false"
                   peerNodeAuthenticationMode="None"
                   port="1000" />
    <security defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
              authenticationMode="UserNameForAnonymous"
              bootstrapBindingConfiguration="String"
              bootstrapBindingSectionName="String"
              defaultProtectionLevel="None/Sign/EncryptAndSign"
              requireDerivedKeys="Boolean"
              securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"
              includeTimestamp="Boolean"
              keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
              messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"
              protectTokens="Boolean"
              requireSecurityContextCancellation="Boolean"
              securityVersion=" WSSecurityJan2004/WSSecurityXXX2005"
              requireSignatureConfirmation="Boolean">
      <localClientSettings cacheCookies="Boolean"
                           detectReplays="Boolean"
                           replayCacheSize="Integer"
                           maxClockSkew="TimeSpan"
                           maxCookieCachingTime="TimeSpan"
                           replayWindow="TimeSpan"
                           sessionKeyRenewalInterval="TimeSpan"
                           sessionKeyRolloverInterval="TimeSpan"
                           reconnectOnTransportFailure="Boolean"
                           timestampValidityDuration="TimeSpan"
                           cookieRenewalThresholdPercentage="Integer" />
      <localServiceSettings detectReplays="Boolean"
                            issuedCookieLifeTime="TimeSpan"
                            maxStatefulNegotiations="Integer"
                            replayCacheSize="Integer"
                            maxClockSkew="TimeSpan"
                            negotiationTimeout="TimeSpan"
                            replayWindow="TimeSpan"
                            inactivityTimeout="TimeSpan"
                            sessionKeyRenewalInterval="TimeSpan"
                            sessionKeyRolloverInterval="TimeSpan"
                            reconnectOnTransportFailure="Boolean"
                            maxConcurrentSessions="Integer"
                            timestampValidityDuration="TimeSpan" />
      <federationParameters trustVersion="WSTrustApr2004/WSTrustFeb2005" />
    </security>
    <security defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
              authenticationMode="UserNameForAnonymous"
              bootstrapBindingConfiguration="String"
              bootstrapBindingSectionName="String"
              defaultProtectionLevel="None/Sign/EncryptAndSign"
              requireDerivedKeys="Boolean"
              securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"
              includeTimestamp="Boolean"
              keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
              messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"
              protectTokens="Boolean"
              requireSecurityContextCancellation="Boolean"
              securityVersion=" WSSecurityJan2004/WSSecurityXXX2005"
              requireSignatureConfirmation="Boolean" >
      <localClientSettings cacheCookies="Boolean"
                           detectReplays="Boolean"
                           replayCacheSize="Integer"
                           maxClockSkew="TimeSpan"
                           maxCookieCachingTime="TimeSpan"
                           replayWindow="TimeSpan"
                           sessionKeyRenewalInterval="TimeSpan"
                           sessionKeyRolloverInterval="TimeSpan"
                           reconnectOnTransportFailure="Boolean"
                           timestampValidityDuration="TimeSpan"
                           cookieRenewalThresholdPercentage="Integer" />
      <localServiceSettings detectReplays="Boolean"
                           issuedCookieLifeTime="TimeSpan"
                           maxStatefulNegotiations="Integer"
                           replayCacheSize="Integer"
                           maxClockSkew="TimeSpan"
                           negotiationTimeout="TimeSpan"
                           replayWindow="TimeSpan"
                           inactivityTimeout="TimeSpan"
                           sessionKeyRenewalInterval="TimeSpan"
                           sessionKeyRolloverInterval="TimeSpan"
                           reconnectOnTransportFailure="Boolean"
                           maxConcurrentSessions="Integer"
                           timestampValidityDuration="TimeSpan" />
      <federationParameters trustVersion="WSTrustApr2004/WSTrustFeb2005" />
      <genericIssuedTokenParameters>
        <localIssuerIssuedTokenParameters keyType="SymmetricKey/PublicKey"
                                          keySize="Integer"
                                          tokenType="String" />
        <issuedTokenParametersEndpointAddress address="URI"
                                              bindingConfiguration="String"
                                              binding="String" />
        <issuedTokenClient localIssuerChannelBehaviors="String"
                           cacheIssuedTokens="Boolean"
                           maxIssuedTokenCachingTime="TimeSpan"
                           keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy" />
        <issuedTokenClientBehavior issuerAddress="String"
                                   behaviorConfiguration="String" />
        <issuedTokenClientBehavior address="URI"
                                   bindingConfiguration="String"
                                   binding="String" />
      </genericIssuedTokenParameters>
    </security>
  </binding>
</customBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f6aa4-108">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="f6aa4-108">Attributes and Elements</span></span>

<span data-ttu-id="f6aa4-109">Nelle sezioni seguenti vengono descritti attributi, elementi figlio ed elementi padre.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-109">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="f6aa4-110">Attributi</span><span class="sxs-lookup"><span data-stu-id="f6aa4-110">Attributes</span></span>

|<span data-ttu-id="f6aa4-111">Attributo</span><span class="sxs-lookup"><span data-stu-id="f6aa4-111">Attribute</span></span>|<span data-ttu-id="f6aa4-112">Descrizione</span><span class="sxs-lookup"><span data-stu-id="f6aa4-112">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="f6aa4-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="f6aa4-113">closeTimeout</span></span>|<span data-ttu-id="f6aa4-114">Valore <xref:System.TimeSpan> che specifica l'intervallo di tempo fornito per il completamento di un'operazione di chiusura.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-114">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="f6aa4-115">Questo valore deve essere maggiore o uguale a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f6aa4-116">L'impostazione predefinita è 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-116">The default is 00:01:00.</span></span>|
|<span data-ttu-id="f6aa4-117">name</span><span class="sxs-lookup"><span data-stu-id="f6aa4-117">name</span></span>|<span data-ttu-id="f6aa4-118">Stringa che contiene il nome della configurazione dell'associazione.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-118">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="f6aa4-119">Questo valore è una stringa definita dall'utente che deve essere univoca in quanto funge da stringa di identificazione dell'associazione personalizzata.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-119">This value is a user-defined string that acts as the identification string for the custom binding.</span></span> <span data-ttu-id="f6aa4-120">A partire da .NET Framework 4, le associazioni e i comportamenti non devono avere un nome.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-120">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="f6aa4-121">Per ulteriori informazioni sulla configurazione predefinita e le associazioni e i comportamenti senza nome, vedere [Configurazione semplificata](../../../wcf/simplified-configuration.md) e [Configurazione semplificata per i servizi WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="f6aa4-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|<span data-ttu-id="f6aa4-122">openTimeout</span><span class="sxs-lookup"><span data-stu-id="f6aa4-122">openTimeout</span></span>|<span data-ttu-id="f6aa4-123">Valore <xref:System.TimeSpan> che specifica l'intervallo di tempo fornito per il completamento di un'operazione di apertura.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="f6aa4-124">Questo valore deve essere maggiore o uguale a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f6aa4-125">L'impostazione predefinita è 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-125">The default is 00:01:00.</span></span>|
|<span data-ttu-id="f6aa4-126">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="f6aa4-126">receiveTimeout</span></span>|<span data-ttu-id="f6aa4-127">Valore <xref:System.TimeSpan> che specifica l'intervallo di tempo fornito per il completamento di un'operazione di ricezione.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="f6aa4-128">Questo valore deve essere maggiore o uguale a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f6aa4-129">L'impostazione predefinita è 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-129">The default is 00:01:00.</span></span>|
|<span data-ttu-id="f6aa4-130">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="f6aa4-130">sendTimeout</span></span>|<span data-ttu-id="f6aa4-131">Valore <xref:System.TimeSpan> che specifica l'intervallo di tempo fornito per il completamento di un'operazione di invio.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-131">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="f6aa4-132">Questo valore deve essere maggiore o uguale a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-132">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f6aa4-133">L'impostazione predefinita è 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-133">The default is 00:01:00.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="f6aa4-134">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="f6aa4-134">Child Elements</span></span>

|<span data-ttu-id="f6aa4-135">Elemento</span><span class="sxs-lookup"><span data-stu-id="f6aa4-135">Element</span></span>|<span data-ttu-id="f6aa4-136">Descrizione</span><span class="sxs-lookup"><span data-stu-id="f6aa4-136">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f6aa4-137">\<compositeDuplex ></span><span class="sxs-lookup"><span data-stu-id="f6aa4-137">\<compositeDuplex></span></span>](compositeduplex.md)|<span data-ttu-id="f6aa4-138">Specifica la messaggistica bidirezionale sull'associazione personalizzata.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-138">Specifies two-way messaging to the custom binding.</span></span> <span data-ttu-id="f6aa4-139">Viene usato con trasporti che non consentono comunicazioni duplex a livello nativo, ad esempio, HTTP.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-139">It is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="f6aa4-140">TCP, al contrario, consente comunicazioni duplex a livello nativo e non richiede l'uso di questo elemento di associazione affinché il servizio invii messaggi a un client.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-140">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span><br /><br /> <span data-ttu-id="f6aa4-141">Il client deve esporre un indirizzo affinché il servizio crei un contatto e stabilisca una connessione.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-141">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="f6aa4-142">Questo indirizzo client è fornito dall'attributo `ClientBaseAddress`.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-142">This client address is provided by the `ClientBaseAddress` attribute.</span></span><br /><br /> <span data-ttu-id="f6aa4-143">L'elemento è di tipo <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-143">This element is of type <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span></span>|
|[<span data-ttu-id="f6aa4-144">\<pnrpPeerResolver ></span><span class="sxs-lookup"><span data-stu-id="f6aa4-144">\<pnrpPeerResolver></span></span>](pnrppeerresolver.md)|<span data-ttu-id="f6aa4-145">Specifica un resolver dei nomi peer PNRP (Peer Name Resolution Protocol).</span><span class="sxs-lookup"><span data-stu-id="f6aa4-145">Specifies a Peer Name Resolution Protocol (PNRP) peer name resolver.</span></span> <span data-ttu-id="f6aa4-146">L'elemento è di tipo <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-146">This element is of type <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span></span>|
|[<span data-ttu-id="f6aa4-147">\<reliableSession ></span><span class="sxs-lookup"><span data-stu-id="f6aa4-147">\<reliableSession></span></span>](reliablesession.md)|<span data-ttu-id="f6aa4-148">Specifica l'impostazione per WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-148">Specifies the setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="f6aa4-149">Quando questo elemento viene aggiunto a un'associazione personalizzata, il canale risultante può supportare assicurazioni di recapito una volta esatta.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-149">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span> <span data-ttu-id="f6aa4-150">L'elemento è di tipo <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-150">This element is of type <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span></span>|
|[<span data-ttu-id="f6aa4-151">> di sicurezza \<</span><span class="sxs-lookup"><span data-stu-id="f6aa4-151">\<security></span></span>](security-of-custombinding.md)|<span data-ttu-id="f6aa4-152">Specifica le opzioni di sicurezza per l'associazione personalizzata.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-152">Specifies the options for security of the custom binding.</span></span> <span data-ttu-id="f6aa4-153">L'elemento è di tipo <xref:System.ServiceModel.Configuration.SecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-153">This element is of type <xref:System.ServiceModel.Configuration.SecurityElement>.</span></span>|
|[<span data-ttu-id="f6aa4-154">\<sslStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="f6aa4-154">\<sslStreamSecurity></span></span>](sslstreamsecurity.md)|<span data-ttu-id="f6aa4-155">Specifica le impostazioni di sicurezza per l'associazione del flusso SSL.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-155">Specifies the security settings for a SSL stream binding.</span></span> <span data-ttu-id="f6aa4-156">L'elemento è di tipo <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-156">This element is of type <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span></span>|
|[<span data-ttu-id="f6aa4-157">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="f6aa4-157">\<transactionFlow></span></span>](transactionflow.md)|<span data-ttu-id="f6aa4-158">Specifica che l'associazione supporta il flusso delle transazioni e il protocollo che deve essere usato dall'attributo `transactionProtocol`.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-158">Specifies that the binding supports transaction flow, and the protocol to be used by the `transactionProtocol` attribute.</span></span> <span data-ttu-id="f6aa4-159">L'elemento è di tipo <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-159">This element is of type <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span></span>|
|[<span data-ttu-id="f6aa4-160">\<windowsStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="f6aa4-160">\<windowsStreamSecurity></span></span>](windowsstreamsecurity.md)|<span data-ttu-id="f6aa4-161">Specifica le opzioni di sicurezza del flusso per un'associazione personalizzata.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-161">Specifies the options for streaming security of the custom binding.</span></span> <span data-ttu-id="f6aa4-162">L'elemento è di tipo <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-162">This element is of type <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f6aa4-163">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="f6aa4-163">Parent Elements</span></span>

|<span data-ttu-id="f6aa4-164">Elemento</span><span class="sxs-lookup"><span data-stu-id="f6aa4-164">Element</span></span>|<span data-ttu-id="f6aa4-165">Descrizione</span><span class="sxs-lookup"><span data-stu-id="f6aa4-165">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="f6aa4-166">associazioni</span><span class="sxs-lookup"><span data-stu-id="f6aa4-166">bindings</span></span>|<span data-ttu-id="f6aa4-167">Contiene tutte le associazioni per le applicazioni Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f6aa4-167">Contains all bindings for Windows Communication Foundation applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f6aa4-168">Note</span><span class="sxs-lookup"><span data-stu-id="f6aa4-168">Remarks</span></span>

<span data-ttu-id="f6aa4-169">Le associazioni personalizzate forniscono il controllo completo dello stack dei messaggi WCF.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-169">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="f6aa4-170">È possibile creare associazioni speciali su misura aggiungendo gli elementi di configurazione per le entità specifiche.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-170">Special tailored bindings can be created my adding the configuration elements for specific entities.</span></span> <span data-ttu-id="f6aa4-171">Ad esempio, l'utente può combinare la sezione `httpsTransport`, la sezione `reliableSession` e la sezione `security` per creare un'associazione affidabile e protetto basata su HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-171">For example, the user can combine the `httpsTransport` section, `reliableSession` section and the `security` section to create a reliable and secure https based binding.</span></span>

<span data-ttu-id="f6aa4-172">Un'associazione singola definisce lo stack dei messaggi specificando gli elementi di configurazione per gli elementi dello stack nell'ordine in cui vengono visualizzati nello stack.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-172">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="f6aa4-173">Ogni elemento definisce e configura un elemento dello stack.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-173">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="f6aa4-174">Deve esistere un solo elemento di trasporto in ogni associazione personalizzata.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-174">There must be one and only one transport element in each custom binding.</span></span> <span data-ttu-id="f6aa4-175">Senza questo elemento, lo stack dei messaggi è incompleto.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-175">Without this element, the messaging stack is incomplete.</span></span>

<span data-ttu-id="f6aa4-176">L'ordine in cui gli elementi vengono visualizzati nello stack è importante, perché è l'ordine in cui le operazioni vengono applicate al messaggio.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-176">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="f6aa4-177">L'ordine consigliato per gli elementi dello stack è il seguente:</span><span class="sxs-lookup"><span data-stu-id="f6aa4-177">The recommended order of stack elements is the following:</span></span>

1. <span data-ttu-id="f6aa4-178">Transazioni (facoltativo)</span><span class="sxs-lookup"><span data-stu-id="f6aa4-178">Transactions (optional)</span></span>

2. <span data-ttu-id="f6aa4-179">Messaggistica affidabile (facoltativo)</span><span class="sxs-lookup"><span data-stu-id="f6aa4-179">Reliable Messaging (optional)</span></span>

3. <span data-ttu-id="f6aa4-180">Sicurezza (facoltativo)</span><span class="sxs-lookup"><span data-stu-id="f6aa4-180">Security (optional)</span></span>

4. <span data-ttu-id="f6aa4-181">Trasporto</span><span class="sxs-lookup"><span data-stu-id="f6aa4-181">Transport</span></span>

5. <span data-ttu-id="f6aa4-182">Codificatore (facoltativo)</span><span class="sxs-lookup"><span data-stu-id="f6aa4-182">Encoder (optional)</span></span>

<span data-ttu-id="f6aa4-183">Usare un'associazione personalizzata quando una delle associazioni fornite dal sistema non soddisfa i requisiti del servizio.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-183">Use a custom binding when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="f6aa4-184">Un'associazione personalizzata potrebbe essere usata, ad esempio, per abilitare l'uso di un nuovo trasporto o di un nuovo codificatore a un endpoint del servizio.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-184">A custom binding could be used, for example, to enable the use of a new transport or a new encoder at a service endpoint.</span></span>

<span data-ttu-id="f6aa4-185">Un'associazione personalizzata viene costruita usando uno dei <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> da una raccolta di elementi di associazione in uno stack in un ordine specifico:</span><span class="sxs-lookup"><span data-stu-id="f6aa4-185">A custom binding is constructed using one of the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> from a collection of binding elements that are "stacked" in a specific order:</span></span>

- <span data-ttu-id="f6aa4-186">All'inizio si trova una classe <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> facoltativa che consente la propagazione delle transazioni.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-186">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> that allows flowing transactions.</span></span>

- <span data-ttu-id="f6aa4-187">Quindi una classe <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> facoltativa che fornisce una sessione e un meccanismo di ordinamento come definito nella specifica WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-187">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> that provides a session and ordering mechanism as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="f6aa4-188">Questa nozione di sessione può attraversare SOAP e può trasportare intermediari.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-188">This notion of a session can cross SOAP and transport intermediaries.</span></span>

- <span data-ttu-id="f6aa4-189">Segue un elemento di associazione di sicurezza facoltativo che fornisce funzionalità di sicurezza quali, ad esempio, autorizzazione, autenticazione, protezione e riservatezza.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-189">Next is an optional security binding element that provides security features like authorization, authentication, protection, and confidentiality.</span></span> <span data-ttu-id="f6aa4-190">I seguenti elementi di associazione di sicurezza vengono forniti da Windows Communication Foundation (WCF):</span><span class="sxs-lookup"><span data-stu-id="f6aa4-190">The following security binding elements are provided by Windows Communication Foundation (WCF):</span></span>

  - <xref:System.ServiceModel.Channels.SecurityBindingElement>

  - <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>

- <span data-ttu-id="f6aa4-191">Seguono i modelli di messaggio facoltativi specificati dagli elementi di associazione:</span><span class="sxs-lookup"><span data-stu-id="f6aa4-191">Next are the optional message-patterns specified by binding elements:</span></span>

- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>

- <span data-ttu-id="f6aa4-192">Quindi gli elementi di associazione di trasporto facoltativi di aggiornamenti/helper:</span><span class="sxs-lookup"><span data-stu-id="f6aa4-192">Next are the optional transport upgrades/helpers binding elements:</span></span>

  - <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>

  - <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>

  - <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>

- <span data-ttu-id="f6aa4-193">Segue quindi un elemento di associazione obbligatorio di codifica dei messaggi.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-193">Next is a required message encoding binding element.</span></span> <span data-ttu-id="f6aa4-194">È possibile usare un trasporto proprio o una delle associazioni di codifica del messaggio seguenti:</span><span class="sxs-lookup"><span data-stu-id="f6aa4-194">You can use your own transport or use one of the following message encoding bindings:</span></span>

  - <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

  - <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

- <span data-ttu-id="f6aa4-195">Segue infine un elemento di trasporto obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-195">At the bottom is a required transport element.</span></span> <span data-ttu-id="f6aa4-196">È possibile utilizzare il trasporto personalizzato o utilizzare uno degli elementi di associazione del trasporto forniti da Windows Communication Foundation (WCF):</span><span class="sxs-lookup"><span data-stu-id="f6aa4-196">You can use your own transport or use one of transport binding elements provided by Windows Communication Foundation (WCF):</span></span>

  - <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpTransportBindingElement>

  - <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>

  - <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

  - <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>

  - <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

<span data-ttu-id="f6aa4-197">Nella tabella seguente viene fornito un riepilogo delle opzioni per ogni livello.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-197">The following table summarizes the options for each layer.</span></span>

|<span data-ttu-id="f6aa4-198">Livello</span><span class="sxs-lookup"><span data-stu-id="f6aa4-198">Layer</span></span>|<span data-ttu-id="f6aa4-199">Opzioni</span><span class="sxs-lookup"><span data-stu-id="f6aa4-199">Options</span></span>|<span data-ttu-id="f6aa4-200">Richiesto</span><span class="sxs-lookup"><span data-stu-id="f6aa4-200">Required</span></span>|
|-----------|-------------|--------------|
|<span data-ttu-id="f6aa4-201">Flusso transazioni</span><span class="sxs-lookup"><span data-stu-id="f6aa4-201">Transaction Flow</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="f6aa4-202">No</span><span class="sxs-lookup"><span data-stu-id="f6aa4-202">No</span></span>|
|<span data-ttu-id="f6aa4-203">Affidabilità</span><span class="sxs-lookup"><span data-stu-id="f6aa4-203">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="f6aa4-204">No</span><span class="sxs-lookup"><span data-stu-id="f6aa4-204">No</span></span>|
|<span data-ttu-id="f6aa4-205">Sicurezza</span><span class="sxs-lookup"><span data-stu-id="f6aa4-205">Security</span></span>|<span data-ttu-id="f6aa4-206">Simmetrico, asimmetrico, livello di trasporto</span><span class="sxs-lookup"><span data-stu-id="f6aa4-206">Symmetric, Asymmetric, Transport-Level</span></span>|<span data-ttu-id="f6aa4-207">No</span><span class="sxs-lookup"><span data-stu-id="f6aa4-207">No</span></span>|
|<span data-ttu-id="f6aa4-208">Cambio di forma</span><span class="sxs-lookup"><span data-stu-id="f6aa4-208">Shape Change</span></span>|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>|<span data-ttu-id="f6aa4-209">No</span><span class="sxs-lookup"><span data-stu-id="f6aa4-209">No</span></span>|
|<span data-ttu-id="f6aa4-210">Aggiornamenti del trasporto</span><span class="sxs-lookup"><span data-stu-id="f6aa4-210">Transport Upgrades</span></span>|<span data-ttu-id="f6aa4-211">Flusso SSL, flusso di Windows, resolver Peer</span><span class="sxs-lookup"><span data-stu-id="f6aa4-211">SSL stream, Windows stream, Peer Resolver</span></span>|<span data-ttu-id="f6aa4-212">No</span><span class="sxs-lookup"><span data-stu-id="f6aa4-212">No</span></span>|
|<span data-ttu-id="f6aa4-213">Codifica</span><span class="sxs-lookup"><span data-stu-id="f6aa4-213">Encoding</span></span>|<span data-ttu-id="f6aa4-214">Testo, binario, MTOM, personalizzata</span><span class="sxs-lookup"><span data-stu-id="f6aa4-214">Text, Binary, MTOM, Custom</span></span>|<span data-ttu-id="f6aa4-215">Yes</span><span class="sxs-lookup"><span data-stu-id="f6aa4-215">Yes</span></span>|
|<span data-ttu-id="f6aa4-216">Trasporto</span><span class="sxs-lookup"><span data-stu-id="f6aa4-216">Transport</span></span>|<span data-ttu-id="f6aa4-217">TCP, named pipe, HTTP, HTTPS, versioni di MSMQ, personalizzato</span><span class="sxs-lookup"><span data-stu-id="f6aa4-217">TCP, Named Pipes, HTTP, HTTPS, flavors of MSMQ, Custom</span></span>|<span data-ttu-id="f6aa4-218">Yes</span><span class="sxs-lookup"><span data-stu-id="f6aa4-218">Yes</span></span>|

<span data-ttu-id="f6aa4-219">È inoltre possibile definire elementi di associazione personalizzati e inserirli tra i livelli appena elencati.</span><span class="sxs-lookup"><span data-stu-id="f6aa4-219">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>

<span data-ttu-id="f6aa4-220">Per una discussione su come usare un'associazione personalizzata per modificare un'associazione fornita dal sistema, vedere [procedura: personalizzare un'associazione fornita dal sistema](../../../wcf/extending/how-to-customize-a-system-provided-binding.md).</span><span class="sxs-lookup"><span data-stu-id="f6aa4-220">For a discussion on how to use a custom binding to modify a system-provided binding, see [How to: Customize a System-Provided Binding](../../../wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f6aa4-221">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f6aa4-221">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.Configuration.BindingsSection>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="f6aa4-222">Binding \<</span><span class="sxs-lookup"><span data-stu-id="f6aa4-222">\<binding></span></span>](bindings.md)
- [<span data-ttu-id="f6aa4-223">Associazioni</span><span class="sxs-lookup"><span data-stu-id="f6aa4-223">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f6aa4-224">Estensione delle associazioni</span><span class="sxs-lookup"><span data-stu-id="f6aa4-224">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="f6aa4-225">Associazioni personalizzate</span><span class="sxs-lookup"><span data-stu-id="f6aa4-225">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="f6aa4-226">CustomBinding (elemento)</span><span class="sxs-lookup"><span data-stu-id="f6aa4-226">customBinding Element</span></span>](custombinding.md)
- [<span data-ttu-id="f6aa4-227">Associazioni</span><span class="sxs-lookup"><span data-stu-id="f6aa4-227">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f6aa4-228">Configurazione di associazioni fornite dal sistema</span><span class="sxs-lookup"><span data-stu-id="f6aa4-228">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f6aa4-229">Uso di associazioni per configurare servizi e client</span><span class="sxs-lookup"><span data-stu-id="f6aa4-229">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
