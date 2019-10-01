---
title: 'Procedura: Compilare un assembly su più file'
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- Al.exe
- command-line compilers
- assembly manifest, multifile assemblies
- assemblies [.NET Framework], compiling
- Assembly Linker
- code modules
- multifile assemblies
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 261c5583-8a76-412d-bda7-9b8ee3b131e5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9b95d686529da83a5a52edb80219874530212dcc
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991263"
---
# <a name="how-to-build-a-multifile-assembly"></a><span data-ttu-id="d1b86-102">Procedura: Compilare un assembly su più file</span><span class="sxs-lookup"><span data-stu-id="d1b86-102">How to: Build a multifile assembly</span></span>

<span data-ttu-id="d1b86-103">In questo articolo viene illustrato come creare un assembly su più file e viene visualizzato il codice che illustra ogni passaggio della procedura.</span><span class="sxs-lookup"><span data-stu-id="d1b86-103">This article explains how to create a multifile assembly and provides code that illustrates each step in the procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="d1b86-104">L'IDE di Visual Studio per C# e Visual Basic può essere utilizzato esclusivamente per creare assembly su singolo file.</span><span class="sxs-lookup"><span data-stu-id="d1b86-104">The Visual Studio IDE for C# and Visual Basic can only be used to create single-file assemblies.</span></span> <span data-ttu-id="d1b86-105">Per creare assembly su più file, è necessario utilizzare i compilatori della riga di comando o Visual Studio con Visual C++.</span><span class="sxs-lookup"><span data-stu-id="d1b86-105">If you want to create multifile assemblies, you must use the command-line compilers or Visual Studio with Visual C++.</span></span> <span data-ttu-id="d1b86-106">Gli assembly su più file sono supportati solo da .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d1b86-106">Multifile assemblies are supported by .NET Framework only.</span></span>

## <a name="create-a-multifile-assembly"></a><span data-ttu-id="d1b86-107">Creare un assembly su più file</span><span class="sxs-lookup"><span data-stu-id="d1b86-107">Create a multifile assembly</span></span>

1. <span data-ttu-id="d1b86-108">Compilare in moduli di codice tutti i file contenenti spazi dei nomi a cui fanno riferimento altri moduli dell'assembly.</span><span class="sxs-lookup"><span data-stu-id="d1b86-108">Compile all files that contain namespaces referenced by other modules in the assembly into code modules.</span></span> <span data-ttu-id="d1b86-109">L'estensione predefinita per i moduli di codice è *. netmodule*.</span><span class="sxs-lookup"><span data-stu-id="d1b86-109">The default extension for code modules is *.netmodule*.</span></span>

   <span data-ttu-id="d1b86-110">Si supponga, ad esempio, che il file `Stringer` abbia uno spazio dei nomi denominato `myStringer`, che include una classe denominata `Stringer`.</span><span class="sxs-lookup"><span data-stu-id="d1b86-110">For example, let's say the `Stringer` file has a namespace called `myStringer`, which includes a class called `Stringer`.</span></span> <span data-ttu-id="d1b86-111">Nella classe `Stringer` è disponibile un metodo denominato `StringerMethod`, che consente di scrivere una singola riga nella console.</span><span class="sxs-lookup"><span data-stu-id="d1b86-111">The `Stringer` class contains a method called `StringerMethod` that writes a single line to the console.</span></span>

   ```cpp
   // Assembly building example in the .NET Framework.
   using namespace System;

   namespace myStringer
   {
       public ref class Stringer
       {
       public:
           void StringerMethod()
           {
               System::Console::WriteLine("This is a line from StringerMethod.");
           }
       };
   }
   ```

   ```csharp
   // Assembly building example in the .NET Framework.
   using System;

   namespace myStringer
   {
       public class Stringer
       {
           public void StringerMethod()
           {
               System.Console.WriteLine("This is a line from StringerMethod.");
           }
       }
   }
   ```

   ```vb
   ' Assembly building example in the .NET Framework.
   Imports System

   Namespace myStringer
       Public Class Stringer
           Public Sub StringerMethod()
               System.Console.WriteLine("This is a line from StringerMethod.")
           End Sub
       End Class
   End Namespace
   ```

