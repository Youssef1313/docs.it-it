---
title: TransactionFlowBindingElement
ms.date: 03/30/2017
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
ms.openlocfilehash: a58d5620abbb636480ceea3020552246ae284842
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "61641684"
---
# <a name="transactionflowbindingelement"></a>TransactionFlowBindingElement
TransactionFlowBindingElement  
  
## <a name="syntax"></a>Sintassi  
  
```csharp
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a>Metodi  
 La classe TransactionFlowBindingElement non definisce metodi.  
  
## <a name="properties"></a>Proprietà  
 La classe TransactionFlowBindingElement dispone delle proprietà seguenti:  
  
### <a name="issuedtokens"></a>IssuedTokens  
 Tipo di dati: stringa  
  
 Tipo di accesso: Sola lettura  
  
 Specifica il requisito per un'intestazione dei token di sicurezza emessi (IssuedTokens da WS-Trust).  
  
### <a name="transactionprotocol"></a>TransactionProtocol  
 Tipo di dati: stringa  
  
 Tipo di accesso: Sola lettura  
  
 Protocollo delle transazioni utilizzato dal servizio per il flusso delle transazioni.  
  
### <a name="transactions"></a>Transazioni  
 Tipo di dati: booleano  
  
 Tipo di accesso: Sola lettura  
  
 Indica se la transazione in ingresso è supportata.  
  
## <a name="requirements"></a>Requisiti  
  
|MOF|Dichiarato in Servicemodel.mof.|  
|---------|-----------------------------------|  
|Spazio dei nomi|Definito in root\ServiceModel|  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
