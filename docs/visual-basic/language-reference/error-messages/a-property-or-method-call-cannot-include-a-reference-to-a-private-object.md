---
title: Una chiamata a una proprietà o a un metodo non può includere un riferimento a un oggetto privato, né come argomento né come valore restituito
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 53f9052555555a5b9dcb038dfee9cd54dc2b4251
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976206"
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a>Una chiamata a una proprietà o a un metodo non può includere un riferimento a un oggetto privato, né come argomento né come valore restituito

Di seguito sono riportate le cause possibili dell'errore:  
  
- Un client ha richiamato una proprietà o un metodo di un componente out-of-process e ha tentato di passare un riferimento a un oggetto privato come uno degli argomenti.  
  
- Un componente out-of-process ha richiamato un metodo di richiamata sul relativo client e ha tentato di passare un riferimento a un oggetto privato.  
  
- Un componente out-of-process ha tentato di passare un riferimento a un oggetto privato come argomento dell'evento che stava generando.  
  
- Un client ha tentato di assegnare un riferimento a un oggetto privato a un argomento `ByRef` dell'evento che stava gestendo.  
  
## <a name="to-correct-this-error"></a>Per correggere l'errore  
  
1. Rimuovere il riferimento.  
  
## <a name="see-also"></a>Vedere anche

- [Private](../../../visual-basic/language-reference/modifiers/private.md)
