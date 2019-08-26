---
title: Parola chiave unchecked - Riferimenti per C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: c31f1243b1394bfe826b02c14c73faf402640849
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608424"
---
# <a name="unchecked-c-reference"></a>unchecked (Riferimenti per C#)

La parola chiave `unchecked` viene usata per eliminare il controllo dell'overflow per le conversioni e le operazioni aritmetiche di tipo integrale.

In un contesto non controllato o di tipo unchecked, se un'espressione produce un valore non compreso nell'intervallo del tipo di destinazione, l'overflow non viene contrassegnato. Poiché, ad esempio, il calcolo nell'esempio seguente viene eseguito in un'espressione o un blocco di tipo `unchecked`, il fatto che il risultato sia troppo grande per un numero intero viene ignorato e a `int1` viene assegnato il valore -2.147.483.639.

[!code-csharp[csrefKeywordsChecked#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#5)]

Se l'ambiente `unchecked` viene rimosso, si verifica un errore di compilazione. È possibile rilevare l'overflow in fase di compilazione perché tutti i termini dell'espressione sono costanti.

Per impostazione predefinita, le espressioni che contengono termini non costanti non vengono controllate in fase di compilazione e di esecuzione. Per informazioni sull'abilitazione di un ambiente controllato, o di tipo checked, vedere [checked](checked.md).

Poiché il controllo dell'overflow richiede tempo, l'uso di codice non controllato in situazioni in cui non vi è pericolo di overflow potrebbe consentire un miglioramento delle prestazioni. Se tuttavia è possibile che si verifichi un overflow, è necessario usare un ambiente controllato.

## <a name="example"></a>Esempio

In questo esempio viene illustrato come usare la parola chiave `unchecked`.

[!code-csharp[csrefKeywordsChecked#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#2)]

## <a name="c-language-specification"></a>Specifiche del linguaggio C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Vedere anche

- [Riferimenti per C#](../index.md)
- [Guida per programmatori C#](../../programming-guide/index.md)
- [Parole chiave di C#](index.md)
- [Checked e Unchecked](checked-and-unchecked.md)
- [checked](checked.md)
