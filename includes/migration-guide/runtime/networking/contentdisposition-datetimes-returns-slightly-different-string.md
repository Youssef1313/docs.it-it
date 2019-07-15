---
ms.openlocfilehash: 529d1b83c0637f705b725a64aa82e2c053bbfd19
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858596"
---
### <a name="contentdisposition-datetimes-returns-slightly-different-string"></a>ContentDisposition DateTimes restituisce una stringa leggermente diversa

|   |   |
|---|---|
|Dettagli|Le rappresentazioni di stringa di <xref:System.Net.Mime.ContentDisposition?displayProperty=name> sono state aggiornate, a partire dalla versione 4.6, in modo da rappresentare sempre il componente dell'ora di un valore <xref:System.DateTime?displayProperty=name> con due cifre. Questo comportamento è conforme a [RFC822](https://www.ietf.org/rfc/rfc0822.txt) e [RFC2822](https://www.ietf.org/rfc/rfc2822.txt). Ne consegue che <xref:System.Net.Mime.ContentDisposition.ToString> restituisce una stringa leggermente diversa nella versione 4.6 negli scenari in cui uno degli elementi di tempo della disposizione precede le 10.00. Si noti che i valori di ContentDisposition vengono a volte serializzati convertendoli in stringhe, pertanto è necessario verificare qualsiasi operazione <xref:System.Net.Mime.ContentDisposition.ToString>, la serializzazione o le chiamate di GetHashCode.|
|Suggerimento|Non dare per scontato che le rappresentazioni di stringa di ContentDisposition da versioni diverse di .NET Framework vengano confrontate correttamente. Se possibile, riconvertire le stringhe in ContentDisposition prima di eseguire un confronto.|
|Ambito|Secondario|
|Versione|4.6|
|Tipo|Runtime|
|API interessate|<ul><li><xref:System.Net.Mime.ContentDisposition.ToString?displayProperty=nameWithType></li><li><xref:System.Net.Mime.ContentDisposition.GetHashCode?displayProperty=nameWithType></li></ul>|

