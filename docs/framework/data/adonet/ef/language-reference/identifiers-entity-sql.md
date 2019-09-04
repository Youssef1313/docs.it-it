---
title: Identificatori (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d58a5edd-7b5c-48e1-b5d7-a326ff426aa4
ms.openlocfilehash: 4a8f98a9ea9601e1bf5f178e404f99e4a9160078
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250714"
---
# <a name="identifiers-entity-sql"></a>Identificatori (Entity SQL)
Gli identificatori vengono usati in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] per rappresentare alias di espressioni di query, riferimenti di variabili, proprietà di oggetti, funzioni e così via. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]in sono disponibili due tipi di identificatori: identificatori semplici e identificatori delimitati.  
  
## <a name="simple-identifiers"></a>Identificatori semplici  
 Un identificatore semplice in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] è una sequenza di caratteri alfanumerici e di sottolineatura. Il primo carattere dell'identificatore deve essere un carattere alfabetico (a-z o A-Z).  
  
## <a name="quoted-identifiers"></a>Identificatori delimitati  
 Un identificatore delimitato è una qualsiasi sequenza di caratteri racchiusi tra parentesi quadre ([]). Gli identificatori delimitati consentono di specificare gli identificatori con caratteri che non sono validi negli identificatori. Tutti i caratteri tra parentesi quadre diventano parte dell'identificatore, inclusi tutti gli spazi vuoti.  
  
 Un identificatore delimitato non può includere i caratteri seguenti:  
  
- Carattere di nuova riga.  
  
- Ritorno a capo.  
  
- Tabulazione.  
  
- Backspace.  
  
- Parentesi quadre aggiuntive (ovvero, parentesi quadre all'interno delle parentesi quadre che delineano l'identificatore).  
  
 Un identificatore delimitato può includere caratteri Unicode.  
  
 Gli identificatori delimitati consentono di creare caratteri per i nomi delle proprietà non validi negli identificatori, come illustrato nell'esempio seguente:  
  
 `SELECT c.ContactName AS [Contact Name] FROM customers AS c`  
  
 È inoltre possibile usare gli identificatori delimitati per specificare un identificatore che corrisponde a una parola chiave riservata di [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Se, ad esempio, il tipo `Email` dispone di una proprietà denominata "From", è possibile evitare l'ambiguità con la parola chiave riservata FROM usando parentesi quadre, come illustrato di seguito:  
  
 `SELECT e.[From] FROM emails AS e`  
  
 È possibile usare un identificatore tra virgolette sul lato destro di un operatore punto (.)  
  
 `SELECT t FROM ts as t WHERE t.[property] == 2`  
  
 Per usare la parentesi quadra in un identificatore, aggiungere un'ulteriore parentesi quadra. Nell'esempio seguente "`abc]`" è l'identificatore:  
  
 `SELECT t from ts as t WHERE t.[abc]]] == 2`  
  
 Per la semantica di confronto degli identificatori tra virgolette, vedere [set di caratteri di input](input-character-set-entity-sql.md).  
  
## <a name="aliasing-rules"></a>Regole relative all'utilizzo degli alias  
 È consigliabile specificare gli alias nelle [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query quando necessario, inclusi i costrutti seguenti: [!INCLUDE[esql](../../../../../../includes/esql-md.md)]  
  
- Campi di un costruttore ROW.  
  
- Elementi nella clausola FROM di un'espressione di query.  
  
- Elementi nella clausola SELECT di un'espressione di query.  
  
- Elementi nella clausola GROUP BY di un'espressione di query.  
  
### <a name="valid-aliases"></a>Alias validi  
 Gli alias validi in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sono qualsiasi identificatore semplice o identificatore tra virgolette.  
  
### <a name="alias-generation"></a>Generazione di alias  
 Se in un' [!INCLUDE[esql](../../../../../../includes/esql-md.md)] espressione di query non viene specificato alcun [!INCLUDE[esql](../../../../../../includes/esql-md.md)] alias, tenta di generare un alias in base alle regole semplici seguenti:  
  
- Se l'espressione di query (per la quale l'alias non è specificato) è un identificatore semplice o delimitato, tale identificatore viene usato come alias. `ROW(a, [b])`, ad esempio, diventa `ROW(a AS a, [b] AS [b])`.  
  
- Se l'espressione di query è un'espressione più complessa, ma l'ultimo componente dell'espressione è un identificatore semplice, tale identificatore viene usato come alias. `ROW(a.a1, b.[b1])`, ad esempio, diventa `ROW(a.a1 AS a1, b.[b1] AS [b1])`.  
  
 Si consiglia di non usare alias impliciti se successivamente si desidera usare il nome dell'alias. Tutte le volte che gli alias (impliciti o espliciti) sono in conflitto o vengono ripetuti nello stesso ambito, si verifica un errore di compilazione. Un alias implicito può essere compilato anche se è presente un alias esplicito o implicito con lo stesso nome.  
  
 Gli alias impliciti vengono generati automaticamente in base all'input dell'utente. La riga di codice seguente consente ad esempio di generare NAME come alias per entrambe le colonne, creando pertanto un conflitto.  
  
```  
SELECT product.NAME, person.NAME  
```  
  
 Anche la riga di codice seguente, in cui vengono usati alias espliciti, provoca la generazione di un errore. L'errore risulta tuttavia più evidente leggendo il codice.  
  
```  
SELECT 1 AS X, 2 AS X …  
```  
  
## <a name="scoping-rules"></a>Regole di ambito  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]definisce le regole di ambito che determinano quando determinate variabili sono visibili nel linguaggio di query. Alcune espressioni o istruzioni introducono nuovi nomi. Le regole di ambito determinano dove possono essere usati tali nomi, nonché quando o dove una nuova dichiarazione con lo stesso nome di un'altra può nascondere il relativo predecessore.  
  
 Quando i nomi vengono definiti in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] una query, vengono definiti all'interno di un ambito. Un ambito include l'intera area della query. I nomi definiti in un ambito sono visibili per tutte le espressioni o i riferimenti ai nomi inclusi in tale ambito. Prima dell'inizio di un ambito e dopo la sua fine, non è possibile fare riferimento ai nomi definiti nell'ambito.  
  
 Gli ambiti possono essere annidati. Parti di [!INCLUDE[esql](../../../../../../includes/esql-md.md)] introducono nuovi ambiti che coprono intere aree e queste aree possono contenere [!INCLUDE[esql](../../../../../../includes/esql-md.md)] altre espressioni che introducono anche gli ambiti. Quando gli ambiti sono annidati, è possibile fare riferimento ai nomi definiti nell'ambito più interno, che contiene il riferimento. È inoltre possibile fare riferimento a qualsiasi nome definito in qualsiasi ambito esterno. Due ambiti qualsiasi definiti all'interno dello stesso ambito sono considerati ambiti di pari livello. Non è possibile fare riferimento ai nomi definiti in ambiti di pari livello.  
  
 Se un nome dichiarato in un ambito interno corrisponde a un nome dichiarato in un ambito esterno, i riferimenti nell'ambito interno o negli ambiti dichiarati all'interno di tale ambito riguardano solo il nome appena dichiarato. Il nome nell'ambito esterno è nascosto.  
  
 Anche all'interno dello stesso ambito non è possibile fare riferimento ai nomi prima che vengano definiti.  
  
 I nomi globali possono esistere come parte dell'ambiente di esecuzione. Sono inclusi nomi di variabili di ambiente o raccolte persistenti. Per essere globale, un nome deve essere dichiarato nell'ambito più esterno.  
  
 I parametri non sono inclusi in un ambito. Poiché i riferimenti ai parametri includono una sintassi speciale, i nomi di parametri non sono mai in conflitto con gli altri nomi nella query.  
  
