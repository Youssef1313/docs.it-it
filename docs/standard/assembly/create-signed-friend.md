---
title: 'Procedura: Crea assembly Friend firmati'
ms.date: 08/19/2019
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
dev_langs:
- csharp
- vb
ms.openlocfilehash: 19c301c6b96e1070447401af9105fba2e0f0837f
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973362"
---
# <a name="how-to-create-signed-friend-assemblies"></a><span data-ttu-id="3f06c-102">Procedura: Crea assembly Friend firmati</span><span class="sxs-lookup"><span data-stu-id="3f06c-102">How to: Create signed friend assemblies</span></span>
<span data-ttu-id="3f06c-103">In questo esempio viene illustrato come usare assembly Friend e assembly con nomi sicuri.</span><span class="sxs-lookup"><span data-stu-id="3f06c-103">This example shows how to use friend assemblies with assemblies that have strong names.</span></span> <span data-ttu-id="3f06c-104">È necessario che entrambi i tipi di assembly abbiano un nome sicuro.</span><span class="sxs-lookup"><span data-stu-id="3f06c-104">Both assemblies must be strong named.</span></span> <span data-ttu-id="3f06c-105">Gli assembly in questo esempio usano le stesse chiavi. È comunque possibile usare chiavi diverse per i due assembly.</span><span class="sxs-lookup"><span data-stu-id="3f06c-105">Although both assemblies in this example use the same keys, you could use different keys for two assemblies.</span></span>  
  
## <a name="create-a-signed-assembly-and-a-friend-assembly"></a><span data-ttu-id="3f06c-106">Creare un assembly firmato e un assembly Friend</span><span class="sxs-lookup"><span data-stu-id="3f06c-106">Create a signed assembly and a friend assembly</span></span>  
  
