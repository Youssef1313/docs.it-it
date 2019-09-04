---
title: Metodo CLR per il mapping di funzioni canoniche
ms.date: 03/30/2017
ms.assetid: e3363261-2cb8-4b54-9555-2870be99b929
ms.openlocfilehash: 6f14ad8d9e8f919fe820447cc991b102319b38d5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251217"
---
# <a name="clr-method-to-canonical-function-mapping"></a>Metodo CLR per il mapping di funzioni canoniche

In Entity Framework è disponibile un set di funzioni canoniche che implementano funzionalità comuni in numerosi sistemi di database, ad esempio modifica delle stringhe e funzioni matematiche. In questo modo gli sviluppatori possono scegliere come destinazione un'ampia gamma di sistemi di database. In caso di chiamata da una tecnologia di query, ad esempio LINQ to Entities, queste funzioni canoniche vengono convertite nella funzione di archivio corrispondente appropriata per il provider usato. Le chiamate alle funzioni possono pertanto essere espresse con una forma comune indipendentemente dall'origine dati, per offrire un'esperienza di query coerente in diverse origini dati. Anche gli operatori AND, OR, NOT e XOR bit per bit vengono mappati alle funzioni canoniche quando l'operando è un tipo numerico. Per gli operandi booleani, gli operatori AND, OR, NOT e XOR bit per bit calcolano le operazioni AND, OR, NOT e XOR dei relativi operandi. Per altre informazioni, vedere [funzioni canoniche](canonical-functions.md).

Per gli scenari LINQ, le query su Entity Framework comportano il mapping di determinati metodi CLR ai metodi nell'origine dati sottostante tramite funzioni canoniche. Qualsiasi chiamata ai metodi in una query LINQ to Entities non mappata in modo esplicito a una funzione canonica comporta la generazione di un'eccezione <xref:System.NotSupportedException> in fase di runtime.

## <a name="systemstring-method-static-mapping"></a>Mapping del metodo System.String (statico)

|Metodo System.String (statico)|Funzione canonica|
|-------------------------------------|------------------------|
|System.String Concat(String `str0`, String `str1`)|Concat(`str0`, `str1`)|
|System.String Concat(String `str0`, String `str1`, String `str2`)|Concat(Concat(`str0`, `str1`), `str2`)|
|System.String Concat(String `str0`, String `str1`, String `str2`, String `str03`)|Concat(Concat(Concat(`str0`, `str1`), `str2`), `str3`)|
|Boolean Equals(String `a`, String `b`)|= (operatore)|
|Boolean IsNullOrEmpty(String `value`)|(IsNull(`value`)) OR Length(`value`) = 0|
|Boolean op_Equality(String `a`, String `b`)|= (operatore)|
|Boolean op_Inequality(String `a`, String `b`)|!= (operatore)|
|Microsoft.VisualBasic.Strings.Trim(String `str`)|Trim(`str`)|
|Microsoft.VisualBasic.Strings.LTrim(String `str`)|Ltrim(`str`)|
|Microsoft.VisualBasic.Strings.RTrim(String `str`)|Rtrim(`str`)|
|Microsoft.VisualBasic.Strings.Len(String `expression`)|Length(`expression`)|
|Microsoft.VisualBasic.Strings.Left(String `str`, Int32 `Length`)|Left(`str`, `Length`)|
|Microsoft.VisualBasic.Strings.Mid(String `str`, Int32 `Start`, Int32 `Length`)|Substring(`str`, `Start`, `Length`)|
|Microsoft.VisualBasic.Strings.Right(String `str`, Int32 `Length`)|Right(`str`, `Length`)|
|Microsoft.VisualBasic.Strings.UCase(String `Value`)|ToUpper(`Value`)|
|Microsoft.VisualBasic.Strings.LCase(String Value)|ToLower(`Value`)|

## <a name="systemstring-method-instance-mapping"></a>Mapping del metodo System.String (istanza)

