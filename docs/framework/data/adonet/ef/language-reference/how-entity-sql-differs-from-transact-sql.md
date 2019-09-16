---
title: Differenze tra Entity SQL e Transact-SQL
ms.date: 03/30/2017
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
ms.openlocfilehash: e809cea2f853eed51d28e55f81a411f7af2e5a33
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854480"
---
# <a name="how-entity-sql-differs-from-transact-sql"></a>Differenze tra Entity SQL e Transact-SQL
In questo argomento vengono descritte le [!INCLUDE[esql](../../../../../../includes/esql-md.md)] differenze tra e Transact-SQL.  
  
## <a name="inheritance-and-relationships-support"></a>Supporto di ereditarietà e relazioni  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]interagisce direttamente con gli schemi di entità concettuali e supporta le funzionalità del modello concettuale, ad esempio l'ereditarietà e le relazioni.  
  
 Quando si usa l'ereditarietà, è spesso utile selezionare le istanze di un sottotipo da una raccolta di istanze di supertipi. Questa capacità è fornita dall'operatore [oftype](oftype-entity-sql.md) in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (simile a `oftype` nelle sequenze in C#).  
  
## <a name="support-for-collections"></a>Supporto per le raccolte  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Considera le raccolte come entità di prima classe. Ad esempio:  
  
- Le espressioni della Collection sono valide in una clausola `from`.  
  
- Le sottoquery `in` e `exists` sono state generalizzate per consentire qualsiasi raccolta.  
  
     Una sottoquery è un tipo di raccolta. `e1 in e2` e `exists(e)` sono i construct [!INCLUDE[esql](../../../../../../includes/esql-md.md)] usati per eseguire queste operazioni.  
  
- Le operazioni Set, ad esempio `union`, `intersect` ed `except`, possono ora essere usate sulle raccolte.  
  
- I join funzionano sulle raccolte.  
  
## <a name="support-for-expressions"></a>Supporto per le espressioni  
 Transact-SQL include sottoquery (tabelle) ed espressioni (righe e colonne).  
  
 Per supportare raccolte e raccolte nidificate [!INCLUDE[esql](../../../../../../includes/esql-md.md)] , in viene eseguita una qualsiasi espressione. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]è più componibile rispetto a Transact-SQL: ogni espressione può essere usata ovunque. Le espressioni di query restituiscono sempre raccolte dei tipi previsti e possono essere usate in qualunque posizione in cui è consentita un'espressione sulle raccolte. Per informazioni sulle espressioni Transact-SQL non supportate in [!INCLUDE[esql](../../../../../../includes/esql-md.md)], vedere [espressioni](unsupported-expressions-entity-sql.md)non supportate.  
  
 Le query seguenti sono tutte query [!INCLUDE[esql](../../../../../../includes/esql-md.md)] valide:  
  
