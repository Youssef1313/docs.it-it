---
title: "Procedura: Compilare un'applicazione Web ASP.NET MVC che può riconoscere attestazioni con WIF"
ms.date: 03/30/2017
ms.assetid: 0efb76bc-9f7b-4afe-be1c-2a57c917010b
author: BrucePerlerMS
ms.openlocfilehash: 4d245288b04d8ed3d997bc5572b40c7f8a9334e5
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045443"
---
# <a name="how-to-build-claims-aware-aspnet-mvc-web-application-using-wif"></a><span data-ttu-id="cd432-102">Procedura: Compilare un'applicazione Web ASP.NET MVC che può riconoscere attestazioni con WIF</span><span class="sxs-lookup"><span data-stu-id="cd432-102">How To: Build Claims-Aware ASP.NET MVC Web Application Using WIF</span></span>
## <a name="applies-to"></a><span data-ttu-id="cd432-103">Si applica a</span><span class="sxs-lookup"><span data-stu-id="cd432-103">Applies To</span></span>  
  
- <span data-ttu-id="cd432-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="cd432-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
- <span data-ttu-id="cd432-105">MVC ASP.NET®</span><span class="sxs-lookup"><span data-stu-id="cd432-105">ASP.NET® MVC</span></span>  
  
## <a name="summary"></a><span data-ttu-id="cd432-106">Riepilogo</span><span class="sxs-lookup"><span data-stu-id="cd432-106">Summary</span></span>  
 <span data-ttu-id="cd432-107">Questo argomento include le procedure dettagliate per creare una semplice applicazione Web MVC ASP.NET in grado di riconoscere attestazioni.</span><span class="sxs-lookup"><span data-stu-id="cd432-107">This How-To provides detailed step-by-step procedures for creating simple claims-aware ASP.NET MVC web application.</span></span> <span data-ttu-id="cd432-108">Sono inoltre disponibili istruzioni su come testare la semplice applicazione Web MVC ASP.NET in grado di riconoscere attestazioni per la corretta implementazione dell'autenticazione basata su attestazioni.</span><span class="sxs-lookup"><span data-stu-id="cd432-108">It also provides instructions how to test the simple claims-aware ASP.NET MVC web application for successful implementation of claims-based authentication.</span></span> <span data-ttu-id="cd432-109">La procedura decritta in questo argomento non include istruzioni dettagliate per la creazione di un servizio token di sicurezza e presuppone che il servizio sia già stato configurato.</span><span class="sxs-lookup"><span data-stu-id="cd432-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and assumes you have already configured an STS.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="cd432-110">Sommario</span><span class="sxs-lookup"><span data-stu-id="cd432-110">Contents</span></span>  
  
- <span data-ttu-id="cd432-111">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="cd432-111">Objectives</span></span>  
  
- <span data-ttu-id="cd432-112">Riepilogo dei passaggi</span><span class="sxs-lookup"><span data-stu-id="cd432-112">Summary of Steps</span></span>  
  
- <span data-ttu-id="cd432-113">Passaggio 1: creare l'applicazione MVC ASP.NET semplice</span><span class="sxs-lookup"><span data-stu-id="cd432-113">Step 1 – Create Simple ASP.NET MVC Application</span></span>  
  
- <span data-ttu-id="cd432-114">Passaggio 2: configurare l'applicazione MVC ASP.NET per l'autenticazione basata su attestazioni</span><span class="sxs-lookup"><span data-stu-id="cd432-114">Step 2 – Configure ASP.NET MVC Application for Claims-Based Authentication</span></span>  
  
- <span data-ttu-id="cd432-115">Passaggio 3: eseguire i test sulla soluzione</span><span class="sxs-lookup"><span data-stu-id="cd432-115">Step 3 – Test Your Solution</span></span>  
  
- <span data-ttu-id="cd432-116">Elementi correlati</span><span class="sxs-lookup"><span data-stu-id="cd432-116">Related Items</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="cd432-117">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="cd432-117">Objectives</span></span>  
  
- <span data-ttu-id="cd432-118">Configurare l'applicazione Web MVC ASP.NET per l'autenticazione basata su attestazioni</span><span class="sxs-lookup"><span data-stu-id="cd432-118">Configure ASP.NET MVC web application for claims-based authentication</span></span>  
  
- <span data-ttu-id="cd432-119">Testare l'applicazione Web MVC ASP.NET in grado di riconoscere attestazioni</span><span class="sxs-lookup"><span data-stu-id="cd432-119">Test successful claims-aware ASP.NET MVC web application</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="cd432-120">Riepilogo dei passaggi</span><span class="sxs-lookup"><span data-stu-id="cd432-120">Summary of Steps</span></span>  
  