|Metodo System.String (istanza)|Funzione canonica|Note|
|---------------------------------------|------------------------|-----------|
|Boolean Contains(String `value`)|`this` LIKE '%`value`%'|Se `value` non è una costante, viene eseguito il mapping a IndexOf`this`( `value`,) > 0|
|Boolean EndsWith(String `value`)|`this`LIKE `'` '% `value`|Se `value` non è una costante, viene eseguito il mapping a Right(`this`, length(`value`)) = `value`.|
|Boolean StartsWith(String `value`)|`this` LIKE '`value`%'|Se `value` non è una costante, viene eseguito il mapping a IndexOf(`this`, `value`) = 1.|
|Length|Length(`this`)||
|Int32 IndexOf(String `value`)|IndexOf(`this`, `value`) - 1||
|System.String Insert(Int32 `startIndex`, String `value`)|Concat(Concat(Substring(`this`, 1, `startIndex`), `value`), Substring(`this`, `startIndex`+1, Length(`this`) - `startIndex`))||
|System.String Remove(Int32 `startIndex`)|Substring(`this`, 1, `startIndex`)||
|System.String Remove(Int32 `startIndex`, Int32 `count`)|Concat (substring (`this`,1, `startIndex`), SUBSTRING`count`(`this`, `count`  +  `startIndex` + 1, Length (`this`)-(`startIndex` + )))|Remove(`startIndex`, `count`) è supportato solo se `count` è un valore intero maggiore o uguale a 0.|
|System.String Replace(String `oldValue`, String `newValue`)|Replace(`this`, `oldValue`, `newValue`)||
|System.String Substring(Int32 `startIndex`)|Substring(`this`, `startIndex` +1, Length(`this`) - `startIndex`)||
|System.String Substring(Int32 `startIndex`, Int32 `length`)|Substring (`this`, `startIndex` + 1, `length`)||
|System.String ToLower()|ToLower(`this`)||
|System.String ToUpper()|ToUpper(`this`)||
|System.String Trim()|Trim(`this`)||
|System.String TrimEnd(Char[] `trimChars`)|RTrim(`this`)||
|System.String TrimStart(Char[]`trimChars`)|LTrim(`this`)||
|Boolean Equals(String `value`)|= (operatore)||

## <a name="systemdatetime-method-static-mapping"></a>Mapping del metodo System.DateTime (statico)

|Metodo System.DateTime (statico)|Funzione canonica|Note|
|---------------------------------------|------------------------|-----------|
|Boolean Equals(DateTime `t1`, DateTime `t2`)|= (operatore)||
|System.DateTime.Now|CurrentDateTime()||
|System.DateTime.UtcNow|CurrentUtcDateTime()||
|Boolean op_Equality(DateTime `d1`, DateTime `d2`)|= (operatore)||
|Boolean op_GreaterThan(DateTime `t1`, DateTime `t2`)|operatore >||
|Boolean op_GreaterThanOrEqual(DateTime `t1`, DateTime `t2`)|operatore > =||
|Boolean op_Inequality(DateTime `t1`, DateTime `t2`)|!= (operatore)||
|Op_LessThan booleano ( `t1`DateTime, `t2`DateTime)|operatore <||
|Boolean op_LessThanOrEqual(DateTime `t1`, DateTime `t2`)|operatore < =||
|Microsoft.VisualBasic.DateAndTime.DatePart( _<br /><br /> ByVal `Interval` come DateInterval,\_<br /><br /> ByVal `DateValue` come DateTime,\_<br /><br /> ByVal `FirstDayOfWeekValue` facoltativo come FirstDayOfWeek = VbSunday,\_<br /><br /> ByVal `FirstWeekOfYearValue` facoltativo As FirstWeekOfYear = VbFirstJan1\_<br /><br /> ) As Integer||Per altre informazioni, vedere la sezione relativa alla funzione DatePart.|
|Microsoft.VisualBasic.DateAndTime.Now|CurrentDateTime()||
|Microsoft.VisualBasic.DateAndTime.Year(DateTime `TimeValue`)|Year()||
|Microsoft.VisualBasic.DateAndTime.Month(DateTime `TimeValue`)|Month()||
|Microsoft.VisualBasic.DateAndTime.Day(DateTime `TimeValue`)|Day()||
|Microsoft.VisualBasic.DateAndTime.Hour(DateTime `TimeValue`)|Hour()||
|Microsoft.VisualBasic.DateAndTime.Minute(DateTime `TimeValue`)|Minute()||
|Microsoft.VisualBasic.DateAndTime.Second(DateTime `TimeValue`)|Second()||

