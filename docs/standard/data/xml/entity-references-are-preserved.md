---
title: Riferimenti alle entità conservati
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e512f2077c2e6b9feba5024c4eabc2568357ecab
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965909"
---
# <a name="entity-references-are-preserved"></a>Riferimenti alle entità conservati
Se il riferimento all'entità non viene espanso, ma conservato, il modello DOM (Document Object Model) XML compila un nodo **XmlEntityReference** quando rileva un riferimento all'entità.  
  
 Usando il seguente codice XML,  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 il modello DOM compila un nodo **XmlEntityReference** quando rileva il riferimento `&publisher;`. Il nodo **XmlEntityReference** contiene nodi figlio copiati dal contenuto della dichiarazione di entità. Nell'esempio di codice precedente è contenuto un testo nella dichiarazione di entità, quindi viene creato un nodo **XmlText** come nodo figlio del nodo del riferimento all'entità.  
  
 ![Struttura ad albero per i riferimenti alle entità conservati](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")  
Struttura ad albero per i riferimenti alle entità conservati  
  
 I nodi figlio di **XmlEntityReference** sono copie di tutti i nodi figlio creati dal nodo **XmlEntity** quando è stata rilevata la dichiarazione di entità.  
  
> [!NOTE]
> I nodi copiati da **XmlEntity** non sono sempre copie esatte dopo che vengono inseriti sotto il nodo del riferimento all'entità. Nell'ambito del nodo del riferimento all'entità possono essere presenti spazi dei nomi che incidono sulla configurazione finale dei nodi figlio.  
  
 Per impostazione predefinita, le entità generali, ad esempio `&abc;`, vengono conservate e vengono sempre creati nodi **XmlEntityReference**.  
  
## <a name="see-also"></a>Vedere anche

- [Modello DOM (Document Object Mode) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
