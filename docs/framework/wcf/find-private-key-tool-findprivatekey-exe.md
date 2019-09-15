---
title: Ricerca dello strumento di chiave privata (FindPrivateKey.exe)
ms.date: 09/11/2017
ms.assetid: b8846a95-3fcc-4e8c-b9c0-128d975a6307
ms.openlocfilehash: 316f55b93cf4d867b99878bf483b73cb3f09ad04
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990344"
---
# <a name="find-private-key-tool-findprivatekeyexe"></a><span data-ttu-id="b3cdf-102">Ricerca dello strumento di chiave privata (FindPrivateKey.exe)</span><span class="sxs-lookup"><span data-stu-id="b3cdf-102">Find Private Key Tool (FindPrivateKey.exe)</span></span>

<span data-ttu-id="b3cdf-103">Questo strumento da riga di comando può essere usato per recuperare una chiave privata da un archivio certificati.</span><span class="sxs-lookup"><span data-stu-id="b3cdf-103">This command-line tool can be used to retrieve a private key from a certificate store.</span></span> <span data-ttu-id="b3cdf-104">Ad esempio, è possibile usare *FindPrivateKey. exe* per trovare il percorso e il nome del file di chiave privata associato a un certificato X. 509 specifico nell'archivio certificati.</span><span class="sxs-lookup"><span data-stu-id="b3cdf-104">For example, *FindPrivateKey.exe* can be used to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b3cdf-105">Lo strumento FindPrivateKey viene fornito come esempio WCF.</span><span class="sxs-lookup"><span data-stu-id="b3cdf-105">The FindPrivateKey tool is shipped as a WCF sample.</span></span> <span data-ttu-id="b3cdf-106">Per ulteriori informazioni su dove trovare l'esempio e su come compilarlo, vedere [FindPrivateKey](./samples/findprivatekey.md).</span><span class="sxs-lookup"><span data-stu-id="b3cdf-106">For more information about where to find the sample and how to build it, see [FindPrivateKey](./samples/findprivatekey.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="b3cdf-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="b3cdf-107">Syntax</span></span>

```console
FindPrivateKey<storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

## <a name="remarks"></a><span data-ttu-id="b3cdf-108">Note</span><span class="sxs-lookup"><span data-stu-id="b3cdf-108">Remarks</span></span>

<span data-ttu-id="b3cdf-109">Nelle tabelle seguenti vengono descritti gli argomenti e le opzioni che possono essere usati con lo strumento di Ricerca della Chiave Privata (FindPrivateKey.exe).</span><span class="sxs-lookup"><span data-stu-id="b3cdf-109">The following tables describe the arguments and the options that can be used with the Find Private Key tool (FindPrivateKey.exe).</span></span>

|<span data-ttu-id="b3cdf-110">Argomento</span><span class="sxs-lookup"><span data-stu-id="b3cdf-110">Argument</span></span>|<span data-ttu-id="b3cdf-111">Descrizione</span><span class="sxs-lookup"><span data-stu-id="b3cdf-111">Description</span></span>|
|--------------|-----------------|
|`storeName`|<span data-ttu-id="b3cdf-112">Nome dell'archivio certificati.</span><span class="sxs-lookup"><span data-stu-id="b3cdf-112">Name of the certificate store.</span></span>|
|`storeLocation`|<span data-ttu-id="b3cdf-113">Percorso dell'archivio certificati.</span><span class="sxs-lookup"><span data-stu-id="b3cdf-113">The location of the certificate store.</span></span>|

|<span data-ttu-id="b3cdf-114">Opzione</span><span class="sxs-lookup"><span data-stu-id="b3cdf-114">Option</span></span>|<span data-ttu-id="b3cdf-115">Descrizione</span><span class="sxs-lookup"><span data-stu-id="b3cdf-115">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="b3cdf-116">`/n <` *subjectName* `>`</span><span class="sxs-lookup"><span data-stu-id="b3cdf-116">`/n <` *subjectName* `>`</span></span>|<span data-ttu-id="b3cdf-117">Specifica il nome dell’oggetto del certificato.</span><span class="sxs-lookup"><span data-stu-id="b3cdf-117">Specifies the subject name of the certificate.</span></span>|
|<span data-ttu-id="b3cdf-118">`/t <` *thumbprint* `>`</span><span class="sxs-lookup"><span data-stu-id="b3cdf-118">`/t <` *thumbprint* `>`</span></span>|<span data-ttu-id="b3cdf-119">Specifica l'identificazione digitale del certificato.</span><span class="sxs-lookup"><span data-stu-id="b3cdf-119">Specifies the thumbprint of the certificate.</span></span> <span data-ttu-id="b3cdf-120">Usare Certmgr.exe per recuperare l'identificazione digitale del certificato.</span><span class="sxs-lookup"><span data-stu-id="b3cdf-120">Use Certmgr.exe to retrieve the thumbprint of the certificate.</span></span>|
|`/f`|<span data-ttu-id="b3cdf-121">Restituisce soltanto il nome file.</span><span class="sxs-lookup"><span data-stu-id="b3cdf-121">Outputs the file name only.</span></span>|
|`/d`|<span data-ttu-id="b3cdf-122">Restituisce soltanto la directory.</span><span class="sxs-lookup"><span data-stu-id="b3cdf-122">Outputs the directory only.</span></span>|
|`/a`|<span data-ttu-id="b3cdf-123">Restituisce il nome file assoluto.</span><span class="sxs-lookup"><span data-stu-id="b3cdf-123">Outputs the absolute file name.</span></span>|

## <a name="examples"></a><span data-ttu-id="b3cdf-124">Esempi</span><span class="sxs-lookup"><span data-stu-id="b3cdf-124">Examples</span></span>

<span data-ttu-id="b3cdf-125">Il comando seguente recupera la chiave privata per John Doe:</span><span class="sxs-lookup"><span data-stu-id="b3cdf-125">The following command retrieves the private key for John Doe:</span></span>

```console
FindPrivateKey My CurrentUser -n "CN=John Doe"
```

<span data-ttu-id="b3cdf-126">Il comando seguente recupera la chiave privata per il computer locale:</span><span class="sxs-lookup"><span data-stu-id="b3cdf-126">The following command retrieves the private key for the local machine:</span></span>

```console
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –a
```
