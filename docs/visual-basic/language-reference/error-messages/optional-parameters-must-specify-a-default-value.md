---
title: I parametri facoltativi devono specificare un valore predefinito
ms.date: 07/20/2015
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
ms.openlocfilehash: b32c150f0faf4a9dcec3cec7620c3a9c050f6f20
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696880"
---
# <a name="optional-parameters-must-specify-a-default-value"></a><span data-ttu-id="7a35c-102">I parametri facoltativi devono specificare un valore predefinito</span><span class="sxs-lookup"><span data-stu-id="7a35c-102">Optional parameters must specify a default value</span></span>
<span data-ttu-id="7a35c-103">I parametri facoltativi devono fornire valori predefiniti che possono essere usati se non viene fornito alcun parametro da una routine chiamante.</span><span class="sxs-lookup"><span data-stu-id="7a35c-103">Optional parameters must provide default values that can be used if no parameter is supplied by a calling procedure.</span></span>  
  
 <span data-ttu-id="7a35c-104">**ID errore:** BC30812</span><span class="sxs-lookup"><span data-stu-id="7a35c-104">**Error ID:** BC30812</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7a35c-105">Per correggere l'errore</span><span class="sxs-lookup"><span data-stu-id="7a35c-105">To correct this error</span></span>  
  
- <span data-ttu-id="7a35c-106">Specificare i valori predefiniti per i parametri facoltativi. Per esempio:</span><span class="sxs-lookup"><span data-stu-id="7a35c-106">Specify default values for optional parameters; for example:</span></span>  
  
    ```vb  
    Sub Proc1(ByVal X As Integer,   
          Optional ByVal Y As String = "Default Value")  
       MsgBox("Default argument is: " & Y)  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7a35c-107">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7a35c-107">See also</span></span>

- [<span data-ttu-id="7a35c-108">Facoltativo</span><span class="sxs-lookup"><span data-stu-id="7a35c-108">Optional</span></span>](../../../visual-basic/language-reference/modifiers/optional.md)
