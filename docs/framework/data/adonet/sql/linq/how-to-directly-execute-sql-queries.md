---
title: 'Procedura: Eseguire direttamente query SQL'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e491b9bf-741a-4296-9f51-76c25ddf6a82
ms.openlocfilehash: a4971bc05b22c38790c5fd1493e70cccf5eaae16
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793790"
---
# <a name="how-to-directly-execute-sql-queries"></a>Procedura: Eseguire direttamente query SQL
In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] le query create vengono convertite in query SQL con parametri, in formato testo, e inviate al server SQL per l'elaborazione.  
  
 Non è possibile eseguire in SQL la varietà di metodi eventualmente disponibili localmente per l'applicazione, pertanto [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tenta di convertire questi metodi locali nelle operazioni e funzioni equivalenti disponibili nell'ambiente SQL. La maggior parte dei metodi e degli operatori nei tipi incorporati .NET Framework dispone di traduzioni dirette nei comandi SQL. Alcuni possono essere prodotti dalle funzioni disponibili. Quelli che non possono essere prodotti generano eccezioni in fase di esecuzione. Per ulteriori informazioni, vedere [mapping dei tipi SQL-CLR](sql-clr-type-mapping.md).  
  
 Nei casi in cui una query [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fosse insufficiente per un'attività specializzata, è possibile usare il metodo <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> per eseguire una query SQL, quindi convertire direttamente il risultato della query in oggetti.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente si supponga che i dati per la classe `Customer` siano distribuiti in due tabelle (customer1 e customer2). La query consente di restituire una sequenza di oggetti `Customer`.  
  
 [!code-csharp[DLinqQuerying#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#4)]
 [!code-vb[DLinqQuerying#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#4)]  
  
 Finché i nomi di colonna nei risultati tabulari corrispondono alle proprietà di colonna della classe di entità [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , crea gli oggetti da qualsiasi query SQL.  
  
## <a name="example"></a>Esempio  
 Il metodo <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> accetta anche parametri. Per eseguire una query con parametri, usare codice analogo al seguente:  
  
 [!code-csharp[DLinqQuerying#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#5)]
 [!code-vb[DLinqQuerying#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#5)]  
  
 I parametri sono espressi nel testo della query usando la stessa notazione con parentesi graffe usata da `Console.WriteLine()` e `String.Format()`. Infatti, `String.Format()` viene effettivamente chiamato sulla stringa di query fornita, sostituendo i parametri con parentesi graffe con i nomi di parametro generati, @p0ad esempio @p1 ,... @p, (n).  
  
## <a name="see-also"></a>Vedere anche

- [Informazioni di base](background-information.md)
- [Esecuzione di query sul database](querying-the-database.md)
