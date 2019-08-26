---
title: Dominio di accessibilità - Riferimenti per C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
ms.openlocfilehash: 814aa8d3965674abe8bdb60b738cbeff93701ceb
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606134"
---
# <a name="accessibility-domain-c-reference"></a>Dominio di accessibilità (Riferimenti per C#)
Il dominio di accessibilità di un membro specifica in quali sezioni del programma è possibile fare riferimento a un membro. Se il membro è annidato all'interno di un altro tipo, il suo dominio di accessibilità viene determinato dal [livello di accessibilità](./accessibility-levels.md) del membro e dal dominio di accessibilità del tipo contenitore.  
  
 Il dominio di accessibilità di un tipo di primo livello è minimo il testo di programma del progetto in cui è dichiarato. Vale a dire che il dominio include tutti i file di origine di questo progetto. Il dominio di accessibilità di un tipo annidato è minimo il testo del programma del tipo in cui è dichiarato. Vale a dire che il dominio è il corpo tipo che include tutti i tipi annidati. Il dominio di accessibilità di un tipo annidato non è mai superiore a quello del tipo contenitore. Questi concetti vengono illustrati nell'esempio seguente.  
  
## <a name="example"></a>Esempio  
 Questo esempio include un tipo di primo livello, `T1`, e due classi annidate, `M1` e `M2`. Le classi contengono campi diversi con accessibilità dichiarate. Nel metodo `Main` un commento segue ogni istruzione per indicare il dominio di accessibilità di ogni membro. Si noti che le istruzioni che fanno riferimento ai membri non accessibili includono un commento. Per rivedere gli errori di compilazione generati dal riferimento a un membro inaccessibile, rimuovere i commenti uno alla volta.  
  
[!code-csharp[csrefKeywordsModifiers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#4)]
  
## <a name="c-language-specification"></a>Specifiche del linguaggio C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Riferimenti per C#](../index.md)
- [Guida per programmatori C#](../../programming-guide/index.md)
- [Parole chiave di C#](./index.md)
- [Modificatori di accesso](./access-modifiers.md)
- [Livelli di accessibilità](./accessibility-levels.md)
- [Restrizioni relative all'uso dei livelli di accessibilità](./restrictions-on-using-accessibility-levels.md)
- [Modificatori di accesso](../../programming-guide/classes-and-structs/access-modifiers.md)
- [public](./public.md)
- [private](./private.md)
- [protected](./protected.md)
- [internal](./internal.md)