- <span data-ttu-id="cd432-121">Passaggio 1: creare l'applicazione MVC ASP.NET semplice</span><span class="sxs-lookup"><span data-stu-id="cd432-121">Step 1 – Create Simple ASP.NET MVC Application</span></span>  
  
- <span data-ttu-id="cd432-122">Passaggio 2: configurare l'applicazione MVC ASP.NET per l'autenticazione basata su attestazioni</span><span class="sxs-lookup"><span data-stu-id="cd432-122">Step 2 – Configure ASP.NET MVC Application for Claims-Based Authentication</span></span>  
  
- <span data-ttu-id="cd432-123">Passaggio 3: eseguire i test sulla soluzione</span><span class="sxs-lookup"><span data-stu-id="cd432-123">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-simple-aspnet-mvc-application"></a><span data-ttu-id="cd432-124">Passaggio 1: creare l'applicazione MVC ASP.NET semplice</span><span class="sxs-lookup"><span data-stu-id="cd432-124">Step 1 – Create Simple ASP.NET MVC Application</span></span>  
 <span data-ttu-id="cd432-125">In questo passaggio si creerà una nuova applicazione MVC ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="cd432-125">In this step, you will create a new ASP.NET MVC application.</span></span>  
  
#### <a name="to-create-simple-aspnet-mvc-application"></a><span data-ttu-id="cd432-126">Per creare un'applicazione MVC ASP.NET semplice</span><span class="sxs-lookup"><span data-stu-id="cd432-126">To create simple ASP.NET MVC application</span></span>  
  
1. <span data-ttu-id="cd432-127">Avviare Visual Studio e fare clic su **File**, **Nuovo** e **Progetto**.</span><span class="sxs-lookup"><span data-stu-id="cd432-127">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2. <span data-ttu-id="cd432-128">Nella finestra **Nuovo progetto** fare clic su **Applicazione Web MVC 3 ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="cd432-128">In the **New Project** window, click **ASP.NET MVC 3 Web Application**.</span></span>  
  
3. <span data-ttu-id="cd432-129">In **Nome** immettere `TestApp` e fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="cd432-129">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
4. <span data-ttu-id="cd432-130">Nella finestra di dialogo **Nuovo progetto MVC 3 ASP.NET** selezionare **Applicazione Internet** tra i modelli disponibili, assicurarsi che **Motore di visualizzazione** sia impostato su **Razor** e quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="cd432-130">In the **New ASP.NET MVC 3 Project** dialog, select **Internet Application** from the available templates, ensure **View Engine** is set to **Razor**, and then click **OK**.</span></span>  
  
5. <span data-ttu-id="cd432-131">All'apertura del nuovo progetto fare clic con il pulsante destro del mouse sul progetto **TestApp** in **Esplora soluzioni** e scegliere **Proprietà**.</span><span class="sxs-lookup"><span data-stu-id="cd432-131">When the new project opens, right-click the **TestApp** project in **Solution Explorer** and select the **Properties** option.</span></span>  
  
6. <span data-ttu-id="cd432-132">Nella pagina delle proprietà del progetto fare clic sulla scheda **Web** a sinistra e assicurarsi che sia selezionata l'opzione **Usa server Web IIS locale**.</span><span class="sxs-lookup"><span data-stu-id="cd432-132">On the project’s properties page, click on the **Web** tab on the left and ensure that the **Use Local IIS Web Server** option is selected.</span></span>  
  
## <a name="step-2--configure-aspnet-mvc-application-for-claims-based-authentication"></a><span data-ttu-id="cd432-133">Passaggio 2: configurare l'applicazione MVC ASP.NET per l'autenticazione basata su attestazioni</span><span class="sxs-lookup"><span data-stu-id="cd432-133">Step 2 – Configure ASP.NET MVC Application for Claims-Based Authentication</span></span>  
 <span data-ttu-id="cd432-134">In questo passaggio si aggiungeranno voci di configurazione al file di configurazione *Web.config* dell'applicazione Web MVC ASP.NET per renderla in grado di riconoscere attestazioni.</span><span class="sxs-lookup"><span data-stu-id="cd432-134">In this step you will add configuration entries to the *Web.config* configuration file of your ASP.NET MVC web application to make it claims-aware.</span></span>  
  
#### <a name="to-configure-aspnet-mvc-application-for-claims-based-authentication"></a><span data-ttu-id="cd432-135">Per configurare l'applicazione MVC ASP.NET per l'autenticazione basata su attestazioni</span><span class="sxs-lookup"><span data-stu-id="cd432-135">To configure ASP.NET MVC application for claims-based authentication</span></span>  
  
