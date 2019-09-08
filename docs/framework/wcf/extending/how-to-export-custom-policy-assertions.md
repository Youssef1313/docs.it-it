---
title: 'Procedura: Esportare asserzioni di criteri personalizzate'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99030386-43b0-4f7b-866d-17ea307f5cbd
ms.openlocfilehash: 992133ff9922e36b00683f4f48db88e1c2b91c1d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795671"
---
# <a name="how-to-export-custom-policy-assertions"></a>Procedura: Esportare asserzioni di criteri personalizzate
Le asserzioni di criteri descrivono le funzionalità e i requisiti di un endpoint del servizio. Le applicazioni del servizio possono utilizzare asserzioni di criteri personalizzate nei metadati del servizio per comunicare informazioni sulla personalizzazione di endpoint, associazione e contratto all'applicazione client. È possibile utilizzare Windows Communication Foundation (WCF) per esportare asserzioni nelle espressioni di criteri collegate nelle associazioni WSDL a livello di endpoint, operazione o messaggio, in base alle funzionalità o ai requisiti che si stanno comunicando.  
  
 Le asserzioni di criteri personalizzate vengono esportate mediante l'implementazione dell'interfaccia <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> in un elemento <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>, inserendo l'elemento dell'associazione direttamente nell'associazione dell'endpoint del servizio o registrando l'elemento dell'associazione nel file di configurazione dell'applicazione. È necessario che l'implementazione dell'esportazione del criterio aggiunga l'asserzione di criteri personalizzata come istanza <xref:System.Xml.XmlElement?displayProperty=nameWithType> all'elemento <xref:System.ServiceModel.Description.PolicyAssertionCollection?displayProperty=nameWithType> appropriato nell'elemento <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> passato al metodo <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A>.  
  
 È inoltre necessario controllare la proprietà <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> della classe <xref:System.ServiceModel.Description.WsdlExporter> ed esportare espressioni del criterio annidate e attributi dello schema dei criteri nello spazio dei nomi corretto in base alla versione del criterio specificata.  
  
 Per importare asserzioni di criteri personalizzate, <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> vedere [e procedura: Importa asserzioni](how-to-import-custom-policy-assertions.md)di criteri personalizzate.  
  
### <a name="to-export-custom-policy-assertions"></a>Per esportare asserzioni di criteri personalizzate  
  
1. Implementare l'interfaccia <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> in una classe <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>. Nell'esempio di codice seguente viene illustrata l'implementazione di un'asserzione di criteri personalizzata a livello di associazione.  
  
     [!code-csharp[CustomPolicySample#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyexporter.cs#14)]
     [!code-vb[CustomPolicySample#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyexporter.vb#14)]  
  
2. Inserire l'elemento di associazione nell'associazione dell'endpoint a livello di programmazione o utilizzando un file di configurazione dell'applicazione. Vedere le procedure seguenti.  
  
### <a name="to-insert-a-binding-element-using-an-application-configuration-file"></a>Per inserire un elemento di associazione utilizzando un file di configurazione dell'applicazione  
  
1. Implementare <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType> per l'elemento di associazione dell'asserzione di criteri personalizzata.  
  
2. Aggiungere l'estensione dell'elemento di associazione al file di configurazione utilizzando l' [ \<elemento BindingElementExtensions >](../../configure-apps/file-schema/wcf/bindingelementextensions.md) .  
  
3. Compilare un'associazione personalizzata utilizzando <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.  
  
### <a name="to-insert-a-binding-element-programmatically"></a>Per inserire un elemento di associazione a livello di programmazione  
  
1. Creare un nuovo elemento <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> e aggiungerlo a <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.  
  
2. Aggiungere l'associazione personalizzata di cui al passaggio 1 a un endpoint nuovo e aggiungere tale nuovo endpoint del servizio all'oggetto <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> chiamando il metodo <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>.  
  
3. Aprire la <xref:System.ServiceModel.ServiceHost>. Nell'esempio di codice seguente sono mostrati la creazione di un'associazione personalizzata e l'inserimento degli elementi dell'associazione a livello di programmazione.  
  
     [!code-csharp[s_imperative#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_imperative/cs/service.cs#1)]
     [!code-vb[s_imperative#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_imperative/vb/service.vb#1)]  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.ServiceModel.Description.IPolicyImportExtension>
- <xref:System.ServiceModel.Description.IPolicyExportExtension>
- [Procedura: Importa asserzioni di criteri personalizzate](how-to-import-custom-policy-assertions.md)
