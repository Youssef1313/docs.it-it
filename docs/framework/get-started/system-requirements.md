---
title: Requisiti di sistema di .NET Framework
description: Informazioni sui requisiti hardware, software e del sistema operativo per installare .NET Framework 4.5 e versioni successive.
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- software requirements
- .NET Framework, system requirements
- system requirements
- operating systems supported
- hardware requirements
ms.assetid: 298275e2-da1d-4618-9f74-6a3567832350
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6f867b53f168a394515a1b1eaa6575a72dfb8d91
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052008"
---
# <a name="net-framework-system-requirements"></a>Requisiti di sistema di .NET Framework

Nelle tabelle presenti in questo argomento sono indicati i requisiti hardware, software e del sistema operativo per le versioni di .NET Framework seguenti:

- .NET framework 4.5 e relative versioni intermedie (4.5.1 e 4.5.2).
- .NET framework 4.6 e relative versioni intermedie (4.6.1 e 4.6.2).
- .NET framework 4.7 e relative versioni intermedie (4.7.1 e 4.7.2).
- .NET Framework 4.8

Per informazioni sulle versioni di .NET Framework precedenti a .NET Framework 4.5, vedere [Versioni e dipendenze di .NET Framework](../migration-guide/versions-and-dependencies.md).

Gli ambienti di sviluppo che consentono di sviluppare app per .NET Framework dispongono di un set di requisiti separato.

[!INCLUDE[net-framework-4-versions](../../../includes/net-framework-4x-versions.md)]

Per informazioni su download e collegamenti, vedere [Install the .NET Framework for developers](../install/guide-for-developers.md) (Installazione di .NET Framework per sviluppatori).

Per informazioni sul ciclo di vita del supporto delle versioni di .NET Framework, vedere [Ciclo di vita del supporto Microsoft](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=Microsoft%20.NET%20Framework&Filter=FilterNO).

## <a name="hardware-requirements"></a>Requisiti hardware

|                          |        |
| ------------------------ | ------ |
| **Processore**            | 1 GHz  |
| **RAM**                  | 512 MB |
| **Spazio su disco (minimo)** |        |
| 32 bit                   | 4,5 GB |
| 64 bit                   | 4,5 GB |

## <a name="installation-requirements"></a>Requisiti di installazione

Per l'installazione di .NET Framework è necessario avere privilegi di amministratore. Se non si hanno diritti di amministratore nel computer in cui si vuole installare .NET Framework, contattare l'amministratore di rete.

## <a name="supported-client-operating-systems"></a>Sistemi operativi client supportati

| Sistema operativo | Edizioni supportate | Preinstallato con il sistema operativo | Installabile separatamente |
| ---------------- | ------------------ | ------------------------ | ---------------------- |
| Aggiornamento di Windows 10 di maggio 2019 | 32 e 64 bit | .NET Framework 4.8 | -- |
| Aggiornamento di Windows 10 (ottobre 2018) | 32 e 64 bit | .NET Framework 4.7.2 | .NET Framework 4.8 |
| Aggiornamento di Windows 10 (aprile 2018) | 32 e 64 bit | .NET Framework 4.7.2 |.NET Framework 4.8|
| Windows 10 Fall Creators Update | 32 e 64 bit | .NET Framework 4.7.1 | .NET Framework 4.7.2<br/><br/>.NET Framework 4.8 |
| Windows 10 Creators Update | 32 e 64 bit | .NET Framework 4.7 | .NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4.8 |
| Aggiornamento dell'anniversario di Windows 10 | 32 e 64 bit | .NET Framework 4.6.2 |.NET Framework 4.7<br/><br/>.NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4.8  |
| Aggiornamento di novembre di Windows 10 | 32 e 64 bit | .NET Framework 4.6.1 | .NET Framework 4.6.2 |
| Windows 10 | 32 e 64 bit | .NET Framework 4.6 | .NET Framework 4.6.1 <br/><br/> .NET Framework 4.6.2 |
| [!INCLUDE[win81](../../../includes/win81-md.md)] | 32 bit, 64 bit e ARM | .NET Framework 4.5.1 | .NET Framework 4.5.2<br /><br /> .NET Framework 4.6<br /><br /> .NET Framework 4.6.1<br /><br /> .NET Framework 4.6.2<br /><br />.NET Framework 4.7<br/><br/>.NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4.8 |
| [!INCLUDE[win8](../../../includes/win8-md.md)] | 32 bit, 64 bit e ARM | .NET Framework 4.5 | .NET Framework 4.5.1<br /><br />.NET Framework 4.5.2<br /><br /> .NET Framework 4.6<br /><br /> .NET Framework 4.6.1 |
| Windows 7 SP1|32 e 64 bit | -- | .NET Framework 4<br /><br /> .NET Framework 4.5<br /><br /> .NET Framework 4.5.1<br /><br /> .NET Framework 4.5.2<br /><br /> .NET Framework 4.6<br /><br /> .NET Framework 4.6.1<br /><br /> .NET Framework 4.6.2<br /><br />.NET Framework 4.7<br/><br/>.NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4.8 |
| Windows Vista SP2|32 e 64 bit | -- | .NET Framework 4<br /><br /> .NET Framework 4.5<br /><br /> .NET Framework 4.5.1<br /><br /> .NET Framework 4.5.2<br /><br /> .NET Framework 4.6 |
| Windows XP |32 e 64 bit | -- | .NET Framework 4 |

 **Note:**