1. <span data-ttu-id="cd432-136">Aggiungere le definizioni di sezione di configurazione seguenti nel file di configurazione *Web.config*,</span><span class="sxs-lookup"><span data-stu-id="cd432-136">Add the following configuration section definitions to the *Web.config* configuration file.</span></span> <span data-ttu-id="cd432-137">che definiscono le sezioni di configurazione richieste da Windows Identity Foundation.</span><span class="sxs-lookup"><span data-stu-id="cd432-137">These define configuration sections required by Windows Identity Foundation.</span></span> <span data-ttu-id="cd432-138">Aggiungere le definizioni subito dopo l'elemento di apertura **\<configuration>** :</span><span class="sxs-lookup"><span data-stu-id="cd432-138">Add the definitions immediately after the **\<configuration>** opening element:</span></span>  
  
    ```xml  
    <configSections>  
        <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
        <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2. <span data-ttu-id="cd432-139">Aggiungere un **elemento \<location>** che consente l'accesso ai metadati di federazione dell'applicazione:</span><span class="sxs-lookup"><span data-stu-id="cd432-139">Add a **\<location>** element that enables access to the application’s federation metadata:</span></span>  
  
    ```xml  
    <location path="FederationMetadata">  
        <system.web>  
            <authorization>  
                <allow users="*" />  
            </authorization>  
        </system.web>  
    </location>  
    ```  
  
3. <span data-ttu-id="cd432-140">Aggiungere le seguenti voci di configurazione all'interno di elementi **\<system.web>** per negare le autorizzazioni agli utenti, disabilitare l'autenticazione nativa e abilitare WIF per gestire l'autenticazione.</span><span class="sxs-lookup"><span data-stu-id="cd432-140">Add the following configuration entries within the **\<system.web>** elements to deny users, disable native authentication, and enable WIF to manage authentication.</span></span>  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4. <span data-ttu-id="cd432-141">Aggiungere le voci di configurazione correlate a Windows Identity Foundation seguenti e assicurarsi che l'URL e il numero di porta dell'applicazione ASP.NET corrispondano ai valori nella voce **\<audienceUris>** , all'attributo **realm** dell'elemento **\<wsFederation>** e all'attributo **reply** dell'elemento **\<wsFederation>** .</span><span class="sxs-lookup"><span data-stu-id="cd432-141">Add the following Windows Identity Foundation related configuration entries and ensure that your ASP.NET application’s URL and port number match the values in the **\<audienceUris>** entry, **realm** attribute of the **\<wsFederation>** element, and the **reply** attribute of the **\<wsFederation>** element.</span></span> <span data-ttu-id="cd432-142">Assicurarsi anche che il valore **issuer** sia appropriato per l'URL del servizio token di sicurezza.</span><span class="sxs-lookup"><span data-stu-id="cd432-142">Also ensure that the **issuer** value fits your Security Token Service (STS) URL.</span></span>  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration>  
            <audienceUris>  
                <add value="http://localhost:28503/" />  
            </audienceUris>  
            <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
                <trustedIssuers>  
                    <add thumbprint="1234567890ABCDEFGHIJKLMNOPQRSTUVWXYZ1234" name="YourSTSName" />  
                </trustedIssuers>   
            </issuerNameRegistry>  
            <certificateValidation certificateValidationMode="None" />  
        </identityConfiguration>  
    </system.identityModel>  
    <system.identityModel.services>  
        <federationConfiguration>  
            <cookieHandler requireSsl="false" />  
            <wsFederation passiveRedirectEnabled="true" issuer="http://localhost:13922/wsFederationSTS/Issue" realm="http://localhost:28503/" reply="http://localhost:28503/" requireHttps="false" />  
        </federationConfiguration>  
    </system.identityModel.services>  
    ```  
  
5. <span data-ttu-id="cd432-143">Aggiungere un riferimento all'assembly <xref:System.IdentityModel>.</span><span class="sxs-lookup"><span data-stu-id="cd432-143">Add reference to the <xref:System.IdentityModel> assembly.</span></span>  
  
6. <span data-ttu-id="cd432-144">Compilare la soluzione e assicurarsi che non ci siano errori.</span><span class="sxs-lookup"><span data-stu-id="cd432-144">Compile the solution to make sure there are errors.</span></span>  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="cd432-145">Passaggio 3: eseguire i test sulla soluzione</span><span class="sxs-lookup"><span data-stu-id="cd432-145">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="cd432-146">In questo passaggio si testerà l'applicazione Web MVC ASP.NET configurata per l'autenticazione basata sulle attestazioni.</span><span class="sxs-lookup"><span data-stu-id="cd432-146">In this step you will test your ASP.NET MVC web application configured for claims-based authentication.</span></span> <span data-ttu-id="cd432-147">Per eseguire un test di base, si aggiungerà codice semplice che visualizza le attestazioni nel token rilasciato dal servizio token di sicurezza.</span><span class="sxs-lookup"><span data-stu-id="cd432-147">To perform basic test you will add simple code that displays claims in the token issued by the Security Token Service (STS).</span></span>  
  
