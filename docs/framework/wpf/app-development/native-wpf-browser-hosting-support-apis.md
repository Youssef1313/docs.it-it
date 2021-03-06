---
title: API native WPF per il supporto dell'hosting del browser
ms.date: 03/30/2017
f1_keywords:
- AutoGeneratedOrientationPage
helpviewer_keywords:
- browser hosting support [WPF]
- WPF browser hosting support APIs [WPF]
ms.assetid: 82c133a8-d760-45fb-a2b9-3a997537f1d4
ms.openlocfilehash: 0e11f0e5751f6d5cc51c32994dc932fd7d3e9f61
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003986"
---
# <a name="native-wpf-browser-hosting-support-apis"></a>API native WPF per il supporto dell'hosting del browser
L'hosting di applicazioni WPF nei Web browser è facilitato da un server di documenti attivo (noto anche come DocObject) registrato fuori dall'host WPF. Internet Explorer può essere attivato e integrato direttamente con un documento attivo. Per l'hosting di applicazioni XBAP e documenti XAML separati nei browser Mozilla, WPF fornisce un plug-in NPAPI, che fornisce un ambiente di hosting simile al server di documenti attivi WPF come Internet Explorer. Tuttavia, il modo più semplice per ospitare le applicazioni XBAP e i documenti XAML in altri browser e applicazioni autonome è tramite il controllo Web browser di Internet Explorer. Il controllo Web browser fornisce l'ambiente di hosting del server di documenti attivo complesso, ma consente al proprio host di personalizzare ed estendere tale ambiente e comunicare direttamente con l'oggetto documento attivo corrente.  
  
 Il server di documenti attivi WPF implementa diverse interfacce di hosting comuni, tra cui [IOleObject](https://go.microsoft.com/fwlink/?LinkId=162049), [IOleDocument](https://go.microsoft.com/fwlink/?LinkId=162050), [IOleInPlaceActiveObject](https://go.microsoft.com/fwlink/?LinkId=162051), [IPersistMoniker](https://go.microsoft.com/fwlink/?LinkId=162045), [IOleCommandTarget](https://go.microsoft.com/fwlink/?LinkId=162047). Quando sono ospitate nel controllo Web browser, queste interfacce possono essere query dall'oggetto restituito dalla proprietà [IWebBrowser2::D bilita](https://go.microsoft.com/fwlink/?LinkId=162048) .  
  
## <a name="iolecommandtarget"></a>IOleCommandTarget  
 L'implementazione del server di documenti attivi WPF di [IOleCommandTarget](https://go.microsoft.com/fwlink/?LinkId=162047) supporta numerosi comandi correlati alla navigazione e specifici del browser del gruppo di comandi OLE standard (con un GUID del gruppo di comandi null). Inoltre, riconosce un gruppo di comandi personalizzato denominato CGID_PresentationHost. Attualmente esiste un solo comando definito in questo gruppo.  
  
```cpp  
DEFINE_GUID(CGID_PresentationHost, 0xd0288c55, 0xd6, 0x4f5e, 0xa8, 0x51, 0x79, 0xde, 0xc5, 0x1b, 0x10, 0xec);  
enum PresentationHostCommands {   
   PHCMDID_TABINTO = 1   
};  
```  
  
 PHCMDID_TABINTO indica a PresentationHost di spostare lo stato attivo al primo o all'ultimo elemento attivabile nel contenuto, a seconda dello stato del tasto MAIUSC.  
  
## <a name="in-this-section"></a>In questa sezione  
 [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md)  
 [IWpfHostSupport](iwpfhostsupport.md)
