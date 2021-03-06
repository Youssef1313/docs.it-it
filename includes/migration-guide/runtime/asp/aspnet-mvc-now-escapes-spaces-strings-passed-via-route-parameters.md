---
ms.openlocfilehash: 8d058d3297471e67459164f18358b1d143465712
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803170"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a>ASP.NET MVC usa ora caratteri di escape per gli spazi nelle stringhe passate tramite i parametri di una route

|   |   |
|---|---|
|Dettagli|Per conformità allo standard RFC 2396, vengono ora usati caratteri di escape per gli spazi nei percorsi di route durante il popolamento dei parametri di azione da una route. Pertanto, mentre <code>/controller/action/some data</code> in precedenza corrispondeva alla route <code>/controller/action/{data}</code> e forniva il parametro dati <code>some data</code>, ora fornisce invece <code>some%20data</code>.|
|Suggerimento|È necessario aggiornare il codice per rimuovere i caratteri di escape dai parametri stringa da una route. Se è necessario l'URI originale, è possibile accedervi con l'API <xref:System.Net.HttpWebRequest.RequestUri>.OriginalString.|
|Ambito|Secondario|
|Versione|4.5.2|
|Tipo|Runtime|
|API interessate|<ul><li><xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)?displayProperty=nameWithType></li></ul>|