2. <span data-ttu-id="d1b86-112">Per compilare il codice, utilizzare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="d1b86-112">Use the following command to compile this code:</span></span>

   ```cpp
   cl /clr:pure /LN Stringer.cpp
   ```

   ```csharp
   csc /t:module Stringer.cs
   ```

   ```vb
   vbc /t:module Stringer.vb
   ```

   <span data-ttu-id="d1b86-113">Specificando il parametro *module* con l'opzione del compilatore **/t:** si indica che è necessario compilare il file come modulo anziché come assembly.</span><span class="sxs-lookup"><span data-stu-id="d1b86-113">Specifying the *module* parameter with the **/t:** compiler option indicates that the file should be compiled as a module rather than as an assembly.</span></span> <span data-ttu-id="d1b86-114">Il compilatore produce un modulo denominato *Stringer. netmodule*, che può essere aggiunto a un assembly.</span><span class="sxs-lookup"><span data-stu-id="d1b86-114">The compiler produces a module called *Stringer.netmodule*, which can be added to an assembly.</span></span>

3. <span data-ttu-id="d1b86-115">Compilare tutti gli altri moduli, utilizzando le opzioni di compilatore necessarie per indicare gli altri moduli a cui si fa riferimento nel codice.</span><span class="sxs-lookup"><span data-stu-id="d1b86-115">Compile all other modules, using the necessary compiler options to indicate the other modules that are referenced in the code.</span></span> <span data-ttu-id="d1b86-116">Questo passaggio usa l'opzione del compilatore **/addmodule**.</span><span class="sxs-lookup"><span data-stu-id="d1b86-116">This step uses the **/addmodule** compiler option.</span></span>

   <span data-ttu-id="d1b86-117">Nell'esempio seguente, un modulo di codice denominato *client* dispone di un metodo `Main` del punto di ingresso che fa riferimento a un metodo nel modulo *Stringer. dll* creato nel passaggio 1.</span><span class="sxs-lookup"><span data-stu-id="d1b86-117">In the following example, a code module called *Client* has an entry point `Main` method that references a method in the *Stringer.dll* module created in step 1.</span></span>

   ```cpp
   #using "Stringer.netmodule"

   using namespace System;
   using namespace myStringer; //The namespace created in Stringer.netmodule.

   ref class MainClientApp
   {
       // Static method Main is the entry point method.
   public:
       static void Main()
       {
           Stringer^ myStringInstance = gcnew Stringer();
           Console::WriteLine("Client code executes");
           myStringInstance->StringerMethod();
       }
   };

   int main()
   {
       MainClientApp::Main();
   }
   ```

   ```csharp
   using System;
   using myStringer;

   class MainClientApp
   {
       // Static method Main is the entry point method.
       public static void Main()
       {
           Stringer myStringInstance = new Stringer();
           Console.WriteLine("Client code executes");
           myStringInstance.StringerMethod();
       }
   }
   ```

   ```vb
   Imports System
   Imports myStringer

   Class MainClientApp
       ' Static method Main is the entry point method.
       Public Shared Sub Main()
           Dim myStringInstance As New Stringer()
           Console.WriteLine("Client code executes")
           myStringInstance.StringerMethod()
       End Sub
   End Class
   ```

