---
title: Istruzione using - Riferimenti per C#
ms.custom: seodec18
ms.date: 10/15/2019
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: f5ff78eaf9d565a9708c7a3a11754579389e79e8
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422241"
---
# <a name="using-statement-c-reference"></a>Istruzione using (Riferimenti per C#)

Offre una comoda sintassi che verifica l'uso corretto degli oggetti <xref:System.IDisposable>.

## <a name="example"></a>Esempio

L'esempio seguente mostra come usare l'istruzione `using`.

[!code-csharp[csrefKeywordsNamespace#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#4)]

A partire C# da 8,0, è possibile usare la sintassi alternativa seguente per l'istruzione `using` che non richiede le parentesi graffe:

[!code-csharp[csrefKeywordsNamespace#New](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#ModernUsing)]

## <a name="remarks"></a>Note

<xref:System.IO.File> e <xref:System.Drawing.Font> sono esempi di tipi gestiti che accedono a risorse non gestite (in questo caso handle di file e contesti di dispositivo). Esistono molti altri tipi di risorse non gestite e tipi della libreria di classi che le incapsulano. Ogni tipo deve implementare l'interfaccia <xref:System.IDisposable>.

Quando la durata di un oggetto `IDisposable` è limitata a un singolo metodo, è necessario dichiararlo e creare un'istanza nell'istruzione `using`. L'istruzione `using` chiama il metodo <xref:System.IDisposable.Dispose%2A> sull'oggetto in modo corretto e, quando viene usata come illustrato in precedenza, fa in modo che l'oggetto stesso esca dall'ambito non appena viene chiamato il metodo <xref:System.IDisposable.Dispose%2A>. All'interno del blocco `using` l'oggetto è di sola lettura e non può essere modificato o riassegnato.

L'istruzione `using` garantisce che <xref:System.IDisposable.Dispose%2A> venga chiamato anche se si verifica un'eccezione nel blocco `using`. È possibile ottenere lo stesso risultato inserendo l'oggetto all'interno di un blocco `try` e chiamando <xref:System.IDisposable.Dispose%2A> in un blocco `finally`. Di fatto questo è il modo in cui l'istruzione `using` viene convertita dal compilatore. L'esempio di codice precedente si espande al codice seguente in fase di compilazione (si notino le parentesi graffe aggiuntive per creare l'ambito limitato per l'oggetto):

[!code-csharp[csrefKeywordsNamespace#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#5)]

La sintassi dell'istruzione `using` più recente si traduce in codice molto simile. Il blocco `try` viene aperto in cui viene dichiarata la variabile. Il blocco `finally` viene aggiunto alla chiusura del blocco di inclusione, in genere alla fine di un metodo.

Per altre informazioni sull'istruzione `try`-`finally`, vedere l'argomento [try-finally](try-finally.md).

È possibile dichiarare più istanze di un tipo nell'istruzione `using`, come illustrato nell'esempio seguente:

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#6)]

È possibile combinare più dichiarazioni dello stesso tipo usando la nuova sintassi introdotta anche con C# 8. Questa operazione è illustrata nell'esempio seguente:

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#MultipleUsing)]

È possibile creare un'istanza dell'oggetto risorsa e quindi passare la variabile all'istruzione `using`, ma questa procedura non è consigliata. In questo caso l'oggetto rimane nell'ambito quando il controllo lascia il blocco `using`, anche se probabilmente non avrà più accesso alle relative risorse non gestite. In altre parole, non è più completamente inizializzato. Se si tenta di usare l'oggetto di fuori del blocco `using`, si rischia di causare la generazione di un'eccezione. Per questo motivo, in genere è preferibile creare un'istanza dell'oggetto nell'istruzione `using` e limitare l'ambito al blocco `using`.

[!code-csharp[csrefKeywordsNamespace#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#7)]

Per altre informazioni sull'eliminazione degli oggetti `IDisposable`, vedere [Uso di oggetti che implementano IDisposable](../../../standard/garbage-collection/using-objects.md).

## <a name="c-language-specification"></a>Specifiche del linguaggio C#

Per altre informazioni, vedere [Istruzione using](~/_csharplang/spec/statements.md#the-using-statement) nella [specifica del linguaggio C#](/dotnet/csharp/language-reference/language-specification/introduction). La specifica del linguaggio costituisce il riferimento ufficiale principale per la sintassi e l'uso di C#.

## <a name="see-also"></a>Vedere anche

- [Riferimenti per C#](../index.md)
- [Guida per programmatori C#](../../programming-guide/index.md)
- [Parole chiave di C#](index.md)
- [Direttiva using](using-directive.md)
- [Garbage Collection](../../../standard/garbage-collection/index.md)
- [Uso di oggetti che implementano IDisposable](../../../standard/garbage-collection/using-objects.md)
- [Interfaccia IDisposable](xref:System.IDisposable)
- [istruzione using in C# 8,0](~/_csharplang/proposals/csharp-8.0/using.md)
