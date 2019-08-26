---
title: -checked (opzioni del compilatore C#)
ms.date: 07/20/2015
f1_keywords:
- /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
ms.openlocfilehash: 4e07698e7abdad00983b61412fa2a57e651d4d46
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606992"
---
# <a name="-checked-c-compiler-options"></a><span data-ttu-id="1a5d9-102">-checked (opzioni del compilatore C#)</span><span class="sxs-lookup"><span data-stu-id="1a5d9-102">-checked (C# Compiler Options)</span></span>
<span data-ttu-id="1a5d9-103">L'opzione **-checked** specifica se un'istruzione di calcolo di interi che risulta in un valore non incluso nell'intervallo dei tipi di dati e nell'ambito di una parola chiave [checked](../keywords/checked.md) o [unchecked](../keywords/unchecked.md) genera un'eccezione in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="1a5d9-103">The **-checked** option specifies whether an integer arithmetic statement that results in a value that is outside the range of the data type, and that is not in the scope of a [checked](../keywords/checked.md) or [unchecked](../keywords/unchecked.md) keyword, causes a run-time exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a5d9-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="1a5d9-104">Syntax</span></span>  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="1a5d9-105">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="1a5d9-105">Remarks</span></span>  
 <span data-ttu-id="1a5d9-106">Un'istruzione di calcolo di interi inclusa nell'ambito di una parola chiave `checked` o `unchecked` non è soggetta all'opzione **-checked**.</span><span class="sxs-lookup"><span data-stu-id="1a5d9-106">An integer arithmetic statement that is in the scope of a `checked` or `unchecked` keyword is not subject to the effect of the **-checked** option.</span></span>  
  
 <span data-ttu-id="1a5d9-107">Se un'istruzione di calcolo di interi che non è compresa nell'ambito di una parola chiave `checked` o `unchecked` risulta in un valore non incluso nell'intervallo del tipo di dati e l'opzione **-checked+** (o **-checked**) viene usata nella compilazione, tale istruzione genera un'eccezione in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="1a5d9-107">If an integer arithmetic statement that is not in the scope of a `checked` or `unchecked` keyword results in a value outside the range of the data type, and **-checked+** (or **-checked**) is used in the compilation, that statement causes an exception at run time.</span></span> <span data-ttu-id="1a5d9-108">Se l'opzione **-checked-** viene usata nella compilazione, tale istruzione non genera un'eccezione in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="1a5d9-108">If **-checked-** is used in the compilation, that statement does not cause an exception at run time.</span></span>  
  
 <span data-ttu-id="1a5d9-109">Il valore predefinito per questa opzione è **-checked-** ; il controllo dell'overflow è disabilitato.</span><span class="sxs-lookup"><span data-stu-id="1a5d9-109">The default value for this option is **-checked-**; overflow checking is disabled.</span></span>
 
 <span data-ttu-id="1a5d9-110">In alcuni casi gli strumenti automatici usati per compilare applicazioni di grandi dimensioni impostano l'opzione -checked su +.</span><span class="sxs-lookup"><span data-stu-id="1a5d9-110">Sometimes, automated tools that are used to build large applications set -checked to +.</span></span> <span data-ttu-id="1a5d9-111">Uno scenario per usare l'opzione -checked- consiste nell'eseguire l'override del valore predefinito globale dello strumento specificando -checked-.</span><span class="sxs-lookup"><span data-stu-id="1a5d9-111">One scenario for using -checked- is to override the tool's global default by specifying -checked-.</span></span>
 
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="1a5d9-112">Per impostare l'opzione del compilatore nell'ambiente di sviluppo di Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1a5d9-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="1a5d9-113">Aprire la pagine **Proprietà** del progetto.</span><span class="sxs-lookup"><span data-stu-id="1a5d9-113">Open the project's **Properties** page.</span></span> <span data-ttu-id="1a5d9-114">Per altre informazioni, vedere [Pagina Compilazione, Creazione progetti (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="1a5d9-114">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="1a5d9-115">Fare clic sulla pagina della proprietà **Compilazione**.</span><span class="sxs-lookup"><span data-stu-id="1a5d9-115">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="1a5d9-116">Fare clic su **Avanzate** .</span><span class="sxs-lookup"><span data-stu-id="1a5d9-116">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="1a5d9-117">Modificare la proprietà **Controlla overflow/underflow aritmetico**.</span><span class="sxs-lookup"><span data-stu-id="1a5d9-117">Modify the **Check for arithmetic overflow/underflow** property.</span></span>  
  
 <span data-ttu-id="1a5d9-118">Per accedere all'opzione del compilatore a livello di codice, vedere <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span><span class="sxs-lookup"><span data-stu-id="1a5d9-118">To access this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a5d9-119">Esempio</span><span class="sxs-lookup"><span data-stu-id="1a5d9-119">Example</span></span>  
 <span data-ttu-id="1a5d9-120">Il comando seguente compila `t2.cs`.</span><span class="sxs-lookup"><span data-stu-id="1a5d9-120">The following command compiles `t2.cs`.</span></span> <span data-ttu-id="1a5d9-121">L'uso di `-checked` nel comando specifica che l'istruzione di calcolo di interi nel file che non è nell'ambito della parola chiave `checked` o `unchecked` e che risulta in un valore non incluso nell'intervallo dei tipi di dati, genera un'eccezione in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="1a5d9-121">The use of `-checked` in the command specifies that any integer arithmetic statement in the file that is not in the scope of a `checked` or `unchecked` keyword, and that results in a value that is outside the range of the data type, causes an exception at run time.</span></span>  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a><span data-ttu-id="1a5d9-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1a5d9-122">See also</span></span>

- [<span data-ttu-id="1a5d9-123">Opzioni del compilatore C#</span><span class="sxs-lookup"><span data-stu-id="1a5d9-123">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="1a5d9-124">Gestione delle proprietà di progetti e soluzioni</span><span class="sxs-lookup"><span data-stu-id="1a5d9-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
