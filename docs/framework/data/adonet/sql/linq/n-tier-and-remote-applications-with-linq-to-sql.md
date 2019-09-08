---
title: Applicazioni a più livelli e remote con LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 854a1cdd-53cb-45f5-83ca-63962a9b3598
ms.openlocfilehash: 94ca057da10c3570e85e17b5caec2d86154d8a3f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781412"
---
# <a name="n-tier-and-remote-applications-with-linq-to-sql"></a>Applicazioni a più livelli e remote con LINQ to SQL
È possibile creare applicazioni a più livelli che usano [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. In genere, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] il contesto dati, le classi di entità e la logica di costruzione delle query si trovano nel livello intermedio come livello di accesso ai dati (dal). La regola business e i dati non persistenti possono essere implementati completamente in classi e metodi parziali di entità e nel contesto dati oppure possono essere implementati in classi separate.

 Il livello client o di presentazione chiama i metodi nell'interfaccia remota del livello intermedio e il DAL di tale livello eseguirà le query o le stored procedure di cui è stato eseguito il mapping ai metodi <xref:System.Data.Linq.DataContext>. Il livello intermedio in genere restituisce i dati ai client come rappresentazioni XML di entità o oggetti proxy.

 Nel livello intermedio, le entità vengono create dal contesto dati che tiene traccia dello stato e gestisce il caricamento posticipato e l'invio delle modifiche al database. Queste entità sono "collegate" all'oggetto `DataContext`. Tuttavia, le entità vengono disconnesse dopo l'invio a un altro livello mediante la serializzazione, ovvero `DataContext` non tiene più traccia del relativo stato. Le entità inviate dal client per gli aggiornamenti devono essere ricollegate al contesto dati prima che [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sia in grado di inviare le modifiche al database. Il client ha lo scopo di fornire al livello intermedio i valori originali e/o i timestamp se richiesti per i controlli di concorrenza ottimistica.

 Nelle applicazioni ASP.NET, <xref:System.Web.UI.WebControls.LinqDataSource> gestisce gran parte di questa complessità. Per ulteriori informazioni, vedere [Cenni preliminari sul controllo server Web LinqDataSource](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100)).

## <a name="additional-resources"></a>Risorse aggiuntive
 Per altre informazioni sull'implementazione delle applicazioni a più livelli che usano [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], vedere gli argomenti seguenti:

- [Più livelli di LINQ to SQL con ASP.NET](linq-to-sql-n-tier-with-aspnet.md)

- [Più livelli di LINQ to SQL con Servizi Web](linq-to-sql-n-tier-with-web-services.md) 

- [Implementazione della logica di business a più livelli](implementing-business-logic-linq-to-sql.md)

- [Recupero di dati e operazioni CUD in applicazioni a più livelli (LINQ to SQL)](data-retrieval-and-cud-operations-in-n-tier-applications.md)

 Per altre informazioni sulle applicazioni a più livelli che usano i set di dati ADO.NET, vedere [lavorare con i set di dati nelle applicazioni a più livelli](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications).

## <a name="see-also"></a>Vedere anche

- [Informazioni di base](background-information.md)
