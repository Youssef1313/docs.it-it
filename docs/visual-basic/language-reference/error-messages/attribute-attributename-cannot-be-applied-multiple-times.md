---
title: Impossibile applicare più volte l'attributo '<attributename>'
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: f2f4dc428a247275f9919c4a8b6e6944a558eef0
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968232"
---
# <a name="attribute-attributename-cannot-be-applied-multiple-times"></a>Impossibile applicare più volte l'attributo '\<AttributeName >'

L'attributo può essere applicato una sola volta. L'attributo `AttributeUsage` determina se un attributo può essere applicato più di una volta.  
  
 **ID errore:** BC30663  
  
## <a name="to-correct-this-error"></a>Per correggere l'errore  
  
1. Verificare che l'attributo venga applicato una sola volta.  
  
2. Se si usano attributi personalizzati sviluppati, provare a modificare l'attributo `AttributeUsage` per consentire l'utilizzo di più attributi, come nell'esempio seguente.  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.AttributeUsageAttribute>
- [Creazione di attributi personalizzati](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [AttributeUsage](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
