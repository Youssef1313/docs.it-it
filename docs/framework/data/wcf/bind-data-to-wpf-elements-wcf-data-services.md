---
title: 'Procedura: associare dati a elementi Windows Presentation Foundation (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding, WCF Data Services
- WCF Data Services, data binding
ms.assetid: d6538ab0-0abe-426a-b9d9-e6f3a5ca2016
ms.openlocfilehash: b623dc10bfe1b723c62b2861b4142a138904e64a
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569335"
---
# <a name="how-to-bind-data-to-windows-presentation-foundation-elements-wcf-data-services"></a>Procedura: associare dati a elementi Windows Presentation Foundation (WCF Data Services)
Con WCF Data Services è possibile associare elementi Windows Presentation Foundation (WPF), ad esempio un <xref:System.Windows.Controls.ListBox> o <xref:System.Windows.Controls.ComboBox> a un'istanza di <xref:System.Data.Services.Client.DataServiceCollection%601>che gestisce gli eventi generati dai controlli per evitare che la <xref:System.Data.Services.Client.DataServiceContext> venga sincronizzata con le modifiche apportate ai dati nei controlli. Per ulteriori informazioni, vedere [associazione di dati a controlli](binding-data-to-controls-wcf-data-services.md).  
  
 Nell'esempio riportato in questo argomento vengono usati il servizio dati Northwind di esempio e le classi del servizio dati client generate automaticamente. Questo servizio e le classi di dati client vengono creati al completamento della [WCF Data Services avvio rapido](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Esempio  
 L'esempio seguente è tratto dalla pagina code-behind per una pagina XAML (Extensible Application Markup Language) che definisce la finestra `SalesOrders` in WPF. Quando la finestra viene caricata, viene creata una <xref:System.Data.Services.Client.DataServiceCollection%601> in base al risultato di una query che restituisce i clienti, filtrati in base al paese/area geografica. Tutte le pagine di questo risultato di paging vengono caricate insieme agli ordini correlati e vengono associate alla proprietà <xref:System.Windows.FrameworkElement.DataContext%2A> dell'oggetto <xref:System.Windows.Controls.StackPanel> che rappresenta il controllo di layout radice per la finestra WPF. Per ulteriori informazioni, vedere [caricamento di contenuto posticipato](loading-deferred-content-wcf-data-services.md).  
  
 [!code-csharp[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf3.xaml.cs#bindpageddata)]
 [!code-vb[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml.vb#bindpageddata)]  
  
## <a name="example"></a>Esempio  
 Nel codice XAML seguente viene definita la finestra `SalesOrders` in WPF per l'esempio precedente.  
  
 [!code-xaml[Astoria Northwind Client#BindPagedDataXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml#bindpageddataxaml)]  
  
## <a name="example"></a>Esempio  
 L'esempio seguente è tratto dalla pagina code-behind per una pagina XAML (Extensible Application Markup Language) che definisce la finestra `SalesOrders` in WPF. Quando la finestra viene caricata, viene creato un <xref:System.Data.Services.Client.DataServiceCollection%601> in base al risultato di una query che restituisce i clienti con gli oggetti correlati, filtrati per paese/area geografica. Questo risultato viene associato alla proprietà <xref:System.Windows.FrameworkElement.DataContext%2A> dell'oggetto <xref:System.Windows.Controls.StackPanel> che rappresenta il controllo di layout radice per la finestra WPF.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf.xaml.cs#wpfdatabinding)]
 [!code-vb[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml.vb#wpfdatabinding)]  
  
## <a name="example"></a>Esempio  
 Nel codice XAML seguente viene definita la finestra `SalesOrders` in WPF per l'esempio precedente.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml#wpfdatabindingxaml)]