### <a name="query-expressions"></a>Espressioni di query  
 Un' [!INCLUDE[esql](../../../../../../includes/esql-md.md)] espressione di query introduce un nuovo ambito. I nomi definiti nella clausola FROM vengono introdotti nell'ambito FROM in base all'ordine con cui appaiono, da sinistra verso destra. Nell'elenco di join, le espressioni possono fare riferimento ai nomi definiti precedentemente nell'elenco. Le proprietà pubbliche (campi e così via) degli elementi identificati nella clausola FROM non vengono aggiunte all'ambito FROM. Per fare riferimento a queste proprietà è sempre necessario usare il nome completo dell'alias. In genere, tutte le parti dell'espressione SELECT vengono considerate all'interno dell'ambito FROM.  
  
 La clausola GROUP BY introduce inoltre un nuovo ambito di pari livello. Ogni gruppo può avere un nome che fa riferimento alla raccolta di elementi nel gruppo. Ogni espressione di raggruppamento introduce inoltre un nuovo nome nell'ambito GROUP. Viene inoltre eseguita l'aggiunta all'ambito dell'aggregazione annidata o del gruppo denominato. Le espressioni di raggruppamento si trovano all'interno dell'ambito FROM. Quando tuttavia viene usata una clausola GROUP BY, l'elenco SELECT (proiezione), la clausola HAVING e la clausola ORDER BY sono considerati inclusi nell'ambito GROUP e non nell'ambito FROM. Per le aggregazioni viene usata una modalità di gestione speciale, come descritto nel seguente elenco puntato.  
  
 Di seguito sono riportate alcune note aggiuntive relative agli ambiti:  
  
- L'elenco SELECT può introdurre nuovi nomi nell'ambito, in ordine. Le espressioni di proiezione a destra possono riferirsi ai nomi proiettati a sinistra.  
  
- La clausola ORDER BY può fare riferimento a nomi (alias) specificati nell'elenco SELECT.  
  
- L'ordine di valutazione delle clausole nell'espressione SELECT determina l'ordine con cui i nomi vengono introdotti nell'ambito. La clausola FROM viene valutata per prima, seguita dalle clausole WHERE, GROUP BY, HAVING, SELECT e infine ORDER BY.  
  
### <a name="aggregate-handling"></a>Gestione delle aggregazioni  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]supporta due forme di aggregazione: aggregazioni basate su raccolte e aggregazioni basate sui gruppi. Le aggregazioni basate sulle raccolte rappresentano il costrutto preferito in [!INCLUDE[esql](../../../../../../includes/esql-md.md)], mentre quelle basate sui gruppi sono supportate per offrire compatibilità con SQL.  
  
 Quando si risolve un'aggregazione, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tenta innanzitutto di considerarla come un'aggregazione basata su raccolte. Se l'operazione ha [!INCLUDE[esql](../../../../../../includes/esql-md.md)] esito negativo, trasforma l'input di aggregazione in un riferimento all'aggregazione annidata e tenta di risolvere la nuova espressione, come illustrato nell'esempio seguente.  
  
 `AVG(t.c) becomes AVG(group..(t.c))`  
  
## <a name="see-also"></a>Vedere anche

- [Riferimento a Entity SQL](entity-sql-reference.md)
- [Panoramica di Entity SQL](entity-sql-overview.md)
- [Set di caratteri di input](input-character-set-entity-sql.md)
