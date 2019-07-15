---
ms.openlocfilehash: 2413e1997b6e729b9d5889677e25254aaa24afea
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859288"
---
### <a name="incorrect-implementation-of-memberdescriptorequals"></a>Implementazione non corretta di MemberDescriptor.Equals

|   |   |
|---|---|
|Dettagli|L'implementazione originale del metodo <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> confronta due diverse proprietà stringa degli oggetti confrontati: la stringa del nome di categoria e la stringa di descrizione. Per risolvere il problema, confrontare <xref:System.ComponentModel.MemberDescriptor.Category> del primo oggetto con <xref:System.ComponentModel.MemberDescriptor.Category> del secondo e <xref:System.ComponentModel.MemberDescriptor.Description> del primo con <xref:System.ComponentModel.MemberDescriptor.Description> del secondo.|
|Suggerimento|Se l'applicazione dipende dal fatto che <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> talvolta restituisca <code>false</code> quando i descrittori sono equivalenti ed è destinata a NET Framework 4.6.2 o versione successiva, sono disponibili varie opzioni:<ol><li>Apportare modifiche al codice per confrontare i campi <xref:System.ComponentModel.MemberDescriptor.Category> e <xref:System.ComponentModel.MemberDescriptor.Description> manualmente oltre a chiamare il metodo <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType>.</li><li>Rifiutare esplicitamente questa modifica aggiungendo il valore seguente al file app.config:</li></ol><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Se l'applicazione è destinata a NET Framework 4.6.1 o versioni precedenti ed è in esecuzione in .NET Framework 4.6.2 o versione successiva e si vuole abilitare questa modifica, è possibile impostare l'opzione di compatibilità su <code>false</code> aggiungendo il valore seguente al file app.config:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Ambito|Microsoft Edge|
|Versione|4.6.2|
|Tipo|Ridestinazione|
|API interessate|<ul><li><xref:System.ComponentModel.MemberDescriptor.Equals(System.Object)?displayProperty=nameWithType></li></ul>|

