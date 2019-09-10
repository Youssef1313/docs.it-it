---
title: CorFlags.exe (strumento di conversione CorFlags)
ms.date: 03/30/2017
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4228da6efe22091c86de95d846c14f504d51457f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851292"
---
# <a name="corflagsexe-corflags-conversion-tool"></a>CorFlags.exe (strumento di conversione CorFlags)
Lo strumento di conversione CorFlags consente di configurare la sezione CorFlags dell'intestazione di un'immagine eseguibile di tipo PE.  
  
 Viene installato automaticamente con Visual Studio. Per eseguire lo strumento, usare il Prompt dei comandi per gli sviluppatori per Visual Studio (o il prompt dei comandi di Visual Studio in Windows 7). Per altre informazioni, vedere [Prompt dei comandi](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Al prompt dei comandi digitare quanto segue:  
  
## <a name="syntax"></a>Sintassi  
  
```console  
CorFlags.exe assembly [options]  
```  
  
## <a name="parameters"></a>Parametri  
  
|Parametro obbligatorio.|Descrizione|  
|------------------------|-----------------|  
|`assembly`|Nome dell'assembly per il quale configurare CorFlags.|  
  
|Opzione|DESCRIZIONE|  
|------------|-----------------|  
|**/32BIT[REQ]+**|Imposta il flag 32BITREQUIRED.|  
|**/32BIT[REQ]-**|Cancella il flag 32BITREQUIRED.|  
|**/32BITPREF+**|Imposta il flag 32BITPREFERRED. L'applicazione viene eseguita come processo a 32 bit anche sulle piattaforme a 64 bit. Impostare questo flag solo su file EXE. Se il flag viene impostato su una DLL, la DLL non viene caricata nei processi a 64 bit e viene generata un'eccezione <xref:System.BadImageFormatException>. Un file EXE con questo flag può essere caricato in un processo a 64 bit.<br /><br /> Novità di .NET Framework 4.5.|  
|**/32BITPREF-**|Cancella il flag 32BITPREFERRED.<br /><br /> Novità di .NET Framework 4.5.|  
|**/?**|Visualizza la sintassi e le opzioni di comando dello strumento.|  
|**/Force**|Forza un aggiornamento anche se l'assembly ha un nome sicuro. **Importante:**  Se si aggiorna un assembly con nome sicuro, è necessario firmarlo nuovamente prima di eseguirne il codice.|  
|**/help**|Visualizza la sintassi e le opzioni di comando dello strumento.|  
|**/ILONLY+**|Imposta il flag ILONLY.|  
|**/ILONLY-**|Cancella il flag ILONLY.|  
|**/nologo**|Evita la visualizzazione del messaggio di avvio Microsoft.|  
|**/RevertCLRHeader**|Ripristina la versione 2.0 dell'intestazione CLR.|  
|**/UpgradeCLRHeader**|Esegue l'aggiornamento dell'intestazione CLR alla versione 2.5. **Nota:**  per l'esecuzione nativa, gli assembly devono avere un'intestazione CLR versione 2.5 o successiva.|  
  
## <a name="remarks"></a>Note  
 Se non viene specificata alcuna opzione, lo strumento di conversione CorFlags visualizza i flag relativi all'assembly specificato.  
  
## <a name="see-also"></a>Vedere anche

- [Strumenti](../../../docs/framework/tools/index.md)
- [Applicazioni a 64 bit](../../../docs/framework/64-bit-apps.md)
- [Prompt dei comandi](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
