---
title: "Procedura: leggere le impostazioni dell'applicazione"
ms.date: 07/20/2015
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
ms.openlocfilehash: 04726381f8d285ae61045d1624b3b41b7f47e491
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74329575"
---
# <a name="how-to-read-application-settings-in-visual-basic"></a><span data-ttu-id="b3df8-102">Procedura: leggere le impostazioni dell'applicazione in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b3df8-102">How to: Read Application Settings in Visual Basic</span></span>

<span data-ttu-id="b3df8-103">È possibile leggere un'impostazione utente accedendo alla proprietà dell'impostazione nell'oggetto `My.Settings`.</span><span class="sxs-lookup"><span data-stu-id="b3df8-103">You can read a user setting by accessing the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="b3df8-104">L'oggetto `My.Settings` espone ogni impostazione come una proprietà.</span><span class="sxs-lookup"><span data-stu-id="b3df8-104">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="b3df8-105">Il nome della proprietà corrisponde allo stesso nome dell'impostazione e il tipo di proprietà al tipo di impostazione.</span><span class="sxs-lookup"><span data-stu-id="b3df8-105">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="b3df8-106">L'**ambito** dell'impostazione indica se la proprietà è di sola lettura. La proprietà di un'impostazione dell'ambito **applicazione** è di sola lettura, mentre la proprietà di un'impostazione dell'ambito **utente** è di lettura e scrittura.</span><span class="sxs-lookup"><span data-stu-id="b3df8-106">The setting's **Scope** indicates if the property is read-only; the property for an **Application** scope setting is read-only, while the property for a **User** scope setting is read-write.</span></span> <span data-ttu-id="b3df8-107">Per altre informazioni, vedere [Oggetto My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="b3df8-107">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3df8-108">Esempio</span><span class="sxs-lookup"><span data-stu-id="b3df8-108">Example</span></span>  

 <span data-ttu-id="b3df8-109">Nell'esempio riportato di seguito viene mostrato il valore dell'impostazione `Nickname`.</span><span class="sxs-lookup"><span data-stu-id="b3df8-109">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 <span data-ttu-id="b3df8-110">Affinché l'esempio funzioni, l'applicazione deve contenere un'impostazione `Nickname` di tipo `String`.</span><span class="sxs-lookup"><span data-stu-id="b3df8-110">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span> <span data-ttu-id="b3df8-111">Per altre informazioni, vedere [Gestione delle impostazioni di un'applicazione (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="b3df8-111">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3df8-112">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b3df8-112">See also</span></span>

- [<span data-ttu-id="b3df8-113">Oggetto My.Settings</span><span class="sxs-lookup"><span data-stu-id="b3df8-113">My.Settings Object</span></span>](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="b3df8-114">Procedura: Modificare le impostazioni utente in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b3df8-114">How to: Change User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="b3df8-115">Procedura: Mantenere le impostazioni utente in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b3df8-115">How to: Persist User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="b3df8-116">Procedura: Creare griglie di proprietà per impostazioni utente in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b3df8-116">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="b3df8-117">Gestione delle impostazioni di un'applicazione (.NET)</span><span class="sxs-lookup"><span data-stu-id="b3df8-117">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
