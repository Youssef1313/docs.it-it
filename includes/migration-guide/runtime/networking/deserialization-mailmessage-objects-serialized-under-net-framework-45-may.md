---
ms.openlocfilehash: a6f93bbdf39a1b525e2daeb12afc3a6392a66e30
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2019
ms.locfileid: "59235754"
---
### <a name="deserialization-of-mailmessage-objects-serialized-under-the-net-framework-45-may-fail"></a>La deserializzazione di oggetti MailMessage serializzati in .NET Framework 4.5 può non riuscire

|   |   |
|---|---|
|Dettagli|A partire da .NET Framework 4.5, gli oggetti <xref:System.Web.Mail.MailMessage> possono includere caratteri non ASCII. In .NET Framework 4, sono supportati solo caratteri ASCII. Gli oggetti <xref:System.Web.Mail.MailMessage> che contengono caratteri non ASCII e che vengono serializzati in .NET Framework 4.5 o versione successiva non possono essere deserializzati in .NET Framework 4.|
|Suggerimento|Quando si deserializza un oggetto <xref:System.Web.Mail.MailMessage>, verificare che il codice consenta la gestione delle eccezioni.|
|Ambito|Secondario|
|Versione|4.5|
|Tipo|Runtime|
|API interessate|<ul><li><xref:System.Web.Mail.MailMessage?displayProperty=nameWithType></li></ul>|