#### <a name="to-test-your-aspnet-mvc-application-for-claims-based-authentication"></a><span data-ttu-id="cd432-148">Per testare l'applicazione MVC ASP.NET per l'autenticazione basata su attestazioni</span><span class="sxs-lookup"><span data-stu-id="cd432-148">To test your ASP.NET MVC application for claims-based authentication</span></span>  
  
1. <span data-ttu-id="cd432-149">In **Esplora soluzioni** espandere la cartella **Controller** e aprire il file *HomeController.cs* nell'editor.</span><span class="sxs-lookup"><span data-stu-id="cd432-149">In the **Solution Explorer**, expand the **Controllers** folder and open *HomeController.cs* file in the editor.</span></span> <span data-ttu-id="cd432-150">Aggiungere il codice seguente al metodo **Index**:</span><span class="sxs-lookup"><span data-stu-id="cd432-150">Add the following code to the **Index** method:</span></span>  
  
    ```csharp  
    public ActionResult Index()  
    {  
        ViewBag.ClaimsIdentity = Thread.CurrentPrincipal.Identity;  
  
        return View();  
    }  
    ```  
  
2. <span data-ttu-id="cd432-151">In **Esplora soluzioni** espandere le cartelle **Visualizzazioni** e **Home** e aprire il file *Index.cshtml* nell'editor.</span><span class="sxs-lookup"><span data-stu-id="cd432-151">In the **Solution Explorer** expand **Views** and then **Home** folders and open *Index.cshtml* file in the editor.</span></span> <span data-ttu-id="cd432-152">Eliminarne il contenuto e aggiungere il markup seguente:</span><span class="sxs-lookup"><span data-stu-id="cd432-152">Delete its contents and add the following markup:</span></span>  
  
    ```html  
    @{  
        ViewBag.Title = "Home Page";  
    }  
  
    <h2>Welcome: @ViewBag.ClaimsIdentity.Name</h2>  
    <h3>Values from Identity</h3>  
    <table>  
        <tr>  
            <th>  
                IsAuthenticated   
            </th>  
            <td>  
                @ViewBag.ClaimsIdentity.IsAuthenticated   
            </td>  
        </tr>  
        <tr>  
            <th>  
                Name   
            </th>          
            <td>  
                @ViewBag.ClaimsIdentity.Name  
            </td>          
        </tr>  
    </table>  
    <h3>Claims from ClaimsIdentity</h3>  
    <table>  
        <tr>  
            <th>  
                Claim Type  
            </th>  
            <th>  
                Claim Value  
            </th>  
            <th>  
                Value Type  
            </th>  
            <th>  
                Subject Name  
            </th>          
            <th>  
                Issuer Name  
            </th>          
        </tr>  
            @foreach (System.Security.Claims.Claim claim in ViewBag.ClaimsIdentity.Claims ) {  
        <tr>  
            <td>  
                @claim.Type  
            </td>  
            <td>  
                @claim.Value  
            </td>  
            <td>  
                @claim.ValueType  
            </td>  
            <td>  
                @claim.Subject.Name  
            </td>  
            <td>  
                @claim.Issuer  
            </td>  
        </tr>  
    }  
    </table>  
    ```  
  
3. <span data-ttu-id="cd432-153">Eseguire la soluzione premendo **F5**.</span><span class="sxs-lookup"><span data-stu-id="cd432-153">Run the solution by pressing the **F5** key.</span></span>  
  
4. <span data-ttu-id="cd432-154">Dovrebbe essere visualizzata la pagina che mostra le attestazioni nel token emesso dal servizio token di sicurezza.</span><span class="sxs-lookup"><span data-stu-id="cd432-154">You should be presented with the page that displays the claims in the token that was issued to you by Security Token Service.</span></span>  
  
## <a name="related-items"></a><span data-ttu-id="cd432-155">Elementi correlati</span><span class="sxs-lookup"><span data-stu-id="cd432-155">Related Items</span></span>  
  
- [<span data-ttu-id="cd432-156">Procedura: Creare un'applicazione Web Form ASP.NET in grado di riconoscere attestazioni con WIF</span><span class="sxs-lookup"><span data-stu-id="cd432-156">How To: Build Claims-Aware ASP.NET Web Forms Application Using WIF</span></span>](how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)
