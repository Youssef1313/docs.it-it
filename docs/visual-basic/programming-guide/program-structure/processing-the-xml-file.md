---
title: Elaborazione del file XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments [Visual Basic], parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
ms.openlocfilehash: 4230fd88b4b60c631135f5b7fb15f4b6272b5351
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347295"
---
# <a name="processing-the-xml-file-visual-basic"></a>Elaborazione del file XML (Visual Basic)
Il compilatore genera una stringa identificativa (ID) per ciascun costrutto del codice che contiene tag per la creazione della documentazione. Per informazioni su come contrassegnare il codice, vedere [tag di commento XML](../../../visual-basic/language-reference/xmldoc/index.md). La stringa ID identifica in modo univoco il costrutto. I programmi che elaborano il file XML possono utilizzare la stringa ID per identificare l'elemento di Reflection/metadati .NET Framework corrispondente.  
  
 Il file XML non è una rappresentazione gerarchica del codice. si tratta di un elenco semplice con un ID generato per ogni elemento.  
  
 Per generare gli ID, il compilatore applica le regole seguenti:  
  
- Assenza di spazi vuoti nella stringa.  
  
- La prima parte della stringa ID specifica il tipo di membro, con un singolo carattere seguito dai due punti. Vengono utilizzati i tipi di membro seguenti.  
  
|Carattere|Descrizione|  
|---|---|  
|N|namespace<br /><br /> Non è possibile aggiungere commenti alla documentazione a uno spazio dei nomi, ma è possibile creare riferimenti CREF, laddove supportati.|  
|Elemento|Tipo: `Class`, `Module`, `Interface`, `Structure`, `Enum`, `Delegate`|  
|F|campo: `Dim`|  
|P|Property: `Property` (incluse le proprietà predefinite)|  
|M|Metodo: `Sub`, `Function`, `Declare`, `Operator`|  
|E|evento: `Event`|  
|!|stringa di errore<br /><br /> Nella parte restante della stringa vengono fornite informazioni sull'errore. Il compilatore Visual Basic genera informazioni sugli errori per i collegamenti che non possono essere risolti.|  
  
- La seconda parte del `String` è il nome completo dell'elemento, a partire dalla radice dello spazio dei nomi. Il nome dell'elemento, i relativi tipi di inclusione e lo spazio dei nomi sono separati da punti. Se il nome dell'elemento contiene punti, questi vengono sostituiti dal simbolo di cancelletto (#). Si presuppone che nessun elemento abbia un segno di cancelletto direttamente nel nome. Il nome completo del costruttore `String`, ad esempio, verrebbe `System.String.#ctor`.  
  
- Per le proprietà e i metodi, se il metodo ha degli argomenti, verrà incluso di seguito l'elenco degli argomenti racchiuso tra parentesi. Se non sono presenti argomenti, non verranno usate le parentesi. Gli argomenti sono separati da virgole. La codifica di ogni argomento segue direttamente il modo in cui viene codificata in una firma .NET Framework.  
  
## <a name="example"></a>Esempio  
 Nel codice seguente viene illustrato come vengono generate le stringhe ID per una classe e i relativi membri.  
  
 [!code-vb[VbVbcnXmlDocComments#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#10)]  
  
## <a name="see-also"></a>Vedere anche

- [-doc](../../../visual-basic/reference/command-line-compiler/doc.md)
- [Procedura: Creare documentazione XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
