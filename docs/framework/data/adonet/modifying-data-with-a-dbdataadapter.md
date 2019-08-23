---
title: Modifica di dati con un oggetto DbDataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e35c7f9e-648b-4fcc-9361-d365c3e42c9a
ms.openlocfilehash: ec4f0527b73a506b3c98675f77f8f49a1eeb1e1f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934450"
---
# <a name="modifying-data-with-a-dbdataadapter"></a>Modifica di dati con un oggetto DbDataAdapter
Il metodo <xref:System.Data.Common.DbProviderFactory.CreateDataAdapter%2A> di un oggetto <xref:System.Data.Common.DbProviderFactory> fornisce un oggetto <xref:System.Data.Common.DbDataAdapter> fortemente tipizzato al provider sottostante specificato durante la creazione della factory. È quindi possibile usare un oggetto <xref:System.Data.Common.DbCommandBuilder> per creare i comandi che consentono di inserire, aggiornare ed eliminare dati da un <xref:System.Data.DataSet> a un'origine dati.  
  
## <a name="retrieving-data-with-a-dbdataadapter"></a>Recupero di dati con un DbDataAdapter  
 In questo esempio viene illustrato come creare un `DbDataAdapter` fortemente tipizzato basato su un nome di provider e una stringa di connessione. Il codice usa il metodo <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> di <xref:System.Data.Common.DbProviderFactory> per creare un oggetto <xref:System.Data.Common.DbConnection>. In seguito, viene usato il metodo <xref:System.Data.Common.DbProviderFactory.CreateCommand%2A> per creare un oggetto <xref:System.Data.Common.DbCommand> per la selezione dei dati impostandone le proprietà `CommandText` e `Connection`. Viene infine creato un oggetto <xref:System.Data.Common.DbDataAdapter> usando il metodo <xref:System.Data.Common.DbProviderFactory.CreateDataAdapter%2A> e ne viene impostata la proprietà `SelectCommand`. Il metodo `Fill` di `DbDataAdapter` carica i dati in un oggetto <xref:System.Data.DataTable>.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbDataAdapter#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapter/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbDataAdapter#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapter/VB/source.vb#1)]  
  
## <a name="modifying-data-with-a-dbdataadapter"></a>Modifica di dati con un oggetto DbDataAdapter  
 In questo esempio viene illustrato come modificare dati in un oggetto `DataTable` che usa un <xref:System.Data.Common.DbDataAdapter> usando un oggetto <xref:System.Data.Common.DbCommandBuilder> per generare i comandi necessari per aggiornare i dati nell'origine dati. Per recuperare CustomerID e CompanyName dalla tabella Customers, viene impostata la proprietà <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> di `DbDataAdapter`. Vengono usati il metodo <xref:System.Data.Common.DbCommandBuilder.GetInsertCommand%2A> per impostare la proprietà <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, il metodo <xref:System.Data.Common.DbCommandBuilder.GetUpdateCommand%2A> per impostare la proprietà <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> e il metodo <xref:System.Data.Common.DbCommandBuilder.GetDeleteCommand%2A> per impostare la proprietà <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A>. Il codice aggiunge una nuova riga alla tabella Customers e aggiorna l'origine dati. Viene quindi individuata la riga aggiunta eseguendo una ricerca su CustomerID, che corrisponde alla chiave primaria definita per la tabella Customers. Viene quindi modificato il valore di CompanyName e viene aggiornata l'origine dati. Viene infine eliminata la riga.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbDataAdapterModify#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapterModify/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbDataAdapterModify#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapterModify/VB/source.vb#1)]  
  
## <a name="handling-parameters"></a>Gestione di parametri  
 I provider di dati .NET Framework gestiscono in modo diverso la denominazione e la specifica di parametri e segnaposto di parametri. Questa sintassi è personalizzata in base a un'origine dati specifica, come descritto nella tabella seguente.  
  
|Provider di dati|Sintassi di denominazione di parametri|  
|-------------------|-----------------------------|  
|`SqlClient`|Usa parametri denominati nel formato `@`*nomeparametro*.|  
|`OracleClient`|Usa parametri denominati nel formato `:`*parmname* (o *parmname*).|  
|`OleDb`|Usa marcatori dei parametri di posizione indicati da un punto interrogativo (`?`).|  
|`Odbc`|Usa marcatori dei parametri di posizione indicati da un punto interrogativo (`?`).|  
  
 Il modello di factory non è utile per la creazione di oggetti `DbCommand` e `DbDataAdapter` con parametri. Sarà necessario creare rami del codice per creare parametri personalizzati in base al provider di dati.  
  
> [!IMPORTANT]
> Per motivi di sicurezza, è consigliabile evitare di usare parametri specifici del provider unitamente alla concatenazione di stringhe per costruire istruzioni SQL dirette. Se anziché i parametri si usa la concatenazione di stringhe, l'applicazione rimane vulnerabile ad attacchi SQL injection.  
  
## <a name="see-also"></a>Vedere anche

- [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)
- [Recupero di una classe DbProviderFactory](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)
- [DbConnection, DbCommand e DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)
- [Provider gestiti ADO.NET e Centro per sviluppatori di set di dati](https://go.microsoft.com/fwlink/?LinkId=217917)
