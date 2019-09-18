---
title: Funzioni di callback
ms.date: 03/30/2017
helpviewer_keywords:
- callback function
- platform invoke, calling unmanaged functions
ms.assetid: c0aa8533-3b3b-42e8-9f60-84919793098c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb30e7daed938b14bd0d936352c7455db6975e73
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/17/2019
ms.locfileid: "71051912"
---
# <a name="callback-functions"></a>Funzioni di callback
Una funzione di callback è il codice di un'applicazione gestita che agevola una funzione di DLL non gestita nel completamento di un'attività. Le chiamate a una funzione di callback passano indirettamente da un'applicazione gestita a una funzione di DLL, per poi tornare nuovamente all'implementazione gestita. Alcune delle numerose funzioni di DLL chiamate tramite platform invoke richiedono, per essere eseguite in modo corretto, una funzione di callback nel codice gestito.  
  
 Nella maggior parte dei casi, per chiamare una funzione di DLL dal codice gestito, si crea e si usa una definizione gestita della funzione. Il processo è semplice.  
  
 L'utilizzo di una funzione di DLL che richiede una funzione di callback prevede alcuni passaggi aggiuntivi. In primo luogo è necessario determinare se la funzione richiede un callback controllando la documentazione relativa alla funzione. Successivamente occorre creare la funzione di callback nell'applicazione gestita. Infine si chiama la funzione di DLL passandole come argomento un puntatore alla funzione di callback. 
 
 La figura seguente presenta una riepilogo della funzione di callback e dei passaggi di implementazione:  
  
 ![Diagramma che illustra il processo di callback di platform invoke.](./media/callback-functions/platform-invoke-callback-process.gif)  
  
 Le funzioni di callback sono ideali per i casi in cui un'attività viene eseguita ripetutamente. Un altro utilizzo comune è quello con le funzioni di enumerazione, ad esempio **EnumFontFamilies**, **EnumPrinters** e **EnumWindows** nell'API Windows. La funzione **EnumWindows** esegue l'enumerazione di tutte le finestre esistenti nel computer, chiamando la funzione di callback per eseguire un'attività su ogni finestra. Per istruzioni e un esempio, vedere [Procedura: Implementare funzioni di callback](how-to-implement-callback-functions.md).  
  
## <a name="see-also"></a>Vedere anche

- [Procedura: Implementare funzioni di callback](how-to-implement-callback-functions.md)
- [Chiamata a una funzione di DLL](calling-a-dll-function.md)
