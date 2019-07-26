---
title: 'Procedura: Chiamare un metodo di estensione (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: f2058162ab939d2619d7255c884d88c35ee63715
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512668"
---
# <a name="how-to-call-an-extension-method-visual-basic"></a><span data-ttu-id="33d6f-102">Procedura: Chiamare un metodo di estensione (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33d6f-102">How to: Call an Extension Method (Visual Basic)</span></span>

<span data-ttu-id="33d6f-103">I metodi di estensione consentono di aggiungere metodi a una classe esistente.</span><span class="sxs-lookup"><span data-stu-id="33d6f-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="33d6f-104">Dopo che un metodo di estensione è stato dichiarato e introdotto nell'ambito, è possibile chiamarlo come metodo di istanza del tipo che estende.</span><span class="sxs-lookup"><span data-stu-id="33d6f-104">After an extension method is declared and brought into scope, you can call it like an instance method of the type that it extends.</span></span> <span data-ttu-id="33d6f-105">Per ulteriori informazioni su come scrivere un metodo di estensione, vedere [procedura: Scrivere un metodo](./how-to-write-an-extension-method.md)di estensione.</span><span class="sxs-lookup"><span data-stu-id="33d6f-105">For more information about how to write an extension method, see [How to: Write an Extension Method](./how-to-write-an-extension-method.md).</span></span>

 <span data-ttu-id="33d6f-106">Nelle istruzioni seguenti si fa riferimento al `PrintAndPunctuate`metodo di estensione, che consente di visualizzare l'istanza di stringa che la richiama, seguito da qualsiasi valore inviato per il secondo `punc`parametro,.</span><span class="sxs-lookup"><span data-stu-id="33d6f-106">The following instructions refer to extension method `PrintAndPunctuate`, which will display the string instance that invokes it, followed by whatever value is sent in for the second parameter, `punc`.</span></span>

```vb
Imports System.Runtime.CompilerServices

Module StringExtensions
    <Extension()>
    Public Sub PrintAndPunctuate(ByVal aString As String,
                                 ByVal punc As String)
        Console.WriteLine(aString & punc)
    End Sub

End Module
```

<span data-ttu-id="33d6f-107">Il metodo deve essere nell'ambito quando viene chiamato.</span><span class="sxs-lookup"><span data-stu-id="33d6f-107">The method must be in scope when it is called.</span></span>

### <a name="to-call-an-extension-method"></a><span data-ttu-id="33d6f-108">Per chiamare un metodo di estensione</span><span class="sxs-lookup"><span data-stu-id="33d6f-108">To call an extension method</span></span>

1. <span data-ttu-id="33d6f-109">Dichiarare una variabile con il tipo di dati del primo parametro del metodo di estensione.</span><span class="sxs-lookup"><span data-stu-id="33d6f-109">Declare a variable that has the data type of the first parameter of the extension method.</span></span> <span data-ttu-id="33d6f-110">Per `PrintAndPunctuate`è necessaria una <xref:System.String> variabile:</span><span class="sxs-lookup"><span data-stu-id="33d6f-110">For `PrintAndPunctuate`, you need a <xref:System.String> variable:</span></span>

    ```vb
    Dim example = "Ready"
    ```

2. <span data-ttu-id="33d6f-111">Tale variabile richiamerà il metodo di estensione e il relativo valore verrà associato al primo parametro `aString`.</span><span class="sxs-lookup"><span data-stu-id="33d6f-111">That variable will invoke the extension method, and its value is bound to the first parameter, `aString`.</span></span> <span data-ttu-id="33d6f-112">Viene visualizzata `Ready?`la seguente istruzione chiamante.</span><span class="sxs-lookup"><span data-stu-id="33d6f-112">The following calling statement will display `Ready?`.</span></span>

    ```vb
    example.PrintAndPunctuate("?")
    ```

     <span data-ttu-id="33d6f-113">Si noti che la chiamata a questo metodo di estensione è simile a una chiamata a uno dei <xref:System.String> metodi di istanza che richiedono un solo parametro:</span><span class="sxs-lookup"><span data-stu-id="33d6f-113">Notice that the call to this extension method looks just like a call to any one of the <xref:System.String> instance methods that require one parameter:</span></span>

    ```vb
    example.EndsWith("dy")
    example.IndexOf("R")
    ```

3. <span data-ttu-id="33d6f-114">Dichiarare un'altra variabile di stringa e chiamare di nuovo il metodo per verificare che funzioni con qualsiasi stringa.</span><span class="sxs-lookup"><span data-stu-id="33d6f-114">Declare another string variable and call the method again to see that it works with any string.</span></span>

    ```vb
    Dim example2 = " or not"
    example2.PrintAndPunctuate("!!!")
    ```

     <span data-ttu-id="33d6f-115">Il risultato è il seguente: `or not!!!`.</span><span class="sxs-lookup"><span data-stu-id="33d6f-115">The result this time is: `or not!!!`.</span></span>

## <a name="example"></a><span data-ttu-id="33d6f-116">Esempio</span><span class="sxs-lookup"><span data-stu-id="33d6f-116">Example</span></span>
 <span data-ttu-id="33d6f-117">Il codice seguente è un esempio completo della creazione e dell'uso di un semplice metodo di estensione.</span><span class="sxs-lookup"><span data-stu-id="33d6f-117">The following code is a complete example of the creation and use of a simple extension method.</span></span>

```vb
Imports System.Runtime.CompilerServices
Imports ConsoleApplication1.StringExtensions

Module Module1

    Sub Main()

        Dim example = "Hello"
        example.PrintAndPunctuate(".")
        example.PrintAndPunctuate("!!!!")

        Dim example2 = "Goodbye"
        example2.PrintAndPunctuate("?")
    End Sub

    <Extension()>
    Public Sub PrintAndPunctuate(ByVal aString As String,
                                 ByVal punc As String)
        Console.WriteLine(aString & punc)
    End Sub
End Module

' Output:
' Hello.
' Hello!!!!
' Goodbye?
```

## <a name="see-also"></a><span data-ttu-id="33d6f-118">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="33d6f-118">See also</span></span>

- [<span data-ttu-id="33d6f-119">Procedura: Scrivere un metodo di estensione</span><span class="sxs-lookup"><span data-stu-id="33d6f-119">How to: Write an Extension Method</span></span>](./how-to-write-an-extension-method.md)
- [<span data-ttu-id="33d6f-120">Metodi di estensione</span><span class="sxs-lookup"><span data-stu-id="33d6f-120">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="33d6f-121">Ambito in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="33d6f-121">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
