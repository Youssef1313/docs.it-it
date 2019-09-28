---
title: Struct - Guida a C#
description: Informazioni sui tipi di struct e su come crearli
ms.date: 10/12/2016
ms.assetid: a7094b8c-7229-4b6f-82fc-824d0ea0ec40
ms.openlocfilehash: e0974b7dcf3c0888cb52bea81b07a58e3a98640b
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/27/2019
ms.locfileid: "71396118"
---
# <a name="structs"></a>Struct

Uno *struct* è un tipo valore. Quando viene creato uno struct, la variabile a cui è assegnato lo struct contiene i dati effettivi dello struct. Quando viene assegnato a una nuova variabile, il tipo struct viene copiato. La nuova variabile e quella originale contengono quindi due copie separate degli stessi dati. Eventuali modifiche apportate a una copia non influiscono sull'altra copia.

Le variabili dei tipi valore contengono direttamente i rispettivi valori, ovvero la memoria viene allocata inline nel contesto in cui è dichiarata la variabile. Non esiste un'allocazione heap o un overhead di Garbage Collection separato per le variabili dei tipi valore.  
  
Esistono due categorie di tipi valore: [struct](./language-reference/keywords/struct.md) e [enum](./language-reference/keywords/enum.md).  
  
I tipi numerici incorporati sono struct i cui metodi e le cui proprietà sono accessibili dall'utente:  
  
[!code-csharp[Static Method](../../samples/snippets/csharp/concepts/structs/static-method.cs)]
  
Ad essi, tuttavia, si dichiarano e si assegnano valori come se fossero tipi non aggregati semplici:  
  
[!code-csharp[Assign Values](../../samples/snippets/csharp/concepts/structs/assign-value.cs)] 
  
I tipi valore sono *sealed*, ovvero non è possibile, ad esempio, derivare un tipo da <xref:System.Int32> e non è possibile definire uno struct da ereditare da uno struct o una classe definita dall'utente, poiché uno struct può ereditare solo da <xref:System.ValueType>. Uno struct può implementare tuttavia una o più interfacce. È possibile eseguire il cast di un tipo struct in un tipo di interfaccia; questa operazione genera tuttavia una *conversione boxing*  con cui si esegue il wrapping dello struct in un oggetto tipo riferimento sull'heap gestito. Le operazioni di conversione boxing si verificano anche quando si passa un tipo valore a un metodo che accetta <xref:System.Object> come parametro di input. Per altre informazioni, vedere [Boxing e unboxing](./programming-guide/types/boxing-and-unboxing.md ).  
  
Usare la parola chiave [struct](./language-reference/keywords/struct.md) per creare tipi valore personalizzati. In genere, un tipo struct viene usato come contenitore per un piccolo set di variabili correlate, come illustrato nell'esempio seguente:  
  
[!code-csharp[Struct Keyword](../../samples/snippets/csharp/concepts/structs/struct-keyword.cs)]  
  
Per altre informazioni sui tipi valore in NET Framework, vedere [Common Type System](../standard/common-type-system.md).  
    
Gli struct condividono la maggior parte della sintassi delle classi, anche sono più limitati rispetto alle classi:  
  
- All'interno di una dichiarazione di struct, non è possibile inizializzare i campi a meno che non siano stati dichiarati come `const` o `static`.  
  
- Uno struct non può dichiarare un costruttore senza parametri o un finalizzatore.  
  
- Gli struct vengono copiati su assegnazione. Quando uno struct viene assegnato a una nuova variabile, tutti i dati vengono copiati e qualsiasi modifica alla nuova copia non modifica i dati nella copia originale. È importante ricordare questo aspetto quando si lavora con le Collection di tipi valore come Dictionary<string, myStruct>.  
  
- Gli struct sono tipi valore e le classi sono tipi di riferimento.  
  
- A differenza delle classi, è possibile creare istanze di struct senza usare un operatore `new`.  
  
- Gli struct possono dichiarare costruttori con parametri.  
  
- Uno struct non può ereditare da un altro struct o da una classe e non può essere la base di una classe. Tutti gli struct ereditano direttamente da <xref:System.ValueType>, che eredita da <xref:System.Object>.  
  
- Uno struct può implementare le interfacce.

## <a name="literal-values"></a>Valori letterali

In C# i valori letterali ricevono un tipo dal compilatore. È possibile specificare come deve essere tipizzato un valore letterale numerico aggiungendo una lettera alla fine del numero. Per specificare, ad esempio, che il valore 4.56 deve essere considerato come un tipo float, aggiungere una "f" o una "F" dopo il numero: `4.56f`. Se non viene aggiunta alcuna lettera, il compilatore dedurrà un tipo `double` per il valore letterale. Per altre informazioni sui tipi che possono essere specificati con suffissi letterali, vedere le pagine di riferimento relative ai singoli tipi in [Tipi valore](./language-reference/keywords/value-types.md).  
  
Poiché i valori letterali sono tipizzati e tutti i tipi derivano in ultima istanza da <xref:System.Object>, è possibile scrivere e compilare codice come il seguente:  
  
[!code-csharp[Literal Values](../../samples/snippets/csharp/concepts/structs/literals.cs)]

Gli ultimi due esempi mostrano le funzionalità del linguaggio introdotte in C# 7.0. Il primo consente di usare un carattere di sottolineatura come un *separatore di cifra* all'interno di valori letterali numerici. È possibile posizionarli ovunque si desideri tra le cifre per migliorare la leggibilità. Non hanno alcun effetto sul valore.

Il secondo indica *valori letterali binari*, che consentono di specificare schemi di bit direttamente anziché usare la notazione esadecimale.

## <a name="nullable-value-types"></a>Tipi valore nullable

I tipi valore comuni non possono avere un valore [null](language-reference/keywords/null.md). È tuttavia possibile creare tipi valore nullable aggiungendo `?` dopo il tipo. Ad esempio, `int?` è un tipo `int` che può avere anche il valore [null](./language-reference/keywords/null.md). I tipi di valore nullable sono istanze del tipo di struct generico <xref:System.Nullable%601>. I tipi di valore nullable sono particolarmente utili quando si passano dati da e verso database in cui i valori numerici possono essere null o non definiti. Per altre informazioni, vedere [tipi di valore Nullable](programming-guide/nullable-types/index.md).

## <a name="see-also"></a>Vedere anche

- [Classi](classes.md)
- [Tipi di base](basic-types.md)
