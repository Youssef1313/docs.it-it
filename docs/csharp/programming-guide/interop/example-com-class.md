---
title: Esempio di classe COM - Guida per programmatori C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
ms.openlocfilehash: 461d5a2afb197596c1c52daeeca0583b7b5e9693
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589145"
---
# <a name="example-com-class-c-programming-guide"></a>Esempio di classe COM (Guida per programmatori C#)
Di seguito è riportato un esempio di una classe esposta come oggetto COM. Dopo aver inserito questo codice in un file con estensione cs e averlo aggiunto al progetto, impostare la proprietà **Registra per interoperabilità COM** su **True**. Per altre informazioni, vedere [Procedura: Registrare un componente per l'interoperabilità COM](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100)).
  
 Per esporre gli oggetti Visual C# a COM è necessario dichiarare un'interfaccia di classe e un'interfaccia di eventi, se necessaria, oltre alla classe stessa. Per essere visibili per COM i membri della classe devono rispettare le regole seguenti:  
  
- La classe deve essere public.  
  
- Le proprietà, i metodi e gli eventi devono essere public.  
  
- Le proprietà e i metodi devono essere dichiarati nell'interfaccia di classe.  
  
- Gli eventi devono essere dichiarati nell'interfaccia eventi.  
  
 Gli altri membri public della classe non dichiarati in queste interfacce non saranno visibili per COM ma lo saranno per altri oggetti di .NET Framework.  
  
 Per esporre le proprietà e i metodi a COM, è necessario dichiararli nell'interfaccia di classe e contrassegnarli con un attributo `DispId`, nonché implementarli nella classe stessa. L'ordine con cui i membri vengono dichiarati nell'interfaccia è quello usato per la vtable COM.  
  
 Per esporre gli eventi all'esterno della classe, è necessario dichiararli nell'interfaccia eventi e contrassegnarli con un attributo `DispId`. La classe non deve implementare questa interfaccia.  
  
 La classe implementa l'interfaccia di classe. È in grado di implementare più interfacce, ma la prima implementazione sarà quella dell'interfaccia di classe predefinita. A questo punto, implementare i metodi e le proprietà esposte a COM, che devono essere contrassegnati come public e corrispondere alle dichiarazioni presenti nell'interfaccia di classe. Dichiarare anche gli eventi generati dalla classe, che devono essere contrassegnati come public e corrispondere alle dichiarazioni presenti nell'interfaccia eventi.  
  
## <a name="example"></a>Esempio  
 [!code-csharp[csProgGuideInterop#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/ExampleCOM.cs#8)]  
  
## <a name="see-also"></a>Vedere anche

- [Guida per programmatori C#](../index.md)
- [Interoperabilità](./index.md)
- [Pagina Compilazione, Creazione progetti (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)
