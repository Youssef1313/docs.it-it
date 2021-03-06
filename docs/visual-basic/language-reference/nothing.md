---
title: Nothing (parola chiave)
ms.date: 07/20/2015
f1_keywords:
- Nothing
- vb.Nothing
helpviewer_keywords:
- Nothing keyword [Visual Basic]
- Nothing keyword [Visual Basic], syntax
ms.assetid: 06176e2d-bbf7-4a37-afaa-a86ad21ee99f
ms.openlocfilehash: 3bd4681341a33cc8db4ecbc2b284be243db56549
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344168"
---
# <a name="nothing-keyword-visual-basic"></a>Parola chiave Nothing (Visual Basic)

Rappresenta il valore predefinito di qualsiasi tipo di dati. Per i tipi di riferimento, il valore predefinito è il riferimento `null`. Per i tipi di valore, il valore predefinito dipende dal tipo di valore che ammette valori null.

> [!NOTE]
> Per i tipi di valore non nullable, `Nothing` in Visual Basic differisce da `null` C#in. In Visual Basic, se si imposta una variabile di un tipo di valore non nullable su `Nothing`, la variabile viene impostata sul valore predefinito per il tipo dichiarato. In C#, se si assegna a `null`una variabile di un tipo di valore non nullable, si verificherà un errore in fase di compilazione.

## <a name="remarks"></a>Note

`Nothing` rappresenta il valore predefinito di un tipo di dati. Il valore predefinito dipende dal fatto che la variabile sia di un tipo di valore o di un tipo di riferimento.

Una variabile di un *tipo di valore* contiene direttamente il relativo valore. I tipi di valore includono tutti i tipi di dati numerici, `Boolean`, `Char`, `Date`, tutte le strutture e tutte le enumerazioni. Una variabile di un *tipo riferimento* archivia un riferimento a un'istanza dell'oggetto in memoria. I tipi di riferimento includono classi, matrici, delegati e stringhe. Per altre informazioni, vedere [Value Types and Reference Types](../programming-guide/language-features/data-types/value-types-and-reference-types.md).

Se una variabile è di un tipo valore, il comportamento di `Nothing` varia a seconda che la variabile sia di un tipo di dati nullable. Per rappresentare un tipo di valore Nullable, aggiungere un modificatore `?` al nome del tipo. Assegnando `Nothing` a una variabile nullable, il valore viene impostato su `null`. Per ulteriori informazioni ed esempi, vedere [tipi di valore Nullable](../programming-guide/language-features/data-types/nullable-value-types.md).

Se una variabile è di un tipo di valore che non ammette valori null, l'assegnazione di `Nothing` a tale variabile lo imposta sul valore predefinito per il tipo dichiarato. Se il tipo contiene membri variabili, vengono impostati tutti sui rispettivi valori predefiniti. Nell'esempio seguente viene illustrato questo per i tipi scalari.

[!code-vb[VbVbalrKeywords#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class2.vb#7)]

Se una variabile è di un tipo riferimento, l'assegnazione di `Nothing` alla variabile lo imposta su un riferimento `null` del tipo della variabile. Una variabile impostata su un riferimento `null` non è associata ad alcun oggetto. Questo concetto è illustrato nell'esempio seguente:

[!code-vb[VbVbalrKeywords#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class3.vb#8)]

Quando si verifica se è `null`una variabile di riferimento (o tipo di valore Nullable), non usare `= Nothing` o `<> Nothing`. Usare sempre `Is Nothing` o `IsNot Nothing`.

Per le stringhe in Visual Basic, la stringa vuota è uguale a `Nothing`. Pertanto, `"" = Nothing` è true.

Nell'esempio seguente vengono illustrati i confronti che utilizzano gli operatori `Is` e `IsNot`:

[!code-vb[VbVbalrKeywords#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class4.vb#9)]

Se si dichiara una variabile senza usare una clausola `As` e la si imposta su `Nothing`, la variabile ha un tipo di `Object`. Un esempio è `Dim something = Nothing`. In questo caso si verifica un errore in fase di compilazione quando `Option Strict` è on e `Option Infer` è disattivato.

Quando si assegna `Nothing` a una variabile oggetto, non fa più riferimento a un'istanza dell'oggetto. Se la variabile ha precedentemente fatto riferimento a un'istanza, impostarla su `Nothing` non termina l'istanza stessa. L'istanza viene terminata e le risorse di memoria e di sistema associate vengono rilasciate, solo dopo che il Garbage Collector (GC) rileva che non sono presenti riferimenti attivi rimanenti.

`Nothing` differisce dall'oggetto <xref:System.DBNull>, che rappresenta una variante non inizializzata o una colonna del database inesistente.

## <a name="see-also"></a>Vedere anche

- [Istruzione Dim](./statements/dim-statement.md)
- [Durata degli oggetti: come creare e distruggere oggetti](../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Durata in Visual Basic](../programming-guide/language-features/declared-elements/lifetime.md)
- [Operatore Is](./operators/is-operator.md)
- [Operatore IsNot](./operators/isnot-operator.md)
- [Tipi di valori nullable](../programming-guide/language-features/data-types/nullable-value-types.md)
