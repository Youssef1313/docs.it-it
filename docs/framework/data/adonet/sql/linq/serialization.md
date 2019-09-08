---
title: Serialization2
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a15ae411-8dc2-4ca3-84d2-01c9d5f1972a
ms.openlocfilehash: bf303f9a79fbcab85d33fcb3ebb132d1d3e2041d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781107"
---
# <a name="serialization"></a>Serializzazione
In questo argomento [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vengono descritte le funzionalità di serializzazione. Nei paragrafi che seguono sono disponibili informazioni sull'aggiunta di serializzazione durante la generazione di codice in fase di progettazione e il comportamento di serializzazione delle classi [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] in fase di esecuzione.  
  
 È possibile aggiungere codice di serializzazione in fase di progettazione usando uno dei metodi seguenti:  
  
- Nella Object Relational Designer modificare la proprietà **modalità di serializzazione** in **unidirezionale**.  
  
- Nella riga di comando SQLMetal aggiungere l'opzione **/Serialization** . Per altre informazioni, vedere [SqlMetal.exe (strumento per la generazione del codice)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="overview"></a>Panoramica  
 Il codice generato da [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fornisce funzionalità di caricamento posticipato per impostazione predefinita. Il caricamento posticipato è molto pratico al livello intermedio per il caricamento trasparente dei dati su richiesta, tuttavia risulta problematico per la serializzazione, in quanto il serializzatore attiva comunque il caricamento posticipato a prescindere che questo sia o meno il comportamento designato. In effetti, quando un oggetto è serializzato, viene serializzata la relativa chiusura transitiva in tutti i riferimenti in uscita con caricamento posticipato.  
  
 La [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] funzionalità di serializzazione risolve questo problema, principalmente tramite due meccanismi:  
  
- Una modalità <xref:System.Data.Linq.DataContext> per la disattivazione del caricamento posticipato (<xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A>). Per altre informazioni, vedere <xref:System.Data.Linq.DataContext>.  
  
- Un'opzione di generazione di codice per generare attributi <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType> e <xref:System.Runtime.Serialization.DataMemberAttribute?displayProperty=nameWithType> sulle entità generate. Questo aspetto, incluso il comportamento delle classi a caricamento posticipato sottoposte a serializzazione, è l'oggetto principale di questo argomento.  
  
### <a name="definitions"></a>Definizioni  
  
- *Serializzatore DataContract*: Serializzatore predefinito utilizzato dal componente Windows Communication Framework (WCF) del .NET Framework 3,0 o versioni successive.  
  
- *Serializzazione unidirezionale*: Versione serializzata di una classe che contiene solo una proprietà di associazione unidirezionale (per evitare un ciclo). Per convenzione, la proprietà sul lato padre di una relazione di chiave primaria-esterna è contrassegnata per la serializzazione. L'altro lato in un'associazione bidirezionale non è serializzato.  
  
     La serializzazione unidirezionale è il solo tipo di serializzazione supportato da [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
## <a name="code-example"></a>Esempio di codice  
 Nel codice seguente vengono usate le classi `Customer` e `Order` tradizionali del database di esempio Northwind e viene descritto in che modo queste classi vengono decorate con gli attributi di serializzazione.  
  
 [!code-csharp[DLinqSerialization#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#1)]
 [!code-vb[DLinqSerialization#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#1)]  
  
 [!code-csharp[DLinqSerialization#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#2)]
 [!code-vb[DLinqSerialization#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#2)]  
  
 [!code-csharp[DLinqSerialization#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#3)]
 [!code-vb[DLinqSerialization#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#3)]  
  
 Per la classe `Order` nell'esempio seguente viene illustrata per brevità solo la proprietà di associazione inversa che corrisponde alla classe `Customer`. Questa classe non dispone di un attributo <xref:System.Runtime.Serialization.DataMemberAttribute> per evitare un ciclo.  
  
 [!code-csharp[DLinqSerialization#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#4)]
 [!code-vb[DLinqSerialization#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#4)]  
  
 [!code-csharp[DLinqSerialization#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#5)]
 [!code-vb[DLinqSerialization#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#5)]  
  
### <a name="how-to-serialize-the-entities"></a>Come serializzare le entità  
 È possibile serializzare le entità nei codici riportati nella sezione precedente come segue:  
  
 [!code-csharp[DLinqSerialization#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/Program.cs#6)]
 [!code-vb[DLinqSerialization#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/Module1.vb#6)]  
  
### <a name="self-recursive-relationships"></a>Relazioni autoricorsive  
 Le relazioni autoricorsive seguono lo stesso modello. La proprietà di associazione che corrisponde alla chiave esterna non dispone di un attributo <xref:System.Runtime.Serialization.DataMemberAttribute>, che invece è disponibile nella proprietà padre.  
  
 Si consideri la classe seguente che presenta due relazioni autoricorsive: Employee. Manager/Reports e Employee. Mentor/Mentos.  
  
 [!code-csharp[DLinqSerialization#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#7)]
 [!code-vb[DLinqSerialization#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#7)]  
  
## <a name="see-also"></a>Vedere anche

- [Informazioni di base](background-information.md)
- [SqlMetal.exe (strumento per la generazione del codice)](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [Procedura: Rendere serializzabili le entità](how-to-make-entities-serializable.md)
