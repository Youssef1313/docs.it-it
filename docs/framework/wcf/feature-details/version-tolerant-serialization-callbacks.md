---
title: Callback di serializzazione a tolleranza di versione
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OnDeserializedAttribute [WCF]
- OnDeserializingAttribute [WCF]
- OnSerializingAttribute [WCF]
- serialization [WCF], setting default values
- OnSerializedAttribute [WCF]
ms.assetid: aa4a3a6f-05ec-4efd-bdbf-2181e13e6468
ms.openlocfilehash: 0736f94b1fe1a91b20ee76da673e0bc139aa802a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959560"
---
# <a name="version-tolerant-serialization-callbacks"></a>Callback di serializzazione a tolleranza di versione
Il modello di programmazione del contratto dati supporta appieno i metodi di callback della serializzazione a tolleranza di versione supportati dalle classi <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> e <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.  
  
## <a name="version-tolerant-attributes"></a>Attributi a tolleranza di versione  
 Sono disponibili quattro attributi di callback. Ogni attributo può essere applicato a un metodo che il motore di serializzazione/deserializzazione chiama in vari momenti. Nella tabella seguente viene illustrato quando utilizzare ogni attributo.  
  
|Attributo|Quando viene chiamato il metodo corrispondente|  
|---------------|---------------------------------------------|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|Chiamato prima di serializzare il tipo.|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|Chiamato dopo aver serializzato il tipo.|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|Chiamato prima di deserializzare il tipo.|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|Chiamato dopo aver deserializzato il tipo.|  
  
 I metodi devono accettare un parametro <xref:System.Runtime.Serialization.StreamingContext>.  
  
 Questi metodi sono destinati principalmente ad essere utilizzati per il controllo della versione o l'inizializzazione. Durante la deserializzazione, non viene chiamato alcun costruttore. È quindi possibile che i membri dati non vengano inizializzati correttamente (sugli appropriati valori predefiniti) se mancano i dati per questi membri nel flusso in ingresso, ad esempio, se i dati provengono da una versione precedente di un tipo in cui mancano alcuni membri dati. Per correggere questo problema, utilizzare il metodo di callback contrassegnato con <xref:System.Runtime.Serialization.OnDeserializingAttribute>, come illustrato nell'esempio seguente.  
  
 È possibile contrassegnare solo uno metodo per tipo con ognuno dei precedenti attributi di callback.  
  
### <a name="example"></a>Esempio  
 [!code-csharp[C_DataContract#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#9)]
 [!code-vb[C_DataContract#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#9)]  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.Runtime.Serialization.OnSerializingAttribute>
- <xref:System.Runtime.Serialization.OnSerializedAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>
- <xref:System.Runtime.Serialization.StreamingContext>
- [Serializzazione a tolleranza di versione](../../../standard/serialization/version-tolerant-serialization.md)
