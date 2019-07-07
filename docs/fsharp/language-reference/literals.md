---
title: Valori letterali
description: Informazioni sui tipi di valore letterali in di F# linguaggio di programmazione.
ms.date: 06/28/2019
ms.openlocfilehash: 0c9ced0b505817a161ca39c6c9f853f94cedf410
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610149"
---
# <a name="literals"></a>Valori letterali

> [!NOTE]
> I collegamenti di riferimento API in questo articolo si passerà a MSDN (per ora).

In questo argomento fornisce una tabella che mostra come specificare il tipo di un valore letterale in F#.

## <a name="literal-types"></a>Tipi letterali

La tabella seguente illustra i tipi di valore letterali in F#. I caratteri che rappresentano cifre in notazione esadecimale non sono tra maiuscole e minuscole; caratteri che identificano il tipo di maiuscole e minuscole.

|Tipo|Descrizione|Prefissi o suffissi|Esempi|
|----|-----------|----------------|--------|
|sbyte|intero con segno a 8 bit|y|`86y`<br /><br />`0b00000101y`|
|byte|Numero naturale senza segno a 8 bit|UY|`86uy`<br /><br />`0b00000101uy`|
|int16|intero con segno a 16 bit|s|`86s`|
|uint16|Numero naturale senza segno a 16 bit|us|`86us`|
|int<br /><br />int32|intero con segno a 32 bit|l o nessuno|`86`<br /><br />`86l`|
|uint<br /><br />uint32|Numero naturale senza segno a 32 bit|u o ul|`86u`<br /><br />`86ul`|
|nativeint|puntatore nativo in un numero naturale con segno|n|`123n`|
|unativeint|puntatore nativo come numero naturale senza segno|Annulla la|`0x00002D3Fun`|
|int64|intero con segno a 64 bit|L|`86L`|
|uint64|Numero naturale senza segno a 64 bit|UL|`86UL`|
|float32 singolo,|numero a virgola mobile a 32 bit|F o f|`4.14F` o `4.14f`|
|||lf|`0x00000000lf`|
|float; Double|numero a virgola mobile a 64 bit|none|`4.14` o `2.3E+32` o `2.3e+32`|
|||LF|`0x0000000000000000LF`|
|bigint|Integer non limitato alla rappresentazione a 64 bit|I|`9999999999999999999999999999I`|
|decimal|numero frazionario rappresentato come un punto fisso o un numero razionale|M o m|`0.7833M` o `0.7833m`|
|Char|Carattere Unicode|none|`'a'`|
|Stringa|Stringa Unicode|none|`"text\n"`<br /><br />oppure<br /><br />`@"c:\filename"`<br /><br />oppure<br /><br />`"""<book title="Paradise Lost">"""`<br /><br />oppure<br /><br />`"string1" + "string2"`<br /><br />Vedere anche [stringhe](Strings.md).|
|byte|Carattere ASCII|B|`'a'B`|
|byte[]|Stringa ASCII|B|`"text"B`|
|String o byte]|stringa verbatim|prefisso @|`@"\\server\share"` (Unicode)<br /><br />`@"\\server\share"B` (ASCII)|

## <a name="named-literals"></a>Valori letterali denominati

I valori che devono essere costanti possono essere contrassegnati con il [letterale](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attributo. Questo attributo ha l'effetto di provocare un valore essere compilato come una costante.

Nelle espressioni dei criteri, gli identificatori che iniziano con caratteri minuscoli vengono sempre trattati come variabili da associare, anziché come valori letterali, pertanto è consigliabile in genere usare lettere maiuscole iniziali quando si definiscono i valori letterali.

```fsharp
[<Literal>]
let SomeJson = """{"numbers":[1,2,3,4,5]}"""

[<Literal>]
let Literal1 = "a" + "b"

[<Literal>]
let FileLocation =   __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let Literal2 = 1 ||| 64

[<Literal>]
let Literal3 = System.IO.FileAccess.Read ||| System.IO.FileAccess.Write
```

## <a name="remarks"></a>Note

Le stringhe Unicode possono contenere codifiche esplicite che è possibile specificare utilizzando `\u` seguita da un codice esadecimale a 16 bit (0000 - FFFF) o le codifiche UTF-32 che è possibile specificare utilizzando `\U` seguita da un codice esadecimale a 32 bit che rappresenta qualsiasi punto di codice Unicode (00000000 - 0010FFFF).

L'uso di altri operatori bit per bit diverso da `|||` non è consentito.

## <a name="integers-in-other-bases"></a>Numeri interi in altre basi

È possibile anche specificare interi con segno a 32 bit binaria, ottale o esadecimale con un `0x`, `0o` o `0b` rispettivamente del prefisso.

```fsharp
let numbers = (0x9F, 0o77, 0b1010)
// Result: numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a>Caratteri di sottolineatura nei valori letterali numerici

È possibile separare cifre con il carattere di sottolineatura (`_`).

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```

## <a name="see-also"></a>Vedere anche

- [Classe Core. LiteralAttribute](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)
