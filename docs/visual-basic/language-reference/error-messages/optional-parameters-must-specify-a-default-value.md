---
title: I parametri facoltativi devono specificare un valore predefinito
ms.date: 07/20/2015
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
ms.openlocfilehash: 8ec4627d070cc670ce04be3a5d0298dba0a279d0
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582141"
---
# <a name="optional-parameters-must-specify-a-default-value"></a>I parametri facoltativi devono specificare un valore predefinito

I parametri facoltativi devono fornire valori predefiniti che possono essere usati se non viene fornito alcun parametro da una routine chiamante.

**ID errore:** BC30812

## <a name="to-correct-this-error"></a>Per correggere l'errore

Specificare i valori predefiniti per i parametri facoltativi. Per esempio:

```vb
Sub Proc1(ByVal X As Integer,
      Optional ByVal Y As String = "Default Value")
    MsgBox("Default argument is: " & Y)
End Sub
```

## <a name="see-also"></a>Vedere anche

- [Optional](../../../visual-basic/language-reference/modifiers/optional.md)
