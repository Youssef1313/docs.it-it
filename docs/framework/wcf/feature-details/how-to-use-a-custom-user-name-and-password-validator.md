---
title: 'Procedura: usare un validator di nome utente e password personalizzato'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
ms.openlocfilehash: 3d01a29671f42e80fdb7ca45223007aa60273ba9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283251"
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="0f1b2-102">Procedura: usare un validator di nome utente e password personalizzato</span><span class="sxs-lookup"><span data-stu-id="0f1b2-102">How to: Use a Custom User Name and Password Validator</span></span>

<span data-ttu-id="0f1b2-103">Per impostazione predefinita, quando si usa un nome utente e una password per l'autenticazione, Windows Communication Foundation (WCF) usa Windows per convalidare il nome utente e la password.</span><span class="sxs-lookup"><span data-stu-id="0f1b2-103">By default, when a user name and password is used for authentication, Windows Communication Foundation (WCF) uses Windows to validate the user name and password.</span></span> <span data-ttu-id="0f1b2-104">Tuttavia, WCF consente schemi di autenticazione con nome utente e password personalizzati, noti anche come *validator*.</span><span class="sxs-lookup"><span data-stu-id="0f1b2-104">However, WCF allows for custom user name and password authentication schemes, also known as *validators*.</span></span> <span data-ttu-id="0f1b2-105">Per incorporare un validator personalizzato di nome utente e password, creare una classe che deriva da <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> e configurarla.</span><span class="sxs-lookup"><span data-stu-id="0f1b2-105">To incorporate a custom user name and password validator, create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> and then configure it.</span></span>

<span data-ttu-id="0f1b2-106">Per un'applicazione di esempio, vedere [validator nome utente password](../samples/user-name-password-validator.md).</span><span class="sxs-lookup"><span data-stu-id="0f1b2-106">For a sample application, see [User Name Password Validator](../samples/user-name-password-validator.md).</span></span>

### <a name="to-create-a-custom-user-name-and-password-validator"></a><span data-ttu-id="0f1b2-107">Per creare un validator di nome utente e password personalizzato</span><span class="sxs-lookup"><span data-stu-id="0f1b2-107">To create a custom user name and password validator</span></span>