4. <span data-ttu-id="d1b86-118">Per compilare il codice, utilizzare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="d1b86-118">Use the following command to compile this code:</span></span>

   ```cpp
   cl /clr:pure /FUStringer.netmodule /LN Client.cpp
   ```

   ```csharp
   csc /addmodule:Stringer.netmodule /t:module Client.cs
   ```

   ```vb
   vbc /addmodule:Stringer.netmodule /t:module Client.vb
   ```

   <span data-ttu-id="d1b86-119">Specificare l'opzione **/t:module** poiché il modulo verrà aggiunto a un assembly in un passaggio successivo.</span><span class="sxs-lookup"><span data-stu-id="d1b86-119">Specify the **/t:module** option because this module will be added to an assembly in a future step.</span></span> <span data-ttu-id="d1b86-120">Specificare l'opzione **/addmodule** perché il codice nel *client* fa riferimento a uno spazio dei nomi creato dal codice in *Stringer. netmodule*.</span><span class="sxs-lookup"><span data-stu-id="d1b86-120">Specify the **/addmodule** option because the code in *Client* references a namespace created by the code in *Stringer.netmodule*.</span></span> <span data-ttu-id="d1b86-121">Il compilatore produce un modulo denominato *client. netmodule* che contiene un riferimento a un altro modulo, *Stringer.* netmodule.</span><span class="sxs-lookup"><span data-stu-id="d1b86-121">The compiler produces a module called *Client.netmodule* that contains a reference to another module, *Stringer.netmodule*.</span></span>

   > [!NOTE]
   > <span data-ttu-id="d1b86-122">Nei compilatori di C# e di Visual Basic viene supportata la creazione diretta di assembly su più file utilizzando le due diverse sintassi descritte di seguito.</span><span class="sxs-lookup"><span data-stu-id="d1b86-122">The C# and Visual Basic compilers support directly creating multifile assemblies using the following two different syntaxes.</span></span>
   >
   > <span data-ttu-id="d1b86-123">Un assembly su due file viene creato da due compilazioni:</span><span class="sxs-lookup"><span data-stu-id="d1b86-123">Two compilations create a two-file assembly:</span></span>
   >
   >   ```cpp
   >   cl /clr:pure /LN Stringer.cpp
   >   cl /clr:pure Client.cpp /link /ASSEMBLYMODULE:Stringer.netmodule
   >   ```
   >
   >   ```csharp
   >   csc /t:module Stringer.cs
   >   csc Client.cs /addmodule:Stringer.netmodule
   >   ```
   >
   >   ```vb
   >   vbc /t:module Stringer.vb
   >   vbc Client.vb /addmodule:Stringer.netmodule
   >   ```
   >
   > <span data-ttu-id="d1b86-124">Un assembly su due file viene creato da una compilazione:</span><span class="sxs-lookup"><span data-stu-id="d1b86-124">One compilation creates a two-file assembly:</span></span>
   >
   >   ```cpp
   >   cl /clr:pure /LN Stringer.cpp
   >   cl /clr:pure Client.cpp /link /ASSEMBLYMODULE:Stringer.netmodule
   >   ```
   >
   >   ```csharp
   >   csc /out:Client.exe Client.cs /out:Stringer.netmodule Stringer.cs
   >   ```
   >
   >   ```vb
   >   vbc /out:Client.exe Client.vb /out:Stringer.netmodule Stringer.vb
   >   ```

