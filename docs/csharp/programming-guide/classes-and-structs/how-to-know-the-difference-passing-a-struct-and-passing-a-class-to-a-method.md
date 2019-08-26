---
title: 'Procedura: Differenza tra il passaggio a un metodo di uno struct e di un riferimento a una classe - Guida per programmatori C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], passing as method parameter
- passing parameters [C#], structs vs. classes
- methods [C#], passing classes vs. structs
ms.assetid: 9c1313a6-32a8-4ea7-a59f-450f66af628b
ms.openlocfilehash: 889e1f5719e094d02f0cc27256e1c430ffce0b8e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596793"
---
# <a name="how-to-know-the-difference-between-passing-a-struct-and-passing-a-class-reference-to-a-method-c-programming-guide"></a>Procedura: Differenza tra il passaggio a un metodo di uno struct e di un riferimento a una classe (Guida per programmatori C#)
L'esempio seguente mostra la differenza tra passare uno [struct](../../language-reference/keywords/struct.md) a un metodo e passare un'istanza di una [classe](../../language-reference/keywords/class.md) a un metodo. Nell'esempio entrambi gli argomenti (struct e istanza di classe) vengono passati in base al valore ed entrambi i metodi modificano il valore di un campo dell'argomento. I risultati dei due metodi non sono tuttavia uguali perché ciò che viene passato quando si passa uno struct è diverso da ciò che viene passato quando si passa un'istanza di una classe.  
  
 Poiché uno struct è un [tipo valore](../../language-reference/keywords/value-types.md), quando si [passa uno struct in base al valore](./passing-value-type-parameters.md) a un metodo, il metodo riceve una copia dell'argomento dello struct, su cui opera. Il metodo non ha accesso allo struct originale nella chiamata e quindi non può modificarlo in alcun modo. Il metodo può modificare solo la copia.  
  
 Un'istanza di classe è un [tipo riferimento](../../language-reference/keywords/reference-types.md), non un tipo valore. Quando si [passa un tipo riferimento in base al valore](./passing-reference-type-parameters.md) a un metodo, il metodo riceve una copia del riferimento all'istanza di classe. Ciò significa che il metodo riceve una copia dell'indirizzo dell'istanza, non una copia dell'istanza stessa. L'istanza di classe nel metodo chiamante ha un indirizzo, il parametro nel metodo chiamato ha una copia dell'indirizzo ed entrambi gli indirizzi fanno riferimento allo stesso oggetto. Poiché il parametro contiene solo una copia dell'indirizzo, il metodo chiamato non può modificare l'indirizzo dell'istanza di classe nel metodo chiamante. Il metodo chiamato può tuttavia usare l'indirizzo per accedere ai membri della classe a cui fanno riferimento sia l'indirizzo originale che la copia. Se il metodo chiamato modifica un membro della classe, viene modificata anche l'istanza di classe originale nel metodo chiamante.  
  
 L'output dell'esempio seguente illustra la differenza. Il valore del campo `willIChange` dell'istanza di classe viene modificato dalla chiamata al metodo `ClassTaker` perché il metodo usa l'indirizzo nel parametro per trovare il campo specificato dell'istanza di classe. Il campo `willIChange` dello struct nel metodo chiamante non viene modificato dalla chiamata al metodo `StructTaker` perché il valore dell'argomento è una copia dello struct, non una copia del relativo indirizzo. `StructTaker` modifica la copia e la copia viene persa quando la chiamata a `StructTaker` viene completata.  
  
## <a name="example"></a>Esempio  
 [!code-csharp[csProgGuideObjects#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#32)]  
  
## <a name="see-also"></a>Vedere anche

- [Guida per programmatori C#](../index.md)
- [Classi](./classes.md)
- [Struct](./structs.md)
- [Passaggio di parametri](./passing-parameters.md)
