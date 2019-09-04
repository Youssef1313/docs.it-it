---
title: 'Procedura: Eseguire una query polimorfica'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2f05da1e-845b-4f14-83e4-c6353a850553
ms.openlocfilehash: 49e0a6b44af0729959fabf6278cc6d8ecf37a16b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251503"
---
# <a name="how-to-execute-a-polymorphic-query"></a>Procedura: Eseguire una query polimorfica

In questo argomento viene illustrato come eseguire una [!INCLUDE[esql](../../../../../includes/esql-md.md)] query polimorfica utilizzando l'operatore [OfType](./language-reference/oftype-entity-sql.md) .

### <a name="to-run-the-code-in-this-example"></a>Per eseguire il codice in questo esempio

1. Aggiungere il [modello School](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) al progetto e configurare il progetto per l'uso del Entity Framework. Per altre informazioni, vedere [Procedura: Utilizzare la procedura guidata](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))Entity Data Model.

2. Nella tabella codici per l'applicazione aggiungere le istruzioni `using` seguenti (`Imports` in Visual Basic):

    [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
    [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]

3. Modificare il modello concettuale in modo che abbia un'ereditarietà tabella per gerarchia attenendosi alla procedura [descritta in procedura dettagliata: Mapping di ereditarietà-tabella per gerarchia](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716683(v=vs.100)).

## <a name="example"></a>Esempio

Nell'esempio seguente viene usato un operatore OFTYPE per ottenere e visualizzare una raccolta di soli oggetti `OnsiteCourses` da una raccolta di oggetti `Courses`.

[!code-csharp[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#polymorphicquery)]
[!code-vb[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#polymorphicquery)]

## <a name="see-also"></a>Vedere anche

- [Provider EntityClient per Entity Framework](entityclient-provider-for-the-entity-framework.md)
- [Linguaggio Entity SQL](./language-reference/entity-sql-language.md)
