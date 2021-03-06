---
title: Elenco degli attributi
ms.date: 07/20/2015
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
ms.openlocfilehash: f9332f52622551bb6b944242f71bd80f439982e9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354056"
---
# <a name="attribute-list-visual-basic"></a>Elenco degli attributi (Visual Basic)
Specifica gli attributi da applicare a un elemento di programmazione dichiarato. Gli attributi sono separati da una virgola. Di seguito è riportata la sintassi per un attributo.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## <a name="parts"></a>Parti  
|||
|---|---|
|`attributemodifier`|Obbligatorio per gli attributi applicati all'inizio di un file di origine. Può essere un [assembly](../../../visual-basic/language-reference/modifiers/assembly.md) o un [modulo](../../../visual-basic/language-reference/modifiers/module-keyword.md).|
|`attributename`| Obbligatoria. Nome dell'attributo.|
|`attributearguments`|Facoltativa. Elenco di argomenti posizionali per questo attributo. Più argomenti sono separati da virgole.|
|`attributeinitializer`|Facoltativa. Elenco di inizializzatori di proprietà o di variabili per l'attributo. Più inizializzatori sono separati da virgole.|
  
## <a name="remarks"></a>Note  
 È possibile applicare uno o più attributi a quasi tutti gli elementi di programmazione (tipi, procedure, proprietà e così via). Gli attributi vengono visualizzati nei metadati dell'assembly e consentono di annotare il codice o di specificare come usare un particolare elemento di programmazione. È possibile applicare gli attributi definiti da Visual Basic e .NET Framework ed è possibile definire attributi personalizzati.  

 Per altre informazioni su quando usare gli attributi, vedere [Cenni preliminari sugli attributi](../../../visual-basic/programming-guide/concepts/attributes/index.md). Per informazioni sui nomi di attributo, vedere [nomi di elementi dichiarati](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="rules"></a>Regole  
  
- **Posizionamento.** È possibile applicare gli attributi agli elementi di programmazione più dichiarati. Per applicare uno o più attributi, inserire un *blocco di attributi* all'inizio della dichiarazione dell'elemento. Ogni voce nell'elenco di attributi specifica un attributo che si vuole applicare e il modificatore e gli argomenti usati per la chiamata dell'attributo.  
  
- **Parentesi angolari.** Se si fornisce un elenco di attributi, è necessario racchiuderlo tra parentesi angolari ("`<`" e "`>`").  
  
- **Parte della dichiarazione.** L'attributo deve essere parte della dichiarazione di elemento, non di un'istruzione separata. È possibile usare la sequenza di continuazione di riga ("`_`") per estendere l'istruzione di dichiarazione su più righe del codice sorgente.  
  
- **Modificatori.** È necessario un modificatore di attributo (`Assembly` o `Module`) per ogni attributo applicato a un elemento di programmazione all'inizio di un file di origine. I modificatori di attributo non sono consentiti per gli attributi applicati a elementi che non si trovano all'inizio di un file di origine.  
  
- **Argomenti.** Tutti gli argomenti posizionali per un attributo devono precedere qualsiasi inizializzatore di proprietà o variabile.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene applicato l'attributo <xref:System.Runtime.InteropServices.DllImportAttribute> a una definizione di scheletro di una routine di `Function`.  
  
 [!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]  
  
 <xref:System.Runtime.InteropServices.DllImportAttribute> indica che la procedura con attributi rappresenta un punto di ingresso in una libreria di collegamento dinamico (DLL) non gestita. L'attributo fornisce il nome della DLL come argomento posizionale e le altre informazioni come inizializzatori di variabile.  
  
## <a name="see-also"></a>Vedere anche

- [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md)
- [Modulo \<parola chiave>](../../../visual-basic/language-reference/modifiers/module-keyword.md)
- [Panoramica degli attributi](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Procedura: Interrompere e combinare istruzioni nel codice](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
