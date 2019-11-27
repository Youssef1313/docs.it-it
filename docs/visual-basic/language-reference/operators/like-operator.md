---
title: Operatore Like
ms.date: 07/20/2015
f1_keywords:
- Like
- vb.Like
helpviewer_keywords:
- similar to
- pattern matching
- Like operator [Visual Basic]
- '? symbol, wildcard character'
- string comparison [Visual Basic], Like operator
- strings [Visual Basic], comparing
- comparison operators [Visual Basic]
- symbols, wildcard
- wildcards, Like operator
- strings [Visual Basic], matching
- string comparison [Visual Basic], sorting data
- data [Visual Basic], sorting
- text [Visual Basic], comparing
- operators [Visual Basic], pattern-matching
- data [Visual Basic], string comparisons
- string comparison [Visual Basic], Like operators
ms.assetid: 966283ec-80e2-4294-baa8-c75baff804f9
ms.openlocfilehash: 5db9488bbec716156a3ab464042c0853241a82b1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350942"
---
# <a name="like-operator-visual-basic"></a><span data-ttu-id="57fc6-102">Like (operatore) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57fc6-102">Like Operator (Visual Basic)</span></span>
<span data-ttu-id="57fc6-103">Confronta una stringa con un modello.</span><span class="sxs-lookup"><span data-stu-id="57fc6-103">Compares a string against a pattern.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="57fc6-104">L'operatore `Like` non è attualmente supportato nei progetti .NET Core e .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="57fc6-104">The `Like` operator is currently not supported in .NET Core and .NET Standard projects.</span></span>

## <a name="syntax"></a><span data-ttu-id="57fc6-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="57fc6-105">Syntax</span></span>  
  
```vb  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="57fc6-106">Parti</span><span class="sxs-lookup"><span data-stu-id="57fc6-106">Parts</span></span>  
 `result`  
 <span data-ttu-id="57fc6-107">Obbligatoria.</span><span class="sxs-lookup"><span data-stu-id="57fc6-107">Required.</span></span> <span data-ttu-id="57fc6-108">Qualsiasi variabile `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="57fc6-108">Any `Boolean` variable.</span></span> <span data-ttu-id="57fc6-109">Il risultato è un valore `Boolean` che indica se il `string` soddisfa o meno il `pattern`.</span><span class="sxs-lookup"><span data-stu-id="57fc6-109">The result is a `Boolean` value indicating whether or not the `string` satisfies the `pattern`.</span></span>  
  
 `string`  
 <span data-ttu-id="57fc6-110">Obbligatoria.</span><span class="sxs-lookup"><span data-stu-id="57fc6-110">Required.</span></span> <span data-ttu-id="57fc6-111">Qualsiasi espressione `String` .</span><span class="sxs-lookup"><span data-stu-id="57fc6-111">Any `String` expression.</span></span>  
  
 `pattern`  
 <span data-ttu-id="57fc6-112">Obbligatoria.</span><span class="sxs-lookup"><span data-stu-id="57fc6-112">Required.</span></span> <span data-ttu-id="57fc6-113">Qualsiasi espressione `String` conforme alle convenzioni dei criteri di ricerca descritte in "osservazioni".</span><span class="sxs-lookup"><span data-stu-id="57fc6-113">Any `String` expression conforming to the pattern-matching conventions described in "Remarks."</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57fc6-114">Note</span><span class="sxs-lookup"><span data-stu-id="57fc6-114">Remarks</span></span>  
 <span data-ttu-id="57fc6-115">Se il valore in `string` soddisfa il modello contenuto in `pattern`, `result` è `True`.</span><span class="sxs-lookup"><span data-stu-id="57fc6-115">If the value in `string` satisfies the pattern contained in `pattern`, `result` is `True`.</span></span> <span data-ttu-id="57fc6-116">Se la stringa non soddisfa il criterio, `result` viene `False`.</span><span class="sxs-lookup"><span data-stu-id="57fc6-116">If the string does not satisfy the pattern, `result` is `False`.</span></span> <span data-ttu-id="57fc6-117">Se sia `string` che `pattern` sono stringhe vuote, il risultato è `True`.</span><span class="sxs-lookup"><span data-stu-id="57fc6-117">If both `string` and `pattern` are empty strings, the result is `True`.</span></span>  
  
