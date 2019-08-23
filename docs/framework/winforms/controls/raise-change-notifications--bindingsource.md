---
title: "Procedura: Generare notifiche di modifica usando BindingSource e l'interfaccia INotifyPropertyChanged"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- change notifications [Windows Forms], raising
- BindingSource component [Windows Forms], and IPropertyChange
- data sources [Windows Forms], detecting changes
- examples [Windows Forms], BindingSource component
- change notifications
- INotifyPropertyChanged interface [Windows Forms], using with BindingSource
- BindingSource component [Windows Forms], examples
ms.assetid: 7fa2cf51-c09f-4375-adf0-e36c5617f099
ms.openlocfilehash: 7dc640f272226da650a63b1a3434822d21053b48
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968287"
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a>Procedura: Generare notifiche di modifica usando BindingSource e l'interfaccia INotifyPropertyChanged
Il componente <xref:System.Windows.Forms.BindingSource> rileva automaticamente le modifiche in un'origine dati quando il tipo contenuto nell'origine dati implementa l'interfaccia <xref:System.ComponentModel.INotifyPropertyChanged> e genera eventi <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> nel momento in cui il valore di una proprietà viene modificato. Si tratta di una caratteristica utile perché i controlli associati al componente <xref:System.Windows.Forms.BindingSource> verranno aggiornati automaticamente al variare dei valori dell'origine dati.  
  
> [!NOTE]
> Se l'origine dati implementa <xref:System.ComponentModel.INotifyPropertyChanged> e devono essere eseguite operazioni asincrone, non devono essere apportate modifiche all'origine dati in un thread in background. In alternativa, è possibile leggere i dati in un thread in background e quindi unire i dati in un elenco nel thread dell'interfaccia utente.  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice riportato di seguito viene illustrata una semplice implementazione dell'interfaccia <xref:System.ComponentModel.INotifyPropertyChanged>. Viene inoltre descritto il modo in cui il componente <xref:System.Windows.Forms.BindingSource> passa automaticamente una modifica dell'origine dati a un controllo associato quando <xref:System.Windows.Forms.BindingSource> è associato a un elenco di tipo <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
 Se si utilizza l'attributo `CallerMemberName`, le chiamate al metodo `NotifyPropertyChanged` non devono specificare il nome della proprietà come argomento di tipo stringa. Per ulteriori informazioni, vedere [informazioni sul chiamanteC#()](../../../csharp/programming-guide/concepts/caller-information.md) o [informazioni sul chiamante (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md).  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 L'esempio presenta i requisiti seguenti:  
  
- Riferimenti agli assembly System, System.Data, System.Drawing e System.Windows.Forms.  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.ComponentModel.INotifyPropertyChanged>
- [Componente BindingSource](bindingsource-component.md)
- [Procedura: Generare notifiche di modifica utilizzando il metodo ResetItem di BindingSource](how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)
