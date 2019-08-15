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
# <a name="effects-of-modifying-a-base-forms-appearance"></a>Effetti della modifica dell'aspetto di un form di base

Durante lo sviluppo di applicazioni, spesso potrebbe essere necessario modificare l'aspetto del form di base da cui ereditano altri form nel progetto (o in altri progetti).

In fase di progettazione, le modifiche all'aspetto del form di base, relative sia all'impostazione di proprietà o all'aggiunta e sottrazione dei controlli, vengono applicate ai form ereditati quando viene compilato il progetto contenente il form di base. Non è sufficiente salvare le modifiche al form di base. Per compilare un progetto, scegliere **Compila** dal menu **Compila**.

Le modifiche apportate al form di base in fase di esecuzione non avranno alcun effetto sui form ereditati in cui è già stata creata un'istanza.

## <a name="see-also"></a>Vedere anche

- [base](~/docs/csharp/language-reference/keywords/base.md)
- [Procedura: Eredita Windows Forms](how-to-inherit-windows-forms.md)
- [Ereditarietà visiva di Windows Form](windows-forms-visual-inheritance.md)
