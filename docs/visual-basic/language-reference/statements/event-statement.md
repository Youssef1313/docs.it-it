---
title: Istruzione Event (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Event
- vb.Custom
helpviewer_keywords:
- Event statement [Visual Basic]
- declaring events [Visual Basic], syntax
- Public keyword [Visual Basic], Event statements
- Custom keyword [Visual Basic]
- declarations [Visual Basic], events
- event keyword [Visual Basic]
- WithEvents keyword [Visual Basic], Event statements
- events [Visual Basic], declaring
- ByVal keyword [Visual Basic], Event statements
- events [Visual Basic], custom
- ByRef keyword [Visual Basic], Event statements
- declaring user-defined events
ms.assetid: 306ff8ed-74dd-4b6a-bd2f-e91b17474042
ms.openlocfilehash: 53d545a0c03749b13276a34f233f05493e5c94b0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944444"
---
# <a name="event-statement"></a>Istruzione Event
Dichiara un evento definito dall'utente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
[ <attrlist> ] [ accessmodifier ] _  
[ Shared ] [ Shadows ] Event eventname[(parameterlist)] _  
[ Implements implementslist ]  
' -or-  
[ <attrlist> ] [ accessmodifier ] _  
[ Shared ] [ Shadows ] Event eventname As delegatename _  
[ Implements implementslist ]  
' -or-  
 [ <attrlist> ] [ accessmodifier ] _  
[ Shared ] [ Shadows ] Custom Event eventname As delegatename _  
[ Implements implementslist ]  
   [ <attrlist> ] AddHandler(ByVal value As delegatename)  
      [ statements ]  
   End AddHandler  
   [ <attrlist> ] RemoveHandler(ByVal value As delegatename)  
      [ statements ]  
   End RemoveHandler  
   [ <attrlist> ] RaiseEvent(delegatesignature)  
      [ statements ]  
   End RaiseEvent  
End Event  
```  
  
## <a name="parts"></a>Parti  
  
|Parte|Descrizione|  
|---|---|  
|`attrlist`|facoltativo. Elenco degli attributi applicabili all'evento. Gli attributi sono separati da una virgola. È necessario racchiudere l' [elenco degli attributi](../../../visual-basic/language-reference/statements/attribute-list.md) tra parentesi angolari`<`(""`>`e "").|  
|`accessmodifier`|facoltativo. Specifica il tipo di codice che può accedere all'evento. Può essere uno dei seguenti:<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md): qualsiasi codice in grado di accedere all'elemento che lo dichiara può accedervi.<br />-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md): solo il codice all'interno della classe o di una classe derivata può accedervi.<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md): solo il codice nello stesso assembly può accedervi.<br />-   [Private](../../../visual-basic/language-reference/modifiers/private.md): solo il codice nell'elemento che lo dichiara può accedervi.<br /> -   Il codice solo [Friend protetto](../../language-reference/modifiers/protected-friend.md)nella classe dell'evento, una classe derivata o lo stesso assembly può accedervi. <br />- Il codice [privato protetto](../../language-reference/modifiers/private-protected.md)solo nella classe dell'evento o in una classe derivata nello stesso assembly può accedervi.|  
|`Shared`|facoltativo. Specifica che l'evento non è associato a una specifica istanza di una classe o di una struttura.|  
|`Shadows`|facoltativo. Indica che l'evento ridichiara e nasconde un elemento di programmazione omonimo o un insieme di elementi in overload di una classe base. È possibile nascondere qualsiasi tipo di elemento dichiarato con qualsiasi altro tipo.<br /><br /> Un elemento nascosto non è disponibile all'interno della classe derivata che lo nasconde, a meno che l'elemento di shadowing sia inaccessibile. Ad esempio, se un elemento `Private` nasconde un elemento della classe base, il codice che non dispone dell'autorizzazione per accedere all'elemento `Private` accede invece all'elemento della classe base.|  
|`eventname`|Richiesto. Nome dell'evento, conforme alle convenzioni di denominazione standard delle variabili.|  
|`parameterlist`|facoltativo. Elenco di variabili locali che rappresentano i parametri dell'evento. È necessario racchiudere l' [elenco di parametri](../../../visual-basic/language-reference/statements/parameter-list.md) tra parentesi.|  
|`Implements`|facoltativo. Indica che l'evento implementa un evento di un'interfaccia.|  
|`implementslist`|Necessario se si fornisce `Implements`. Elenco delle routine `Sub` implementate. Nel caso di più routine, è possibile separarle mediante virgole.<br /><br /> *implementedprocedure* [, *implementedprocedure* ...]<br /><br /> Ogni `implementedprocedure` presenta la sintassi e le parti seguenti:<br /><br /> `interface`.`definedname`<br /><br /> -   `interface`Necessaria. Nome di un'interfaccia implementata dalla classe o dalla struttura che contiene la routine.<br />-   `Definedname`Necessaria. Nome mediante il quale la routine viene definita in `interface`. Non è necessario che questo nome corrisponda al nome usato dalla routine per implementare la routine definita, ossia `name`.|  
|`Custom`|Richiesto. È necessario che gli eventi dichiarati come `Custom` definiscano funzioni di accesso `AddHandler`, `RemoveHandler` e `RaiseEvent` personalizzate.|  
|`delegatename`|facoltativo. Nome del delegato che specifica la firma del gestore eventi.|  
|`AddHandler`|Richiesto. Dichiara una funzione di accesso `AddHandler` che specifica le istruzioni da eseguire quando viene aggiunto un gestore eventi, sia in modo esplicito mediante l'istruzione `AddHandler` che in modo implicito mediante la clausola `Handles`|  
|`End AddHandler`|Richiesto. Termina il blocco `AddHandler`.|  
|`value`|Richiesto. Nome parametro.|  
|`RemoveHandler`|Richiesto. Dichiara una funzione di accesso `RemoveHandler`, che specifica le istruzioni da eseguire quando un gestore eventi viene rimosso mediante l'istruzione `RemoveHandler`.|  
|`End RemoveHandler`|Richiesto. Termina il blocco `RemoveHandler`.|  
|`RaiseEvent`|Richiesto. Dichiara una funzione di accesso `RaiseEvent`, che specifica le istruzioni da eseguire quando l'evento viene generato mediante l'istruzione `RaiseEvent`. In genere, viene richiamato un elenco di delegati gestito dalle funzioni di accesso `AddHandler` e `RemoveHandler`.|  
|`End RaiseEvent`|Richiesto. Termina il blocco `RaiseEvent`.|  
|`delegatesignature`|Richiesto. Elenco di parametri che corrisponde ai parametri richiesti dal delegato `delegatename`. È necessario racchiudere l' [elenco di parametri](../../../visual-basic/language-reference/statements/parameter-list.md) tra parentesi.|  
|`statements`|facoltativo. Istruzioni che includono i corpi dei metodi `AddHandler`, `RemoveHandler` e `RaiseEvent`.|  
|`End Event`|Richiesto. Termina il blocco `Event`.|  
  
## <a name="remarks"></a>Note  
 Dopo aver dichiarato l'evento, usare l'istruzione `RaiseEvent` per generarlo. Nei frammenti seguenti viene mostrato un esempio tipico di dichiarazione e generazione di un evento:  
  
 [!code-vb[VbVbalrEvents#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#13)]  
  
> [!NOTE]
> È possibile dichiarare argomenti per gli eventi analogamente a quanto avviene per gli argomenti di routine, tenendo però conto che non è possibile specificare per gli eventi argomenti denominati, argomenti `ParamArray` o argomenti `Optional`, né ottenere da essi valori restituiti.  
  
 Per gestire un evento è necessario associarlo a una subroutine del gestore eventi mediante l'istruzione `Handles` o `AddHandler`. Le firme della subroutine e dell'evento devono corrispondere. Per gestire un evento condiviso è necessario usare l'istruzione `AddHandler`.  
  
 Si può usare `Event` solo a livello di modulo. Ciò significa che il *contesto di dichiarazione* per un evento deve essere una classe, una struttura, un modulo o un'interfaccia e non può essere un file di origine, uno spazio dei nomi, una procedura o un blocco. Per altre informazioni, vedere [Contesti delle dichiarazioni e livelli di accesso predefiniti](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Nella maggior parte dei casi, per dichiarare un evento è possibile usare la prima sintassi nella sezione relativa alla sintassi di questo argomento. In alcuni scenari è tuttavia necessario disporre di un controllo maggiore sui dettagli del comportamento dell'evento. L'ultima sintassi nella sezione relativa alla sintassi di questo argomento, che usa la parola chiave `Custom`, offre questa possibilità consentendo la definizione di eventi personalizzati. In un evento personalizzato si specifica esattamente ciò che accade quando il codice aggiunge o rimuove un gestore eventi a o dall'evento oppure quando il codice genera l'evento. Per esempi, vedere [Procedura: Dichiarare eventi personalizzati per conservare la memoria](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md) e [procedura: Dichiarare eventi personalizzati per evitare il](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)blocco.  
  
## <a name="example"></a>Esempio  
 Negli esempi seguenti, gli eventi vengono usati per il conto alla rovescia dei secondi, da 10 a 0. Il codice illustra numerosi metodi, proprietà e istruzioni correlati agli eventi, inclusa l'istruzione `RaiseEvent`.  
  
 La classe che genera un evento viene definita origine e i metodi che lo elaborano vengono definiti gestori eventi. Un'origine eventi può disporre di più gestori per gli eventi generati. Quando la classe genera l'evento, lo stesso evento viene generato in tutte le classi per cui è stato scelto di gestire eventi per tale istanza dell'oggetto.  
  
 Nell'esempio vengono usati anche un form (`Form1`) con un pulsante (`Button1`) e una casella di testo (`TextBox1`). Quando si fa clic sul pulsante, nella prima casella di testo viene visualizzato il conto alla rovescia dei secondi da 10 a 0. Al termine dei 10 secondi, nella prima casella di testo viene visualizzato "Done".  
  
 Il codice di `Form1` specifica gli stati di inizio e fine del form. Contiene inoltre il codice eseguito quando vengono generati gli eventi.  
  
 Per usare l'esempio, aprire un nuovo progetto Windows Form. Aggiungere quindi un pulsante denominato `Button1` e una casella di testo denominata `TextBox1` al form principale, denominato `Form1`. Fare quindi clic con il pulsante destro del mouse sul form e scegliere **Visualizza codice** per aprire l'editor di codice.  
  
 Aggiungere una variabile `WithEvents` alla sezione delle dichiarazioni della classe `Form1`:  
  
 [!code-vb[VbVbalrEvents#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#14)]  
  
 Aggiungere il codice seguente al codice per `Form1`: Sostituire eventuali routine duplicate, ad esempio `Form_Load` o `Button_Click`.  
  
 [!code-vb[VbVbalrEvents#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#15)]  
  
 Premere F5 per eseguire l'esempio precedente e fare clic sul pulsante **Avvia**. Nella prima casella di testo viene avviato il conto alla rovescia dei secondi. Al termine dei 10 secondi, nella prima casella di testo viene visualizzato "Done".  
  
> [!NOTE]
> Il metodo `My.Application.DoEvents` non elabora gli eventi allo stesso modo del form. Per consentire al form di gestire direttamente gli eventi, si può ricorrere al multithreading. Per altre informazioni, vedere [Threading gestito](../../../standard/threading/index.md).  
  
## <a name="see-also"></a>Vedere anche

- [Istruzione RaiseEvent](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
- [Istruzione Implements](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Eventi](../../../visual-basic/programming-guide/language-features/events/index.md)
- [Istruzione AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [Istruzione RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Istruzione Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Procedura: Dichiarare eventi personalizzati per proteggere la memoria](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
- [Procedura: Dichiarare eventi personalizzati per evitare il blocco](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
