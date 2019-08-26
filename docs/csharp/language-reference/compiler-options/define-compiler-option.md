---
title: -define (opzioni del compilatore C#)
ms.date: 07/20/2015
f1_keywords:
- /define
helpviewer_keywords:
- -define compiler option [C#]
- /define compiler option [C#]
- -d compiler option [C#]
- define compiler option [C#]
- /d compiler option [C#]
- d compiler option [C#]
ms.assetid: f17d7b4d-82d0-4133-8563-68cced1cac6e
ms.openlocfilehash: cb9de387b319ff4b81dcd1ccc37f04d8b6b3123a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924791"
---
# <a name="-define-c-compiler-options"></a><span data-ttu-id="ee5dd-102">-define (opzioni del compilatore C#)</span><span class="sxs-lookup"><span data-stu-id="ee5dd-102">-define (C# Compiler Options)</span></span>
<span data-ttu-id="ee5dd-103">L'opzione **-define** definisce `name` come simbolo in tutti i file del codice sorgente nel programma.</span><span class="sxs-lookup"><span data-stu-id="ee5dd-103">The **-define** option defines `name` as a symbol in all source code files your program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee5dd-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ee5dd-104">Syntax</span></span>  
  
```console  
-define:name[;name2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="ee5dd-105">Argomenti</span><span class="sxs-lookup"><span data-stu-id="ee5dd-105">Arguments</span></span>  
 <span data-ttu-id="ee5dd-106">`name`, `name2`</span><span class="sxs-lookup"><span data-stu-id="ee5dd-106">`name`, `name2`</span></span>  
 <span data-ttu-id="ee5dd-107">Nome di uno o più simboli che si vuole definire.</span><span class="sxs-lookup"><span data-stu-id="ee5dd-107">The name of one or more symbols that you want to define.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee5dd-108">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="ee5dd-108">Remarks</span></span>  
 <span data-ttu-id="ee5dd-109">L'opzione **-define** ha lo stesso effetto dell'uso di una direttiva [#define](../preprocessor-directives/preprocessor-define.md) per il preprocessore, ad eccezione del fatto che l'opzione del compilatore è valida per tutti i file nel progetto.</span><span class="sxs-lookup"><span data-stu-id="ee5dd-109">The **-define** option has the same effect as using a [#define](../preprocessor-directives/preprocessor-define.md) preprocessor directive except that the compiler option is in effect for all files in the project.</span></span> <span data-ttu-id="ee5dd-110">Un simbolo resta definito in un file del codice sorgente finché una direttiva [#undef](../preprocessor-directives/preprocessor-undef.md) nel file non rimuove la definizione.</span><span class="sxs-lookup"><span data-stu-id="ee5dd-110">A symbol remains defined in a source file until an [#undef](../preprocessor-directives/preprocessor-undef.md) directive in the source file removes the definition.</span></span> <span data-ttu-id="ee5dd-111">Quando si usa l'opzione -define, una direttiva `#undef` in un file non ha effetto in altri file del codice sorgente nel progetto.</span><span class="sxs-lookup"><span data-stu-id="ee5dd-111">When you use the -define option, an `#undef` directive in one file has no effect on other source code files in the project.</span></span>  
  
 <span data-ttu-id="ee5dd-112">È possibile usare i simboli creati da questa opzione con [#if](../preprocessor-directives/preprocessor-if.md), [#else](../preprocessor-directives/preprocessor-else.md), [#elif](../preprocessor-directives/preprocessor-elif.md) e [#endif](../preprocessor-directives/preprocessor-endif.md) per la compilazione condizionale dei file del codice sorgente.</span><span class="sxs-lookup"><span data-stu-id="ee5dd-112">You can use symbols created by this option with [#if](../preprocessor-directives/preprocessor-if.md), [#else](../preprocessor-directives/preprocessor-else.md), [#elif](../preprocessor-directives/preprocessor-elif.md), and [#endif](../preprocessor-directives/preprocessor-endif.md) to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="ee5dd-113">**-d** è la versione abbreviata di **-define**.</span><span class="sxs-lookup"><span data-stu-id="ee5dd-113">**-d** is the short form of **-define**.</span></span>  
  
 <span data-ttu-id="ee5dd-114">È possibile definire più simboli con **-define** separando i nomi di simbolo con virgole o punti e virgola.</span><span class="sxs-lookup"><span data-stu-id="ee5dd-114">You can define multiple symbols with **-define** by using a semicolon or comma to separate symbol names.</span></span> <span data-ttu-id="ee5dd-115">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="ee5dd-115">For example:</span></span>  
  
```console  
-define:DEBUG;TUESDAY  
```  
  
 <span data-ttu-id="ee5dd-116">Il compilatore C# stesso non definisce alcun simbolo o macro che è possibile usare nel codice sorgente. Tutte le definizioni dei simboli devono essere definite dall'utente.</span><span class="sxs-lookup"><span data-stu-id="ee5dd-116">The C# compiler itself defines no symbols or macros that you can use in your source code; all symbol definitions must be user-defined.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee5dd-117">`#define` in C# non consente di assegnare un valore a un simbolo, diversamente dai linguaggi come C++.</span><span class="sxs-lookup"><span data-stu-id="ee5dd-117">The C# `#define` does not allow a symbol to be given a value, as in languages such as C++.</span></span> <span data-ttu-id="ee5dd-118">Ad esempio, non è possibile usare `#define` per creare una macro o per definire una costante.</span><span class="sxs-lookup"><span data-stu-id="ee5dd-118">For example, `#define` cannot be used to create a macro or to define a constant.</span></span> <span data-ttu-id="ee5dd-119">Se è necessario definire una costante, usare una variabile `enum`.</span><span class="sxs-lookup"><span data-stu-id="ee5dd-119">If you need to define a constant, use an `enum` variable.</span></span> <span data-ttu-id="ee5dd-120">Se si vuole creare una macro in stile C++, prendere in considerazione altre alternative, ad esempio i generics.</span><span class="sxs-lookup"><span data-stu-id="ee5dd-120">If you want to create a C++ style macro, consider alternatives such as generics.</span></span> <span data-ttu-id="ee5dd-121">Poiché le macro sono notoriamente soggette a errori, C# non ne consente l'uso, ma offre alternative più sicure.</span><span class="sxs-lookup"><span data-stu-id="ee5dd-121">Since macros are notoriously error-prone, C# disallows their use but provides safer alternatives.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="ee5dd-122">Per impostare l'opzione del compilatore nell'ambiente di sviluppo di Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ee5dd-122">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="ee5dd-123">Aprire la pagine **Proprietà** del progetto.</span><span class="sxs-lookup"><span data-stu-id="ee5dd-123">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="ee5dd-124">Nella scheda **Compila** digitare il simbolo che deve essere definito nella casella **Simboli di compilazione condizionale**.</span><span class="sxs-lookup"><span data-stu-id="ee5dd-124">On the **Build** tab, type the symbol that is to be defined in the **Conditional compilation symbols** box.</span></span> <span data-ttu-id="ee5dd-125">Se si usa l'esempio di codice seguente, ad esempio, digitare `xx` nella casella di testo.</span><span class="sxs-lookup"><span data-stu-id="ee5dd-125">For example, if you are using the code example that follows, just type `xx` into the text box.</span></span>  
  
 <span data-ttu-id="ee5dd-126">Per informazioni su come impostare questa opzione del compilatore a livello di codice, vedere <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.</span><span class="sxs-lookup"><span data-stu-id="ee5dd-126">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee5dd-127">Esempio</span><span class="sxs-lookup"><span data-stu-id="ee5dd-127">Example</span></span>  
  
```csharp  
// preprocessor_define.cs  
// compile with: -define:xx  
// or uncomment the next line  
// #define xx  
using System;  
public class Test   
{  
    public static void Main()   
    {  
        #if (xx)   
            Console.WriteLine("xx defined");  
        #else  
            Console.WriteLine("xx not defined");  
        #endif  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="ee5dd-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ee5dd-128">See also</span></span>

- [<span data-ttu-id="ee5dd-129">Opzioni del compilatore C#</span><span class="sxs-lookup"><span data-stu-id="ee5dd-129">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="ee5dd-130">Gestione delle proprietà di progetti e soluzioni</span><span class="sxs-lookup"><span data-stu-id="ee5dd-130">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
