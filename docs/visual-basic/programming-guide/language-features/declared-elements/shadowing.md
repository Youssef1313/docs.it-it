---
title: Shadowing
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], shadowing
- overriding, and shadowing
- shadowing
- duplicate names [Visual Basic]
- shadowing, by inheritance
- declared elements [Visual Basic], referencing
- shadowing, by scope
- declared elements [Visual Basic], hiding
- naming conflicts, shadowing
- declared elements [Visual Basic], shadowing
- shadowing, and overriding
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic], about
- objects [Visual Basic], names
- names [Visual Basic], shadowing
ms.assetid: 54bb4c25-12c4-4181-b4a0-93546053964e
ms.openlocfilehash: 034b5c0ecf3be6e77048fb7318e931801575f07a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345320"
---
# <a name="shadowing-in-visual-basic"></a>Shadowing in Visual Basic
Quando due elementi di programmazione condividono lo stesso nome, uno di essi può nascondere, o *ombreggiare*, l'altro. In una situazione di questo tipo, l'elemento ombreggiato non è disponibile per riferimento. al contrario, quando il codice usa il nome dell'elemento, il compilatore Visual Basic lo risolve nell'elemento ombreggiatura.  
  
## <a name="purpose"></a>Scopo  
 Lo scopo principale dello shadowing consiste nel proteggere la definizione dei membri della classe. La classe base può subire una modifica che crea un elemento con lo stesso nome di uno già definito. In tal caso, il modificatore di `Shadows` impone la risoluzione dei riferimenti attraverso la classe al membro definito, anziché al nuovo elemento della classe base.  
  
## <a name="types-of-shadowing"></a>Tipi di ombreggiatura  
 Un elemento può nascondere un altro elemento in due modi diversi. L'elemento shadowing può essere dichiarato all'interno di un'area secondaria dell'area contenente l'elemento ombreggiato, nel qual caso l'ombreggiatura viene eseguita *tramite l'ambito*. O una classe di derivazione può ridefinire un membro di una classe di base, nel qual caso l'ombreggiatura viene eseguita *tramite ereditarietà*.  
  
