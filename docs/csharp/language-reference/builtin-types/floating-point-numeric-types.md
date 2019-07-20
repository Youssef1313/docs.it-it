---
title: Tipi numerici a virgola mobile - Riferimenti per C#
description: Panoramica dei tipi a virgola mobile incorporati di C#
ms.date: 06/30/2019
f1_keywords:
- float
- float_CSharpKeyword
- double
- double_CSharpKeyword
- decimal_CSharpKeyword
- decimal
helpviewer_keywords:
- floating-point numbers [C#]
- ranges of floating-point types [C#]
- types [C#], floating-point types
- float keyword [C#]
- floating-point numbers [C#], float keyword
- double data type [C#]
- decimal keyword [C#]
ms.openlocfilehash: 738368abd9db75fbd97d1913324cab3b6e869c56
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/09/2019
ms.locfileid: "67664191"
---
# <a name="floating-point-numeric-types-c-reference"></a>Tipi numerici a virgola mobile (riferimenti per C#)

I **tipi numerici a virgola mobile** sono un subset dei **tipi semplici** e possono essere inizializzati con [*valori letterali*](#floating-point-literals). Tutti i tipi a virgola mobile sono anche tipi di valore. Tutti i tipi numerici a virgola mobile supportano gli operatori [aritmetici](../operators/arithmetic-operators.md), [di confronto e di uguaglianza](../operators/equality-operators.md).

La tabella seguente illustra la precisione e gli intervalli approssimativi per i tipi a virgola mobile:
  
|Tipo|Intervallo approssimativo|Precisione|  
|----------|-----------------------|---------------|  
|`float`|Compreso tra ±1.5 x 10<sup>−45</sup> e ±3.4 x 10<sup>38</sup>|~6-9 cifre|  
|`double`|Compreso tra ±5,0 × 10<sup>−324</sup> e ±1,7 × 10<sup>308</sup>|~15-17 cifre|  
|`decimal`|Compreso tra ±1.0 x 10<sup>-28</sup> e ±7.9228 x 10<sup>28</sup>|28-29 cifre|  

Il valore predefinito per tutti i tipi a virgola mobile è `0`. Ogni tipo a virgola mobile ha costanti denominate `MinValue` e `MaxValue` per il valore minimo e massimo del tipo. I tipi `float` e `double` hanno costanti aggiuntive per `PositiveInfinity`, `NegativeInfinity`, e `NaN` (per "Non un numero"). Il tipo `decimal` include costanti per `Zero`, `One` e `MinusOne`.

Il tipo `decimal` è caratterizzato da una maggiore precisione e da un intervallo ridotto rispetto a `float` e `double`, che lo rendono appropriato per calcoli finanziari e monetari.

In un'espressione è possibile combinare tipi integrali e tipi a virgola mobile. In questo caso i tipi integrali vengono convertiti in tipi a virgola mobile. La valutazione dell'espressione viene eseguita in base alle regole seguenti:

- Se uno dei tipi a virgola mobile è `double`, l'espressione restituirà un valore `double` o [bool](../keywords/bool.md) nei confronti relazionali o nei confronti per l'uguaglianza.
- Se l'espressione non contiene un tipo `double`, restituirà un valore `float` o [bool](../keywords/bool.md) nei confronti relazionali o nei confronti per l'uguaglianza.

Un'espressione a virgola mobile può contenere gli insiemi di valori seguenti:

- Zero positivo e negativo
- Infinito positivo e negativo
- Non un numero
- Insieme finito di valori diversi da zero

Per altre informazioni su questi valori, vedere lo standard IEEE per l'aritmetica a virgola mobile binaria, disponibile nel sito Web [IEEE](https://www.ieee.org).

È possibile usare [stringhe di formato numerico standard](../../../standard/base-types/standard-numeric-format-strings.md) oppure [stringhe di formato numerico personalizzato](../../../standard/base-types/custom-numeric-format-strings.md) per formattare un valore a virgola mobile.

## <a name="floating-point-literals"></a>Valori letterali a virgola mobile

Per impostazione predefinita, un valore letterale numerico a virgola mobile a destra dell'operatore di assegnazione viene gestito come tipo `double`. È possibile usare suffissi per convertire un valore letterale a virgola mobile o integrale in un tipo specifico:

- Il suffisso `d` o `D` converte un valore letterale in un tipo `double`.
- Il suffisso `f` o `F` converte un valore letterale in un tipo `float`.
- Il suffisso `m` o `M` converte un valore letterale in un tipo `decimal`.

Negli esempi riportati di seguito viene illustrato ogni suffisso:

```csharp
double d = 3D;
d = 4d;
float f = 3.5F;
f = 5.4f;
decimal myMoney = 300.5m;
myMoney = 400.75M;
```

## <a name="conversions"></a>Conversioni

La conversione è implicita (denominata *conversione verso un tipo di dati più grande*) da `float` in `double` perché l'intervallo di valori `float` è un subset corretto di `double` e non si perde precisione da `float` in `double`. 

È necessario usare un cast esplicito per convertire un tipo a virgola mobile in un altro tipo a virgola mobile quando non è definita una conversione implicita dal tipo di origine nel tipo di destinazione. Questa operazione è definita *conversione verso un tipo di dati più piccolo*. Il caso esplicito è necessario perché la conversione può comportare una perdita di dati. La conversione non è implicita tra altri tipi a virgola mobile e il tipo `decimal` perché il tipo `decimal` ha una maggiore precisione rispetto a `float` o `double`.

Per altre informazioni sulle conversioni numeriche implicite, vedere [Tabella delle conversioni numeriche implicite](../keywords/implicit-numeric-conversions-table.md).

Per altre informazioni sulle conversioni numeriche esplicite, vedere [Tabella delle conversioni numeriche esplicite](../keywords/explicit-numeric-conversions-table.md).

## <a name="see-also"></a>Vedere anche

- [Riferimenti per C#](../index.md)
- [Tipi integrali](integral-numeric-types.md)
- [Tabella dei valori predefiniti](../keywords/default-values-table.md)
- [Tabella di formattazione dei risultati numerici](../keywords/formatting-numeric-results-table.md)
- [Tabella dei tipi incorporati](../keywords/built-in-types-table.md)
- [Dati numerici in .NET](../../../standard/numerics.md)
- [Cast e conversioni di tipi](../../programming-guide/types/casting-and-type-conversions.md)
- [Tabella delle conversioni numeriche implicite](../keywords/implicit-numeric-conversions-table.md)
- [Tabella delle conversioni numeriche esplicite](../keywords/explicit-numeric-conversions-table.md)
- <xref:System.Single?displayProperty=nameWithType>
- <xref:System.Double?displayProperty=nameWithType>
- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
- [Standard Numeric Format Strings](../../../standard/base-types/standard-numeric-format-strings.md)