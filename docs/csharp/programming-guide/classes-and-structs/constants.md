---
title: Costanti - Guida per programmatori C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 1fb39621-1738-49b1-a1b3-8587f109123f
ms.openlocfilehash: 7da86a8999f6cc36a7b71f70fd92a363673824b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924539"
---
# <a name="constants-c-programming-guide"></a>Costanti (Guida per programmatori C#)
Le costanti sono valori non modificabili, che sono noti nella fase di compilazione e non cambiano per la durata del programma. Le costanti vengono dichiarate con il modificatore [const](../../language-reference/keywords/const.md). Solo i tipi incorporati C# (ad esclusione di <xref:System.Object?displayProperty=nameWithType>) possono essere dichiarati come `const`. Per l'elenco dei tipi incorporati, vedere [Tabella dei tipi incorporati](../../language-reference/keywords/built-in-types-table.md). I tipi definiti dall'utente, incluse le classi, gli struct e le matrici, non possono essere `const`. Usare il modificatore [readonly](../../language-reference/keywords/readonly.md) per creare una classe, una matrice o uno struct che viene inizializzato una sola volta in fase di runtime (ad esempio in un costruttore) e successivamente non può più essere modificato.  
  
 C# non supporta metodi, proprietà o eventi `const`.  
  
 Il tipo enum consente di definire costanti denominate per i tipi incorporati interi (ad esempio `int`, `uint`, `long` e così via). Per altre informazioni, vedere [enum](../../language-reference/keywords/enum.md).  
  
 Le costanti devono essere inizializzate come vengono dichiarate. Ad esempio:  
  
 [!code-csharp[csProgGuideObjects#64](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#64)]  
  
 In questo esempio la costante `months` è sempre 12 e non può essere modificata neanche dalla stessa classe. In realtà, quando il compilatore incontra un identificatore costante nel codice sorgente C# (ad esempio `months`), lo sostituisce direttamente con il relativo valore letterale nel codice Intermediate Language (IL) che produce. Poiché non esiste alcun indirizzo di variabile associato a una costante in fase di esecuzione, i campi `const` non possono essere passati per riferimento e non possono sostituire un l-value in un'espressione.  
  
> [!NOTE]
> Prestare attenzione quando si creano riferimenti a valori costanti definiti in un altro codice, ad esempio in file DLL. Se una nuova versione della DLL definisce un nuovo valore per la costante, il programma mantiene il vecchio valore letterale finché non viene ricompilato per la nuova versione.  
  
 È possibile dichiarare contemporaneamente più costanti dello stesso tipo, ad esempio:  
  
 [!code-csharp[csProgGuideObjects#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#65)]  
  
 L'espressione usata per inizializzare una costante può fare riferimento a un'altra costante, a condizione che crei un riferimento circolare. Ad esempio:  
  
 [!code-csharp[csProgGuideObjects#66](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#66)]  
  
 Le costanti possono essere contrassegnate come [public](../../language-reference/keywords/public.md), [private](../../language-reference/keywords/private.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md) o [private protected](../../language-reference/keywords/private-protected.md). Questi modificatori definiscono l'accesso alla costante per gli utenti della classe. Per altre informazioni, vedere [Modificatori di accesso](./access-modifiers.md).  
  
 L’accesso alle costanti avviene come se fossero campi [statici](../../language-reference/keywords/static.md), perché il valore della costante è lo stesso per tutte le istanze del tipo. Per dichiararle non viene usata la parola chiave `static`. Per accedere alla costante, le espressioni non incluse nella classe che la definisce devono usare il nome della classe seguito da un punto e dal nome della costante stessa. Ad esempio:  
  
 [!code-csharp[csProgGuideObjects#67](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#67)]  
  
## <a name="c-language-specification"></a>Specifiche del linguaggio C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Guida per programmatori C#](../index.md)
- [Classi e struct](./index.md)
- [Proprietà](./properties.md)
- [Tipi](../types/index.md)
- [readonly](../../language-reference/keywords/readonly.md)
- [Immutabilità in C# parte 1: Tipi di immutabilità](https://blogs.msdn.microsoft.com/ericlippert/2007/11/13/immutability-in-c-part-one-kinds-of-immutability)