## <a name="systemdatetime-method-instance-mapping"></a>Mapping del metodo System.DateTime (istanza)

|Metodo System.DateTime (istanza)|Funzione canonica|
|-----------------------------------------|------------------------|
|Boolean Equals(DateTime `value`)|= (operatore)|
|Giorno|Day(`this`)|
|Ora|Hour(`this`)|
|Millisecond|Millisecond(`this`)|
|Minuto|Minute(`this`)|
|Mese|Month(`this`)|
|Secondo|Second(`this`)|
|Year|Year(`this`)|

## <a name="systemdatetimeoffset-method-instance-mapping"></a>Mapping del metodo System.DateTimeOffset (istanza)

Viene mostrato il mapping per i metodi `get` sulle proprietà elencate.

|Metodo System.DateTimeOffset (istanza)|Funzione canonica|Note|
|-----------------------------------------------|------------------------|-----------|
|Giorno|Day(`this`)|Non supportato in SQL Server 2005.|
|Ora|Hour(`this`)|Non supportato in SQL Server 2005.|
|Millisecond|Millisecond(`this`)|Non supportato in SQL Server 2005.|
|Minuto|Minute(`this`)|Non supportato in SQL Server 2005.|
|Mese|Month(`this`)|Non supportato in SQL Server 2005.|
|Secondo|Second(`this`)|Non supportato in SQL Server 2005.|
|Year|Year(`this`)|Non supportato in SQL Server 2005.|

> [!NOTE]
> Il metodo <xref:System.DateTimeOffset.Equals%2A> restituisce `true` se gli oggetti <xref:System.DateTimeOffset> confrontati sono uguali; in caso contrario, restituisce `false`. Il metodo <xref:System.DateTimeOffset.CompareTo%2A> restituisce 0, 1 o -1 a seconda che l'oggetto <xref:System.DateTimeOffset> confrontato sia rispettivamente uguale, maggiore o minore.

## <a name="systemdatetimeoffset-method-static-mapping"></a>Mapping del metodo System.DateTimeOffset (statico)

Viene mostrato il mapping per i metodi `get` sulle proprietà elencate.

|Metodo System.DateTimeOffset (statico)|Funzione canonica|Note|
|---------------------------------------------|------------------------|-----------|
|System.DateTimeOffset.Now()|CurrentDateTimeOffset()|Non supportato in SQL Server 2005.|

## <a name="systemtimespan-method-instance-mapping"></a>Mapping del metodo System.TimeSpan (istanza)

Viene mostrato il mapping per i metodi `get` sulle proprietà elencate.

|Metodo System.TimeSpan (istanza)|Funzione canonica|Note|
|-----------------------------------------|------------------------|-----------|
|Ore|Hour(`this`)|Non supportato in SQL Server 2005.|
|Milliseconds|Millisecond(`this`)|Non supportato in SQL Server 2005.|
|Minuti|Minute(`this`)|Non supportato in SQL Server 2005.|
|Seconds|Second(`this`)|Non supportato in SQL Server 2005.|

> [!NOTE]
> Il metodo <xref:System.TimeSpan.Equals%2A> restituisce `true` se gli oggetti <xref:System.TimeSpan> confrontati sono uguali; in caso contrario, restituisce `false`. Il metodo <xref:System.TimeSpan.CompareTo%2A> restituisce 0, 1 o -1 a seconda che l'oggetto <xref:System.TimeSpan> confrontato sia rispettivamente uguale, maggiore o minore.

### <a name="datepart-function"></a>Funzione DatePart

La funzione `DatePart` è mappata a una di numerose funzioni canoniche diverse, a seconda del valore di `Interval`. Nella tabella seguente viene illustrato il mapping alla funzione canonica per i valori supportati di `Interval`:

