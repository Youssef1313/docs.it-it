---
title: Main() e argomenti della riga di comando - Guida per programmatori C#
ms.custom: seodec18
ms.date: 08/02/2017
f1_keywords:
- CS5001
- main_CSharpKeyword
- Main
helpviewer_keywords:
- Main method [C#]
- C# language, command-line arguments
- arguments [C#], command-line
- command line [C#], arguments
- command-line arguments [C#], Main method
ms.assetid: 73a17231-cf96-44ea-aa8a-54807c6fb1f4
ms.openlocfilehash: db4464cdd3d98103bbc61b824081b59cb1e01cb9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588913"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a>Main() e argomenti della riga di comando (Guida per programmatori C#)

Il metodo `Main` è il punto di ingresso di un'applicazione C#. Le librerie e i servizi non richiedono un metodo `Main` come punto di ingresso. All'avvio dell'applicazione, `Main` è il primo metodo richiamato.

 In un programma C# può essere presente un solo punto di ingresso. Se sono presenti più classi con un metodo `Main`, è necessario compilare il programma con l'opzione del compilatore **/main** per specificare quale metodo `Main` deve essere usato come punto di ingresso. Per altre informazioni, vedere [/main (Opzioni del compilatore C#)](../../language-reference/compiler-options/main-compiler-option.md).

 [!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

## <a name="overview"></a>Panoramica

- Il metodo `Main` è il punto di ingresso di un programma eseguibile, ovvero il punto in cui il controllo del programma inizia e termina.
- `Main` viene dichiarato in una classe o in un tipo struct. `Main` deve essere [static](../../language-reference/keywords/static.md) e non [public](../../language-reference/keywords/public.md). Nell'esempio precedente riceve l'accesso predefinito di [private](../../language-reference/keywords/private.md). Non è necessario che la classe o il tipo struct che lo contiene sia statico.
- Il tipo restituito da `Main` può essere `void`, `int` o, a partire da C# 7.1, `Task` o `Task<int>`.
- Se e solo se `Main` restituisce `Task` o `Task<int>`, la dichiarazione di `Main` può includere il modificatore [`async`](../../language-reference/keywords/async.md). Si noti che questo esclude specificamente un metodo `async void Main`.
- Il metodo `Main` può essere dichiarato con o senza un parametro `string[]` contenente argomenti della riga di comando. Quando si usa Visual Studio per creare applicazioni Windows, è possibile aggiungere il parametro manualmente o usare la classe <xref:System.Environment> per ottenere gli argomenti della riga di comando. I parametri vengono letti come argomenti della riga di comando a indice zero. A differenza di quanto avviene in C e C++, il nome del programma non viene considerato il primo argomento della riga di comando.

L'aggiunta dei tipi restituiti `async`, `Task` e `Task<int>` semplifica il codice del programma quando è necessario avviare le applicazioni console e per operazioni asincrone `await` in `Main`.

## <a name="c-language-specification"></a>Specifiche del linguaggio C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Vedere anche

- [Compilazione dalla riga di comando con csc.exe](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [Guida per programmatori C#](../index.md)
- [Metodi](../classes-and-structs/methods.md)
- [Contenuto di un programma C#](../inside-a-program/index.md)
