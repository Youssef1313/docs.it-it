---
title: SqlTypes e DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
ms.openlocfilehash: dea5a2017479443cb747d31e253c1c83585ddd09
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791495"
---
# <a name="sqltypes-and-the-dataset"></a>SqlTypes e DataSet
In ADO.NET 2.0 è stato introdotto il supporto migliorato per i tipi per `DataSet` tramite lo spazio dei nomi  <xref:System.Data.SqlTypes>. I tipi <xref:System.Data.SqlTypes> sono progettati per fornire tipi di dati con la stessa semantica e la stessa precisione dei tipi di dati di un database di SQL Server. Ogni tipo di dati in <xref:System.Data.SqlTypes> dispone di un tipo di dati equivalente in SQL Server, con la stessa rappresentazione di dati sottostante.  
  
 L'utilizzo di <xref:System.Data.SqlTypes> direttamente in un oggetto <xref:System.Data.DataSet> offre numerosi vantaggi quando si lavora con tipi di dati SQL Server. <xref:System.Data.SqlTypes> supporta la stessa semantica dei tipi di dati nativi SQL Server. La specifica di uno degli oggetti <xref:System.Data.SqlTypes> nella definizione di un oggetto <xref:System.Data.DataColumn> elimina la perdita di precisione che può verificarsi in caso di conversione di tipi di dati numerici o decimali in uno dei tipi di dati CLR (Common Language Runtime).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene creato un oggetto <xref:System.Data.DataTable>, definendo in modo esplicito i tipi di dati <xref:System.Data.DataColumn> usando <xref:System.Data.SqlTypes> invece dei tipi CLR. Il codice consente di compilare <xref:System.Data.DataTable> con i dati della tabella Sales.SalesOrderDetail nel database AdventureWorks in SQL Server. L'output visualizzato nella finestra della console mostra i tipi di dati di ogni colonna e i valori recuperati da SQL Server.  
  
 [!code-csharp[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/VB/source.vb#1)]  
  
## <a name="see-also"></a>Vedere anche

- [Mapping dei tipi di dati SQL Server](../sql-server-data-type-mappings.md)
- [Configurazione di parametri e tipi di dati dei parametri](../configuring-parameters-and-parameter-data-types.md)
- [Panoramica di ADO.NET](../ado-net-overview.md)