|Valore di Interval|Funzione canonica|
|--------------------|------------------------|
|DateInterval.Year|Year()|
|DateInterval.Month|Month()|
|DateInterval.Day|Day()|
|DateInterval.Hour|Hour()|
|DateInterval.Minute|Minute()|
|DateInterval.Second|Second()|

## <a name="mathematical-function-mapping"></a>Mapping delle funzioni matematiche

|Metodo CLR|Funzione canonica|
|----------------|------------------------|
|System.Decimal.Ceiling(Decimal `d`)|Ceiling(`d`)|
|System.Decimal.Floor(Decimal `d`)|Floor(`d`)|
|System.Decimal.Round(Decimal `d`)|Round(`d`)|
|System.Math.Ceiling(Decimal `d`)|Ceiling(`d`)|
|System.Math.Floor(Decimal `d`)|Floor(`d`)|
|System.Math.Round(Decimal `d`)|Round(`d`)|
|System.Math.Ceiling(Double `a`)|Ceiling(`a`)|
|System.Math.Floor(Double `a`)|Floor(`a`)|
|System.Math.Round(Double `a`)|Round(`a`)|
|System.Math.Round(Double value, Int16 digits)|Round(value, digits)|
|System.Math.Round(Double value, Int32 digits)|Round(value, digits)|
|System.Math.Round(Decimal value, Int16 digits)|Round(value, digits)|
|System.Math.Round(Decimal value, Int32, digits)|Round(value, digits)|
|System.Math.Abs(Int16 value)|Abs(value)|
|System.Math.Abs(Int32 value)|Abs(value)|
|System.Math.Abs(Int64 value)|Abs(value)|
|System.Math.Abs(Byte value)|Abs(value)|
|System.Math.Abs(Single value)|Abs(value)|
|System.Math.Abs(Double value)|Abs(value)|
|System.Math.Abs(Decimal value)|Abs(value)|
|System.Math.Truncate(Double value, Int16 digits)|Truncate(value, digits)|
|System.Math.Truncate(Double value, Int32 digits)|Truncate(value, digits)|
|System.Math.Truncate(Decimal value, Int16 digits)|Truncate(value, digits)|
|System.Math.Truncate(Decimal value, Int32 digits)|Truncate(value, digits)|
|System.Math.Power(Int32 value, Int64 exponent)|Power(value, exponent)|
|System.Math.Power(Int32 value, Double exponent)|Power(value, exponent)|
|System.Math.Power(Int32 value, Decimal exponent)|Power(value, exponent)|
|System.Math.Power(Int64 value, Int64 exponent)|Power(value, exponent)|
|System.Math.Power(Int64 value, Double exponent)|Power(value, exponent)|
|System.Math.Power(Int64 value, Decimal exponent)|Power(value, exponent)|
|System.Math.Power(Double value, Int64 exponent)|Power(value, exponent)|
|System.Math.Power(Double value, Double exponent)|Power(value, exponent)|
|System.Math.Power(Double value, Decimal exponent)|Power(value, exponent)|
|System.Math.Power(Decimal value, Int64 exponent)|Power(value, exponent)|
|System.Math.Power(Decimal value, Double exponent)|Power(value, exponent)|
|System.Math.Power(Decimal value, Decimal exponent)|Power(value, exponent)|

## <a name="bitwise-operator-mapping"></a>Mapping degli operatori bit per bit

|Operatore bit per bit|Funzione canonica per gli operandi non booleani|Funzione canonica per gli operandi booleani|
|----------------------|--------------------------------------------------|---------------------------------------------|
|Operatore AND bit per bit|BitWiseAnd|op1 AND op2|
|Operatore OR bit per bit|BitWiseOr|op1 OR op2|
|Operatore NOT bit per bit|BitWiseNot|NOT(op)|
|Operatore XOR bit per bit|BitWiseXor|((op1 AND NOT(op2)) OR (NOT(op1) AND op2))|

## <a name="other-mapping"></a>Altro mapping

|Metodo|Funzione canonica|
|------------|------------------------|
|Guid.NewGuid()|NewGuid()|

## <a name="see-also"></a>Vedere anche

- [LINQ to Entities](linq-to-entities.md)