```  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}   
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a>Modalità di gestione uniforme delle sottoquery  
 Data l'enfasi sulle tabelle, Transact-SQL esegue l'interpretazione contestuale delle sottoquery. Una sottoquery nella `from` clausola, ad esempio, viene considerata come multiset (tabella). La stessa sottoquery usata nella clausola `select` viene invece considerata come una sottoquery scalare. Analogamente, una sottoquery utilizzata sul lato sinistro di un `in` operatore viene considerata una sottoquery scalare, mentre il lato destro dovrebbe essere una sottoquery multiset.  
  
 In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] vengono eliminate queste differenze. Un'espressione dispone di un'interpretazione uniforme che non dipende dal contesto in cui viene usata. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]considera tutte le sottoquery come sottoquery multiset. Se si desidera un valore scalare dalla sottoquery, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fornisce l' `anyelement` operatore che opera su una raccolta (in questo caso, la sottoquery) ed estrae un valore singleton dalla raccolta.  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a>Eliminazione della presenza di coercizioni implicite per le sottoquery  
 Un effetto collaterale della modalità di gestione uniforme delle sottoquery è la conversione implicita delle sottoquery in valori scalari. In particolare, in Transact-SQL, un multiset di righe (con un singolo campo) viene convertito in modo implicito in un valore scalare il cui tipo di dati è quello del campo.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] non supporta questa coercizione implicita. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fornisce un operatore ANYELEMENT per estrarre un valore Singleton da una raccolta e una clausola `select value` per evitare di creare un wrapper di riga durante un'espressione di query.  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a>Seleziona valore: Evitare il wrapper di riga implicito  
 La clausola SELECT in una sottoquery Transact-SQL crea in modo implicito un wrapper di riga intorno agli elementi nella clausola. Questo implica che non si possono creare raccolte di scalari o oggetti. Transact-SQL consente una coercizione implicita tra un RowType con un campo e un valore singleton dello stesso tipo di dati.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fornisce la clausola `select value` per ignorare la costruzione di riga implicita. Nella clausola `select value` è possibile specificare un solo elemento. Quando viene usata questa clausola, non viene costruito alcun wrapper di riga intorno agli elementi nella clausola `select` e può essere prodotta una raccolta della forma desiderata, ad esempio `select value a`.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fornisce inoltre il costruttore ROW per la costruzione di righe arbitrarie. `select` prende uno o più elementi nella proiezione e crea un record di dati con campi, come mostrato di seguito:  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a>Correlazione sinistra e utilizzo di alias  
 In Transact-SQL le espressioni in un determinato ambito (una singola clausola come `select` o `from`) non possono fare riferimento a espressioni definite in precedenza nello stesso ambito. Alcuni dialetti di SQL (incluso Transact-SQL) supportano formati limitati di questi nella `from` clausola.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]generalizza le `from` correlazioni a sinistra nella clausola e le gestisce in modo uniforme. Le espressioni nella clausola `from` possono fare riferimento a definizioni precedenti (definizioni a sinistra) nella stessa clausola senza che sia necessaria sintassi aggiuntiva.  
  
 In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] vengono inoltre imposte restrizioni aggiuntive sulle query che implicano l'uso di clausole `group by`. Le espressioni nella `select` clausola e `having` nella clausola di tali query `group by` possono fare riferimento solo alle chiavi tramite i relativi alias. Il costrutto seguente è valido in Transact-SQL, ma non [!INCLUDE[esql](../../../../../../includes/esql-md.md)]in:  
  
```  
select t.x + t.y from T as t group by t.x + t.y  
```  
  
 Per eseguire questa operazione in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:  
  
```  
select k from T as t group by (t.x + t.y) as k  
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a>Riferimento a colonne (proprietà) di tabelle (raccolte)  
 Tutti i riferimenti alle colonne in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] devono essere qualificati con l'alias di tabella. Il costrutto seguente (presupponendo che `a` sia una colonna valida della tabella `T`) è valido in Transact-SQL [!INCLUDE[esql](../../../../../../includes/esql-md.md)]ma non in.  
  
```  
select a from T  
```  
  
 Il formato in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] è:  
  
```  
select t.a as A from T as t  
```  
  
 Gli alias di tabella sono facoltativi nella clausola `from`. Il nome della tabella viene usato come l'alias implicito. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] consente anche l'uso del formato seguente:  
  
```  
select Tab.a from Tab  
```  
  
## <a name="navigation-through-objects"></a>Navigazione negli oggetti  
 Transact-SQL utilizza la notazione "." per fare riferimento a colonne di (una riga di) una tabella. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] estende questa notazione (preso in prestito dai linguaggi di programmazione) per supportare la navigazione tra le proprietà di un oggetto.  
  
 Se, ad esempio, `p` è un'espressione del tipo Person, di seguito è riportata la sintassi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] che consente di fare riferimento alla città dell'indirizzo di tale persona.  
  
```  
p.Address.City   
```  
  
## <a name="no-support-for-"></a>Mancanza di supporto per *  
 Transact-SQL supporta la sintassi * non qualificata come alias per l'intera riga e la sintassi qualificata \* (t.\*) come collegamento per i campi di tale tabella. Transact-SQL consente inoltre di effettuare un'aggregazione Count (\*) speciale, che include valori null.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] non supporta il construct *. Le query Transact-SQL del form `select * from T` e `select T1.* from T1, T2...` possono essere espresse rispettivamente [!INCLUDE[esql](../../../../../../includes/esql-md.md)] in `select value t from T as t` come `select value t1 from T1 as t1, T2 as t2...`e. Questi costrutti consentono inoltre di gestire l'ereditarietà (sostituibilità del valore), mentre le varianti `select *` sono limitate alle proprietà di primo livello del tipo dichiarato.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] non supporta l'aggregato `count(*)`. In alternativa, utilizzare `count(0)`.  
  
