---
title: Eccezioni generate dal compilatore - Guida per programmatori C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
ms.openlocfilehash: d0e0a304c8f7d77e7ba5c89b643fc5658c458558
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590364"
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a>Eccezioni generate dal compilatore (Guida per programmatori C#)
Alcune eccezioni vengono generate automaticamente da Common Language Runtime (CLR) di .NET Framework quando le operazioni di base hanno esito negativo. Nella tabella seguente sono elencate queste eccezioni e le relative condizioni di errore.  
  
|Eccezione|DESCRIZIONE|  
|---------------|-----------------|  
|<xref:System.ArithmeticException>|Classe di base per le eccezioni che si verificano durante operazioni aritmetiche, quali <xref:System.DivideByZeroException> e <xref:System.OverflowException>.|  
|<xref:System.ArrayTypeMismatchException>|Generata quando una matrice non può archiviare un determinato elemento perché il tipo effettivo dell'elemento non è compatibile con il tipo effettivo della matrice.|  
|<xref:System.DivideByZeroException>|Generata quando viene eseguito un tentativo di dividere un valore integrale per zero.|  
|<xref:System.IndexOutOfRangeException>|Generata quando viene eseguito un tentativo di indicizzare una matrice, quando l'indice è minore di zero o supera i limiti della matrice.|  
|<xref:System.InvalidCastException>|Generata quando una conversione esplicita dal tipo di base a un'interfaccia o a un tipo derivato ha esito negativo in fase di runtime.|  
|<xref:System.NullReferenceException>|Generata quando si tenta di fare riferimento a un oggetto il cui valore è [null](../../language-reference/keywords/null.md).|  
|<xref:System.OutOfMemoryException>|Generata quando un tentativo di allocazione della memoria tramite l'operatore [new](../../language-reference/operators/new-operator.md) ha esito negativo. Ciò indica che è stata esaurita la memoria disponibile per Common Language Runtime.|  
|<xref:System.OverflowException>|Generata quando si verifica un overflow di un'operazione aritmetica in un contesto `checked`.|  
|<xref:System.StackOverflowException>|Generata quando viene esaurito lo stack di esecuzione da un numero eccessivo di chiamate in sospeso verso il metodo; in genere indica un problema di ricorsione molto profondo o infinito.|  
|<xref:System.TypeInitializationException>|Generata quando un costruttore statico genera un'eccezione e non è presente una clausola `catch` compatibile per intercettarla.|  
  
## <a name="see-also"></a>Vedere anche

- [Guida per programmatori C#](../index.md)
- [Eccezioni e gestione delle eccezioni](./index.md)
- [Gestione delle eccezioni](./exception-handling.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