1. <span data-ttu-id="3f06c-107">Aprire un prompt dei comandi.</span><span class="sxs-lookup"><span data-stu-id="3f06c-107">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="3f06c-108">Eseguire la sequenza di comandi seguente con lo strumento Nome sicuro per generare un keyfile e per visualizzare la relativa chiave pubblica.</span><span class="sxs-lookup"><span data-stu-id="3f06c-108">Use the following sequence of commands with the Strong Name tool to generate a keyfile and to display its public key.</span></span> <span data-ttu-id="3f06c-109">Per ulteriori informazioni, vedere [sn. exe (strumento nome sicuro)](../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="3f06c-109">For more information, see [Sn.exe (Strong Name tool)](../../framework/tools/sn-exe-strong-name-tool.md).</span></span>  
  
    1. <span data-ttu-id="3f06c-110">Generare una chiave con nome sicuro per questo esempio e archiviarla nel file *FriendAssemblies. snk*:</span><span class="sxs-lookup"><span data-stu-id="3f06c-110">Generate a strong-name key for this example and store it in the file *FriendAssemblies.snk*:</span></span>  
  
         `sn -k FriendAssemblies.snk`  
  
    2. <span data-ttu-id="3f06c-111">Estrarre la chiave pubblica da *FriendAssemblies. snk* e inserirla in *FriendAssemblies. PublicKey*:</span><span class="sxs-lookup"><span data-stu-id="3f06c-111">Extract the public key from *FriendAssemblies.snk* and put it into *FriendAssemblies.publickey*:</span></span>  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3. <span data-ttu-id="3f06c-112">Visualizzare la chiave pubblica archiviata nel file *FriendAssemblies. PublicKey*:</span><span class="sxs-lookup"><span data-stu-id="3f06c-112">Display the public key stored in the file *FriendAssemblies.publickey*:</span></span>  
  
         `sn -tp FriendAssemblies.publickey`  
  
3. <span data-ttu-id="3f06c-113">Creare un C# file o Visual Basic denominato *friend_signed_A* contenente il codice seguente.</span><span class="sxs-lookup"><span data-stu-id="3f06c-113">Create a C# or Visual Basic file named *friend_signed_A* that contains the following code.</span></span> <span data-ttu-id="3f06c-114">Il codice usa l' <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attributo per dichiarare *friend_signed_B* come assembly Friend.</span><span class="sxs-lookup"><span data-stu-id="3f06c-114">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare *friend_signed_B* as a friend assembly.</span></span>  
   
   <span data-ttu-id="3f06c-115">Ogni volta che viene eseguito, lo strumento Nome sicuro genera una chiave pubblica nuova.</span><span class="sxs-lookup"><span data-stu-id="3f06c-115">The Strong Name tool generates a new public key every time it runs.</span></span> <span data-ttu-id="3f06c-116">È pertanto necessario sostituire la chiave pubblica nel codice seguente con la chiave pubblica appena generata, come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="3f06c-116">Therefore, you must replace the public key in the following code with the public key you just generated, as shown in the following example.</span></span>  
   
   ```csharp  
   // friend_signed_A.cs  
   // Compile with:   
   // csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   using System.Runtime.CompilerServices;  
   
   [assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")]  
   class Class1  
   {  
       public void Test()  
       {  
           System.Console.WriteLine("Class1.Test");  
           System.Console.ReadLine();  
       }  
   }  
   ```  
   
   ```vb  
   ' friend_signed_A.vb  
   ' Compile with:   
   ' Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   Imports System.Runtime.CompilerServices  
   
   <Assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")>   
   Public Class Class1  
       Public Sub Test()  
           System.Console.WriteLine("Class1.Test")  
           System.Console.ReadLine()  
       End Sub  
   End Class  
   ```  
   
4. <span data-ttu-id="3f06c-117">Compilare e firmare *friend_signed_A* usando il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="3f06c-117">Compile and sign *friend_signed_A* by using the following command.</span></span>  
   
   ```csharp
   csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   ```  
   
   ```vb
   Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   ```  
   
5. <span data-ttu-id="3f06c-118">Creare un C# file o Visual Basic denominato *friend_signed_B* contenente il codice seguente.</span><span class="sxs-lookup"><span data-stu-id="3f06c-118">Create a C# or Visual Basic file named *friend_signed_B* that contains the following code.</span></span> <span data-ttu-id="3f06c-119">Poiché *friend_signed_A* specifica *friend_signed_B* come assembly Friend, il codice in *friend_signed_B* può `internal` accedere a (C#) o `Friend` (Visual Basic) i tipi e i membri da *friend_signed_A*.</span><span class="sxs-lookup"><span data-stu-id="3f06c-119">Because *friend_signed_A* specifies *friend_signed_B* as a friend assembly, the code in *friend_signed_B* can access `internal` (C#) or `Friend` (Visual Basic) types and members from *friend_signed_A*.</span></span> <span data-ttu-id="3f06c-120">Il file contiene il codice seguente.</span><span class="sxs-lookup"><span data-stu-id="3f06c-120">The file contains the following code.</span></span>  
   
   ```csharp  
   // friend_signed_B.cs  
   // Compile with:   
   // csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   public class Program  
   {  
       static void Main()  
       {  
           Class1 inst = new Class1();  
           inst.Test();  
       }  
   }  
   ```  
   
   ```vb  
   ' friend_signed_B.vb  
   ' Compile with:   
   ' Vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   Module Sample  
       Public Sub Main()  
           Dim inst As New Class1  
           inst.Test()  
       End Sub  
   End Module  
   ```  
   
6. <span data-ttu-id="3f06c-121">Compilare e firmare *friend_signed_B* usando il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="3f06c-121">Compile and sign *friend_signed_B* by using the following command.</span></span>  
   
   ```csharp
   csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   ```  
   
   ```vb
   vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   ```  
   
   <span data-ttu-id="3f06c-122">Il nome dell'assembly generato dal compilatore deve corrispondere al nome dell'assembly Friend passato all'attributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.</span><span class="sxs-lookup"><span data-stu-id="3f06c-122">The name of the assembly generated by the compiler must match the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="3f06c-123">È necessario specificare in modo esplicito il nome dell'assembly di output (con*estensione exe* o *dll*) utilizzando `/out` l'opzione del compilatore.</span><span class="sxs-lookup"><span data-stu-id="3f06c-123">You must explicitly specify the name of the output assembly (*.exe* or *.dll*) by using the `/out` compiler option.</span></span> <span data-ttu-id="3f06c-124">Per ulteriori informazioni, vedere [/out (C# opzioni del compilatore)](../../csharp/language-reference/compiler-options/out-compiler-option.md) o [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="3f06c-124">For more information, see [/out (C# compiler options)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span></span>  
   
7. <span data-ttu-id="3f06c-125">Eseguire il file *friend_signed_B. exe* .</span><span class="sxs-lookup"><span data-stu-id="3f06c-125">Run the *friend_signed_B.exe* file.</span></span>  
   
   <span data-ttu-id="3f06c-126">Il programma restituisce la stringa **Class1. test**.</span><span class="sxs-lookup"><span data-stu-id="3f06c-126">The program outputs the string **Class1.Test**.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="3f06c-127">Protezione .NET</span><span class="sxs-lookup"><span data-stu-id="3f06c-127">.NET security</span></span>  
 <span data-ttu-id="3f06c-128">Ci sono alcune analogie tra l'attributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> e la classe <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="3f06c-128">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="3f06c-129">La differenza principale è che <xref:System.Security.Permissions.StrongNameIdentityPermission> può richiedere le autorizzazioni di sicurezza per eseguire una particolare sezione di codice, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> mentre l'attributo controlla la `internal` visibilitàC#dei tipi `Friend` e membri () o (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="3f06c-129">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal` (C#) or `Friend` (Visual Basic) types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f06c-130">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3f06c-130">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="3f06c-131">Assembly in .NET</span><span class="sxs-lookup"><span data-stu-id="3f06c-131">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="3f06c-132">Assembly Friend</span><span class="sxs-lookup"><span data-stu-id="3f06c-132">Friend assemblies</span></span>](friend.md)
- [<span data-ttu-id="3f06c-133">Procedura: Crea assembly Friend non firmati</span><span class="sxs-lookup"><span data-stu-id="3f06c-133">How to: Create unsigned friend assemblies</span></span>](create-unsigned-friend.md)
- [<span data-ttu-id="3f06c-134">/keyfile (C#)</span><span class="sxs-lookup"><span data-stu-id="3f06c-134">/keyfile (C#)</span></span>](../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)
- [<span data-ttu-id="3f06c-135">-filefile (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f06c-135">-keyfile (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/keyfile.md)
- [<span data-ttu-id="3f06c-136">Sn. exe (strumento nome sicuro)</span><span class="sxs-lookup"><span data-stu-id="3f06c-136">Sn.exe (Strong Name tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="3f06c-137">Creazione e utilizzo di assembly con nome sicuro</span><span class="sxs-lookup"><span data-stu-id="3f06c-137">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="3f06c-138">Guida per programmatori C#</span><span class="sxs-lookup"><span data-stu-id="3f06c-138">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="3f06c-139">Concetti di programmazione (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f06c-139">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)