### <a name="shadowing-through-scope"></a>Shadowing tramite ambito  
 È possibile che gli elementi di programmazione dello stesso modulo, classe o struttura abbiano lo stesso nome ma un ambito diverso. Quando due elementi sono dichiarati in questo modo e il codice fa riferimento al nome che condividono, l'elemento con l'ambito più piccolo ombreggia l'altro elemento (l'ambito del blocco è il più piccolo).  
  
 Un modulo, ad esempio, può definire una variabile di `Public` denominata `temp`e una routine all'interno del modulo può dichiarare una variabile locale denominata `temp`. I riferimenti a `temp` dall'interno della procedura accedono alla variabile locale, mentre i riferimenti a `temp` dall'esterno della procedura accedono alla variabile `Public`. In questo caso, la variabile di routine `temp` nasconde la variabile del modulo `temp`.  
  
 Nella figura seguente sono illustrate due variabili, entrambe denominate `temp`. La variabile locale `temp` nasconde la variabile membro `temp` quando viene eseguito l'accesso dall'interno della propria procedura `p`. Tuttavia, la parola chiave `MyClass` ignora lo shadowing e accede alla variabile membro.  
  
 ![Immagine che mostra lo shadowing attraverso l'ambito.](./media/shadowing/shadow-scope-diagram.gif)
  
 Per un esempio di shadowing tramite l'ambito, vedere [procedura: nascondere una variabile con lo stesso nome della variabile](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).  
  
### <a name="shadowing-through-inheritance"></a>Shadowing tramite ereditarietà  
 Se una classe derivata ridefinisce un elemento di programmazione ereditato da una classe base, l'elemento di ridefinizione nasconde l'elemento originale. È possibile nascondere qualsiasi tipo di elemento dichiarato o set di elementi di overload con qualsiasi altro tipo. Ad esempio, una variabile di `Integer` può nascondere una `Function` routine. Se si nasconde una routine con un'altra procedura, è possibile usare un elenco di parametri diverso e un tipo restituito diverso.  
  
 Nella figura seguente vengono illustrati una `b` della classe di base e una classe derivata `d` che eredita da `b`. La classe base definisce una routine denominata `proc`e la classe derivata la nasconde con un'altra routine con lo stesso nome. La prima istruzione `Call` accede al `proc` shadowing nella classe derivata. Tuttavia, la parola chiave `MyBase` ignora lo shadowing e accede alla procedura ombreggiata nella classe di base.  
  
 ![Diagramma grafico dello shadowing tramite eredità](./media/shadowing/shadowing-inherit-diagram.gif)  
  
 Per un esempio di shadowing tramite ereditarietà, vedere [procedura: nascondere una variabile con lo stesso nome della variabile](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) e [procedura: nascondere una variabile ereditata](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).  
  
#### <a name="shadowing-and-access-level"></a>Ombreggiatura e livello di accesso  
 L'elemento shadowing non è sempre accessibile dal codice usando la classe derivata. Ad esempio, potrebbe essere dichiarata `Private`. In tal caso, lo shadowing viene sconfitto e il compilatore risolve tutti i riferimenti allo stesso elemento che avrebbe se non fosse presente alcuna ombreggiatura. Questo elemento è l'elemento accessibile, il minor numero di passaggi derivazionali dalla classe shadowing. Se l'elemento ombreggiato è una routine, la risoluzione è la versione accessibile più vicina con lo stesso nome, l'elenco di parametri e il tipo restituito.  
  
 Nell'esempio seguente viene illustrata una gerarchia di ereditarietà di tre classi. Ogni classe definisce una procedura `Sub` `display`e ogni classe derivata nasconde la routine `display` nella relativa classe base.  
  
```vb  
Public Class firstClass  
    Public Sub display()  
        MsgBox("This is firstClass")  
    End Sub  
End Class  
Public Class secondClass  
    Inherits firstClass  
    Private Shadows Sub display()  
        MsgBox("This is secondClass")  
    End Sub  
End Class  
Public Class thirdClass  
    Inherits secondClass  
    Public Shadows Sub display()  
        MsgBox("This is thirdClass")  
    End Sub  
End Class  
Module callDisplay  
    Dim first As New firstClass  
    Dim second As New secondClass  
    Dim third As New thirdClass  
    Public Sub callDisplayProcedures()  
        ' The following statement displays "This is firstClass".  
        first.display()  
        ' The following statement displays "This is firstClass".  
        second.display()  
        ' The following statement displays "This is thirdClass".  
        third.display()  
    End Sub  
End Module  
```  
  
 Nell'esempio precedente, la classe derivata `secondClass` Shadows `display` con una procedura di `Private`. Quando il modulo `callDisplay` chiama `display` in `secondClass`, il codice chiamante è esterno `secondClass` e pertanto non può accedere alla procedura `display` privata. Lo shadowing viene sconfitto e il compilatore risolve il riferimento alla classe di base `display` routine.  
  
 Tuttavia, l'ulteriore classe derivata `thirdClass` dichiara `display` come `Public`, quindi il codice `callDisplay` può accedervi.  
  
## <a name="shadowing-and-overriding"></a>Shadowing e override  
 Non confondere lo shadowing con l'override di. Entrambi vengono usati quando una classe derivata eredita da una classe di base ed entrambi ridefiniscono un elemento dichiarato con un altro. Tuttavia, esistono differenze significative tra i due. Per un confronto, vedere [differenze tra shadowing e override](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).  
  
## <a name="shadowing-and-overloading"></a>Shadowing e overload  
 Se si nasconde lo stesso elemento della classe di base con più di un elemento della classe derivata, gli elementi di shadowing diventano versioni di overload di tale elemento. Per altre informazioni, vedere [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).  
  
## <a name="accessing-a-shadowed-element"></a>Accesso a un elemento ombreggiato  
 Quando si accede a un elemento da una classe derivata, in genere si esegue questa operazione attraverso l'istanza corrente della classe derivata, qualificando il nome dell'elemento con la parola chiave `Me`. Se la classe derivata nasconde l'elemento nella classe di base, è possibile accedere all'elemento della classe base qualificando la parola chiave `MyBase`.  
  
 Per un esempio di accesso a un elemento ombreggiato, vedere [procedura: accedere a una variabile nascosta da una classe derivata](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).  
  
### <a name="declaration-of-the-object-variable"></a>Dichiarazione della variabile oggetto  
 La modalità di creazione della variabile oggetto può influire anche sul fatto che la classe derivata acceda a un elemento ombreggiato o all'elemento ombreggiato. Nell'esempio seguente vengono creati due oggetti da una classe derivata, ma un oggetto viene dichiarato come la classe base e l'altro come classe derivata.  
  
```vb  
Public Class baseCls  
    ' The following statement declares the element that is to be shadowed.  
    Public z As Integer = 100  
End Class  
Public Class dervCls  
    Inherits baseCls  
    ' The following statement declares the shadowing element.  
    Public Shadows z As String = "*"  
End Class  
Public Class useClasses  
    ' The following statement creates the object declared as the base class.  
    Dim basObj As baseCls = New dervCls()  
    ' Note that dervCls widens to its base class baseCls.  
    ' The following statement creates the object declared as the derived class.  
    Dim derObj As dervCls = New dervCls()  
    Public Sub showZ()   
    ' The following statement outputs 100 (the shadowed element).  
        MsgBox("Accessed through base class: " & basObj.z)  
    ' The following statement outputs "*" (the shadowing element).  
        MsgBox("Accessed through derived class: " & derObj.z)  
    End Sub  
End Class  
```  
  
 Nell'esempio precedente, la variabile `basObj` viene dichiarata come classe base. L'assegnazione di un oggetto `dervCls` a esso costituisce una conversione verso un tipo di conversione più ampio ed è quindi valida. Tuttavia, la classe base non può accedere alla versione Shadow della variabile `z` nella classe derivata, quindi il compilatore risolve `basObj.z` nel valore della classe di base originale.  
  
## <a name="see-also"></a>Vedere anche

- [Riferimenti a elementi dichiarati](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Ambito in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Conversioni di ampliamento e restrizione](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me, My, MyBase e MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Nozioni fondamentali sull'ereditarietà](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
