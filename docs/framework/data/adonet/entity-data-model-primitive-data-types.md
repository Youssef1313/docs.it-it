---
title: 'Entity Data Model: tipi di dati primitivi'
ms.date: 03/30/2017
ms.assetid: 7635168e-0566-4fdd-8391-7941b0d9f787
ms.openlocfilehash: dd688a06a47f4c44c27ddee2120b9de6980672fc
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795167"
---
# <a name="entity-data-model-primitive-data-types"></a>Entity Data Model: tipi di dati primitivi
Il Entity Data Model (EDM) supporta un set di tipi di dati primitivi astratti, ad esempio String, Boolean, Int32 e così via, utilizzati per definire le [Proprietà](property.md) in un modello concettuale. Questi tipi di dati primitivi sono proxy per i tipi di dati primitivi effettivi supportati nell'ambiente di archiviazione o host, ad esempio un database SQL Server o Common Language Runtime (CLR). EDM non definisce la semantica di operazioni o conversioni su tipi di dati primitivi. Questa semantica viene definita dall'ambiente di archiviazione o host. I tipi di dati primitivi in EDM sono in genere associati ai corrispondenti tipi di dati primitivi nell'ambiente di archiviazione o host. Per informazioni sul modo in cui il Entity Framework esegue il mapping dei tipi primitivi nel modello EDM ai tipi di dati SQL Server, vedere [SqlClient per l'entità Framework](./ef/sqlclient-for-ef-types.md).  
  
> [!NOTE]
> EDM non supporta raccolte di tipi di dati primitivi.  
  
 Per informazioni sui tipi di dati strutturati in EDM, vedere [tipo di entità](entity-type.md) e [tipo complesso](complex-type.md).  
  
## <a name="primitive-data-types-supported-in-the-entity-data-model"></a>Tipi di dati primitivi supportati in Entity Data Model  
 Nella tabella seguente vengono elencati i tipi di dati primitivi supportati da EDM. Nella tabella sono inoltre elencati i [facet](facet.md) che è possibile applicare a ogni tipo di dati primitivo.  
  
|Tipi di dati primitivi|DESCRIZIONE|Facet applicabili|  
|-------------------------|-----------------|-----------------------|  
|Binary|Contiene dati binari.|MaxLength, FixedLength, Nullable, Default|  
|Boolean|Contiene il valore `true` o `false`.|Nullable, Default|  
|Byte|Contiene un Unsigned Integer a 8 bit.|Precision, Nullable, Default|  
|DateTime|Rappresenta una data e un'ora.|Precision, Nullable, Default|  
|DateTimeOffset|Contiene una data e un'ora come offset in minuti rispetto all'ora GMT.|Precision, Nullable, Default|  
|Decimal|Contiene un valore numerico con scala e precisione fisse.|Precision, Nullable, Default|  
|Double|Contiene un numero a virgola mobile con precisione a 15 cifre.|Precision, Nullable, Default|  
|Float|Contiene un numero a virgola mobile con precisione a sette cifre.|Precision, Nullable, Default|  
|Guid|Contiene un identificatore univoco a 16 byte.|Precision, Nullable, Default|  
|Int16|Contiene un Signed Integer a 16 bit.|Precision, Nullable, Default|  
|Int32|Contiene un Signed Integer a 32 bit.|Precision, Nullable, Default|  
|Int64|Contiene un Signed Integer a 64 bit.|Precision, Nullable, Default|  
|SByte|Contiene un Signed Integer a 8 bit.|Precision, Nullable, Default|  
|String|Contiene dati di tipo carattere.|Unicode, FixedLength, MaxLength, Collation, Precision, Nullable, Default|  
|Time|Contiene un'ora del giorno.|Precision, Nullable, Default|  
  
## <a name="see-also"></a>Vedere anche

- [Concetti chiave di Entity Data Model](entity-data-model-key-concepts.md)
- [Entity Data Model](entity-data-model.md)
