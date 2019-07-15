---
ms.openlocfilehash: 060da3ebc60057554fd572bd2569652afee6bd0f
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804411"
---
### <a name="il-ret-not-allowed-in-a-try-region"></a>Istruzione IL ret non consentita in un'area try

|   |   |
|---|---|
|Dettagli|A differenza del compilatore JIT JIT64, RyuJIT (usato in .NET Framework 4.6) non consente un'istruzione IL ret in un'area try. La restituzione da un'area try non è consentita dalla specifica ECMA-335 e nessun compilatore gestito noto genera tale IL. Tuttavia, il compilatore JIT64 eseguirà tale livello di integrità se viene generato tramite reflection emit.|
|Suggerimento|Se un'app genera IL che include un codice operativo ret in un'area try, è possibile destinare l'app a .NET Framework 4.5 per usare il compilatore JIT precedente ed evitare l'interruzione. In alternativa, l'IL generato può essere aggiornato per restituire il controllo dopo l'area try.|
|Ambito|Microsoft Edge|
|Versione|4.6|
|Tipo|Ridestinazione|

