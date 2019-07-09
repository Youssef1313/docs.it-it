---
title: Risoluzione dei problemi
ms.date: 03/30/2017
ms.assetid: 8cd4401c-b12c-4116-a421-f3dcffa65670
ms.openlocfilehash: c09871abcdfb9243b5170386ffe79012c9c3f71d
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661857"
---
# <a name="troubleshooting"></a>Risoluzione dei problemi
Nelle informazioni seguenti vengono illustrati alcuni problemi che è possibile incontrare nelle applicazioni [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] e vengono forniti suggerimenti per evitare o altrimenti ridurre l'effetto di questi problemi.  
  
 Altri problemi verranno risolti nelle [Frequently Asked Questions](../../../../../../docs/framework/data/adonet/sql/linq/frequently-asked-questions.md).  
  
## <a name="unsupported-standard-query-operators"></a>Operatori di query standard non supportati  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] non supporta tutti i metodi degli operatori di query standard, ad esempio <xref:System.Linq.Enumerable.ElementAt%2A>. Di conseguenza, durante la compilazione dei progetti possono comunque verificarsi errori di runtime. Per altre informazioni, vedere [conversione dell'operatore Query Standard](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md).  
  
## <a name="memory-issues"></a>Problemi di memoria  
 Se una query implica una raccolta in memoria e [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601>, potrebbe essere eseguita la query in memoria, in base all'ordine in cui vengono specificate le due raccolte. Se la query deve essere eseguita in memoria, sarà necessario recuperare i dati dalla tabella di database.  
  
 Questo approccio non è quindi consigliato poiché può comportare un utilizzo significativo della memoria e del processore. Tentare di evitare tali query multidominio.  
  
## <a name="file-names-and-sqlmetal"></a>Nomi file e SQLMetal  
 Per specificare un nome file di input, aggiungere il nome nella riga di comando come file di input. Non è possibile includere il nome file nella stringa di connessione mediante l'opzione **/conn** . Per altre informazioni, vedere [SqlMetal.exe (strumento per la generazione del codice)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="class-library-projects"></a>Progetti di librerie di classi  
 La [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] crea una stringa di connessione nel file `app.config` del progetto. Nei progetti di librerie di classi il file `app.config` non viene usato. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] usa la stringa di connessione fornita nei file della fase di progettazione. La modifica del valore in `app.config` non comporta la modifica del database al quale si connette l'applicazione.  
  
## <a name="cascade-delete"></a>Eliminazione a catena  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] non supporta o non riconosce operazioni di eliminazione a catena. Se si desidera eliminare una riga in una tabella contenente vincoli, è necessario effettuare una delle operazioni seguenti:  
  
- Impostare la regola `ON DELETE CASCADE` nel vincolo di chiave esterna del database.  
  
- Usare il codice personalizzato per eliminare prima gli oggetti figlio che impediscono l'eliminazione dell'oggetto padre.  
  
 In caso contrario, viene generata un'eccezione <xref:System.Data.SqlClient.SqlException>.  
  
 Per altre informazioni, vedere [Procedura: Eliminare le righe dal Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).  
  
## <a name="expression-not-queryable"></a>Espressione che non può essere sottoposta a query  
 Se viene visualizzato il "espressione [espressione] non è disponibile per query; Probabilmente manca un riferimento all'assembly" errore, verificare quanto segue:  
  
- L'applicazione è destinato a .NET Compact Framework 3.5.  
  
- È presente un riferimento a `System.Core.dll` e `System.Data.Linq.dll`.  
  
- È necessario un `Imports` (Visual Basic) o `using` direttiva (c#) per <xref:System.Linq> e <xref:System.Data.Linq>.  
  
## <a name="duplicatekeyexception"></a>DuplicateKeyException  
 Nel corso del debug un [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] progetto, è possibile attraversare le relazioni di un'entità. In questo modo offre questi elementi nella cache e [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] viene a conoscenza della loro presenza. Se si tenta quindi di eseguire <xref:System.Data.Linq.Table%601.Attach%2A> o <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> oppure un metodo simile che crea più righe con la stessa chiave, viene generata un'eccezione <xref:System.Data.Linq.DuplicateKeyException>.  
  
## <a name="string-concatenation-exceptions"></a>Eccezioni di concatenazione di stringhe  
 La concatenazione su operandi di cui viene eseguito il mapping a `[n]text` e altri `[n][var]char` non è supportata. Viene generata un'eccezione per la concatenazione di stringhe di cui viene eseguito il mapping a due set di tipi diversi. Per altre informazioni, vedere [metodi System. String](../../../../../../docs/framework/data/adonet/sql/linq/system-string-methods.md).  
  
## <a name="skip-and-take-exceptions-in-sql-server-2000"></a>Come ignorare e accettare le eccezioni in SQL Server 2000  
 È necessario usare i membri di identità (<xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>) quando si usa <xref:System.Linq.Queryable.Take%2A> o <xref:System.Linq.Queryable.Skip%2A> su un database SQL Server 2000. La query deve essere eseguita su una singola tabella, ovvero non un join, o deve essere un'operazione <xref:System.Linq.Queryable.Distinct%2A>, <xref:System.Linq.Queryable.Except%2A>, <xref:System.Linq.Queryable.Intersect%2A> o <xref:System.Linq.Queryable.Union%2A> e non deve includere un'operazione <xref:System.Linq.Queryable.Concat%2A>. Per altre informazioni, vedere la sezione "Supporto di SQL Server 2000" nella [conversione dell'operatore Query Standard](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md).  
  
 Questo requisito non si applica a SQL Server 2005.  
  
## <a name="groupby-invalidoperationexception"></a>GroupBy InvalidOperationException  
 Questa eccezione viene generata quando un valore di colonna è null in una query <xref:System.Linq.Enumerable.GroupBy%2A> che esegue il raggruppamento in base a un'espressione `boolean`, ad esempio `group x by (Phone==@phone)`. Poiché l'espressione è `boolean`, si deduce che la chiave sia `boolean`, non `nullable` `boolean`. Quando il confronto convertito produce un valore null, viene effettuato un tentativo di assegnare un `nullable` `boolean` a un `boolean` e viene generata l'eccezione.  
  
 Per evitare questa situazione, presupponendo che si desideri trattare i valori null come false, usare un approccio analogo al seguente:  
  
 `GroupBy="(Phone != null) && (Phone=@Phone)"`  
  
## <a name="oncreated-partial-method"></a>Metodo parziale OnCreated()  
 Il metodo `OnCreated()` generato viene chiamato ogni volta che viene chiamato il costruttore dell'oggetto, incluso lo scenario in cui [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] chiama il costruttore per creare una copia dei valori originali. Tenere conto di questo comportamento se si implementa il metodo `OnCreated()` nella classe parziale personalizzata.  
  
## <a name="see-also"></a>Vedere anche

- [Supporto per il debug](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)
- [Domande frequenti](../../../../../../docs/framework/data/adonet/sql/linq/frequently-asked-questions.md)
