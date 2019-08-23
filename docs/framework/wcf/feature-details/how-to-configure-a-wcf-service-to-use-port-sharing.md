---
title: "Procedura: Configurare un servizio di Windows Communication Foundation per l'uso della condivisione delle porte"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6400bc71-a858-4ac2-8d5a-caa72d3b5482
ms.openlocfilehash: e92ce3468bd43456ac3f838cfc44ea7c6624502b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912213"
---
# <a name="how-to-configure-a-windows-communication-foundation-service-to-use-port-sharing"></a>Procedura: Configurare un servizio di Windows Communication Foundation per l'uso della condivisione delle porte
Il modo più semplice per utilizzare la <xref:System.ServiceModel.NetTcpBinding>condivisione delle porte net. TCP://nell'applicazione Windows Communication Foundation (WCF) consiste nell'esporre un servizio utilizzando.  
  
 Questa associazione fornisce una proprietà <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> che controlla se la condivisione delle porte net.tcp:// è attivata per il servizio configurato con questa associazione.  
  
 La procedura seguente mostra come utilizzare la classe <xref:System.ServiceModel.NetTcpBinding> per aprire un endpoint all'URI (Uniform Resource Identifier) net.tcp://localhost/MyService, prima in codice e quindi tramite elementi di configurazione.  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-code"></a>Per attivare in codice la condivisione delle porte net.tcp:// in un'associazione NetTcpBinding  
  
1. Creare un servizio per implementare un contratto denominato `IMyService` e `MyService`chiamarlo,.  
  
     [!code-csharp[c_ConfigurePortSharing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#1)]
     [!code-vb[c_ConfigurePortSharing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#1)]  
  
2. Creare un'istanza della classe <xref:System.ServiceModel.NetTcpBinding> e impostare la proprietà <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> su `true`.  
  
     [!code-csharp[c_ConfigurePortSharing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#2)]
     [!code-vb[c_ConfigurePortSharing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#2)]  
  
3. Creare un host <xref:System.ServiceModel.ServiceHost> e aggiungervi l'endpoint del servizio `MyService` che utilizza l'associazione in cui è stata attivata la condivisione delle porte <xref:System.ServiceModel.NetTcpBinding> e che è in attesa presso l'URI "net.tcp://localhost/MyService".  
  
     [!code-csharp[c_ConfigurePortSharing#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#3)]
     [!code-vb[c_ConfigurePortSharing#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#3)]  
  
    > [!NOTE]
    > In questo esempio viene utilizzata la porta TCP predefinita 808 in quanto l'indirizzo URI dell'endpoint non specifica un numero di porta diverso. Poiché la condivisione delle porte è stata attivata in modo esplicito nell'associazione di trasporto, questo servizio può condividere la porta 808 con altri servizi appartenenti ad altri processi. Se invece non si attiva la condivisione delle porte e la porta 808 è già utilizzata da un'altra applicazione, il servizio genera un'eccezione <xref:System.ServiceModel.AddressAlreadyInUseException> quando viene aperto.  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-configuration"></a>Per attivare in configurazione la condivisione delle porte net.tcp:// in un'associazione NetTcpBinding  
  
1. Nell'esempio seguente viene illustrato come attivare la condivisione delle porte e aggiungere l'endpoint di servizio tramite elementi di configurazione.  
  
```xml  
<system.serviceModel>  
  <bindings>  
    <netTcpBinding name="portSharingBinding"   
                   portSharingEnabled="true" />  
  </bindings>  
  <services>  
    <service name="MyService">  
        <endpoint address="net.tcp://localhost/MyService"  
                  binding="netTcpBinding"  
                  contract="IMyService"  
                  bindingConfiguration="portSharingBinding" />  
    </service>  
  </services>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a>Vedere anche

- [Condivisione delle porte Net.TCP](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)
- [Procedura: Abilitare il servizio di condivisione porte net. TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
