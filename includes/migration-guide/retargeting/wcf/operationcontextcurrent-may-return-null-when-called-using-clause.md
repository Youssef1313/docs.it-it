---
ms.openlocfilehash: 62ba525a28960d96c5458aa1481e1f319d5bc875
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859321"
---
### <a name="operationcontextcurrent-may-return-null-when-called-in-a-using-clause"></a>OperationContext.Current può restituire Null in caso di chiamata in una clausola using

|   |   |
|---|---|
|Dettagli|<xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> può restituire <code>null</code> e può essere generata un'eccezione <xref:System.NullReferenceException> se vengono soddisfatte tutte le condizioni seguenti:<ul><li>Si recupera il valore della proprietà <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> in un metodo che restituisce <xref:System.Threading.Tasks.Task> o <xref:System.Threading.Tasks.Task%601>.</li><li>Si crea un'istanza dell'oggetto <xref:System.ServiceModel.OperationContextScope> in una clausola <code>using</code>.</li><li>Si recupera il valore della proprietà <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> all'interno di <code>using statement</code>. Ad esempio:</li></ul><pre><code class="lang-csharp">using (new OperationContextScope(OperationContext.Current))&#13;&#10;{&#13;&#10;OperationContext context = OperationContext.Current;      // OperationContext.Current is null.&#13;&#10;// ...&#13;&#10;}&#13;&#10;</code></pre>|
|Suggerimento|Per risolvere questo problema, è possibile eseguire le operazioni seguenti:<ul><li>Modificare il codice come indicato di seguito per creare un'istanza di un nuovo oggetto <xref:System.ServiceModel.OperationContext.Current%2A> non <code>null</code>:</li></ul><pre><code class="lang-csharp">OperationContext ocx = OperationContext.Current;&#13;&#10;using (new OperationContextScope(OperationContext.Current))&#13;&#10;{&#13;&#10;OperationContext.Current = new OperationContext(ocx.Channel);&#13;&#10;// ...&#13;&#10;}&#13;&#10;</code></pre><ul><li>Installare l'aggiornamento più recente di .NET Framework 4.6.2 oppure eseguire l'aggiornamento a una versione successiva di .NET Framework. Viene così disabilitato il flusso di <xref:System.Threading.ExecutionContext> in <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> e ripristinato il comportamento delle applicazioni WCF in .NET Framework 4.6.1 e versioni precedenti. Questo comportamento è configurabile ed è equivalente all'aggiunta dell'impostazione dell'app seguente nel file di configurazione:</li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.ServiceModel.DisableOperationContextAsyncFlow&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>Se questa modifica non è opportuna e l'applicazione dipende dal flusso del contesto di esecuzione tra i contesti operativi, è possibile abilitare il flusso come indicato di seguito:<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.ServiceModel.DisableOperationContextAsyncFlow&quot; value=&quot;false&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Ambito|Microsoft Edge|
|Versione|4.6.2|
|Tipo|Ridestinazione|
|API interessate|<ul><li><xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType></li></ul>|

