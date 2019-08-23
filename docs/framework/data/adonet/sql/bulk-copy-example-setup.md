---
title: Creazione di esempi di copia di massa
ms.date: 03/30/2017
ms.assetid: d4dde6ac-b8b6-4593-965a-635c8fb2dadb
ms.openlocfilehash: 2a7c0ddef42ff56306a42288c6960987ce7f714a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918084"
---
# <a name="bulk-copy-example-setup"></a>Creazione di esempi di copia di massa
La classe <xref:System.Data.SqlClient.SqlBulkCopy> consente di scrivere dati solo su tabelle SQL Server. Negli esempi di codice illustrati in questo argomento viene utilizzato il database di esempio SQL Server, **AdventureWorks**. Per evitare di modificare gli esempi di codice delle tabelle esistenti, è necessario creare tabelle in cui scrivere i dati.  
  
 Le tabelle **BulkCopyDemoMatchingColumns** e **BulkCopyDemoDifferentColumns** sono entrambe basate sulla tabella **Production. Products** di **AdventureWorks** . Negli esempi di codice che usano queste tabelle, i dati vengono aggiunti dalla tabella **Production. Products** a una di queste tabelle di esempio. La tabella **BulkCopyDemoDifferentColumns** viene utilizzata quando nell'esempio viene illustrato come eseguire il mapping delle colonne dei dati di origine alla tabella di destinazione. **BulkCopyDemoMatchingColumns** viene usato per la maggior parte degli altri esempi.  
  
 Alcuni degli esempi di codice illustrano come usare una classe <xref:System.Data.SqlClient.SqlBulkCopy> per scrivere più tabelle. Per questi esempi, le tabelle **BulkCopyDemoOrderHeader** e **BulkCopyDemoOrderDetail** vengono utilizzate come tabelle di destinazione. Queste tabelle sono basate sulle tabelle **Sales. SalesOrderHeader** e **Sales. SalesOrderDetail** di **AdventureWorks**.  
  
> [!NOTE]
> Gli esempi di codice **SqlBulkCopy** sono forniti per illustrare la sintassi per l'uso solo di **SqlBulkCopy** . Se la tabella di origine e quella di destinazione risiedono nella stessa istanza di SQL Server, per copiare i dati è più semplice e rapido usare un'istruzione `INSERT … SELECT` Transact-SQL.  
  
## <a name="table-setup"></a>Impostazione delle tabelle  
 Per creare le tabelle necessarie affinché i codici di esempio vengano eseguiti correttamente, è necessario eseguire le seguenti istruzioni Transact-SQL su un database SQL Server.  
  
```  
USE AdventureWorks  
  
IF EXISTS (SELECT * FROM dbo.sysobjects   
 WHERE id = object_id(N'[dbo].[BulkCopyDemoMatchingColumns]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoMatchingColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoMatchingColumns]([ProductID] [int] IDENTITY(1,1) NOT NULL,  
    [Name] [nvarchar](50) NOT NULL,  
    [ProductNumber] [nvarchar](25) NOT NULL,  
 CONSTRAINT [PK_ProductID] PRIMARY KEY CLUSTERED  
(  
    [ProductID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects   
 WHERE id = object_id(N'[dbo].[BulkCopyDemoDifferentColumns]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoDifferentColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoDifferentColumns]([ProdID] [int] IDENTITY(1,1) NOT NULL,  
    [ProdNum] [nvarchar](25) NOT NULL,  
    [ProdName] [nvarchar](50) NOT NULL,  
 CONSTRAINT [PK_ProdID] PRIMARY KEY CLUSTERED  
(  
    [ProdID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects   
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderHeader]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderHeader]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderHeader]([SalesOrderID] [int] IDENTITY(1,1) NOT NULL,  
    [OrderDate] [datetime] NOT NULL,  
    [AccountNumber] [nvarchar](15) NULL,  
 CONSTRAINT [PK_SalesOrderID] PRIMARY KEY CLUSTERED  
(  
    [SalesOrderID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects   
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderDetail]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderDetail]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderDetail]([SalesOrderID] [int] NOT NULL,  
    [SalesOrderDetailID] [int] NOT NULL,  
    [OrderQty] [smallint] NOT NULL,  
    [ProductID] [int] NOT NULL,  
    [UnitPrice] [money] NOT NULL,  
 CONSTRAINT [PK_LineNumber] PRIMARY KEY CLUSTERED  
(  
    [SalesOrderID] ASC,  
    [SalesOrderDetailID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
```  
  
## <a name="see-also"></a>Vedere anche

- [Operazioni di copia di massa in SQL Server](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)
- [Provider gestiti ADO.NET e Centro per sviluppatori di set di dati](https://go.microsoft.com/fwlink/?LinkId=217917)
