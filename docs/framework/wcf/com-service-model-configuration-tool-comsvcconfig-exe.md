---
title: Strumento per la configurazione del modello di servizio di COM+ (ComSvcConfig.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: 7717c6c2-85fc-418b-a8ed-bad8e61cec5c
ms.openlocfilehash: 13368dfa7ca9d7981ac146b87e83f77077eaf537
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320730"
---
# <a name="com-service-model-configuration-tool-comsvcconfigexe"></a>Strumento per la configurazione del modello di servizio di COM+ (ComSvcConfig.exe)
Lo strumento da riga di comando per la configurazione del modello del servizio di COM+ (ComSvcConfig.exe) consente di configurare le interfacce COM+ che si desidera siano esposte come servizi Web.  
  
## <a name="syntax"></a>Sintassi  
  
```console  
ComSvcConfig.exe /install | /uninstall | /list [/application:<ApplicationID | ApplicationName>] [/contract:<ClassID | ProgID | *,InterfaceID | InterfaceName | *>] [/hosting:<complus | was>] [/webSite:<WebsiteName>] [/webDirectory:<WebDirectoryName>] [/mex] [/id] [/nologo] [/verbose] [/help] [/partial]  
```  
  
## <a name="remarks"></a>Note  
  
> [!NOTE]
> Per utilizzare ComSvcConfig.exe è necessario disporre dei privilegi di amministratore per il computer.  
  
 Lo strumento si trova nel percorso seguente  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\  
  
 Per ulteriori informazioni su ComSvcConfig. exe, vedere [procedura: utilizzare lo strumento di configurazione del modello di servizi com+](./feature-details/how-to-use-the-com-service-model-configuration-tool.md).  
  
 Nella tabella riportata di seguito sono descritti le modalità di utilizzo di ComSvcConfig.exe.  
  
|Opzione|Descrizione|  
|------------|-----------------|  
|`install`|Installa una configurazione per un'interfaccia COM+ per l'integrazione del Modello di servizio.<br /><br /> Forma abbreviata `/i`.|  
|`uninstall`|Disinstalla una configurazione per un'interfaccia COM+ dall'integrazione del Modello di servizio.<br /><br /> Forma abbreviata `/u`.|  
|`list`|Elenca le informazioni su applicazioni e componenti COM+ dotati di interfacce configurate per l'integrazione del Modello di servizio.<br /><br /> Forma abbreviata `/l`.|  
  
 Nella tabella riportata di seguito sono descritti i flag che possono essere utilizzati con ComSvcConfig.exe.  
  
|Opzione|Descrizione|  
|------------|-----------------|  
|`/application:` \<*ApplicationID* &#124; *ApplicationName* \>|Specifica l'applicazione COM+ da configurare.<br /><br /> Forma abbreviata `/a`.|  
|`/contract:` \<*ClassID* &#124; *ProgID* &#124; \*,*InterfaceID* &#124; *InterfaceName* &#124; 1 2|Specifica componente e interfaccia COM+ che verranno configurati come contratto del servizio.<br /><br /> Forma abbreviata `/c`.<br /><br /> Sebbene sia possibile utilizzare il carattere jolly (\*) quando si specificano i nomi dei componenti e delle interfacce, è consigliabile non utilizzarlo perché è possibile esporre interfacce che non si intendevano.|  
|`/hosting:` \<*ComPlus* &#124; *è stato* \>|Specifica se utilizzare la modalità di hosting COM+ o Web.<br /><br /> Forma abbreviata `/h`.<br /><br /> L'utilizzo della modalità di hosting COM+ richiede l’attivazione esplicita dell'applicazione COM+. L'utilizzo della modalità di hosting Web, consente l’attivazione automatica dell’applicazione COM+ come necessario. Se l'applicazione COM+ è un'applicazione della libreria, essa viene eseguita nel processo di Internet Information Services (IIS). Se l'applicazione COM+ è un'applicazione server, essa viene eseguita nel processo di Dllhost.exe.|  
|`/webSite:` \<*websitename* \>|Specifica il sito Web per l’hosting quando viene utilizzata la modalità di hosting Web (vedere il flag `/hosting` ).<br /><br /> Forma abbreviata `/w`.<br /><br /> Se non viene specificato nessun sito Web, verrà utilizzato il sito Web predefinito.|  
|`/webDirectory:` \<*Webdirectoryname* \>|Specifica la directory virtuale per l’hosting quando viene utilizzata la modalità di hosting Web (vedere il flag `/hosting` ).<br /><br /> Forma abbreviata `/d`.|  
|`/mex`|Aggiunge l'endpoint del servizio MEX (Metadata Exchange) alla configurazione del servizio predefinita per supportare client che desiderano recuperare una definizione del contratto dal servizio.<br /><br /> Forma abbreviata `/x`.|  
|`/id`|Visualizza applicazione, componente e informazioni sull'interfaccia come ID.<br /><br /> Forma abbreviata `/k`.|  
|`/nologo`|Impedisce la visualizzazione del logo di ComSvcConfig.exe.<br /><br /> Forma abbreviata `/n`.|  
|`/verbose`|Restituisce tutti gli avvisi o testo informativo oltre a qualsiasi errore incontrato.<br /><br /> Forma abbreviata `/v`.|  
|`/help`|Il messaggio di utilizzo viene visualizzato.<br /><br /> Forma abbreviata `/?`.|  
|`/partial`|Genera una configurazione del servizio quando l'interfaccia specificata include una o più firme del metodo che possono essere esposte. In corrispondenza dell’ora di inizializzazione del servizio, metodi compatibili vengono visualizzati come operazioni sul contratto di servizio, mentre i metodi non compatibili vengono ignorati e non sono presenti nel contratto di servizio.<br /><br /> Se questo flag manca, lo strumento non genererà una configurazione del servizio quando l'interfaccia specificata include uno o più metodi incompatibili.|  
  
## <a name="examples"></a>Esempi  
  
### <a name="description"></a>Descrizione  
 Nell'esempio seguente viene aggiunta l'interfaccia `IFinances` del componente `ItemOrders.IFinancial` (dall'applicazione OnlineStore COM+) al set di interfacce esposte come servizi Web, utilizzando la modalità di hosting COM+. Tutti gli avvisi verranno restituiti oltre a qualsiasi errore incontrato.  
  
### <a name="code"></a>Codice  
  
```console  
ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
```  
  
### <a name="description"></a>Descrizione  
 Nell'esempio seguente viene aggiunta l'interfaccia `IStockLevels` del componente `ItemInventory.Warehouse` (dall'applicazione OnlineWarehouse COM+) al set di interfacce esposte come servizi Web, utilizzando la modalità di hosting Web. Il Servizio Web è ospitato sul Web nella directory virtuale OnlineWarehouse di IIS.  
  
### <a name="code"></a>Codice  
  
```console  
ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse  
```  
  
### <a name="description"></a>Descrizione  
 Nell'esempio seguente viene rimossa l'interfaccia `IFinances` del componente `ItemOrders.Financial` (dall'applicazione OnlineStore COM+) dal set di interfacce esposte come servizi Web, utilizzando la modalità di hosting COM+.  
  
### <a name="code"></a>Codice  
  
```console  
ComSvcConfig.exe /uninstall /application:OnlineStore /interface:ItemOrders.Financial,IFinances /hosting:complus  
```  
  
### <a name="description"></a>Descrizione  
 L’esempio di seguito riportato elenca le interfacce ospitate COM+ attualmente esposte, insieme all'indirizzo corrispondente e ai dettagli di associazione, per l'applicazione OnlineStore COM+ sul computer locale.  
  
### <a name="code"></a>Codice  
  
```console  
ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
```  
  
## <a name="see-also"></a>Vedere anche

- [Procedura: Usare lo strumento di configurazione del modello di servizi COM+](./feature-details/how-to-use-the-com-service-model-configuration-tool.md)
