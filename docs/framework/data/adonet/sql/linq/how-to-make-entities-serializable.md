---
title: 'Procedura: Rendere serializzabili le entità'
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: 5e9d078ed2daacfa48b09693f533e9aade613281
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002705"
---
# <a name="how-to-make-entities-serializable"></a><span data-ttu-id="aa6cb-102">Procedura: Rendere serializzabili le entità</span><span class="sxs-lookup"><span data-stu-id="aa6cb-102">How to: Make Entities Serializable</span></span>
<span data-ttu-id="aa6cb-103">Quando si genera il codice, è possibile rendere serializzabili le entità.</span><span class="sxs-lookup"><span data-stu-id="aa6cb-103">You can make entities serializable when you generate your code.</span></span> <span data-ttu-id="aa6cb-104">Le classi di entità vengono decorate con l'attributo <xref:System.Runtime.Serialization.DataContractAttribute> e le colonne con l'attributo <xref:System.Runtime.Serialization.DataMemberAttribute>.</span><span class="sxs-lookup"><span data-stu-id="aa6cb-104">Entity classes are decorated with the <xref:System.Runtime.Serialization.DataContractAttribute> attribute, and columns with the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="aa6cb-105">Gli sviluppatori che usano Visual Studio possono usare la Object Relational Designer a questo scopo.</span><span class="sxs-lookup"><span data-stu-id="aa6cb-105">Developers using Visual Studio can use the Object Relational Designer for this purpose.</span></span>  
  
 <span data-ttu-id="aa6cb-106">Se si utilizza lo strumento da riga di comando SQLMetal, utilizzare l'opzione **/Serialization** con l'argomento `unidirectional`.</span><span class="sxs-lookup"><span data-stu-id="aa6cb-106">If you are using the SQLMetal command-line tool, use the **/serialization** option with the `unidirectional` argument.</span></span> <span data-ttu-id="aa6cb-107">Per altre informazioni, vedere [SqlMetal.exe (strumento per la generazione del codice)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="aa6cb-107">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa6cb-108">Esempio</span><span class="sxs-lookup"><span data-stu-id="aa6cb-108">Example</span></span>  
 <span data-ttu-id="aa6cb-109">Le righe di comando SQLMetal seguenti consentono di produrre file con entità serializzabili.</span><span class="sxs-lookup"><span data-stu-id="aa6cb-109">The following SQLMetal command lines produce files that have serializable entities.</span></span>  
  
```console  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```console  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a><span data-ttu-id="aa6cb-110">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="aa6cb-110">See also</span></span>

- [<span data-ttu-id="aa6cb-111">Serializzazione</span><span class="sxs-lookup"><span data-stu-id="aa6cb-111">Serialization</span></span>](serialization.md)
- [<span data-ttu-id="aa6cb-112">Creazione del modello a oggetti</span><span class="sxs-lookup"><span data-stu-id="aa6cb-112">Creating the Object Model</span></span>](creating-the-object-model.md)
