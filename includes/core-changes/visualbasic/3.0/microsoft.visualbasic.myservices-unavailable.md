---
ms.openlocfilehash: 58e65bae1593f23945a971b896a1db4a929b4587
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567439"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a>Tipi nello spazio dei nomi Microsoft. VisualBasic. MyServices non disponibili

I tipi nello spazio dei nomi <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> non sono disponibili.

#### <a name="version-introduced"></a>Versione introdotta

.NET Core 3,0 Preview 8

#### <a name="change-description"></a>Descrizione della modifica

I tipi nello spazio dei nomi <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> sono disponibili in alcune versioni di .NET Core 3,0 Preview. Non sono più disponibili a partire da .NET Core 3,0 Preview 9.

I tipi sono stati rimossi per evitare dipendenze di assembly non necessarie o modifiche di rilievo nelle versioni successive.

#### <a name="recommended-action"></a>Azione consigliata

Se il codice dipende dall'uso dei tipi **Microsoft. VisualBasic. MyServices** e dei relativi membri, nella libreria di classi .NET sono presenti tipi e membri corrispondenti. Di seguito è riportato un mapping dei tipi **Microsoft. VisualBasic. MyServices** ai tipi di libreria di classi .NET equivalenti:

|Tipo Microsoft. VisualBasic. MyServices|Tipo libreria di classi .NET|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|<xref:System.Windows.Clipboard?displayProperty=nameWithType> per applicazioni WPF <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> per applicazioni Windows Forms|
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|Tipi nello spazio dei nomi <xref:System.IO>|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|Tipi correlati al registro di sistema nello spazio dei nomi <xref:Microsoft.Win32>|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a>Category

Visual Basic -

#### <a name="affected-apis"></a>API interessate

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-- >

