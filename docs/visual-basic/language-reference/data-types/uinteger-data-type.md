---
title: Tipo di dati UInteger
ms.date: 01/31/2018
f1_keywords:
- vb.uinteger
helpviewer_keywords:
- numbers [Visual Basic], whole
- UInteger data type
- literal type characters [Visual Basic], UI
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- UI literal type characters [Visual Basic]
- data types [Visual Basic], integral
ms.assetid: db7ddd34-4f23-46f5-84dd-8b0f83bb8729
ms.openlocfilehash: ccff61608aed797734cb4f5ca0571d7ed73ba98b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343895"
---
# <a name="uinteger-data-type"></a>UInteger (tipo di dati)

Include interi senza segno a 32 bit (4 byte) compresi tra 0 e 4.294.967.295.

## <a name="remarks"></a>Note

Il tipo di dati `UInteger` fornisce il valore senza segno più grande nella larghezza dei dati più efficiente.

Il valore predefinito di `UInteger` è 0.

## <a name="literal-assignments"></a>Assegnazioni di valori letterali

È possibile dichiarare e inizializzare una variabile di `UInteger` assegnando un valore letterale decimale, un valore letterale esadecimale, un valore letterale ottale o (a partire da Visual Basic 2017) un valore letterale binario. Se il valore letterale integer è esterno all'intervallo di `UInteger`, vale a dire se è minore di <xref:System.UInt32.MinValue?displayProperty=nameWithType> o maggiore di <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, si verifica un errore di compilazione.

Nell'esempio seguente, i valori interi uguali a 3.000.000.000 rappresentati come valori letterali decimali, esadecimali o binari vengono assegnati a valori `UInteger`.

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]

> [!NOTE]
> Usare il prefisso `&h` o `&H` per indicare un valore letterale esadecimale, il prefisso `&b` o `&B` per indicare un valore letterale binario e il prefisso `&o` o `&O` per indicare un valore letterale ottale. I valori letterali decimali non hanno prefissi.

A partire da Visual Basic 2017, è anche possibile usare il carattere di sottolineatura, `_`, come separatore di cifre per migliorare la leggibilità, come illustrato nell'esempio seguente.

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]

A partire da Visual Basic 15,5, è anche possibile usare il carattere di sottolineatura (`_`) come separatore iniziale tra il prefisso e le cifre esadecimali, binarie o ottali. Ad esempio:

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

I valori letterali numerici possono includere anche il [carattere di tipo](../../programming-guide/language-features/data-types/type-characters.md) `UI` o `ui` per indicare il tipo di dati `UInteger`, come illustrato nell'esempio seguente.

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a>Suggerimenti per la programmazione

I tipi di dati `UInteger` e `Integer` offrono prestazioni ottimali in un processore a 32 bit, perché i tipi integer più piccoli (`UShort`, `Short`, `Byte`e `SByte`), anche se usano meno bit, richiedono più tempo per il caricamento, l'archiviazione e il recupero.

- **Numeri negativi.** Poiché `UInteger` è un tipo senza segno, non può rappresentare un numero negativo. Se si usa l'operatore meno unario (`-`) su un'espressione che restituisce il tipo `UInteger`, Visual Basic converte prima l'espressione in `Long`.

- **Conformità a CLS.** Il tipo di dati `UInteger` non fa parte della [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), pertanto il codice conforme a CLS non può utilizzare un componente che lo utilizza.

- **Considerazioni sull'interoperabilità.** Se si è connessi con componenti non scritti per il .NET Framework, ad esempio oggetti COM o di automazione, tenere presente che i tipi come `uint` possono avere una larghezza di dati diversa (16 bit) in altri ambienti. Se si passa un argomento a 16 bit a tale componente, dichiararlo come `UShort` anziché `UInteger` nel codice di Visual Basic gestito.

- **Conversioni.** Il tipo di dati `UInteger` viene ampliato in `Long`, `ULong`, `Decimal`, `Single`e `Double`. Ciò significa che è possibile convertire `UInteger` in uno di questi tipi senza riscontrare un errore <xref:System.OverflowException?displayProperty=nameWithType>.

- **Digitare i caratteri.** L'aggiunta di caratteri di tipo letterale `UI` a un valore letterale forza il tipo di dati `UInteger`. `UInteger` non dispone di alcun carattere di tipo identificatore.

- **Tipo di Framework.** Il tipo corrispondente in .NET Framework è la struttura <xref:System.UInt32?displayProperty=nameWithType>.

## <a name="see-also"></a>Vedere anche

- <xref:System.UInt32>
- [Tipi di dati](../../../visual-basic/language-reference/data-types/index.md)
- [CString](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Riepilogo della conversione](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Procedura: Chiamare una funzione Windows che accetta tipi senza segno](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Uso efficiente dei tipi di dati](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
