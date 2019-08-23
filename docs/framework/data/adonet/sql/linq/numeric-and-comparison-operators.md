---
title: Operatori numerici e di confronto
ms.date: 03/30/2017
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
ms.openlocfilehash: ff54856a66ad5e9c0362c013f8df5f1147055cd0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915703"
---
# <a name="numeric-and-comparison-operators"></a>Operatori numerici e di confronto

Gli operatori aritmetici e di confronto funzionano correttamente in Common Language Runtime (CLR), ad eccezione di quanto descritto di seguito:

- In SQL non è supportato l'operatore modulo per i numeri a virgola mobile.

- In SQL non è supportato l'operatore aritmetico unchecked.

- Gli operatori di incremento e decremento provocano effetti collaterali quando vengono usati in espressioni che non possono essere replicate in SQL e, di conseguenza, non sono supportati.

## <a name="supported-operators"></a>Operatori supportati

In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sono supportati gli operatori riportati di seguito.

- Operatori aritmetici di base:

  - `+`

  - `-` (sottrazione)

  - `*`

  - `/`

  - Divisione con valori integer di Visual Basic (`\`)

  - `%` (`Mod` di Visual Basic)

  - `<<`

  - `>>`

  - `-` (negazione unaria)

- Operatori di confronto di base:

  - `=` di Visual Basic e `==` di C#

  - `<>` di Visual Basic e `!=` di C#

  - `Is/IsNot` Visual Basic

  - `<`

  - `<=`

  - `>`

  - `>=`

## <a name="see-also"></a>Vedere anche

- [Tipi di dati e funzioni](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
- [Operatori C#](../../../../../csharp/language-reference/operators/index.md)
- [Operatori](../../../../../visual-basic/language-reference/operators/index.md)