## <a name="comparison-method"></a><span data-ttu-id="57fc6-118">Metodo di confronto</span><span class="sxs-lookup"><span data-stu-id="57fc6-118">Comparison Method</span></span>  
 <span data-ttu-id="57fc6-119">Il comportamento dell'operatore `Like` dipende dall' [istruzione Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="57fc6-119">The behavior of the `Like` operator depends on the [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span> <span data-ttu-id="57fc6-120">Il metodo di confronto tra stringhe predefinito per ogni file di origine è `Option Compare Binary`.</span><span class="sxs-lookup"><span data-stu-id="57fc6-120">The default string comparison method for each source file is `Option Compare Binary`.</span></span>  
  
## <a name="pattern-options"></a><span data-ttu-id="57fc6-121">Opzioni modello</span><span class="sxs-lookup"><span data-stu-id="57fc6-121">Pattern Options</span></span>  
 <span data-ttu-id="57fc6-122">Criteri di ricerca predefiniti fornisce uno strumento versatile per i confronti tra stringhe.</span><span class="sxs-lookup"><span data-stu-id="57fc6-122">Built-in pattern matching provides a versatile tool for string comparisons.</span></span> <span data-ttu-id="57fc6-123">Le funzionalità dei criteri di ricerca consentono di associare ogni carattere in `string` a un carattere specifico, a un carattere jolly, a un elenco di caratteri o a un intervallo di caratteri.</span><span class="sxs-lookup"><span data-stu-id="57fc6-123">The pattern-matching features allow you to match each character in `string` against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="57fc6-124">Nella tabella seguente vengono illustrati i caratteri consentiti in `pattern` e le relative corrispondenze.</span><span class="sxs-lookup"><span data-stu-id="57fc6-124">The following table shows the characters allowed in `pattern` and what they match.</span></span>  
  
|<span data-ttu-id="57fc6-125">Caratteri in `pattern`</span><span class="sxs-lookup"><span data-stu-id="57fc6-125">Characters in `pattern`</span></span>|<span data-ttu-id="57fc6-126">Corrispondenze in `string`</span><span class="sxs-lookup"><span data-stu-id="57fc6-126">Matches in `string`</span></span>|  
|-----------------------------|-------------------------|  
|`?`|<span data-ttu-id="57fc6-127">Qualsiasi carattere singolo</span><span class="sxs-lookup"><span data-stu-id="57fc6-127">Any single character</span></span>|  
|`*`|<span data-ttu-id="57fc6-128">Zero o più caratteri</span><span class="sxs-lookup"><span data-stu-id="57fc6-128">Zero or more characters</span></span>|  
|`#`|<span data-ttu-id="57fc6-129">Qualsiasi cifra singola (0-9)</span><span class="sxs-lookup"><span data-stu-id="57fc6-129">Any single digit (0–9)</span></span>|  
|`[charlist]`|<span data-ttu-id="57fc6-130">Qualsiasi carattere singolo in `charlist`</span><span class="sxs-lookup"><span data-stu-id="57fc6-130">Any single character in `charlist`</span></span>|  
|`[!charlist]`|<span data-ttu-id="57fc6-131">Qualsiasi carattere singolo non presente in `charlist`</span><span class="sxs-lookup"><span data-stu-id="57fc6-131">Any single character not in `charlist`</span></span>|  
  
## <a name="character-lists"></a><span data-ttu-id="57fc6-132">Elenchi di caratteri</span><span class="sxs-lookup"><span data-stu-id="57fc6-132">Character Lists</span></span>  
 <span data-ttu-id="57fc6-133">Un gruppo di uno o più caratteri (`charlist`) racchiusi tra parentesi quadre (`[ ]`) può essere usato per trovare la corrispondenza con qualsiasi carattere singolo in `string` e può includere quasi tutti i codici carattere, incluse le cifre.</span><span class="sxs-lookup"><span data-stu-id="57fc6-133">A group of one or more characters (`charlist`) enclosed in brackets (`[ ]`) can be used to match any single character in `string` and can include almost any character code, including digits.</span></span>  
  
 <span data-ttu-id="57fc6-134">Un punto esclamativo (`!`) all'inizio di `charlist` indica che viene effettuata una corrispondenza se viene trovato un carattere qualsiasi, ad eccezione dei caratteri in `charlist` `string`.</span><span class="sxs-lookup"><span data-stu-id="57fc6-134">An exclamation point (`!`) at the beginning of `charlist` means that a match is made if any character except the characters in `charlist` is found in `string`.</span></span> <span data-ttu-id="57fc6-135">Quando viene usato all'esterno delle parentesi quadre, il punto esclamativo corrisponde a se stesso.</span><span class="sxs-lookup"><span data-stu-id="57fc6-135">When used outside brackets, the exclamation point matches itself.</span></span>  
  
## <a name="special-characters"></a><span data-ttu-id="57fc6-136">Caratteri speciali</span><span class="sxs-lookup"><span data-stu-id="57fc6-136">Special Characters</span></span>  
 <span data-ttu-id="57fc6-137">Per trovare la corrispondenza tra i caratteri speciali (`[`), il punto interrogativo (`?`), il simbolo di cancelletto (`#`) e l'asterisco (`*`), racchiuderli tra parentesi quadre.</span><span class="sxs-lookup"><span data-stu-id="57fc6-137">To match the special characters left bracket (`[`), question mark (`?`), number sign (`#`), and asterisk (`*`), enclose them in brackets.</span></span> <span data-ttu-id="57fc6-138">La parentesi quadra chiusa (`]`) non può essere usata all'interno di un gruppo per la corrispondenza, ma può essere usata all'esterno di un gruppo come singolo carattere.</span><span class="sxs-lookup"><span data-stu-id="57fc6-138">The right bracket (`]`) cannot be used within a group to match itself, but it can be used outside a group as an individual character.</span></span>  
  
 <span data-ttu-id="57fc6-139">La sequenza di caratteri `[]` viene considerata una stringa di lunghezza zero (`""`).</span><span class="sxs-lookup"><span data-stu-id="57fc6-139">The character sequence `[]` is considered a zero-length string (`""`).</span></span> <span data-ttu-id="57fc6-140">Tuttavia, non può far parte di un elenco di caratteri racchiuso tra parentesi quadre.</span><span class="sxs-lookup"><span data-stu-id="57fc6-140">However, it cannot be part of a character list enclosed in brackets.</span></span> <span data-ttu-id="57fc6-141">Se si desidera controllare se una posizione in `string` contiene uno di un gruppo di caratteri o nessun carattere, è possibile utilizzare `Like` due volte.</span><span class="sxs-lookup"><span data-stu-id="57fc6-141">If you want to check whether a position in `string` contains one of a group of characters or no character at all, you can use `Like` twice.</span></span> <span data-ttu-id="57fc6-142">Per un esempio, vedere [procedura: trovare la corrispondenza di una stringa con un modello](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="57fc6-142">For an example, see [How to: Match a String against a Pattern](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span></span>  
  
## <a name="character-ranges"></a><span data-ttu-id="57fc6-143">Intervalli di caratteri</span><span class="sxs-lookup"><span data-stu-id="57fc6-143">Character Ranges</span></span>  
 <span data-ttu-id="57fc6-144">Utilizzando un trattino (`–`) per separare i limiti inferiore e superiore dell'intervallo, `charlist` possibile specificare un intervallo di caratteri.</span><span class="sxs-lookup"><span data-stu-id="57fc6-144">By using a hyphen (`–`) to separate the lower and upper bounds of the range, `charlist` can specify a range of characters.</span></span> <span data-ttu-id="57fc6-145">Ad esempio, `[A–Z]` restituisce una corrispondenza se la posizione del carattere corrispondente in `string` contiene un carattere compreso nell'intervallo `A`–`Z`e `[!H–L]` restituisce una corrispondenza se la posizione del carattere corrispondente contiene un carattere non compreso nell'intervallo `H`–`L`.</span><span class="sxs-lookup"><span data-stu-id="57fc6-145">For example, `[A–Z]` results in a match if the corresponding character position in `string` contains any character within the range `A`–`Z`, and `[!H–L]` results in a match if the corresponding character position contains any character outside the range `H`–`L`.</span></span>  
  
 <span data-ttu-id="57fc6-146">Quando si specifica un intervallo di caratteri, questi devono essere visualizzati in ordine crescente, ovvero dal più basso al più alto.</span><span class="sxs-lookup"><span data-stu-id="57fc6-146">When you specify a range of characters, they must appear in ascending sort order, that is, from lowest to highest.</span></span> <span data-ttu-id="57fc6-147">Pertanto, `[A–Z]` è un modello valido, ma `[Z–A]` non lo è.</span><span class="sxs-lookup"><span data-stu-id="57fc6-147">Thus, `[A–Z]` is a valid pattern, but `[Z–A]` is not.</span></span>  
  
### <a name="multiple-character-ranges"></a><span data-ttu-id="57fc6-148">Più intervalli di caratteri</span><span class="sxs-lookup"><span data-stu-id="57fc6-148">Multiple Character Ranges</span></span>  
 <span data-ttu-id="57fc6-149">Per specificare più intervalli per la stessa posizione del carattere, inserirli all'interno delle stesse parentesi quadre senza delimitatori.</span><span class="sxs-lookup"><span data-stu-id="57fc6-149">To specify multiple ranges for the same character position, put them within the same brackets without delimiters.</span></span> <span data-ttu-id="57fc6-150">Ad esempio, `[A–CX–Z]` restituisce una corrispondenza se la posizione del carattere corrispondente in `string` contiene qualsiasi carattere compreso nell'intervallo `A`-`C` o nell'intervallo `X`-`Z`.</span><span class="sxs-lookup"><span data-stu-id="57fc6-150">For example, `[A–CX–Z]` results in a match if the corresponding character position in `string` contains any character within either the range `A`–`C` or the range `X`–`Z`.</span></span>  
  
### <a name="usage-of-the-hyphen"></a><span data-ttu-id="57fc6-151">Utilizzo del trattino</span><span class="sxs-lookup"><span data-stu-id="57fc6-151">Usage of the Hyphen</span></span>  
 <span data-ttu-id="57fc6-152">Un trattino (`–`) può apparire all'inizio (dopo un punto esclamativo, se presente) o alla fine di `charlist` per la corrispondenza.</span><span class="sxs-lookup"><span data-stu-id="57fc6-152">A hyphen (`–`) can appear either at the beginning (after an exclamation point, if any) or at the end of `charlist` to match itself.</span></span> <span data-ttu-id="57fc6-153">In qualsiasi altra posizione, il segno meno identifica un intervallo di caratteri delimitati dai caratteri su entrambi i lati del segno meno.</span><span class="sxs-lookup"><span data-stu-id="57fc6-153">In any other location, the hyphen identifies a range of characters delimited by the characters on either side of the hyphen.</span></span>  
  
## <a name="collating-sequence"></a><span data-ttu-id="57fc6-154">Sequenza di fascicolazione</span><span class="sxs-lookup"><span data-stu-id="57fc6-154">Collating Sequence</span></span>  
 <span data-ttu-id="57fc6-155">Il significato di un intervallo specificato dipende dall'ordinamento dei caratteri in fase di esecuzione, come determinato dall'`Option Compare` e dalle impostazioni locali del sistema in cui è in esecuzione il codice.</span><span class="sxs-lookup"><span data-stu-id="57fc6-155">The meaning of a specified range depends on the character ordering at run time, as determined by `Option Compare` and the locale setting of the system the code is running on.</span></span> <span data-ttu-id="57fc6-156">Con `Option Compare Binary`, l'intervallo `[A–E]` corrisponde `A`, `B`, `C`, `D`e `E`.</span><span class="sxs-lookup"><span data-stu-id="57fc6-156">With `Option Compare Binary`, the range `[A–E]` matches `A`, `B`, `C`, `D`, and `E`.</span></span> <span data-ttu-id="57fc6-157">Con `Option Compare Text`, `[A–E]` corrisponde `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`e `e`.</span><span class="sxs-lookup"><span data-stu-id="57fc6-157">With `Option Compare Text`, `[A–E]` matches `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, and `e`.</span></span> <span data-ttu-id="57fc6-158">L'intervallo non corrisponde `Ê` o `ê` perché i caratteri accentati vengono ordinati dopo caratteri non accentati nell'ordinamento.</span><span class="sxs-lookup"><span data-stu-id="57fc6-158">The range does not match `Ê` or `ê` because accented characters collate after unaccented characters in the sort order.</span></span>  
  
## <a name="digraph-characters"></a><span data-ttu-id="57fc6-159">Caratteri di digramma</span><span class="sxs-lookup"><span data-stu-id="57fc6-159">Digraph Characters</span></span>  
 <span data-ttu-id="57fc6-160">In alcune lingue sono presenti caratteri alfabetici che rappresentano due caratteri distinti.</span><span class="sxs-lookup"><span data-stu-id="57fc6-160">In some languages, there are alphabetic characters that represent two separate characters.</span></span> <span data-ttu-id="57fc6-161">Ad esempio, diversi linguaggi utilizzano il carattere `æ` per rappresentare i caratteri `a` e `e` quando vengono visualizzati insieme.</span><span class="sxs-lookup"><span data-stu-id="57fc6-161">For example, several languages use the character `æ` to represent the characters `a` and `e` when they appear together.</span></span> <span data-ttu-id="57fc6-162">L'operatore `Like` riconosce che il singolo carattere di digramma e i due caratteri singoli sono equivalenti.</span><span class="sxs-lookup"><span data-stu-id="57fc6-162">The `Like` operator recognizes that the single digraph character and the two individual characters are equivalent.</span></span>  
  
 <span data-ttu-id="57fc6-163">Quando nelle impostazioni locali del sistema viene specificata una lingua che usa un carattere digraph, un'occorrenza del singolo carattere di digramma in `pattern` o `string` corrisponde alla sequenza di due caratteri equivalente nell'altra stringa.</span><span class="sxs-lookup"><span data-stu-id="57fc6-163">When a language that uses a digraph character is specified in the system locale settings, an occurrence of the single digraph character in either `pattern` or `string` matches the equivalent two-character sequence in the other string.</span></span> <span data-ttu-id="57fc6-164">Analogamente, un carattere di digramma in `pattern` racchiuso tra parentesi quadre (di per sé, in un elenco o in un intervallo) corrisponde alla sequenza di due caratteri equivalente nella `string`.</span><span class="sxs-lookup"><span data-stu-id="57fc6-164">Similarly, a digraph character in `pattern` enclosed in brackets (by itself, in a list, or in a range) matches the equivalent two-character sequence in `string`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="57fc6-165">Overload</span><span class="sxs-lookup"><span data-stu-id="57fc6-165">Overloading</span></span>  
 <span data-ttu-id="57fc6-166">L'operatore `Like` può essere sottoposto a *Overload*, il che significa che una classe o una struttura può ridefinire il comportamento quando un operando ha il tipo della classe o della struttura.</span><span class="sxs-lookup"><span data-stu-id="57fc6-166">The `Like` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="57fc6-167">Se il codice usa questo operatore su una classe o una struttura di questo tipo, assicurarsi di comprendere il comportamento ridefinito.</span><span class="sxs-lookup"><span data-stu-id="57fc6-167">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="57fc6-168">Per altre informazioni, vedere [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="57fc6-168">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="57fc6-169">Esempio</span><span class="sxs-lookup"><span data-stu-id="57fc6-169">Example</span></span>  
 <span data-ttu-id="57fc6-170">In questo esempio viene usato l'operatore `Like` per confrontare le stringhe con i vari modelli.</span><span class="sxs-lookup"><span data-stu-id="57fc6-170">This example uses the `Like` operator to compare strings to various patterns.</span></span> <span data-ttu-id="57fc6-171">I risultati vengono inseriti in una variabile `Boolean` che indica se ogni stringa soddisfa il modello.</span><span class="sxs-lookup"><span data-stu-id="57fc6-171">The results go into a `Boolean` variable indicating whether each string satisfies the pattern.</span></span>  
  
 [!code-vb[VbVbalrOperators#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="57fc6-172">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="57fc6-172">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [<span data-ttu-id="57fc6-173">Operatori di confronto</span><span class="sxs-lookup"><span data-stu-id="57fc6-173">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="57fc6-174">Precedenza tra gli operatori in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="57fc6-174">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="57fc6-175">Elenco degli operatori per funzionalità</span><span class="sxs-lookup"><span data-stu-id="57fc6-175">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="57fc6-176">Istruzione Option Compare</span><span class="sxs-lookup"><span data-stu-id="57fc6-176">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="57fc6-177">Operatori ed espressioni</span><span class="sxs-lookup"><span data-stu-id="57fc6-177">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="57fc6-178">Procedura: Confrontare una stringa con un modello</span><span class="sxs-lookup"><span data-stu-id="57fc6-178">How to: Match a String against a Pattern</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