1. <span data-ttu-id="0f1b2-108">Creare una classe che deriva da <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span><span class="sxs-lookup"><span data-stu-id="0f1b2-108">Create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span>

    [!code-csharp[C_CustomUsernameAndPasswordValidator#3](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]

2. <span data-ttu-id="0f1b2-109">Implementare lo schema di autenticazione personalizzato eseguendo l'override del metodo <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="0f1b2-109">Implement the custom authentication scheme by overriding the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>

    <span data-ttu-id="0f1b2-110">Non utilizzare il codice contenuto nell'esempio seguente, che esegue l'override del metodo <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>, in un ambiente di produzione.</span><span class="sxs-lookup"><span data-stu-id="0f1b2-110">Do not use the code in the following example that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="0f1b2-111">Sostituire il codice con lo schema di convalida di nome utente e password personalizzato, operazione che potrebbe comportare il recupero di coppie di nome utente e password da un database.</span><span class="sxs-lookup"><span data-stu-id="0f1b2-111">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>

    <span data-ttu-id="0f1b2-112">Affinché gli errori di autenticazione vengano restituiti al client, generare una classe <xref:System.ServiceModel.FaultException> nel metodo <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="0f1b2-112">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>

    [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]

### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="0f1b2-113">Per configurare un servizio per l'utilizzo di un validator di nome utente e password personalizzato</span><span class="sxs-lookup"><span data-stu-id="0f1b2-113">To configure a service to use a custom user name and password validator</span></span>

1. <span data-ttu-id="0f1b2-114">Configurare un'associazione che utilizza meccanismi di sicurezza a livello di messaggio su qualsiasi trasporto o meccanismi di sicurezza a livello di trasporto su HTTP(S).</span><span class="sxs-lookup"><span data-stu-id="0f1b2-114">Configure a binding that uses message security over any transport or transport-level security over HTTP(S).</span></span>

    <span data-ttu-id="0f1b2-115">Quando si utilizza la sicurezza dei messaggi, aggiungere una delle associazioni fornite dal sistema, ad esempio un [\<wshttpbinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)o un [\<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) che supporta la sicurezza dei messaggi e il tipo di credenziale `UserName`.</span><span class="sxs-lookup"><span data-stu-id="0f1b2-115">When using message security, add one of the system-provided bindings, such as a  [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), or a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) that supports message security and the `UserName` credential type.</span></span>

    <span data-ttu-id="0f1b2-116">Quando si utilizza la sicurezza a livello di trasporto su HTTP (S), aggiungere il [\<wshttpbinding >](../../configure-apps/file-schema/wcf/wshttpbinding.md) o [\<BasicHttpBinding >](../../configure-apps/file-schema/wcf/basichttpbinding.md), un\<[NetTcpBinding](../../configure-apps/file-schema/wcf/nettcpbinding.md) > oppure un\<[customBinding](../../configure-apps/file-schema/wcf/custombinding.md) > che utilizza http (s) e lo schema di autenticazione di `Basic`.</span><span class="sxs-lookup"><span data-stu-id="0f1b2-116">When using transport-level security over HTTP(S), add either the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md), a [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) or a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) that uses HTTP(S) and the `Basic` authentication scheme.</span></span>

    > [!NOTE]
    > <span data-ttu-id="0f1b2-117">Quando si usa .NET Framework 3,5 o versioni successive, è possibile usare un validator personalizzato di nome utente e password con la sicurezza dei messaggi e del trasporto.</span><span class="sxs-lookup"><span data-stu-id="0f1b2-117">When using .NET Framework 3.5 or later versions, you can use a custom username and password validator with message and transport security.</span></span> <span data-ttu-id="0f1b2-118">Con WinFX, un validator personalizzato di nome utente e password può essere utilizzato solo con la sicurezza dei messaggi.</span><span class="sxs-lookup"><span data-stu-id="0f1b2-118">With WinFX, a custom username and password validator can only be used with message security.</span></span>

    > [!TIP]
    > <span data-ttu-id="0f1b2-119">Per ulteriori informazioni sull'utilizzo di \<NetTcpBinding > in questo contesto, vedere [\<security >](../../configure-apps/file-schema/wcf/security-of-nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="0f1b2-119">For more information on using \<netTcpBinding> in this context, see [\<security>](../../configure-apps/file-schema/wcf/security-of-nettcpbinding.md).</span></span>

    1. <span data-ttu-id="0f1b2-120">Nel file di configurazione, sotto l'elemento [\<System. serviceModel >](../../configure-apps/file-schema/wcf/system-servicemodel.md) aggiungere un elemento [\<bindings >](../../configure-apps/file-schema/wcf/bindings.md) .</span><span class="sxs-lookup"><span data-stu-id="0f1b2-120">In the configuration file, under the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) element.</span></span>

    2. <span data-ttu-id="0f1b2-121">Aggiungere un [\<wshttpbinding >](../../configure-apps/file-schema/wcf/wshttpbinding.md) o [\<elemento BasicHttpBinding >](../../configure-apps/file-schema/wcf/basichttpbinding.md) alla sezione Bindings.</span><span class="sxs-lookup"><span data-stu-id="0f1b2-121">Add a [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) element to the bindings section.</span></span> <span data-ttu-id="0f1b2-122">Per ulteriori informazioni sulla creazione di un elemento di associazione WCF, vedere [procedura: specificare un'associazione al servizio nella configurazione](../how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="0f1b2-122">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../how-to-specify-a-service-binding-in-configuration.md).</span></span>

    3. <span data-ttu-id="0f1b2-123">Impostare l'attributo `mode` del [> di sicurezza\<](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) o [\<> di sicurezza](../../configure-apps/file-schema/wcf/security-of-basichttpbinding.md) su `Message`, `Transport`o `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="0f1b2-123">Set the `mode` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) or [\<security>](../../configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message`, `Transport`, or `TransportWithMessageCredential`.</span></span>

    4. <span data-ttu-id="0f1b2-124">Impostare l'attributo `clientCredentialType` del [messaggio di\<>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) o [\<> di trasporto](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="0f1b2-124">Set the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) or [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>

        <span data-ttu-id="0f1b2-125">Quando si utilizza la sicurezza del messaggio, impostare l'attributo `clientCredentialType` del [messaggio di\<>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) `UserName`.</span><span class="sxs-lookup"><span data-stu-id="0f1b2-125">When using message security, set the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) to `UserName`.</span></span>

        <span data-ttu-id="0f1b2-126">Quando si utilizza la sicurezza a livello di trasporto su HTTP (S), impostare l'attributo `clientCredentialType` del [> di trasporto\<](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) o [\<> del trasporto](../../configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) su `Basic`.</span><span class="sxs-lookup"><span data-stu-id="0f1b2-126">When using transport-level security over HTTP(S), set the `clientCredentialType` attribute of the [\<transport>](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) or [\<transport>](../../configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) to `Basic`.</span></span>

        > [!NOTE]
        > <span data-ttu-id="0f1b2-127">Quando un servizio WCF è ospitato in Internet Information Services (IIS) utilizzando la sicurezza a livello di trasporto e la proprietà <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> è impostata su <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, lo schema di autenticazione personalizzato utilizza un subset di autenticazione di Windows.</span><span class="sxs-lookup"><span data-stu-id="0f1b2-127">When a WCF service is hosted in Internet Information Services (IIS) using transport-level security and the <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> property is set to <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, the custom authentication scheme uses a subset of Windows authentication.</span></span> <span data-ttu-id="0f1b2-128">Ciò è dovuto al fatto che in questo scenario IIS esegue l'autenticazione di Windows prima che WCF richiami l'autenticatore personalizzato.</span><span class="sxs-lookup"><span data-stu-id="0f1b2-128">That is because in this scenario, IIS performs Windows authentication prior to WCF invoking the custom authenticator.</span></span>

    <span data-ttu-id="0f1b2-129">Per ulteriori informazioni sulla creazione di un elemento di associazione WCF, vedere [procedura: specificare un'associazione al servizio nella configurazione](../how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="0f1b2-129">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../how-to-specify-a-service-binding-in-configuration.md).</span></span>

    <span data-ttu-id="0f1b2-130">Nell'esempio seguente viene illustrato il codice di configurazione per l'associazione:</span><span class="sxs-lookup"><span data-stu-id="0f1b2-130">The following example shows the configuration code for the binding:</span></span>

    ```xml
    <system.serviceModel>
      <bindings>
      <wsHttpBinding>
          <binding name="Binding1">
            <security mode="Message">
              <message clientCredentialType="UserName" />
            </security>
          </binding>
        </wsHttpBinding>
      </bindings>
    </system.serviceModel>
    ```

2. <span data-ttu-id="0f1b2-131">Configurare un comportamento che specifica che un validator personalizzato di nome utente e password viene utilizzato per convalidare coppie di nome utente e password per i token di sicurezza <xref:System.IdentityModel.Tokens.UserNameSecurityToken> in arrivo.</span><span class="sxs-lookup"><span data-stu-id="0f1b2-131">Configure a behavior that specifies that a custom user name and password validator is used to validate user name and password pairs for incoming <xref:System.IdentityModel.Tokens.UserNameSecurityToken> security tokens.</span></span>

    1. <span data-ttu-id="0f1b2-132">Come elemento figlio dell'elemento [\<System. serviceModel >](../../configure-apps/file-schema/wcf/system-servicemodel.md) , aggiungere un elemento [\<> dei comportamenti](../../configure-apps/file-schema/wcf/behaviors.md) .</span><span class="sxs-lookup"><span data-stu-id="0f1b2-132">As a child to the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

    2. <span data-ttu-id="0f1b2-133">Aggiungere un [\<serviceBehaviors >](../../configure-apps/file-schema/wcf/servicebehaviors.md) all'elemento [\<behaviors >](../../configure-apps/file-schema/wcf/behaviors.md) .</span><span class="sxs-lookup"><span data-stu-id="0f1b2-133">Add a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

    3. <span data-ttu-id="0f1b2-134">Aggiungere un [\<comportamento >](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elemento e impostare l'attributo `name` su un valore appropriato.</span><span class="sxs-lookup"><span data-stu-id="0f1b2-134">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>

    4. <span data-ttu-id="0f1b2-135">Aggiungere un [> di\<ServiceCredentials](../../configure-apps/file-schema/wcf/servicecredentials.md) all'elemento [> del comportamento\<](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) .</span><span class="sxs-lookup"><span data-stu-id="0f1b2-135">Add a [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) to the [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>

    5. <span data-ttu-id="0f1b2-136">Aggiungere un [\<> UserNameAuthentication](../../configure-apps/file-schema/wcf/usernameauthentication.md) al [>\<ServiceCredentials](../../configure-apps/file-schema/wcf/servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="0f1b2-136">Add a [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) to the [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md).</span></span>

    6. <span data-ttu-id="0f1b2-137">Impostare `userNamePasswordValidationMode` su `Custom`.</span><span class="sxs-lookup"><span data-stu-id="0f1b2-137">Set the `userNamePasswordValidationMode` to `Custom`.</span></span>

        > [!IMPORTANT]
        > <span data-ttu-id="0f1b2-138">Se il valore `userNamePasswordValidationMode` non è impostato, WCF usa l'autenticazione di Windows anziché il validator personalizzato di nome utente e password.</span><span class="sxs-lookup"><span data-stu-id="0f1b2-138">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the custom user name and password validator.</span></span>

    7. <span data-ttu-id="0f1b2-139">Impostare `customUserNamePasswordValidatorType` sul tipo che rappresenta il validator personalizzato di nome utente e password.</span><span class="sxs-lookup"><span data-stu-id="0f1b2-139">Set the `customUserNamePasswordValidatorType` to the type that represents your custom user name and password validator.</span></span>

    <span data-ttu-id="0f1b2-140">Nell'esempio seguente viene illustrato il frammento di `<serviceCredentials>` fino a questo punto:</span><span class="sxs-lookup"><span data-stu-id="0f1b2-140">The following example shows the `<serviceCredentials>` fragment to this point:</span></span>

    ```xml
    <serviceCredentials>
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />
    </serviceCredentials>
    ```

## <a name="example"></a><span data-ttu-id="0f1b2-141">Esempio</span><span class="sxs-lookup"><span data-stu-id="0f1b2-141">Example</span></span>

<span data-ttu-id="0f1b2-142">Nel codice di esempio seguente viene dimostrato come creare un validator personalizzato di nome utente e password.</span><span class="sxs-lookup"><span data-stu-id="0f1b2-142">The following code example demonstrates how to create a custom user name and password validator.</span></span> <span data-ttu-id="0f1b2-143">Non utilizzare il codice che esegue l'override del metodo <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> in un ambiente di produzione.</span><span class="sxs-lookup"><span data-stu-id="0f1b2-143">Do not use the code that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="0f1b2-144">Sostituire il codice con lo schema di convalida di nome utente e password personalizzato, operazione che potrebbe comportare il recupero di coppie di nome utente e password da un database.</span><span class="sxs-lookup"><span data-stu-id="0f1b2-144">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>

[!code-csharp[C_CustomUsernameAndPasswordValidator#1](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
[!code-vb[C_CustomUsernameAndPasswordValidator#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]

## <a name="see-also"></a><span data-ttu-id="0f1b2-145">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0f1b2-145">See also</span></span>

- <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>
- [<span data-ttu-id="0f1b2-146">Procedura: Usare provider di appartenenza ASP.NET</span><span class="sxs-lookup"><span data-stu-id="0f1b2-146">How to: Use the ASP.NET Membership Provider</span></span>](how-to-use-the-aspnet-membership-provider.md)
- [<span data-ttu-id="0f1b2-147">Autenticazione</span><span class="sxs-lookup"><span data-stu-id="0f1b2-147">Authentication</span></span>](authentication-in-wcf.md)
