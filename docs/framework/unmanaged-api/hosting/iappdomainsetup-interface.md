---
title: Interfaccia IAppDomainSetup
ms.date: 03/30/2017
api_name:
- IAppDomainSetup
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IAppDomainSetup
helpviewer_keywords:
- IAppDomainSetup interface [.NET Framework hosting]
ms.assetid: 1844da85-c031-40bf-bea4-1a3d12a36c8c
topic_type:
- apiref
ms.openlocfilehash: 0fab64c31d4a73995c16d21767f4569f21c7df9a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126864"
---
# <a name="iappdomainsetup-interface"></a>Interfaccia IAppDomainSetup
Fornisce le proprietà che consentono all'host di configurare un tipo di <xref:System.AppDomain?displayProperty=nameWithType> prima di chiamare il metodo [ICorRuntimeHost:: CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) per crearlo.  
  
## <a name="properties"></a>Proprietà  
  
|proprietà|Descrizione|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|Ottiene o imposta il nome della directory che contiene l'applicazione.|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|Ottiene o imposta il nome dell'applicazione.|  
|<xref:System.AppDomainSetup.CachePath%2A>|Ottiene o imposta il nome di un'area specifica per l'applicazione in cui viene eseguita la copia shadow dei file.|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|Ottiene o imposta il nome del file di configurazione per un'applicazione.|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|Ottiene o imposta il nome della directory in cui vengono archiviati e accessibili i file generati dinamicamente.|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|Ottiene o imposta il percorso del file di licenza associato al dominio.|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|Ottiene o imposta l'elenco di directory combinate con la directory <xref:System.AppDomainSetup.ApplicationBase%2A> per verificare la presenza di assembly privati.|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|Ottiene o imposta un valore stringa che include o esclude <xref:System.AppDomainSetup.ApplicationBase%2A> dal percorso di ricerca dell'applicazione.|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|Ottiene o imposta i nomi delle directory che contengono gli assembly di cui eseguire la copia shadow.|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|Ottiene o imposta una stringa che indica se la copia shadow è attivata o disattivata. I valori validi sono "true" o "false".|  
  
## <a name="remarks"></a>Note  
 L'interfaccia `IAppDomainSetup` corrisponde all'interfaccia <xref:System.IAppDomainSetup> gestita, implementata dal tipo di <xref:System.AppDomainSetup>. Per una descrizione dettagliata delle proprietà, vedere <xref:System.IAppDomainSetup?displayProperty=nameWithType>.  
  
 `IAppDomainSetup` rappresenta le informazioni di associazione dell'assembly che possono essere aggiunte a un'istanza di <xref:System.AppDomain> prima della creazione. Un host può, ad esempio, impostare la proprietà <xref:System.AppDomainSetup.ApplicationBase%2A> per stabilire una directory radice, che Common Language Runtime (CLR) esegue il probe per gli assembly gestiti.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** MSCorEE. h  
  
 **Libreria:** Incluso come risorsa in MSCorEE. dll  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup>
- [Interfacce di hosting](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
