---
title: 'Procedura: Associare un controllo di Windows Forms a un oggetto Factory'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], binding
- factory objects [Windows Forms], binding to
- BindingSource component [Windows Forms], binding to a factory object
- BindingSource component [Windows Forms], examples
ms.assetid: 7d59af89-ff82-41d8-a48a-f1fbae788b0d
ms.openlocfilehash: b64545528746e50d00f88d626a07ac98839e926c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/14/2019
ms.locfileid: "65589731"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-factory-object"></a>Procedura: Associare un controllo di Windows Forms a un oggetto Factory
Quando si compilano controlli che interagiscono con i dati, è a volte necessario associare un controllo a un oggetto o metodo che genera altri oggetti. Tale oggetto o metodo è definito factory. L'origine dati, ad esempio, potrebbe essere il valore restituito da una chiamata al metodo anziché un oggetto in memoria o un tipo. È possibile associare un controllo a tale tipo di origine dati purché l'origine restituisca una raccolta.  
  
 È possibile associare facilmente un controllo a un oggetto factory usando il controllo <xref:System.Windows.Forms.BindingSource>.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene dimostrato come associare un controllo <xref:System.Windows.Forms.DataGridView> a un metodo factory mediante un controllo <xref:System.Windows.Forms.BindingSource>. Il metodo factory, denominato `GetOrdersByCustomerId`, restituisce tutti gli ordini di un dato cliente nel database Northwind.  
  
 [!code-cpp[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 L'esempio presenta i requisiti seguenti:  
  
- Riferimenti agli assembly System, System.Data, System.Drawing e System.Windows.Forms.  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Componente BindingSource](bindingsource-component.md)
- [Procedura: Associare un controllo di Windows Form a un tipo](how-to-bind-a-windows-forms-control-to-a-type.md)
