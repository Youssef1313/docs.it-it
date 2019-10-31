---
title: 'Attenuazione: Frame PNG in oggetti icona'
ms.date: 03/30/2017
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
ms.openlocfilehash: 28787eff0dd4ce92394a66a936b3d422dfe513bb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126183"
---
# <a name="mitigation-png-frames-in-icon-objects"></a><span data-ttu-id="0f3b6-102">Attenuazione: Frame PNG in oggetti icona</span><span class="sxs-lookup"><span data-stu-id="0f3b6-102">Mitigation: PNG Frames in Icon Objects</span></span>
<span data-ttu-id="0f3b6-103">A partire da .NET Framework 4.6, il metodo <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> converte correttamente le icone con i frame PNG in oggetti <xref:System.Drawing.Bitmap> .</span><span class="sxs-lookup"><span data-stu-id="0f3b6-103">Starting with the .NET Framework 4.6, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method successfully converts icons with PNG frames into <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 <span data-ttu-id="0f3b6-104">Nelle app destinate a .NET Framework 4.5.2 e alle versioni precedenti, il metodo <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> genera un'eccezione <xref:System.ArgumentOutOfRangeException> se l'oggetto <xref:System.Drawing.Icon> presenta frame PNG.</span><span class="sxs-lookup"><span data-stu-id="0f3b6-104">In apps that target the .NET Framework 4.5.2 and earlier versions, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method throws an <xref:System.ArgumentOutOfRangeException> exception if the <xref:System.Drawing.Icon> object has PNG frames.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="0f3b6-105">Impatto</span><span class="sxs-lookup"><span data-stu-id="0f3b6-105">Impact</span></span>  
 <span data-ttu-id="0f3b6-106">Questa modifica influisce sulle app che vengono ricompilate per essere destinate a .NET Framework 4.6 e che implementano una gestione speciale per l'eccezione <xref:System.ArgumentOutOfRangeException> generata quando un oggetto <xref:System.Drawing.Icon> presenta frame PNG.</span><span class="sxs-lookup"><span data-stu-id="0f3b6-106">This change affects apps that are recompiled to target the .NET Framework 4.6 and that implement special handling for the <xref:System.ArgumentOutOfRangeException> that is thrown when an <xref:System.Drawing.Icon> object has PNG frames.</span></span> <span data-ttu-id="0f3b6-107">Quando è in esecuzione su .NET Framework 4.6, la conversione viene completata correttamente, non viene più generata un'eccezione <xref:System.ArgumentOutOfRangeException> e quindi non viene più richiamato il gestore di eccezioni.</span><span class="sxs-lookup"><span data-stu-id="0f3b6-107">When running under the .NET Framework 4.6, the conversion is successful, an <xref:System.ArgumentOutOfRangeException> is no longer thrown, and therefore the exception handler is no longer invoked.</span></span>  
  
### <a name="mitigation"></a><span data-ttu-id="0f3b6-108">Attenuazione</span><span class="sxs-lookup"><span data-stu-id="0f3b6-108">Mitigation</span></span>  
 <span data-ttu-id="0f3b6-109">Se questo comportamento è indesiderato, è possibile conservare il comportamento precedente aggiungendo l'elemento seguente alla sezione [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) del file app.config:</span><span class="sxs-lookup"><span data-stu-id="0f3b6-109">If this behavior is undesirable, you can retain the previous behavior by adding the following element to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 <span data-ttu-id="0f3b6-110">Se il file app.config contiene già l'elemento `AppContextSwitchOverrides` , il nuovo valore deve essere unito con l'attributo `value` come nell'esempio seguente:</span><span class="sxs-lookup"><span data-stu-id="0f3b6-110">If the app.config file already contains the `AppContextSwitchOverrides` element, the new value should be merged with the `value` attribute like this:</span></span>  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;<previous key>=<previous value>" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="0f3b6-111">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0f3b6-111">See also</span></span>

- [<span data-ttu-id="0f3b6-112">Modifiche di reindirizzamento</span><span class="sxs-lookup"><span data-stu-id="0f3b6-112">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6.md)
