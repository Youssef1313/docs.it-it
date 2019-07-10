---
title: Progettazione di struct
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
author: KrzysztofCwalina
ms.openlocfilehash: e787c5b34848a561b43c3457341673f11cc2bd00
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775549"
---
# <a name="struct-design"></a>Progettazione di struct
Il tipo di valore per utilizzo generico è più noto anche come uno struct, la parola chiave c#. In questa sezione vengono fornite linee guida per la progettazione di struct generale.  
  
 **X non** fornire un costruttore senza parametri per uno struct.  
  
 Attenendosi a questa linea guida consente le matrici di struct da creare senza dover eseguire il costruttore su ogni elemento della matrice. Si noti che C# non consente di struct hanno costruttori senza parametri.  
  
 **X DO NOT** definire i tipi di valore modificabile.  
  
 I tipi di valore modificabile presentano problemi diversi. Ad esempio, quando un getter della proprietà viene restituito un tipo di valore, il chiamante riceve una copia. Poiché la copia viene creata in modo implicito, gli sviluppatori potrebbero non essere consapevoli che essi siano mutazione la copia e non il valore originale. Inoltre, in alcuni linguaggi (linguaggi dinamici, in particolare) sono i problemi usando i tipi di valore modificabile perché anche le variabili locali, quando viene dereferenziato, causare una copia da apportare.  
  
 **✓ DO** garantire che in uno stato in cui tutti i dati dell'istanza è impostato su zero, false o null (se necessario) è valido.  
  
 Questo impedisce la creazione accidentale di istanze non valide quando viene creata una matrice degli struct.  
  
 **✓ DO** implementare <xref:System.IEquatable%601> sui tipi di valore.  
  
 Il <xref:System.Object.Equals%2A?displayProperty=nameWithType> metodo sui tipi di valore determina la conversione boxing e l'implementazione predefinita non è molto efficiente, perché usa la reflection. <xref:System.IEquatable%601.Equals%2A> può avere migliori prestazioni e può essere implementata in modo che questo evento non comporta la conversione boxing.  
  
 **X DO NOT** estendere in modo esplicito <xref:System.ValueType>. In effetti, la maggior parte dei linguaggi evitare questo problema.  
  
 In generale, gli struct possono rivelarsi molto utili, ma devono essere utilizzati solo per i valori di piccole dimensioni, single, non modificabili che non essere boxed frequentemente.  
  
 *Parti protette da copyright © 2005, 2009 Microsoft Corporation. Tutti i diritti riservati.*  
  
 *Ristampato con l'autorizzazione di Pearson Education, Inc. dal [linee guida di progettazione di Framework: Convenzioni, linguaggi e modelli per le librerie .NET di riutilizzabile, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina e Brad Abrams, pubblicato il 22 ottobre 2008 da Addison-Wesley Professional come parte della serie di sviluppo di Microsoft Windows.*  
  
## <a name="see-also"></a>Vedere anche

- [Linee guida per la progettazione di tipi](../../../docs/standard/design-guidelines/type.md)
- [Linee guida per la progettazione di Framework](../../../docs/standard/design-guidelines/index.md)
- [Scelta tra classi e struct](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)
