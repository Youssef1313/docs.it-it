---
title: Pubblicazione di endpoint dei metadati
ms.date: 03/30/2017
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
ms.openlocfilehash: 4c6ac81f0c97415dc21ff3346178dd1e9936b7a5
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319901"
---
# <a name="publishing-metadata-endpoints"></a>Pubblicazione di endpoint dei metadati
I servizi Windows Communication Foundation (WCF) pubblicano i metadati tramite la pubblicazione di uno o più endpoint di metadati. La pubblicazione di metadati del servizio rende disponibili i metadati utilizzando protocolli standard, ad esempio le richieste WS-MetadataExchange (MEX) e HTTP/GET. Gli endpoint dei metadati sono simili ad altri endpoint del servizio per indirizzo, associazione e contratto e possono essere aggiunti a un host del servizio tramite configurazione o codice. Per consentire la pubblicazione di endpoint dei metadati, è necessario aggiungere al servizio il comportamento del servizio <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Procedura: Pubblicare metadati per un servizio usando un file di configurazione](./feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 Viene illustrato come configurare un servizio WCF per pubblicare metadati in modo che i client possano recuperare i metadati utilizzando una richiesta WS-MetadataExchange o HTTP/GET utilizzando la stringa di query `?wsdl`.  
  
 [Procedura: Pubblicare metadati per un servizio usando il codice](./feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 Viene illustrato come abilitare la pubblicazione dei metadati per un servizio WCF nel codice in modo che i client possano recuperare i metadati utilizzando una richiesta WS-MetadataExchange o HTTP/GET utilizzando la stringa di query `?wsdl`.  
  
## <a name="see-also"></a>Vedere anche

- [Pubblicazione di metadati](./feature-details/publishing-metadata.md)
