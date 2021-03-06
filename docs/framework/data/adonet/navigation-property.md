---
title: Proprietà di navigazione-ADO.NET
ms.date: 03/30/2017
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
ms.openlocfilehash: afb2043abf70fa92ea7cdf8d1e8246d5cdfdba74
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738382"
---
# <a name="navigation-property"></a>Proprietà di navigazione

Una *proprietà di navigazione* è una proprietà facoltativa di un [tipo di entità](entity-type.md) che consente la navigazione da un'entità [finale](association-end.md) di un' [associazione](association-type.md) all'altra end. A differenza di altre [Proprietà](property.md), le proprietà di navigazione non contengono dati.

Una definizione di proprietà di navigazione include quanto segue:

- Un nome (obbligatorio).

- L'associazione all'interno della quale naviga (obbligatorio).

- Le entità finali dell'associazione all'interno della quale naviga (obbligatorio).

Si noti che le proprietà di navigazione sono facoltative in entrambi tipi di entità nelle entità finali di un'associazione. Se si definisce una proprietà di navigazione su un tipo di entità nell'entità finale di un'associazione, non è necessario definire una proprietà di navigazione sul tipo di entità nell'altra entità finale dell'associazione.

Il tipo di dati di una proprietà di navigazione è determinato dalla [molteplicità](association-end-multiplicity.md) dell' [estremità dell'associazione](association-end.md)remota. Si supponga ad esempio che esista una proprietà di navigazione, `OrdersNavProp`, in un tipo di entità `Customer` e che tale proprietà navighi in un'associazione uno-a-molti tra `Customer` e `Order`. Poiché l'entità finale dell'associazione remota per la proprietà di navigazione ha molteplicità di molti (\*), il relativo tipo di dati è una raccolta (di `Order`). Analogamente, se esiste una proprietà di navigazione `CustomerNavProp` nel tipo di entità `Order`, il relativo tipo di dati sarebbe `Customer`, perché la molteplicità dell'entità finale remota è uno (1).

## <a name="example"></a>Esempio

Nel diagramma seguente viene illustrato un modello concettuale con tre tipi di entità: `Book`, `Publisher` e `Author`. Le proprietà di navigazione, `Publisher` e `Authors`, vengono definite nel tipo di entità Book. La proprietà di navigazione `Books` viene definita sia nel tipo di entità Publisher che nel tipo di entità `Author`.

 ![Diagramma che illustra un modello concettuale con tre tipi di entità.](./media/navigation-property/conceptual-model-entity-types-associations.gif)  

Il [Entity Framework ADO.NET](./ef/index.md) utilizza un linguaggio specifico di dominio (DSL) denominato Conceptual Schema Definition Language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) per definire i modelli concettuali. Il linguaggio CSDL seguente definisce il tipo di entità `Book` illustrato nel diagramma precedente:

[!code-xml[EDM_Example_Model#EntityExample](~/samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]

Si noti che, per comunicare le informazioni necessarie per definire una proprietà di navigazione, vengono usati attributi XML: l'attributo `Name` contiene il nome della proprietà, `Relationship` contiene il nome dell'associazione all'interno della quale naviga e `FromRole` e `ToRole` contengono le entità finali dell'associazione.

## <a name="see-also"></a>Vedere anche

- [Concetti chiave di Entity Data Model](entity-data-model-key-concepts.md)
- [Entity Data Model](entity-data-model.md)
- [Relazioni, proprietà di navigazione e chiavi esterne](/ef/ef6/fundamentals/relationships)
