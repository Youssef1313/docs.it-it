---
title: Utilizzo di Data Definition Language
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec50083d-44f4-4093-9b23-5eacd601f96e
ms.openlocfilehash: 788388b93a00cf5393174d35b8a160b4991da3bc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743722"
---
# <a name="working-with-data-definition-language"></a>Utilizzo di Data Definition Language
A partire da .NET Framework versione 4, il [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] supporta il linguaggio di definizione dei dati (DDL). Ciò consente di creare o eliminare un'istanza di database in base alla stringa di connessione e ai metadati del modello di archiviazione (SSDL).  
  
 Di seguito sono indicati i metodi di <xref:System.Data.Objects.ObjectContext> che usano la stringa di connessione e il contenuto SSDL per portare a termine le operazioni seguenti: creare o eliminare il database, verificare l'esistenza del database e visualizzare lo script DDL generato.  
  
- <xref:System.Data.Objects.ObjectContext.CreateDatabase%2A>  
  
- <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A>  
  
- <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A>  
  
- <xref:System.Data.Objects.ObjectContext.CreateDatabaseScript%2A>  
  
> [!NOTE]
>  Per l'esecuzione dei comandi DDL si presuppone che si disponga di autorizzazioni sufficienti.  
  
 I metodi elencati precedentemente delegano la maggior parte del lavoro al provider di dati ADO.NET sottostante. È responsabilità del provider assicurarsi che la convenzione di denominazione usata per generare oggetti di database sia coerente con le convenzioni usate per l'esecuzione di query e aggiornamenti.  
  
 Nell'esempio seguente viene mostrato come generare il database in base al modello esistente. Viene inoltre aggiunto un nuovo oggetto entità al contesto dell'oggetto che viene quindi salvato nel database.  
  
## <a name="procedures"></a>Procedure  
  
### <a name="to-define-a-database-based-on-the-existing-model"></a>Per definire un database in base al modello esistente  
  
1. Creare un'applicazione console.  
  
2. Aggiungere un modello esistente all'applicazione.  
  
    1. Aggiungere un modello vuoto denominato `SchoolModel`. Per creare un modello vuoto, vedere il [come: Creare un File con estensione edmx nuovo](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100)) argomento.  
  
     Il file SchoolModel.edmx verrà aggiunto al progetto.  
  
    1. Copiare la risorsa di archiviazione, concettuale e il mapping del contenuto per il modello School dal [modello School](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) argomento.  
  
    2. Aprire il file SchoolModel.edmx e incollare il contenuto all'interno dei tag `edmx:Runtime`.  
  
3. Aggiungere il codice seguente alla funzione principale. Il codice inizializza la stringa di connessione nel server database, visualizza lo script DDL, crea il database, aggiunge una nuova entità al contesto e salva le modifiche nel database.  
  
     [!code-csharp[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/csharp/VS_Snippets_Data/DP ObjectServices Concepts/CS/Source.cs#ddl)]
     [!code-vb[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP ObjectServices Concepts/VB/Source.vb#ddl)]