- Nei sistemi Windows 7, .NET Framework richiede Windows 7 SP1. Se si ha Windows 7 ma non è ancora stato installato Service Pack 1, è necessario farlo prima di installare .NET Framework.

- .NET Framework 4.5 è supportato nell'Ambiente preinstallazione di Windows (Windows PE). Non tutte le funzionalità sono supportate in Windows PE.

- .NET Framework 4 supporta anche la piattaforma IA64.

- Per tutte le piattaforme, si consiglia di eseguire l'aggiornamento al Service Pack di Windows più recente e di installare gli aggiornamenti critici disponibili nel [sito Web Windows Update](https://go.microsoft.com/fwlink/?LinkId=168461) per garantire la massima compatibilità e sicurezza.

- Nei sistemi operativi a 64 bit, .NET Framework supporta sia WOW64 (elaborazione a 32 bit su un computer a 64 bit) che l'elaborazione nativa a 64 bit.

## <a name="supported-server-operating-systems"></a>Sistemi operativi server supportati

| Sistema operativo | Edizioni supportate | Preinstallato con il sistema operativo | Installabile separatamente |
| ---------------- | ------------------ | ------------------------ | ---------------------- |
| Windows Server 2019 | 64 bit | .NET Framework 4.7.2 | .NET Framework 4.8 |
| Windows Server, versione 1809 | 64 bit | .NET Framework 4.7.2 | .NET Framework 4.8 |
| Windows Server, versione 1803 | 64 bit | .NET Framework 4.7.2 | .NET Framework 4.8 |
| Windows Server, versione 1709 | 64 bit | .NET Framework 4.7.1 | .NET Framework 4.7.2|
| Windows Server 2016 | 64 bit | .NET Framework 4.6.2 | .NET Framework 4.7<br/><br/> .NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4.8 |
| Windows Server 2012 R2 | 64 bit | .NET Framework 4.5.1 | .NET Framework 4.5.2<br /><br /> .NET Framework 4.6<br /><br /> .NET Framework 4.6.1<br /><br /> .NET Framework 4.6.2<br /><br />.NET Framework 4.7<br/><br/> .NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4.8 |
| Windows Server 2012 (edizione a 64 bit) | 64 bit| .NET Framework 4.5 | .NET Framework 4.5.1<br /><br /> .NET Framework 4.5.2<br /><br /> .NET Framework 4.6<br /><br /> .NET Framework 4.6.1<br /><br /> .NET Framework 4.6.2<br /><br />.NET Framework 4.7<br/><br/>.NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4.8 |
| Windows Server 2008 R2 SP1|64 bit | -- | .NET Framework 4<br /><br /> .NET Framework 4.5<br /><br /> .NET Framework 4.5.1<br /><br /> .NET Framework 4.5.2<br /><br /> .NET Framework 4.6<br /><br /> .NET Framework 4.6.1<br /><br /> .NET Framework 4.6.2<br /><br />.NET Framework 4.7<br/><br/>.NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4.8 |
| Windows Server 2008 SP2|32 e 64 bit | -- | .NET Framework 4<br /><br /> .NET Framework 4.5<br /><br /> .NET Framework 4.5.1<br /><br /> .NET Framework 4.5.2<br /><br /> .NET Framework 4.6 |

 **Note:**

- [!INCLUDE[winserver8](../../../includes/winserver8-md.md)] include .NET Framework 4.5, che di conseguenza non deve essere installato separatamente. Analogamente, [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)] include .NET Framework 4.5.1.

- .NET Framework ha supporto limitato per il ruolo Server Core con Windows Server 2008 R2 SP1 o versioni successive. Per un elenco di API non supportate, vedere [Server Core .NET Functionality](https://docs.microsoft.com/previous-versions//dd745015(v=vs.85)) (Funzionalità .NET di Server Core).

- .NET Framework non è supportato in Windows Server 2008 R2 per sistemi basati su Itanium.

- .NET Framework non è supportato nel ruolo Server Core in Windows Server 2008 SP2.

- Per tutte le piattaforme, si consiglia di eseguire l'aggiornamento al Service Pack di Windows più recente e installare gli aggiornamenti critici disponibili nel [sito Web Windows Update](https://go.microsoft.com/fwlink/?LinkId=168461) per garantire la massima compatibilità e sicurezza. Su alcuni sistemi operativi potrebbe essere necessaria l'installazione dell'ultimo Windows Service Pack.

- Nei sistemi operativi a 64 bit, .NET Framework supporta sia WOW64 (elaborazione a 32 bit su un computer a 64 bit) che l'elaborazione nativa a 64 bit.

## <a name="see-also"></a>Vedere anche

- [Guida all'installazione](../install/index.md)
- [Introduzione](index.md)
- [Risolvere i problemi relativi alle installazioni e alle disinstallazioni bloccate di .NET Framework](../install/troubleshoot-blocked-installations-and-uninstallations.md)