## <a name="changes-to-group-by"></a>Modifiche a Group By  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] supporta l'uso di alias delle chiavi `group by`. Le espressioni nella clausola `select` e nella clausola `having` devono fare riferimento alle chiavi `group by` attraverso questi alias. La sintassi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] seguente:  
  
```  
select k1, count(t.a), sum(t.a)  
from T as t  
group by t.b + t.c as k1  
```  
  
 ... equivale al seguente Transact-SQL:  
  
```  
select b + c, count(*), sum(a)   
from T  
group by b + c  
```  
  
## <a name="collection-based-aggregates"></a>Aggregazioni basate sulle raccolte  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] supporta due tipi di aggregazioni.  
  
 Le aggregazioni basate sulle raccolte operano sulle raccolte e producono il risultato aggregato. Possono essere presenti in un punto qualsiasi nella query e non richiedono una clausola `group by`. Ad esempio:  
  
```  
select t.a as a, count({1,2,3}) as b from T as t     
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] supporta inoltre le aggregazioni di tipo SQL. Ad esempio:  
  
```  
select a, sum(t.b) from T as t group by t.a as a  
```  
  
## <a name="order-by-clause-usage"></a>Utilizzo della clausola ORDER BY  
 Transact-SQL consente di specificare le clausole ORDER BY solo nell'oggetto SELECT più in alto. FROM . WHERE di livello superiore. In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] è possibile usare un'espressione ORDER BY annidata e posizionarla in un punto qualsiasi nella query, ma l'ordinamento in una query annidata non viene mantenuto.  
  
```  
-- The following query will order the results by the last name  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="identifiers"></a>Identificatori  
 In Transact-SQL il confronto degli identificatori si basa sulle regole di confronto del database corrente. In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], gli identificatori non applicano mai la distinzione tra maiuscole e minuscole, mentre applicano la distinzione tra caratteri accentati e non accentati. In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] viene infatti applicata la distinzione tra caratteri accentati e non accentati, ad esempio 'a' è diverso da 'à'. In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] le versioni delle lettere che hanno lo stesso aspetto ma che provengono da tabelle codici diverse vengono gestite come caratteri differenti. Per altre informazioni, vedere [set di caratteri di input](input-character-set-entity-sql.md).  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a>Funzionalità Transact-SQL non disponibili in Entity SQL  
 La seguente funzionalità di Transact-SQL non è disponibile [!INCLUDE[esql](../../../../../../includes/esql-md.md)]in.  
  
 DML  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]non fornisce attualmente supporto per le istruzioni DML (Insert, Update, Delete).  
  
 DDL  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] non fornisce supporto per DDL nella versione corrente.  
  
 programmazione imperativa  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]non fornisce supporto per la programmazione imperativa, a differenza di Transact-SQL. Usare invece un linguaggio di programmazione.  
  
 Funzioni di raggruppamento  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] non fornisce ancora supporto per le funzioni di raggruppamento (ad esempio CUBE, ROLLUP e GROUPING_SET).  
  
 Funzioni analitiche  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] non fornisce (ancora) supporto per le funzioni analitiche.  
  
 Funzioni e operatori predefiniti  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]supporta un subset di funzioni e operatori predefiniti di Transact-SQL. Questi operatori e funzioni saranno supportati probabilmente dai provider dell'archivio principali. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Usa le funzioni specifiche dell'archivio dichiarate in un manifesto del provider. Inoltre, il Entity Framework consente di dichiarare le funzioni di archiviazione predefinite e definite dall'utente, per [!INCLUDE[esql](../../../../../../includes/esql-md.md)] l'utilizzo di.  
  
 Hint  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] non fornisce meccanismi per gli hint per le query.  
  
 Invio in batch dei risultati di query  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] non supporta l'invio in batch dei risultati di query. Ad esempio, di seguito è riportato un codice Transact-SQL valido (inviato come batch):  
  
```  
select * from products;  
select * from catagories;  
```  
  
 Tuttavia, l'espressione equivalente [!INCLUDE[esql](../../../../../../includes/esql-md.md)] non è supportata:  
  
```  
Select value p from Products as p;  
Select value c from Categories as c;  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] supporta solo un'istruzione di query che restituisce un risultato per comando.  
  
## <a name="see-also"></a>Vedere anche

- [Panoramica di Entity SQL](entity-sql-overview.md)
- [Espressioni non supportate](unsupported-expressions-entity-sql.md)