5. <span data-ttu-id="d1b86-125">Usare [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) per creare il file di output contenente il manifesto dell'assembly.</span><span class="sxs-lookup"><span data-stu-id="d1b86-125">Use the [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to create the output file that contains the assembly manifest.</span></span> <span data-ttu-id="d1b86-126">In questo file sono contenute informazioni di riferimento per tutti i moduli o le risorse che fanno parte dell'assembly.</span><span class="sxs-lookup"><span data-stu-id="d1b86-126">This file contains reference information for all modules or resources that are part of the assembly.</span></span>

    <span data-ttu-id="d1b86-127">Al prompt dei comandi digitare il seguente comando:</span><span class="sxs-lookup"><span data-stu-id="d1b86-127">At the command prompt, type the following command:</span></span>

    <span data-ttu-id="d1b86-128">**al** \<*nome modulo*> \<*nome modulo*> …</span><span class="sxs-lookup"><span data-stu-id="d1b86-128">**al** \<*module name*> \<*module name*> …</span></span> <span data-ttu-id="d1b86-129">**/main:** \<*nome metodo*>  **/out:** \<*nome file*>  **/target:** \<*tipo file di assembly*></span><span class="sxs-lookup"><span data-stu-id="d1b86-129">**/main:**\<*method name*> **/out:**\<*file name*> **/target:**\<*assembly file type*></span></span>

    <span data-ttu-id="d1b86-130">In questo comando gli argomenti *nome modulo* specificano il nome di ogni modulo da includere nell'assembly.</span><span class="sxs-lookup"><span data-stu-id="d1b86-130">In this command, the *module name* arguments specify the name of each module to include in the assembly.</span></span> <span data-ttu-id="d1b86-131">L'opzione **/main:** specifica il nome del metodo che corrisponde al punto di ingresso dell'assembly.</span><span class="sxs-lookup"><span data-stu-id="d1b86-131">The **/main:** option specifies the method name that is the assembly's entry point.</span></span> <span data-ttu-id="d1b86-132">L'opzione **/out:** specifica il nome del file di output che contiene i metadati dell'assembly.</span><span class="sxs-lookup"><span data-stu-id="d1b86-132">The **/out:** option specifies the name of the output file, which contains assembly metadata.</span></span> <span data-ttu-id="d1b86-133">L'opzione **/target:** specifica che l'assembly è un file eseguibile dell'applicazione console (*exe*), un file eseguibile di Windows (con*estensione win*) o un file di libreria (con*estensione LIB*).</span><span class="sxs-lookup"><span data-stu-id="d1b86-133">The **/target:** option specifies that the assembly is a console application executable (*.exe*) file, a Windows executable (*.win*) file, or a library (*.lib*) file.</span></span>

    <span data-ttu-id="d1b86-134">Nell'esempio seguente, *al. exe* crea un assembly che è un eseguibile dell'applicazione console denominato *myAssembly. exe*.</span><span class="sxs-lookup"><span data-stu-id="d1b86-134">In the following example, *Al.exe* creates an assembly that is a console application executable called *myAssembly.exe*.</span></span> <span data-ttu-id="d1b86-135">L'applicazione è costituita da due moduli denominati *client. netmodule* e *Stringer. netmodule*e il file eseguibile denominato *myAssembly. exe*, che contiene solo i metadati dell'assembly.</span><span class="sxs-lookup"><span data-stu-id="d1b86-135">The application consists of two modules called *Client.netmodule* and *Stringer.netmodule*, and the executable file called *myAssembly.exe*, which contains only assembly metadata.</span></span> <span data-ttu-id="d1b86-136">Il punto di ingresso dell'assembly è il `Main` metodo nella classe `MainClientApp`, disponibile in *client. dll*.</span><span class="sxs-lookup"><span data-stu-id="d1b86-136">The entry point of the assembly is the `Main` method in the class `MainClientApp`, which is located in *Client.dll*.</span></span>

    ```cmd
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe
    ```

    <span data-ttu-id="d1b86-137">È possibile usare [MSIL Disassembler (Ildasm.exe)](../tools/ildasm-exe-il-disassembler.md) per esaminare i contenuti di un assembly o determinare se un file è un assembly o un modulo.</span><span class="sxs-lookup"><span data-stu-id="d1b86-137">You can use the [MSIL Disassembler (Ildasm.exe)](../tools/ildasm-exe-il-disassembler.md) to examine the contents of an assembly, or determine whether a file is an assembly or a module.</span></span>

## <a name="see-also"></a><span data-ttu-id="d1b86-138">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d1b86-138">See also</span></span>

- [<span data-ttu-id="d1b86-139">Creazione di assembly</span><span class="sxs-lookup"><span data-stu-id="d1b86-139">Create assemblies</span></span>](../../standard/assembly/create.md)
- [<span data-ttu-id="d1b86-140">Procedura: Visualizza contenuto assembly</span><span class="sxs-lookup"><span data-stu-id="d1b86-140">How to: View assembly contents</span></span>](../../standard/assembly/view-contents.md)
- [<span data-ttu-id="d1b86-141">Come il runtime individua gli assembly</span><span class="sxs-lookup"><span data-stu-id="d1b86-141">How the runtime locates assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="d1b86-142">Assembly su più file</span><span class="sxs-lookup"><span data-stu-id="d1b86-142">Multifile assemblies</span></span>](multifile-assemblies.md)