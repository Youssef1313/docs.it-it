---
title: Il nome di variabile di intervallo può essere dedotto solo da un nome semplice o completo senza argomenti
ms.date: 07/20/2015
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords:
- BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
ms.openlocfilehash: ca50ddd86cfbba8db0148ed315645714acabc18d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582417"
---
# <a name="range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a>Il nome di variabile di intervallo può essere dedotto solo da un nome semplice o completo senza argomenti

Un elemento di programmazione che accetta uno o più argomenti è incluso in una query LINQ. Il compilatore non è in grado di dedurre una variabile di intervallo da tale elemento di programmazione.

**ID errore:** BC36599

## <a name="to-correct-this-error"></a>Per correggere l'errore

Specificare un nome di variabile esplicito per l'elemento di programmazione, come illustrato nel codice seguente:

```vb
Dim query = From var1 In collection1
            Select VariableAlias= SampleFunction(var1), var1
```

## <a name="see-also"></a>Vedere anche

- [Introduzione a LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Clausola Select](../../../visual-basic/language-reference/queries/select-clause.md)
