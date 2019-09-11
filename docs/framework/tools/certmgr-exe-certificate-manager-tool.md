---
title: Certmgr.exe (strumento di gestione certificati)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates, managing
- CRLs
- certificate trust lists
- Certmgr.exe
- Certificate Manager tool
- CTLs
- certificate revocation lists
ms.assetid: 7e953b43-1374-4bbc-814f-53ca1b6b52bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d13c2d2cc391e61c8ed764c26e5e5b5e7ea2a3bb
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851375"
---
# <a name="certmgrexe-certificate-manager-tool"></a><span data-ttu-id="44223-102">Certmgr.exe (strumento di gestione certificati)</span><span class="sxs-lookup"><span data-stu-id="44223-102">Certmgr.exe (Certificate Manager Tool)</span></span>
<span data-ttu-id="44223-103">Lo strumento di gestione certificati (Certmgr.exe) gestisce certificati, elenchi di scopi consentiti ai certificati ed elenchi di revoche di certificati (CRL, Certificate Revocation List).</span><span class="sxs-lookup"><span data-stu-id="44223-103">The Certificate Manager tool (Certmgr.exe) manages certificates, certificate trust lists (CTLs), and certificate revocation lists (CRLs).</span></span>  
  
 <span data-ttu-id="44223-104">Lo strumento viene installato automaticamente insieme a Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="44223-104">The Certificate Manager is automatically installed with Visual Studio.</span></span> <span data-ttu-id="44223-105">Per avviare lo strumento, utilizzare il [Prompt dei comandi](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="44223-105">To start the tool, use the [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="44223-106">Lo strumento di gestione dei certificati (Certmgr.exe) è un'utilità da riga di comando, da non confondere con lo snap-in certificati (Certmgr.msc) di Microsoft Management Console (MMC).</span><span class="sxs-lookup"><span data-stu-id="44223-106">The Certificate Manager tool (Certmgr.exe) is a command-line utility, whereas Certificates (Certmgr.msc) is a Microsoft Management Console (MMC) snap-in.</span></span> <span data-ttu-id="44223-107">Poiché Certmgr.msc in genere si trova nella directory di sistema di Windows, l'immissione di `certmgr` nella riga di comando potrebbe caricare lo snap-in di MMC Certificati anche se è stato aperto il Prompt dei comandi per gli sviluppatori per Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="44223-107">Because Certmgr.msc is usually found in the Windows System directory, entering `certmgr` at the command line may load the Certificates MMC snap-in even if you have opened the Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="44223-108">Questo accade perché il percorso dello snap-in precede il percorso dello strumento di gestione dei certificati nella variabile di ambiente PATH.</span><span class="sxs-lookup"><span data-stu-id="44223-108">This occurs because the path to the snap-in precedes the path to the Certificate Manager tool in the PATH environment variable.</span></span> <span data-ttu-id="44223-109">Se si verifica questo problema, è possibile eseguire i comandi Certmgr.exe specificando il percorso dell'eseguibile.</span><span class="sxs-lookup"><span data-stu-id="44223-109">If you encounter this problem, you can execute Certmgr.exe commands by specifying the path to the executable.</span></span>  
  
 <span data-ttu-id="44223-110">Viene installato automaticamente con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="44223-110">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="44223-111">Per eseguire lo strumento, usare il Prompt dei comandi per gli sviluppatori per Visual Studio (o il prompt dei comandi di Visual Studio in Windows 7).</span><span class="sxs-lookup"><span data-stu-id="44223-111">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="44223-112">Per altre informazioni, vedere [Prompt dei comandi](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="44223-112">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="44223-113">Per una panoramica dei certificati X.509, vedere [Utilizzo dei certificati](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="44223-113">For an overview of X.509 certificates, see [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
 <span data-ttu-id="44223-114">Al prompt dei comandi digitare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="44223-114">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44223-115">Sintassi</span><span class="sxs-lookup"><span data-stu-id="44223-115">Syntax</span></span>  
  
```console  
      certmgr [/add | /del | /put] [options]  
[/s[/r registryLocation]] [sourceStorename]  
[/s[/r registryLocation]] [destinationStorename]  
```  
  
## <a name="parameters"></a><span data-ttu-id="44223-116">Parametri</span><span class="sxs-lookup"><span data-stu-id="44223-116">Parameters</span></span>  
  
|<span data-ttu-id="44223-117">Argomento</span><span class="sxs-lookup"><span data-stu-id="44223-117">Argument</span></span>|<span data-ttu-id="44223-118">Descrizione</span><span class="sxs-lookup"><span data-stu-id="44223-118">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="44223-119">*sourceStorename*</span><span class="sxs-lookup"><span data-stu-id="44223-119">*sourceStorename*</span></span>|<span data-ttu-id="44223-120">Archivio certificati contenente certificati, elenchi di scopi consentiti ai certificati o CRL da aggiungere, eliminare, salvare o visualizzare.</span><span class="sxs-lookup"><span data-stu-id="44223-120">The certificate store that contains the existing certificates, CTLs, or CRLs to add, delete, save, or display.</span></span> <span data-ttu-id="44223-121">Può trattarsi di un file di archivio o di un archivio di sistema.</span><span class="sxs-lookup"><span data-stu-id="44223-121">This can be a store file or a systems store.</span></span>|  
|<span data-ttu-id="44223-122">*destinationStorename*</span><span class="sxs-lookup"><span data-stu-id="44223-122">*destinationStorename*</span></span>|<span data-ttu-id="44223-123">File o archivio certificati di output.</span><span class="sxs-lookup"><span data-stu-id="44223-123">The output certificate store or file.</span></span>|  
  
|<span data-ttu-id="44223-124">Opzione</span><span class="sxs-lookup"><span data-stu-id="44223-124">Option</span></span>|<span data-ttu-id="44223-125">Descrizione</span><span class="sxs-lookup"><span data-stu-id="44223-125">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="44223-126">**/add**</span><span class="sxs-lookup"><span data-stu-id="44223-126">**/add**</span></span>|<span data-ttu-id="44223-127">Aggiunge certificati, elenchi di scopi consentiti ai certificati e CRL a un archivio certificati.</span><span class="sxs-lookup"><span data-stu-id="44223-127">Adds certificates, CTLs, and CRLs to a certificate store.</span></span>|  
|<span data-ttu-id="44223-128">**/all**</span><span class="sxs-lookup"><span data-stu-id="44223-128">**/all**</span></span>|<span data-ttu-id="44223-129">Aggiunge tutte le voci se usata con **/add**,</span><span class="sxs-lookup"><span data-stu-id="44223-129">Adds all entries when used with **/add**.</span></span> <span data-ttu-id="44223-130">le elimina se usata con **/del** e le visualizza se usata senza le opzioni **/add** o **/del**.</span><span class="sxs-lookup"><span data-stu-id="44223-130">Deletes all entries when used with **/del**. Displays all entries when used without the **/add** or **/del** options.</span></span> <span data-ttu-id="44223-131">Non è possibile usare l'opzione **/all** con **/put**.</span><span class="sxs-lookup"><span data-stu-id="44223-131">The **/all** option cannot be used with **/put**.</span></span>|  
|<span data-ttu-id="44223-132">**/c**</span><span class="sxs-lookup"><span data-stu-id="44223-132">**/c**</span></span>|<span data-ttu-id="44223-133">Aggiunge i certificati se usata con **/add**,</span><span class="sxs-lookup"><span data-stu-id="44223-133">Adds certificates when used with **/add**.</span></span> <span data-ttu-id="44223-134">li elimina se usata con **/del** e li salva se usata con **/put**.</span><span class="sxs-lookup"><span data-stu-id="44223-134">Deletes certificates when used with **/del**. Saves certificates when used with **/put**.</span></span> <span data-ttu-id="44223-135">Visualizza certificati quando usata senza le opzioni **/add**, **/del** o **/put**.</span><span class="sxs-lookup"><span data-stu-id="44223-135">Displays certificates when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="44223-136">**/CRL**</span><span class="sxs-lookup"><span data-stu-id="44223-136">**/CRL**</span></span>|<span data-ttu-id="44223-137">Aggiunge i CRL se usata con **/add**,</span><span class="sxs-lookup"><span data-stu-id="44223-137">Adds CRLs when used with **/add**.</span></span> <span data-ttu-id="44223-138">li elimina se usata con **/del** e li salva se usata con **/put**.</span><span class="sxs-lookup"><span data-stu-id="44223-138">Deletes CRLs when used with **/del**. Saves CRLs when used with **/put**.</span></span> <span data-ttu-id="44223-139">Visualizza CRL quando usata senza le opzioni **/add**, **/del** o **/put**.</span><span class="sxs-lookup"><span data-stu-id="44223-139">Displays CRLs when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="44223-140">**/CTL**</span><span class="sxs-lookup"><span data-stu-id="44223-140">**/CTL**</span></span>|<span data-ttu-id="44223-141">Aggiunge gli elenchi di scopi consentiti se usata con **/add**,</span><span class="sxs-lookup"><span data-stu-id="44223-141">Adds CTLs when used with **/add**.</span></span> <span data-ttu-id="44223-142">li elimina se usata con **/del** e li salva se usata con **/put**.</span><span class="sxs-lookup"><span data-stu-id="44223-142">Deletes CTLs when used with **/del**. Saves CTLs when used with **/put**.</span></span> <span data-ttu-id="44223-143">Visualizza gli elenchi di scopi consentiti quando usata senza le opzioni **/add**, **/del** o **/put**.</span><span class="sxs-lookup"><span data-stu-id="44223-143">Displays CTLs when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="44223-144">**/del**</span><span class="sxs-lookup"><span data-stu-id="44223-144">**/del**</span></span>|<span data-ttu-id="44223-145">Elimina certificati, elenchi di scopi consentiti e CRL da un archivio certificati.</span><span class="sxs-lookup"><span data-stu-id="44223-145">Deletes certificates, CTLs, and CRLs from a certificate store.</span></span>|  
|<span data-ttu-id="44223-146">**/e** *encodingType*</span><span class="sxs-lookup"><span data-stu-id="44223-146">**/e** *encodingType*</span></span>|<span data-ttu-id="44223-147">Specifica il tipo di codifica dei certificati.</span><span class="sxs-lookup"><span data-stu-id="44223-147">Specifies the certificate encoding type.</span></span> <span data-ttu-id="44223-148">Il valore predefinito è `X509_ASN_ENCODING`.</span><span class="sxs-lookup"><span data-stu-id="44223-148">The default is `X509_ASN_ENCODING`.</span></span>|  
|<span data-ttu-id="44223-149">**/f** *dwFlags*</span><span class="sxs-lookup"><span data-stu-id="44223-149">**/f** *dwFlags*</span></span>|<span data-ttu-id="44223-150">Specifica il flag di archivio aperto.</span><span class="sxs-lookup"><span data-stu-id="44223-150">Specifies the store open flag.</span></span> <span data-ttu-id="44223-151">Si tratta del parametro *dwFlags* passato a **CertOpenStore**.</span><span class="sxs-lookup"><span data-stu-id="44223-151">This is the *dwFlags* parameter passed to **CertOpenStore**.</span></span> <span data-ttu-id="44223-152">Il valore predefinito è CERT_SYSTEM_STORE_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="44223-152">The default value is CERT_SYSTEM_STORE_CURRENT_USER.</span></span> <span data-ttu-id="44223-153">Questa opzione viene considerata solo se viene usata l'opzione **/y**.</span><span class="sxs-lookup"><span data-stu-id="44223-153">This option is considered only if the **/y** option is used.</span></span>|  
|<span data-ttu-id="44223-154">**/h**[**elp**]</span><span class="sxs-lookup"><span data-stu-id="44223-154">**/h**[**elp**]</span></span>|<span data-ttu-id="44223-155">Visualizza la sintassi e le opzioni di comando dello strumento.</span><span class="sxs-lookup"><span data-stu-id="44223-155">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="44223-156">**/n** *nam*</span><span class="sxs-lookup"><span data-stu-id="44223-156">**/n** *nam*</span></span>|<span data-ttu-id="44223-157">Specifica il nome comune del certificato da aggiungere, eliminare o salvare.</span><span class="sxs-lookup"><span data-stu-id="44223-157">Specifies the common name of the certificate to add, delete, or save.</span></span> <span data-ttu-id="44223-158">È possibile usare questa opzione solo con certificati, non con elenchi di scopi consentiti o CRL.</span><span class="sxs-lookup"><span data-stu-id="44223-158">This option can only be used with certificates; it cannot be used with CTLs or CRLs.</span></span>|  
|<span data-ttu-id="44223-159">**/put**</span><span class="sxs-lookup"><span data-stu-id="44223-159">**/put**</span></span>|<span data-ttu-id="44223-160">Salva su file un certificato X.509, un elenco di scopi consentiti o un CRL da un archivio certificati.</span><span class="sxs-lookup"><span data-stu-id="44223-160">Saves an X.509 certificate, CTL, or CRL from a certificate store to a file.</span></span> <span data-ttu-id="44223-161">Il file viene salvato nel formato X.509.</span><span class="sxs-lookup"><span data-stu-id="44223-161">The file is saved in X.509 format.</span></span> <span data-ttu-id="44223-162">È possibile usare l'opzione **/7** con l'opzione **/put** per salvare il file nel formato PKCS #7.</span><span class="sxs-lookup"><span data-stu-id="44223-162">You can use the **/7** option with the **/put** option to save the file in PKCS #7 format.</span></span> <span data-ttu-id="44223-163">L'opzione **/put** deve essere seguita da **/c**, **/CTL** o **/CRL**.</span><span class="sxs-lookup"><span data-stu-id="44223-163">The **/put** option must be followed by either **/c**, **/CTL**, or **/CRL**.</span></span> <span data-ttu-id="44223-164">Non è possibile usare l'opzione **/all** con **/put**.</span><span class="sxs-lookup"><span data-stu-id="44223-164">The **/all** option cannot be used with **/put**.</span></span>|  
|<span data-ttu-id="44223-165">**/r** *location*</span><span class="sxs-lookup"><span data-stu-id="44223-165">**/r** *location*</span></span>|<span data-ttu-id="44223-166">Identifica la posizione dell'archivio di sistema all'interno del Registro di sistema.</span><span class="sxs-lookup"><span data-stu-id="44223-166">Identifies the registry location of the system store.</span></span> <span data-ttu-id="44223-167">Questa opzione viene considerata solo se viene specificata l'opzione **/s**.</span><span class="sxs-lookup"><span data-stu-id="44223-167">This option is considered only if you specify the **/s** option.</span></span> <span data-ttu-id="44223-168">*location* deve essere uno degli elementi seguenti:</span><span class="sxs-lookup"><span data-stu-id="44223-168">*location* must be one of the following:</span></span><br /><br /> <span data-ttu-id="44223-169">-   `currentUser` indica che l'archivio certificati si trova sotto la chiave HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="44223-169">-   `currentUser` indicates that the certificate store is under the HKEY_CURRENT_USER key.</span></span> <span data-ttu-id="44223-170">Questa è l'impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="44223-170">This is the default.</span></span><br /><span data-ttu-id="44223-171">-   `localMachine` indica che l'archivio certificati si trova sotto la chiave HKEY_LOCAL_MACHINE.</span><span class="sxs-lookup"><span data-stu-id="44223-171">-   `localMachine` indicates that the certificate store is under the HKEY_LOCAL_MACHINE key.</span></span>|  
|<span data-ttu-id="44223-172">**/s**</span><span class="sxs-lookup"><span data-stu-id="44223-172">**/s**</span></span>|<span data-ttu-id="44223-173">Indica che l'archivio certificati è un archivio di sistema.</span><span class="sxs-lookup"><span data-stu-id="44223-173">Indicates that the certificate store is a system store.</span></span> <span data-ttu-id="44223-174">Se non si specifica questa opzione, l'archivio viene considerato come **StoreFile**.</span><span class="sxs-lookup"><span data-stu-id="44223-174">If you do not specify this option, the store is considered to be a **StoreFile**.</span></span>|  
|<span data-ttu-id="44223-175">**/sha1** *sha1Hash*</span><span class="sxs-lookup"><span data-stu-id="44223-175">**/sha1** *sha1Hash*</span></span>|<span data-ttu-id="44223-176">Specifica l'hash SHA1 del certificato, dell'elenco di scopi consentiti o del CRL da aggiungere, eliminare o salvare.</span><span class="sxs-lookup"><span data-stu-id="44223-176">Specifies the SHA1 hash of the certificate, CTL, or CRL to add, delete, or save.</span></span>|  
|<span data-ttu-id="44223-177">**/v**</span><span class="sxs-lookup"><span data-stu-id="44223-177">**/v**</span></span>|<span data-ttu-id="44223-178">Specifica la modalità dettagliata. Visualizza informazioni dettagliate su certificati, elenchi di scopi consentiti e CRL.</span><span class="sxs-lookup"><span data-stu-id="44223-178">Specifies verbose mode; displays detailed information about certificates, CTLs, and CRLs.</span></span> <span data-ttu-id="44223-179">Non è possibile usare questa opzione con le opzioni **/add**, **/del** o **/put**.</span><span class="sxs-lookup"><span data-stu-id="44223-179">This option cannot be used with the **/add**, **/del**, or **/put** options.</span></span>|  
|<span data-ttu-id="44223-180">**/y** *provider*</span><span class="sxs-lookup"><span data-stu-id="44223-180">**/y** *provider*</span></span>|<span data-ttu-id="44223-181">Specifica il nome del provider dell'archivio.</span><span class="sxs-lookup"><span data-stu-id="44223-181">Specifies the store provider name.</span></span>|  
|<span data-ttu-id="44223-182">**/7**</span><span class="sxs-lookup"><span data-stu-id="44223-182">**/7**</span></span>|<span data-ttu-id="44223-183">Salva l'archivio di destinazione come oggetto PKCS #7.</span><span class="sxs-lookup"><span data-stu-id="44223-183">Saves the destination store as a PKCS #7 object.</span></span>|  
|<span data-ttu-id="44223-184">**/?**</span><span class="sxs-lookup"><span data-stu-id="44223-184">**/?**</span></span>|<span data-ttu-id="44223-185">Visualizza la sintassi e le opzioni di comando dello strumento.</span><span class="sxs-lookup"><span data-stu-id="44223-185">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44223-186">Note</span><span class="sxs-lookup"><span data-stu-id="44223-186">Remarks</span></span>  
 <span data-ttu-id="44223-187">Certmgr.exe svolge le seguenti funzioni di base:</span><span class="sxs-lookup"><span data-stu-id="44223-187">Certmgr.exe performs the following basic functions:</span></span>  
  
- <span data-ttu-id="44223-188">Visualizza certificati, elenchi di scopi consentiti e CRL sulla console.</span><span class="sxs-lookup"><span data-stu-id="44223-188">Displays certificates, CTLs, and CRLs to the console.</span></span>  
  
- <span data-ttu-id="44223-189">Aggiunge certificati, elenchi di scopi consentiti ai certificati e CRL a un archivio certificati.</span><span class="sxs-lookup"><span data-stu-id="44223-189">Adds certificates, CTLs, and CRLs to a certificate store.</span></span>  
  
- <span data-ttu-id="44223-190">Elimina certificati, elenchi di scopi consentiti e CRL da un archivio certificati.</span><span class="sxs-lookup"><span data-stu-id="44223-190">Deletes certificates, CTLs, and CRLs from a certificate store.</span></span>  
  
- <span data-ttu-id="44223-191">Salva su file un certificato X.509, un elenco di scopi consentiti o un CRL da un archivio certificati.</span><span class="sxs-lookup"><span data-stu-id="44223-191">Saves an X.509 certificate, CTL, or CRL from a certificate store to a file.</span></span>  
  
 <span data-ttu-id="44223-192">Certmgr.exe funziona con due tipi di archivi certificati: **StoreFile** e archivi di sistema.</span><span class="sxs-lookup"><span data-stu-id="44223-192">Certmgr.exe works with two types of certificate stores: **StoreFile** and system store.</span></span> <span data-ttu-id="44223-193">Non è necessario specificare il tipo di archivio certificati: Certmgr.exe è infatti in grado di identificare il tipo di archivio e di eseguire le operazioni appropriate.</span><span class="sxs-lookup"><span data-stu-id="44223-193">It is not necessary to specify the type of certificate store; Certmgr.exe can identify the store type and perform the appropriate operations.</span></span>  
  
 <span data-ttu-id="44223-194">Se Certmgr.exe viene eseguito senza specificare alcuna opzione, verrà avviato lo snap-in certmgr.msc, che comprende una GUI che assisterà l'utente nell'esecuzione delle attività di gestione dei certificati disponibili anche dalla riga di comando.</span><span class="sxs-lookup"><span data-stu-id="44223-194">Running Certmgr.exe without specifying any options launches the certmgr.msc snap-in, which has a GUI that helps with the certificate management tasks that are also available from the command line.</span></span> <span data-ttu-id="44223-195">La GUI fornisce una procedura guidata di importazione che consente di copiare certificati, elenchi di scopi consentiti e CRL dal disco a un archivio certificati.</span><span class="sxs-lookup"><span data-stu-id="44223-195">The GUI provides an import wizard, which copies certificates, CTLs, and CRLs from your disk to a certificate store.</span></span>  
  
 <span data-ttu-id="44223-196">È possibile trovare i nomi degli archivi X509Certificate per i parametri `sourceStorename` e `destinationStorename` compilando ed eseguendo il codice seguente.</span><span class="sxs-lookup"><span data-stu-id="44223-196">You can find the names of X509Certificate stores for the `sourceStorename` and `destinationStorename` parameters by compiling and running the following code.</span></span>  
  
 [!code-csharp[Tools.CertMgr#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tools.certmgr/cs/storenames1.cs#1)]
 [!code-vb[Tools.CertMgr#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tools.certmgr/vb/storenames1.vb#1)]  
  
 <span data-ttu-id="44223-197">Per altre informazioni sui certificati, vedere [Utilizzo dei certificati](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="44223-197">For more information about certificates, see [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="44223-198">Esempi</span><span class="sxs-lookup"><span data-stu-id="44223-198">Examples</span></span>  
 <span data-ttu-id="44223-199">Il comando che segue visualizza un archivio di sistema predefinito denominato `my` con output dettagliato.</span><span class="sxs-lookup"><span data-stu-id="44223-199">The following command displays a default system store called `my` with verbose output.</span></span>  
  
```console  
certmgr /v /s my  
```  
  
 <span data-ttu-id="44223-200">Il comando che segue aggiunge tutti i certificati contenuti in un file denominato `myFile.ext` in un nuovo file denominato `newFile.ext`.</span><span class="sxs-lookup"><span data-stu-id="44223-200">The following command adds all the certificates in a file called `myFile.ext` to a new file called `newFile.ext`.</span></span>  
  
```console  
certmgr /add /all /c myFile.ext newFile.ext  
```  
  
 <span data-ttu-id="44223-201">Il comando che segue aggiunge il certificato contenuto in un file denominato `testcert.cer` all'archivio di sistema `my`.</span><span class="sxs-lookup"><span data-stu-id="44223-201">The following command adds the certificate in a file named `testcert.cer` to the `my` system store.</span></span>  
  
```console  
certmgr /add /c testcert.cer /s my  
```  
  
 <span data-ttu-id="44223-202">Il comando che segue aggiunge il certificato contenuto in un file denominato `TrustedCert.cer` all'archivio certificati radice.</span><span class="sxs-lookup"><span data-stu-id="44223-202">The following command adds the certificate in a file named `TrustedCert.cer` to the root certificate store.</span></span>  
  
```console  
certmgr /c /add TrustedCert.cer /s root  
```  
  
 <span data-ttu-id="44223-203">Il comando che segue salva un certificato con il nome comune `myCert` contenuto nell'archivio di sistema `my` in un file denominato `newCert.cer`.</span><span class="sxs-lookup"><span data-stu-id="44223-203">The following command saves a certificate with the common name `myCert` in the `my` system store to a file called `newCert.cer`.</span></span>  
  
```console  
certmgr /add /c /n myCert /s my newCert.cer  
```  
  
 <span data-ttu-id="44223-204">Il comando che segue elimina tutti gli elenchi di scopi consentiti contenuti nell'archivio di sistema `my` e salva l'archivio ottenuto in un file denominato `newStore.str`.</span><span class="sxs-lookup"><span data-stu-id="44223-204">The following command deletes all CTLs in the `my` system store and saves the resulting store to a file called `newStore.str`.</span></span>  
  
```console  
certmgr /del /all /ctl /s my newStore.str  
```  
  
 <span data-ttu-id="44223-205">Il comando che segue salva nel file `my` un certificato contenuto nell'archivio di sistema `newFile`.</span><span class="sxs-lookup"><span data-stu-id="44223-205">The following command saves a certificate in the `my` system store in the file `newFile`.</span></span> <span data-ttu-id="44223-206">Verrà chiesto di inserire il numero del certificato presente in `my` per inserirlo in `newFile`.</span><span class="sxs-lookup"><span data-stu-id="44223-206">You will be prompted to enter the certificate number from `my` to put in `newFile`.</span></span>  
  
```console  
certmgr /put /c /s my newFile  
```  
  
## <a name="see-also"></a><span data-ttu-id="44223-207">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="44223-207">See also</span></span>

- [<span data-ttu-id="44223-208">Strumenti</span><span class="sxs-lookup"><span data-stu-id="44223-208">Tools</span></span>](../../../docs/framework/tools/index.md)
- <span data-ttu-id="44223-209">[Makecert.exe (Certificate Creation Tool)](/windows/desktop/SecCrypto/makecert) (Makecert.exe, strumento di creazione certificati)</span><span class="sxs-lookup"><span data-stu-id="44223-209">[Makecert.exe (Certificate Creation Tool)](/windows/desktop/SecCrypto/makecert)</span></span>
- [<span data-ttu-id="44223-210">Prompt dei comandi</span><span class="sxs-lookup"><span data-stu-id="44223-210">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
