---
title: 'Procedura: Eseguire una query che restituisce risultati StructuralType'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2314f2a2-b1c3-40c4-95bb-cdf9b21a7b53
ms.openlocfilehash: 7b649abb21b8f6ebbbd8aadc279b2902b3e21e25
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854542"
---
# <a name="how-to-execute-a-query-that-returns-structuraltype-results"></a>Procedura: Eseguire una query che restituisce risultati StructuralType
In questo argomento viene illustrato come eseguire un comando su un modello concettuale usando un oggetto <xref:System.Data.EntityClient.EntityCommand> e viene mostrato come recuperare i risultati di <xref:System.Data.Metadata.Edm.StructuralType> usando un oggetto <xref:System.Data.EntityClient.EntityDataReader>. Le classi <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.RowType> e <xref:System.Data.Metadata.Edm.ComplexType> derivano dalla classe <xref:System.Data.Metadata.Edm.StructuralType>.  
  
### <a name="to-run-the-code-in-this-example"></a>Per eseguire il codice in questo esempio  
  
1. Aggiungere il [modello Sales di AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) al progetto e configurare il progetto per l'utilizzo del Entity Framework. Per altre informazioni, vedere [Procedura: Utilizzare la procedura guidata](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))Entity Data Model.  
  
2. Nella tabella codici per l'applicazione aggiungere le istruzioni `using` seguenti (`Imports` in Visual Basic):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a>Esempio  
 In questo esempio viene eseguita una query che restituisce risultati dell'oggetto <xref:System.Data.Metadata.Edm.EntityType>. Se si passa la query riportata di seguito come argomento alla funzione `ExecuteStructuralTypeQuery`, quest'ultima visualizza i dettagli relativi a `Products`:  
  
 [!code-csharp[DP EntityServices Concepts 2#SelectProduct](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#selectproduct)]  
  
 Se si passa una query con parametri, come quella riportata di seguito, aggiungere gli oggetti <xref:System.Data.EntityClient.EntityParameter> alla proprietà <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> nell'oggetto <xref:System.Data.EntityClient.EntityCommand>.  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER_OR_EQUALS](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater_or_equals)]  
  
 [!code-csharp[DP EntityServices Concepts#eSQLStructuralTypes](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#esqlstructuraltypes)]
 [!code-vb[DP EntityServices Concepts#eSQLStructuralTypes](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#esqlstructuraltypes)]  
  
## <a name="see-also"></a>Vedere anche

- [Riferimento a Entity SQL](./language-reference/entity-sql-reference.md)
- [Provider EntityClient per Entity Framework](entityclient-provider-for-the-entity-framework.md)
