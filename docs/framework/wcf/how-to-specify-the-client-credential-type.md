---
title: 'Procedura: Specificare il tipo di credenziali client'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security credentials, adding to SOAP messages
- WCF, security
ms.assetid: 10f51bee-5f92-4c1a-9126-fa5418535d8f
ms.openlocfilehash: df18f89ee18bfa33ecc0aced617d168c805e3515
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2019
ms.locfileid: "74138569"
---
# <a name="how-to-specify-the-client-credential-type"></a>Procedura: Specificare il tipo di credenziali client
Dopo avere impostato una modalità di sicurezza (trasporto o messaggio), è possibile impostare il tipo di credenziali client. Questa proprietà specifica il tipo di credenziali che il client deve fornire al servizio per l'autenticazione. Per ulteriori informazioni sull'impostazione della modalità di sicurezza (un passaggio necessario prima di impostare il tipo di credenziale client), vedere [How: Impostare la modalità di sicurezza ](how-to-set-the-security-mode.md).  
  
### <a name="to-set-the-client-credential-type-in-code"></a>Per impostare il tipo di credenziali client nel codice  
  
1. Creare un'istanza dell'associazione che verrà utilizzata dal servizio. In questo esempio viene utilizzata l'associazione <xref:System.ServiceModel.WSHttpBinding>.  
  
2. Impostare la proprietà <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> su un valore appropriato. In questo esempio viene utilizzata la modalità messaggio.  
  
3. Impostare la proprietà <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> su un valore appropriato. In questo esempio viene impostata per utilizzare l'autenticazione di Windows (<xref:System.ServiceModel.MessageCredentialType.Windows>).  
  
     [!code-csharp[c_ProgrammingSecurity#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#14)]
     [!code-vb[c_ProgrammingSecurity#14](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#14)]  
  
### <a name="to-set-the-client-credential-type-in-configuration"></a>Per impostare il tipo di credenziali client nella configurazione  
  
1. Aggiungere un elemento [\<system. serviceModel >](../configure-apps/file-schema/wcf/system-servicemodel.md) al file di configurazione.  
  
2. Come elemento figlio, aggiungere un elemento [\<bindings >](../configure-apps/file-schema/wcf/bindings.md) .  
  
3. Aggiungere un'associazione appropriata. Questo esempio usa l'elemento [\<wsHttpBinding >](../configure-apps/file-schema/wcf/wshttpbinding.md) .  
  
4. Aggiungere un elemento [\<binding >](../configure-apps/file-schema/wcf/bindings.md) e impostare l'attributo `name` su un valore appropriato. In questo esempio viene utilizzato il nome "SecureBinding."  
  
5. Aggiungere un'associazione `<security>`. Impostare l'attributo `mode` su un valore appropriato. In questo esempio viene impostato su `"Message"`.  
  
6. Aggiungere un `<message>` o `<transport>` elemento, come determinato dalla modalità di sicurezza. Impostare l'attributo `clientCredentialType` su un valore appropriato. In questo esempio viene usato `"Windows"`.  
  
    ```xml  
    <system.serviceModel>  
      <bindings>  
        <wsHttpBinding>  
          <binding name="SecureBinding">  
            <security mode="Message">  
                 <message clientCredentialType="Windows" />  
             </security>  
          </binding>  
        </wsHttpBinding>  
      </bindings>  
    </system.serviceModel>  
    ```  
  
## <a name="see-also"></a>Vedere anche

- [Protezione dei servizi](securing-services.md)
- [Procedura: Impostare la modalità di sicurezza ](how-to-set-the-security-mode.md)
