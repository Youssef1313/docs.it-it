---
title: Clausola Group By
ms.date: 07/20/2015
f1_keywords:
- vb.QueryGroupByInto
- vb.QueryGroupBy
- vb.QueryGroupRef
- vb.QueryGroupInto
- vb.QueryGroup
helpviewer_keywords:
- queries [Visual Basic], Group By
- Group By statement [Visual Basic]
- Group By clause [Visual Basic]
ms.assetid: b1b5dcea-6654-473b-a2db-01f7e4c265d7
ms.openlocfilehash: 87080254ad5d237a593f0c35e7c3fdaef3a8ad59
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350467"
---
# <a name="group-by-clause-visual-basic"></a>Clausola Group By (Visual Basic)
Raggruppa gli elementi di un risultato della query. Può essere usata anche per applicare funzioni di aggregazione a ogni gruppo. L'operazione di raggruppamento è basata su una o più chiavi.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
Group [ listField1 [, listField2 [...] ] By keyExp1 [, keyExp2 [...] ]  
  Into aggregateList  
```  
  
## <a name="parts"></a>Parti  
  
- `listField1`, `listField2`  
  
     Parametro facoltativo. Uno o più campi della variabile o delle variabili di query che identificano in modo esplicito i campi da includere nel risultato raggruppato. Se non sono specificati campi, tutti i campi della variabile o delle variabili di query vengono inclusi nel risultato raggruppato.  
  
- `keyExp1`  
  
     Obbligatorio. Espressione che identifica la chiave da usare per determinare i gruppi di elementi. È possibile specificare più di una chiave per specificare una chiave composta.  
  
- `keyExp2`  
  
     Parametro facoltativo. Uno o più tasti aggiuntivi che vengono combinati con `keyExp1` per creare una chiave composta.  
  
- `aggregateList`  
  
     Obbligatorio. Una o più espressioni che identificano come vengono aggregati i gruppi. Per identificare un nome di membro per i risultati raggruppati, usare la parola chiave `Group` , che può essere in uno dei seguenti formati:  
  
    ```vb  
    Into Group  
    ```  
  
     oppure  
  
    ```vb  
    Into <alias> = Group  
    ```  
  
     È anche possibile includere funzioni di aggregazione da applicare al gruppo.  
  
## <a name="remarks"></a>Note  
 È possibile usare la clausola `Group By` per suddividere i risultati di una query in gruppi. Il raggruppamento è basato su una chiave o una chiave composta costituita da più chiavi. Gli elementi associati ai valori della chiave corrispondenti vengono inclusi nello stesso gruppo.  
  
 Per identificare il nome del membro che viene usato per fare riferimento al gruppo, usare il parametro `aggregateList` della clausola `Into` e la parola chiave `Group` . È anche possibile includere funzioni di aggregazione nella clausola `Into` per calcolare i valori per gli elementi raggruppati. Per un elenco di funzioni di aggregazione standard, vedere [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
## <a name="example"></a>Esempio  
 The following code example groups a list of customers based on their location (country/region) and provides a count of the customers in each group. The results are ordered by country/region name. I risultati raggruppati vengono ordinati in base al nome della città.  
  
 [!code-vb[VbSimpleQuerySamples#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#11)]  
  
## <a name="see-also"></a>Vedere anche

- [Introduzione a LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Query](../../../visual-basic/language-reference/queries/index.md)
- [Clausola Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Clausola From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Clausola Order By](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Clausola Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Clausola Group Join](../../../visual-basic/language-reference/queries/group-join-clause.md)
