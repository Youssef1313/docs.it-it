---
title: Effetti della modifica dell'aspetto di un form di base
ms.date: 03/30/2017
helpviewer_keywords:
- parent forms [Windows Forms]
- inherited forms [Windows Forms], modifications to base form
- Windows Forms, base form appearance
- base forms
- inheritance [Windows Forms], forms
ms.assetid: 1c3f2b29-a05c-4c6f-aa1a-4e66b94f343a
ms.openlocfilehash: 5239017eb63ca6360ae8811a76497256fafbd1b1
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040139"
---
# <a name="effects-of-modifying-a-base-forms-appearance"></a><span data-ttu-id="f996c-102">Effetti della modifica dell'aspetto di un form di base</span><span class="sxs-lookup"><span data-stu-id="f996c-102">Effects of modifying a base form's appearance</span></span>

<span data-ttu-id="f996c-103">Durante lo sviluppo di applicazioni, spesso potrebbe essere necessario modificare l'aspetto del form di base da cui ereditano altri form nel progetto (o in altri progetti).</span><span class="sxs-lookup"><span data-stu-id="f996c-103">During application development, you may often need to change the appearance of the base form from which other forms in the project (or in other projects) are inheriting.</span></span>

<span data-ttu-id="f996c-104">In fase di progettazione, le modifiche all'aspetto del form di base, relative sia all'impostazione di proprietà o all'aggiunta e sottrazione dei controlli, vengono applicate ai form ereditati quando viene compilato il progetto contenente il form di base.</span><span class="sxs-lookup"><span data-stu-id="f996c-104">At design time, changes to the base form's appearance (be it the setting of properties or the addition and subtraction of controls) are reflected on inherited forms when the project containing the base form is built.</span></span> <span data-ttu-id="f996c-105">Non è sufficiente salvare le modifiche al form di base.</span><span class="sxs-lookup"><span data-stu-id="f996c-105">It is not sufficient for you to simply save the changes to the base form.</span></span> <span data-ttu-id="f996c-106">Per compilare un progetto, scegliere **Compila** dal menu **Compila**.</span><span class="sxs-lookup"><span data-stu-id="f996c-106">To build a project, choose **Build** from the **Build** menu.</span></span>

<span data-ttu-id="f996c-107">Le modifiche apportate al form di base in fase di esecuzione non avranno alcun effetto sui form ereditati in cui è già stata creata un'istanza.</span><span class="sxs-lookup"><span data-stu-id="f996c-107">Modifications made to the base form at run time have no affect on inherited forms that are already instantiated.</span></span>

## <a name="see-also"></a><span data-ttu-id="f996c-108">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f996c-108">See also</span></span>

- [<span data-ttu-id="f996c-109">base</span><span class="sxs-lookup"><span data-stu-id="f996c-109">base</span></span>](~/docs/csharp/language-reference/keywords/base.md)
- [<span data-ttu-id="f996c-110">Procedura: Eredita Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f996c-110">How to: Inherit Windows Forms</span></span>](how-to-inherit-windows-forms.md)
- [<span data-ttu-id="f996c-111">Ereditarietà visiva di Windows Form</span><span class="sxs-lookup"><span data-stu-id="f996c-111">Windows Forms Visual Inheritance</span></span>](windows-forms-visual-inheritance.md)
