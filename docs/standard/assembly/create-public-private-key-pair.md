---
title: 'Procedura: Creare una coppia di chiavi pubblica/privata'
ms.date: 08/20/2019
helpviewer_keywords:
- key pairs for strong-named assemblies
- signing assemblies
- assemblies [.NET Framework], signing
- cryptographic key pairs
- snk files (key pair files)
- public-private key pairs
- .snk files
- strong-named assemblies, key pairs
ms.assetid: 05026813-f3bd-4d7c-9e0b-fc588eb3d114
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 62c38494e29541bd490d69ccc8de485217b9514a
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991694"
---
# <a name="how-to-create-a-public-private-key-pair"></a><span data-ttu-id="fe413-102">Procedura: Creare una coppia di chiavi pubblica/privata</span><span class="sxs-lookup"><span data-stu-id="fe413-102">How to: Create a public-private key pair</span></span>

<span data-ttu-id="fe413-103">Per firmare un assembly con un nome sicuro, è necessario disporre di una coppia di chiavi pubblica/privata.</span><span class="sxs-lookup"><span data-stu-id="fe413-103">To sign an assembly with a strong name, you must have a public/private key pair.</span></span> <span data-ttu-id="fe413-104">Questa coppia di chiavi crittografiche, pubblica e privata, viene usata durante la compilazione per creare un assembly con nome sicuro.</span><span class="sxs-lookup"><span data-stu-id="fe413-104">This public and private cryptographic key pair is used during compilation to create a strong-named assembly.</span></span> <span data-ttu-id="fe413-105">È possibile creare una coppia di chiavi usando lo [strumento Nome sicuro (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="fe413-105">You can create a key pair using the [Strong Name tool (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md).</span></span> <span data-ttu-id="fe413-106">I file delle coppie di chiavi hanno in genere un'estensione *SNK* .</span><span class="sxs-lookup"><span data-stu-id="fe413-106">Key pair files usually have an *.snk* extension.</span></span>

> [!NOTE]
> <span data-ttu-id="fe413-107">In Visual Studio, le C# pagine delle proprietà del progetto e Visual Basic includono una scheda **firma** che consente di selezionare i file di chiave esistenti o di generare nuovi file di chiave senza utilizzare *sn. exe*.</span><span class="sxs-lookup"><span data-stu-id="fe413-107">In Visual Studio, the C# and Visual Basic project property pages include a **Signing** tab that enables you to select existing key files or to generate new key files without using *Sn.exe*.</span></span> <span data-ttu-id="fe413-108">In Visual C++ è possibile specificare il percorso di un file di chiave esistente nella pagina delle proprietà **Avanzate** nella sezione **Linker** della sezione **Proprietà di configurazione** della finestra **Pagine delle proprietà**.</span><span class="sxs-lookup"><span data-stu-id="fe413-108">In Visual C++, you can specify the location of an existing key file in the **Advanced** property page in the **Linker** section of the **Configuration Properties** section of the **Property Pages** window.</span></span> <span data-ttu-id="fe413-109">L'uso dell'attributo <xref:System.Reflection.AssemblyKeyFileAttribute> per identificare le coppie di file di chiave è diventato obsoleto a partire da Visual Studio 2005.</span><span class="sxs-lookup"><span data-stu-id="fe413-109">The use of the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute to identify key file pairs was made obsolete beginning with Visual Studio 2005.</span></span>

## <a name="create-a-key-pair"></a><span data-ttu-id="fe413-110">Creare una coppia di chiavi</span><span class="sxs-lookup"><span data-stu-id="fe413-110">Create a key pair</span></span>

<span data-ttu-id="fe413-111">Per creare una coppia di chiavi, al prompt dei comandi digitare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="fe413-111">To create a key pair, at a command prompt, type the following command:</span></span>

<span data-ttu-id="fe413-112">**sn –k** \<*nome file*></span><span class="sxs-lookup"><span data-stu-id="fe413-112">**sn –k** \<*file name*></span></span>

<span data-ttu-id="fe413-113">In questo comando *nome file* corrisponde al nome del file di output contenente la coppia di chiavi.</span><span class="sxs-lookup"><span data-stu-id="fe413-113">In this command, *file name* is the name of the output file containing the key pair.</span></span>

<span data-ttu-id="fe413-114">Nell'esempio seguente viene creata una coppia di chiavi denominata *sgKey. snk*.</span><span class="sxs-lookup"><span data-stu-id="fe413-114">The following example creates a key pair called *sgKey.snk*.</span></span>

```cmd
sn -k sgKey.snk
```

<span data-ttu-id="fe413-115">Se si desidera ritardare la firma di un assembly e si controlla l'intera coppia di chiavi (situazione improbabile al di fuori degli scenari di testing), è possibile usare i comandi seguenti per generare una coppia di chiavi e quindi estrarre da tale coppia la chiave pubblica, che viene salvata in un file distinto.</span><span class="sxs-lookup"><span data-stu-id="fe413-115">If you intend to delay sign an assembly and you control the whole key pair (which is unlikely outside test scenarios), you can use the following commands to generate a key pair and then extract the public key from it into a separate file.</span></span> <span data-ttu-id="fe413-116">Creare innanzitutto la coppia di chiavi:</span><span class="sxs-lookup"><span data-stu-id="fe413-116">First, create the key pair:</span></span>

```cmd
sn -k keypair.snk
```

<span data-ttu-id="fe413-117">Estrarre quindi la chiave pubblica dalla coppia di chiavi e copiarla in un file distinto:</span><span class="sxs-lookup"><span data-stu-id="fe413-117">Next, extract the public key from the key pair and copy it to a separate file:</span></span>

```cmd
sn -p keypair.snk public.snk
```

<span data-ttu-id="fe413-118">Dopo avere creato la coppia di chiavi, è necessario salvare il file in una posizione accessibile agli strumenti di firma con nome sicuro.</span><span class="sxs-lookup"><span data-stu-id="fe413-118">Once you create the key pair, you must put the file where the strong name signing tools can find it.</span></span>

<span data-ttu-id="fe413-119">Quando firma un assembly con un nome sicuro, [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) cerca il file della chiave relativo alla directory corrente e alla directory di output.</span><span class="sxs-lookup"><span data-stu-id="fe413-119">When signing an assembly with a strong name, the [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) looks for the key file relative to the current directory and to the output directory.</span></span> <span data-ttu-id="fe413-120">Se si utilizzano i compilatori della riga di comando, è sufficiente copiare la chiave nella directory corrente contenente i moduli di codice.</span><span class="sxs-lookup"><span data-stu-id="fe413-120">When using command-line compilers, you can simply copy the key to the current directory containing your code modules.</span></span>

<span data-ttu-id="fe413-121">Se si usa una versione precedente di Visual Studio in cui non è disponibile una scheda **Firma** nelle proprietà del progetto, il percorso del file di chiave consigliato è la directory del progetto con l'attributo di file specificato come segue:</span><span class="sxs-lookup"><span data-stu-id="fe413-121">If you are using an earlier version of Visual Studio that does not have a **Signing** tab in the project properties, the recommended key file location is the project directory with the file attribute specified as follows:</span></span>

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

## <a name="see-also"></a><span data-ttu-id="fe413-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="fe413-122">See also</span></span>

- [<span data-ttu-id="fe413-123">Creazione e utilizzo di assembly con nome sicuro</span><span class="sxs-lookup"><span data-stu-id="fe413-123">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)