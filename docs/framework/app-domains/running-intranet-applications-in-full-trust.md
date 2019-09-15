---
title: Esecuzione di applicazioni Intranet in attendibilità totale
ms.date: 03/30/2017
helpviewer_keywords:
- full trust, running intranet applications in
- intranet applications, running in full trust
- running intranet applications in full trust
ms.assetid: ee13c0a8-ab02-49f7-b8fb-9eab16c6c4f0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1996c8b317bbfed6362c759a257cafef8400e919
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971916"
---
# <a name="running-intranet-applications-in-full-trust"></a>Esecuzione di applicazioni Intranet in attendibilità totale
A partire da .NET Framework versione 3.5 Service Pack 1 (SP1), le applicazioni e i relativi assembly di librerie possono essere eseguiti come assembly con attendibilità totale da una condivisione di rete. Agli assembly caricati da una condivisione nella rete Intranet viene automaticamente aggiunta l'evidenza della zona <xref:System.Security.SecurityZone.MyComputer>. Questa evidenza concede agli assembly lo stesso set di autorizzazioni, in genere l'attendibilità totale, degli assembly che si trovano nel computer. Questa funzionalità non è applicabile alle applicazioni ClickOnce o alle applicazioni progettate per l'esecuzione in un host.  
  
## <a name="rules-for-library-assemblies"></a>Regole per gli assembly di librerie  
 Le regole seguenti si applicano agli assembly caricati da un eseguibile su una condivisione di rete:  
  
- Gli assembly di librerie devono trovarsi nella stessa cartella dell'assembly eseguibile. Agli assembly che si trovano in una sottocartella o a cui viene fatto riferimento in un percorso diverso non verrà concessa l'attendibilità totale.  
  
- Se l'eseguibile esegue il caricamento ritardato di un assembly, dovrà usare lo stesso percorso che è stato usato per avviare l'eseguibile. Se ad esempio la condivisione \\\\*network-computer*\\*share* è mappata a una lettera di unità e l'eseguibile viene eseguito da questo percorso, agli assembly caricati dall'eseguibile tramite il percorso di rete non verrà concessa l'attendibilità totale. Per eseguire il caricamento ritardato di un assembly nella zona <xref:System.Security.SecurityZone.MyComputer>, l'eseguibile deve usare il percorso della lettera di unità.  
  
## <a name="restoring-the-former-intranet-policy"></a>Ripristino dei criteri Intranet precedenti  
 Nelle versioni precedenti di .NET Framework agli assembly condivisi veniva concessa l'evidenza della zona <xref:System.Security.SecurityZone.Intranet>. Per concedere l'attendibilità totale a un assembly su una condivisione era necessario specificare i criteri di sicurezza dall'accesso di codice.  
  
 Questo nuovo comportamento è quello predefinito per gli assembly Intranet. È possibile ripristinare il comportamento precedente che consiste nel concedere l'evidenza <xref:System.Security.SecurityZone.Intranet> impostando una chiave del Registro di sistema applicabile a tutte le applicazioni presenti sul computer. Questo processo è diverso per i computer a 32 bit e a 64 bit:  
  
- Nei computer a 32 bit creare una sottochiave della chiave HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework nel Registro di sistema. Usare il nome di chiave LegacyMyComputerZone con il valore DWORD impostato su 1.  
  
- Nei computer a 64 bit creare una sottochiave della chiave HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework nel Registro di sistema. Usare il nome di chiave LegacyMyComputerZone con il valore DWORD impostato su 1. Creare la stessa sottochiave nella chiave HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework.  
  
## <a name="see-also"></a>Vedere anche

- [Programmazione con gli assembly](../../standard/assembly/program.md)
