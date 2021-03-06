---
title: Necessario riferimento all'assembly '<assemblyidentity>' contenente il tipo '<typename>'. Impossibile trovare un riferimento adatto a causa dell'ambiguità tra i progetti '<projectname1>' e '<projectname2>'
ms.date: 07/20/2015
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords:
- BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
ms.openlocfilehash: 9868598b32ae17ef5bfb5dd738f8a7541515f5ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013746"
---
# <a name="reference-required-to-assembly-assemblyidentity-containing-type-typename-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-projectname1-and-projectname2"></a>Necessario riferimento all'assembly '\<identitàassembly >' contenente il tipo '\<nomeTipo >', ma non è stato possibile trovare un riferimento appropriato a causa dell'ambiguità tra dei progetti\<projectname1 >' e '\< projectname2 >'
In un'espressione viene usato un tipo, ad esempio una classe, una struttura, un'interfaccia, un'enumerazione o un delegato, definito all'esterno del progetto. Tuttavia, sono presenti riferimenti di progetto a più assembly che definiscono quel tipo.  
  
 I progetti citati generano assembly con lo stesso nome. Pertanto, il compilatore non può determinare l'assembly da usare per il tipo a cui si accede.  
  
 Per accedere a un tipo definito in un altro assembly, il compilatore Visual Basic deve avere un riferimento a tale assembly. Deve trattarsi di un riferimento unico, non ambiguo, che non generi riferimenti circolari tra i progetti.  
  
 **ID errore:** BC30969  
  
## <a name="to-correct-this-error"></a>Per correggere l'errore  
  
1. Determinare quale progetto produce l'assembly migliore per il progetto a cui fare riferimento. Per questa decisione si potrebbero usare criteri quali la facilità di accesso al file e la frequenza di aggiornamenti.  
  
2. Nelle proprietà del progetto aggiungere un riferimento al file contenente l'assembly che definisce il tipo in uso.  
  
## <a name="see-also"></a>Vedere anche

- [Gestione dei riferimenti in un progetto](/visualstudio/ide/managing-references-in-a-project)
- [Riferimenti a elementi dichiarati](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [Gestione delle proprietà di progetti e soluzioni](/visualstudio/ide/managing-project-and-solution-properties)
- [Risoluzione dei problemi relativi ai riferimenti interrotti](/visualstudio/ide/troubleshooting-broken-references)
