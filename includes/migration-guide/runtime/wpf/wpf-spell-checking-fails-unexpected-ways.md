---
ms.openlocfilehash: 8049bf01bc10c5913fa11b25e49afd1b1317eecc
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802945"
---
### <a name="wpf-spell-checking-fails-in-unexpected-ways"></a>Il controllo ortografico in WPF restituisce errori imprevisti

|   |   |
|---|---|
|Dettagli|Questa condizione riunisce vari problemi riscontrati con il controllo ortografico WPF:<ul><li>In determinati casi il controllo ortografico WPF genera <xref:System.Runtime.InteropServices.COMException?displayProperty=name></li><li>Il controllo ortografico WPF non riesce con <xref:System.UnauthorizedAccessException> quando le applicazioni vengono avviate usando "Esegui come altro utente"</li><li>Il controllo ortografico WPF identifica in modo errato gli errori di ortografia di parole composte, ad esempio "Hausnummer" in tedesco.</li></ul>|
|Suggerimento|Problema n. 1: risolto in .NET Framework 4.6.2. Problema n. 2: il controllo ortografico WPF non è più supportato quando le applicazioni vengono avviate usando l'opzione "Esegui come altro utente". A partire da .NET Framework 4.6.2, le applicazioni avviate in questo modo non si arrestano più in modo anomalo, ma il controllo ortografico viene disabilitato automaticamente. Problema n. 3: risolto in .NET Framework 4.6.2.|
|Ambito|Microsoft Edge|
|Versione|4.6.1|
|Tipo|Runtime|

