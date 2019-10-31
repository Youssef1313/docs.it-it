---
title: 'Mitigazione: Layout WPF'
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
ms.openlocfilehash: 3e08a2d11e815248d0fe73f804e9ef7edb7c04da
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126104"
---
# <a name="mitigation-wpf-layout"></a>Mitigazione: Layout WPF
Il layout dei controlli WPF può cambiare leggermente.  
  
## <a name="impact"></a>Impatto  
 Come conseguenza di questo cambiamento:  
  
- La larghezza o l'altezza degli elementi può aumentare o diminuire al massimo di un pixel.  
  
- La posizione di un oggetto può cambiare al massimo di un pixel.  
  
- Gli elementi centrati possono risultare decentrati in orizzontale o in verticale al massimo di un pixel.  
  
 Per impostazione predefinita, questo nuovo layout è disponibile solo per app destinate a .NET Framework 4.6.  
  
## <a name="mitigation"></a>Attenuazione  
 Poiché questa modifica tende a eliminare il ritaglio del lato destro o inferiore dei controlli WPF a DPI elevati, le app destinate a versioni precedenti di .NET Framework ma eseguite su .NET Framework 4.6 possono adottare questo nuovo comportamento aggiungendo la riga seguente alla sezione `<runtime>` del file app.config:  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 Le app destinate a .NET Framework 4.6 ma che richiedono che il rendering dei controlli WPF venga eseguito mediante l'algoritmo di layout precedente possono aggiungere a questo scopo la riga seguente alla sezione `<runtime>` del file app.config:  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a>Vedere anche

- [Modifiche di reindirizzamento](retargeting-changes-in-the-net-framework-4-6.md)
