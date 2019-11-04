---
title: 'Procedura: implementare notifiche di modifiche alle proprietà'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- notifications of change [WPF]
- data binding [WPF], property change notifications
- change notifications [WPF]
- properties [WPF], change notifications
ms.assetid: 30b59d9e-8c3a-4349-aa82-4be837e841cf
ms.openlocfilehash: 4f9ff49a443577e119b0c1079abbe23bd7ede4c4
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459741"
---
# <a name="how-to-implement-property-change-notification"></a>Procedura: implementare notifiche di modifiche alle proprietà
Per supportare <xref:System.Windows.Data.BindingMode.OneWay> o <xref:System.Windows.Data.BindingMode.TwoWay> binding per abilitare le proprietà di destinazione del binding in modo da riflettere automaticamente le modifiche dinamiche dell'origine del binding, ad esempio per fare in modo che il riquadro di anteprima venga aggiornato automaticamente quando l'utente modifica un modulo, la classe deve fornire le notifiche appropriate per le modifiche alle proprietà. Questo esempio illustra come creare una classe che implementa <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
## <a name="example"></a>Esempio  
 Per implementare <xref:System.ComponentModel.INotifyPropertyChanged> è necessario dichiarare l'evento <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> e creare il metodo di `OnPropertyChanged`. Quindi, per ogni proprietà per cui si desidera ricevere notifiche per le modifiche, chiamare `OnPropertyChanged` ogni volta che la proprietà viene aggiornata.  
  
 [!code-csharp[SimpleBinding#PersonClass](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 Per un esempio di come è possibile usare la classe `Person` per supportare l'associazione <xref:System.Windows.Data.BindingMode.TwoWay>, vedere [controllo quando il testo della casella di testo aggiorna l'origine](how-to-control-when-the-textbox-text-updates-the-source.md).  
  
## <a name="see-also"></a>Vedere anche

- [Panoramica delle origini di associazione](binding-sources-overview.md)
- [Panoramica sul data binding](../../../desktop-wpf/data/data-binding-overview.md)
- [Procedure relative alle proprietà](data-binding-how-to-topics.md)
