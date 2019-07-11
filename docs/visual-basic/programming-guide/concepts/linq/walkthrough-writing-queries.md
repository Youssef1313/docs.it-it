---
title: Scrittura di query in Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ [Visual Basic], walkthroughs
- LINQ [Visual Basic], writing queries
- writing LINQ queries [Visual Basic]
ms.assetid: f0045808-b9fe-4d31-88d1-473d9957211e
ms.openlocfilehash: 55ded2f2fbd5c2c6e33627ce7fafe6bb4248d5ef
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783252"
---
# <a name="walkthrough-writing-queries-in-visual-basic"></a>Procedura dettagliata: Scrittura di query in Visual Basic
Questa procedura dettagliata illustra come è possibile usare le funzionalità del linguaggio Visual Basic per scrivere [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] le espressioni di query. La procedura dettagliata illustra come creare query in un elenco di oggetti per studenti, come eseguire la query e come modificarli. Le query integrare diverse funzionalità tra cui i tipi anonimi, inferenza del tipo locale e gli inizializzatori di oggetto.  
  
 Dopo aver completato questa procedura dettagliata, sarà possibile passare agli esempi e documentazione per lo specifico [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provider si è interessati. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provider sono inclusi [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], LINQ to DataSet, e [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
## <a name="create-a-project"></a>Creare un progetto  
  
### <a name="to-create-a-console-application-project"></a>Per creare un progetto di applicazione console  
  
1. Avviare Visual Studio.  
  
2. Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.  
  
3. Nel **modelli installati** fare clic su **Visual Basic**.  
  
4. Nell'elenco dei tipi di progetto, fare clic su **applicazione Console**. Nel **Name** casella, digitare un nome per il progetto e quindi fare clic su **OK**.  
  
     Viene creato un progetto. Per impostazione predefinita, contiene un riferimento alla DLL. Inoltre, il **spazi dei nomi importati** elenco il [riferimenti (pagina), creazione progetti (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic) include il <xref:System.Linq?displayProperty=nameWithType> dello spazio dei nomi.  
  
5. Nel [pagina compilazione, creazione progetti (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), assicurarsi che **Option infer** è impostata su **su**.  
  
## <a name="add-an-in-memory-data-source"></a>Aggiungere un'origine dati In memoria  
 L'origine dati per le query in questa procedura dettagliata è un elenco di `Student` oggetti. Ogni `Student` oggetto contiene un nome, cognome, un anno di classe e un grado accademico il corpo degli studenti.  
  
### <a name="to-add-the-data-source"></a>Per aggiungere l'origine dati  
  
- Definire un `Student` classe e creare un elenco di istanze della classe.  
  
    > [!IMPORTANT]
    >  Il codice necessario per definire le `Student` classe e creare l'elenco utilizzato nella procedura dettagliata gli esempi viene fornito [come: Creare un elenco di elementi](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md). È possibile copiarlo da tale posizione e incollarlo nel progetto. Il nuovo codice sostituisce il codice che si verificava quando è stato creato il progetto.  
  
### <a name="to-add-a-new-student-to-the-students-list"></a>Per aggiungere un nuovo studente all'elenco degli studenti  
  
- Seguire il modello nel `getStudents` metodo per aggiungere un'altra istanza del `Student` classe all'elenco. Aggiungere gli studenti vengono introdotti gli inizializzatori di oggetto. Per altre informazioni, vedere [gli inizializzatori di oggetto: Tipi denominati e anonimi](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).  
  
## <a name="create-a-query"></a>Creare una query  
 Quando viene eseguita, la query è stato aggiunto in questa sezione produce un elenco degli studenti con una classificazione academic li inserisce i primi dieci. Poiché la query seleziona l'intero `Student` ogni volta, il tipo del risultato della query di oggetto è `IEnumerable(Of Student)`. Tuttavia, il tipo della query in genere non è specificato nelle definizioni di query. Al contrario, il compilatore Usa l'inferenza del tipo locale per determinare il tipo. Per altre informazioni, vedere [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md). Variabile di intervallo della query, `currentStudent`, funge da riferimento a ogni `Student` istanza dell'origine `students`, che fornisce accesso alle proprietà di ogni oggetto `students`.  
  
### <a name="to-create-a-simple-query"></a>Per creare una query semplice  
  
1. Individuare il punto nel `Main` metodo del progetto che è contrassegnato come indicato di seguito:  
  
     [!code-vb[VbLINQWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#1)]  
  
     Copiare il codice seguente e incollarlo in.  
  
     [!code-vb[VbLINQWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#2)]  
  
2. Posiziona il puntatore del mouse sul `studentQuery` nel codice per verificare che il tipo assegnato dal compilatore è `IEnumerable(Of Student)`.  
  
## <a name="run-the-query"></a>Eseguire la Query  
 La variabile `studentQuery` contiene la definizione della query, non i risultati dell'esecuzione della query. È un meccanismo tipico per l'esecuzione di una query un `For Each` ciclo. Ogni elemento della sequenza restituita si accede tramite la variabile di iterazione del ciclo. Per altre informazioni sull'esecuzione di query, vedere [Writing Your prima Query LINQ](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
### <a name="to-run-the-query"></a>Per eseguire la query  
  
1. Aggiungere il codice seguente `For Each` ciclo sotto la query nel progetto.  
  
     [!code-vb[VbLINQWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#3)]  
  
2. Posizionare il puntatore del mouse sulla variabile di controllo del ciclo `studentRecord` per visualizzarne il tipo di dati. Il tipo della `studentRecord` viene dedotto come `Student`, in quanto `studentQuery` restituisce una raccolta di `Student` istanze.  
  
3. Compilare ed eseguire l'applicazione premendo CTRL+F5. Si noti che i risultati nella finestra della console.  
  
## <a name="modify-the-query"></a>Modificare la query  
 È più semplice analizzare i risultati della query, se si trovano in un ordine specifico. È possibile ordinare la sequenza restituita in base a qualsiasi campo disponibile.  
  
### <a name="to-order-the-results"></a>Per ordinare i risultati  
  
1. Aggiungere il codice seguente `Order By` clausola tra il `Where` istruzione e `Select` istruzione della query. Il `Order By` clausola ordina i risultati in ordine alfabetico dalla alla Z, in base all'ultimo nome di ogni studente.  
  
    ```  
    Order By currentStudent.Last Ascending   
    ```  
  
2. Per ordinare in base a cognome e quindi nome, aggiungere entrambi i campi alla query:  
  
    ```  
    Order By currentStudent.Last Ascending, currentStudent.First Ascending   
    ```  
  
     È inoltre possibile specificare `Descending` all'ordine da Z ad A.  
  
3. Compilare ed eseguire l'applicazione premendo CTRL+F5. Si noti che i risultati nella finestra della console.  
  
### <a name="to-introduce-a-local-identifier"></a>Per introdurre un identificatore locale  
  
1. Aggiungere il codice in questa sezione per introdurre un identificatore locale nell'espressione di query. L'identificatore locale conterrà un risultato intermedio. Nell'esempio seguente, `name` è un identificatore che contiene una concatenazione dello studente nome e cognome. Un identificatore locale può essere utilizzato per comodità, o può migliorare le prestazioni archiviando i risultati di un'espressione che in caso contrario, viene calcolato più volte.  
  
     [!code-vb[VbLINQWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#4)]  
  
2. Compilare ed eseguire l'applicazione premendo CTRL+F5. Si noti che i risultati nella finestra della console.  
  
### <a name="to-project-one-field-in-the-select-clause"></a>Per proiettare un campo nella clausola Select  
  
1. Aggiungere la query e `For Each` ciclo da questa sezione per creare una query che produce una sequenza i cui elementi differiscono dagli elementi nell'origine. Nell'esempio seguente, l'origine è una raccolta di `Student` oggetti, ma solo un membro di ogni oggetto viene restituito: il nome di studenti il cui cognome è Garcia. In quanto `currentStudent.First` è una stringa, il tipo di dati della sequenza restituita da `studentQuery3` è `IEnumerable(Of String)`, una sequenza di stringhe. Come negli esempi precedenti, l'assegnazione di un dato tipo per `studentQuery3` spetta al compilatore di determinare con l'inferenza del tipo locale.  
  
     [!code-vb[VbLINQWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#5)]  
  
2. Posiziona il puntatore del mouse sul `studentQuery3` nel codice per verificare che il tipo assegnato sia `IEnumerable(Of String)`.  
  
3. Compilare ed eseguire l'applicazione premendo CTRL+F5. Si noti che i risultati nella finestra della console.  
  
### <a name="to-create-an-anonymous-type-in-the-select-clause"></a>Per creare un tipo anonimo nella clausola Select  
  
1. Aggiungere il codice da questa sezione per visualizzare i tipi anonimi come vengono usati nelle query. Usarli nelle query, quando si desidera restituire diversi campi dall'origine dati anziché record completi (`currentStudent` record negli esempi precedenti) o singoli campi (`First` nella sezione precedente). Invece di definire un nuovo tipo denominato che contiene i campi da includere nel risultato, consente di specificare i campi nel `Select` clausola e il compilatore crea un tipo anonimo con questi campi come le relative proprietà. Per altre informazioni, vedere [Tipi anonimi](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
     L'esempio seguente crea una query che restituisce il nome e il rango di dirigenti cui rango accademico è compreso tra 1 e 10, in ordine di rango accademico. In questo esempio, il tipo della `studentQuery4` deve essere dedotto perché il `Select` la clausola restituisce un'istanza di un tipo anonimo, e un tipo anonimo non hanno nome utilizzabile.  
  
     [!code-vb[VbLINQWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#6)]  
  
2. Compilare ed eseguire l'applicazione premendo CTRL+F5. Si noti che i risultati nella finestra della console.  
  
## <a name="additional-examples"></a>Esempi aggiuntivi  
 Dopo avere appreso le nozioni di base, ecco un elenco di altri esempi per illustrare la flessibilità e potenza di [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] le query. Ogni esempio è preceduto da una breve descrizione del risultato. Posizionare il puntatore del mouse sulla variabile di risultato di query per ogni query visualizzare il tipo dedotto. Usare un `For Each` ciclo per produrre i risultati.  
  
 [!code-vb[VbLINQWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#7)]  
  
## <a name="additional-information"></a>Informazioni aggiuntive  
 Dopo aver acquisito familiarità con i concetti di base dell'uso delle query, si è pronti per leggere la documentazione e gli esempi per il tipo specifico di [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provider che si è interessati:  
  
 [LINQ to Objects](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
  
 [LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)  
  
 [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
## <a name="see-also"></a>Vedere anche

- [LINQ (Language-Integrated Query) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)
- [Introduzione a LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Inferenza del tipo di variabile locale](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Inizializzatori di oggetto: Tipi denominati e anonimi](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Tipi anonimi](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Introduzione a LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Query](../../../../visual-basic/language-reference/queries/index.md)
