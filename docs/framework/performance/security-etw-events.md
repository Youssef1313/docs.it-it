---
title: Eventi ETW di sicurezza
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8d09b5b76c39f33848d44beb43d9b09c5e6ed13b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046168"
---
# <a name="security-etw-events"></a>Eventi ETW di sicurezza
<a name="top"></a> Gli eventi di sicurezza vengono generati durante la verifica del nome sicuro e la verifica Authenticode.  
  
 Questa categoria include i seguenti eventi:  
  
- [Eventi StrongNameVerificationStart_V1 e StrongNameVerificationStop_V1](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
- [Eventi AuthenticodeVerificationStart_V1 e AuthenticodeVerificationStop_V1](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstart_v1-and-strongnameverificationstop_v1-events"></a>Eventi StrongNameVerificationStart_V1 e StrongNameVerificationStop_V1  
 La tabella seguente illustra la parola chiave e il livello Per altre informazioni, vedere [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).  
  
|Parola chiave per la generazione dell'evento|Level|  
|-----------------------------------|-----------|  
|`SecurityKeyword` (0x400)|Informativo (4)|  
  
 La tabella seguente mostra le informazioni sull'evento.  
  
|event|ID evento|Generato quando|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|181|Inizio della verifica del nome sicuro.|  
|`StrongNameVerificationStop_V1`|182|Fine della verifica del nome sicuro.|  
  
 La tabella seguente mostra i dati dell'evento.  
  
|Nome campo|Tipo di dati|DESCRIZIONE|  
|----------------|---------------|-----------------|  
|VerificationFlags|win:UInt32|Flag di verifica.|  
|ErrorCode|win:UInt32|Codice errore HResult.|  
|FullyQualifiedAssemblyName|win:UnicodeString|Nome completo dell'assembly.|  
|ClrInstanceID|win:UInt16|ID univoco per l'istanza di CLR o CoreCLR.|  
  
 [Torna all'inizio](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstart_v1-and-authenticodeverificationstop_v1-events"></a>Eventi AuthenticodeVerificationStart_V1 e AuthenticodeVerificationStop_V1  
 La tabella seguente illustra la parola chiave e il livello  
  
|Parola chiave per la generazione dell'evento|Level|  
|-----------------------------------|-----------|  
|`SecurityKeyword` (0x400)|Informativo (4)|  
  
 La tabella seguente mostra le informazioni sull'evento.  
  
|event|ID evento|Generato quando|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|183|Inizio della verifica Authenticode.|  
|`AuthenticodeVerificationStop_V1`|184|Fine della verifica Authenticode.|  
  
 La tabella seguente mostra i dati dell'evento.  
  
|Nome campo|Tipo di dati|DESCRIZIONE|  
|----------------|---------------|-----------------|  
|VerificationFlags|win:UInt32|Flag di verifica.|  
|ErrorCode|win:UInt32|Codice errore HResult.|  
|ModulePath|win:UnicodeString|Percorso del modulo.|  
|ClrInstanceID|win:UInt16|ID univoco per l'istanza di CLR o CoreCLR.|  
  
## <a name="see-also"></a>Vedere anche

- [Eventi ETW di CLR](clr-etw-events.md)
