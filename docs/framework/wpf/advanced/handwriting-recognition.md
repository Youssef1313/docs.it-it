---
title: Riconoscimento della grafia
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handwriting recognition [WPF]
- recognition of handwriting [WPF]
ms.assetid: f4e8576d-e731-4bac-9818-22e2ae636636
ms.openlocfilehash: d6c09f063b6bd0eef2cb9f6bb444eac980ad4832
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956523"
---
# <a name="handwriting-recognition"></a>Riconoscimento della grafia
Questa sezione illustra alcune nozioni di base del riconoscimento relativamente all'input penna digitale nella piattaforma WPF.  
  
## <a name="recognition-solutions"></a>Soluzioni di riconoscimento  
 Nell'esempio seguente viene mostrato come riconoscere l'input penna usando la classe [Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)).  
  
> [!NOTE]
> Per questo esempio è necessario che il riconoscimento grafia sia installato nel sistema.  
  
 Creare un nuovo progetto di applicazione WPF in Visual Studio denominato **InkRecognition**. Sostituire il contenuto del file Window1.xaml con il codice XAML seguente. Questo codice esegue il rendering dell'interfaccia utente dell'applicazione.  
  
 [!code-xaml[InkRecognition#1](~/samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml#1)]  
  
 Aggiungere un riferimento all'assembly Microsoft Ink Microsoft.Ink.dll, che può trovarsi in \Programmi\File comuni\Microsoft Shared\Ink. Sostituire il contenuto del file code-behind con il codice seguente.  
  
 [!code-csharp[InkRecognition#2](~/samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml.cs#2)]
 [!code-vb[InkRecognition#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InkRecognition/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Vedere anche

- [Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90))
