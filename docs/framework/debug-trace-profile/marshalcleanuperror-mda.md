---
title: MDA marshalCleanupError
ms.date: 03/30/2017
helpviewer_keywords:
- cleanup operations
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- marshaling cleanup error
- MarshalCleanupError MDA
- memory, cleanup errors
ms.assetid: 2f5d9e7c-ae51-4155-a435-54347aa1f091
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ab3690cac28ef572b19cadb632662590d1ea04c7
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052473"
---
# <a name="marshalcleanuperror-mda"></a>MDA marshalCleanupError
L'assistente al debug gestito `marshalCleanupError` viene attivato quando in Common Language Runtime si verifica un errore durante il tentativo di eseguire la pulizia di strutture temporanee e della memoria usata per effettuare il marshalling dei tipi di dati tra limiti del codice gestito e nativo.  
  
## <a name="symptoms"></a>Sintomi  
 Si verifica una perdita di memoria durante transizioni di codice gestito e nativo, lo stato di esecuzione, ad esempio le impostazioni cultura del thread, non viene ripristinato o si verificano errori durante la pulizia di <xref:System.Runtime.InteropServices.SafeHandle>.  
  
## <a name="cause"></a>Causa  
 Si è verificato un errore imprevisto durante la pulizia delle strutture temporanee.  
  
## <a name="resolution"></a>Risoluzione  
 Rivedere tutte le implementazioni del marshaler personalizzato, del finalizzatore e del distruttore <xref:System.Runtime.InteropServices.SafeHandle> per individuare eventuali errori.  
  
## <a name="effect-on-the-runtime"></a>Effetto sull'ambiente di esecuzione  
 L'assistente al debug gestito non ha alcun effetto su CLR.  
  
## <a name="output"></a>Output  
 Un messaggio che indica l'operazione non riuscita durante la pulizia.  
  
## <a name="configuration"></a>Configurazione  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshalCleanupError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostica degli errori tramite gli assistenti al debug gestito](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshalling di interoperabilità](../interop/interop-marshaling.md)
