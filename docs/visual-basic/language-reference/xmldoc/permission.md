---
title: <permission>
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: 71b00b669804e644d1171480192b9d55455bdf53
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352269"
---
# <a name="permission-visual-basic"></a><span data-ttu-id="76035-101">> di autorizzazione \<(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="76035-101">\<permission> (Visual Basic)</span></span>
<span data-ttu-id="76035-102">Specifica un'autorizzazione necessaria per il membro.</span><span class="sxs-lookup"><span data-stu-id="76035-102">Specifies a required permission for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76035-103">Sintassi</span><span class="sxs-lookup"><span data-stu-id="76035-103">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
## <a name="parameters"></a><span data-ttu-id="76035-104">Parametri</span><span class="sxs-lookup"><span data-stu-id="76035-104">Parameters</span></span>  
 `member`  
 <span data-ttu-id="76035-105">Riferimento a un membro o a un campo disponibile per essere chiamato dall'ambiente di compilazione corrente.</span><span class="sxs-lookup"><span data-stu-id="76035-105">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="76035-106">Il compilatore verifica l'esistenza dell'elemento di codice specificato e converte `member` nel nome canonico dell'elemento nel file XML di output.</span><span class="sxs-lookup"><span data-stu-id="76035-106">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="76035-107">Racchiudere `member` tra virgolette ("").</span><span class="sxs-lookup"><span data-stu-id="76035-107">Enclose `member` in quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="76035-108">Descrizione dell'accesso al membro.</span><span class="sxs-lookup"><span data-stu-id="76035-108">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76035-109">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="76035-109">Remarks</span></span>  
 <span data-ttu-id="76035-110">Usare il tag `<permission>` per documentare l'accesso di un membro.</span><span class="sxs-lookup"><span data-stu-id="76035-110">Use the `<permission>` tag to document the access of a member.</span></span> <span data-ttu-id="76035-111">Usare la classe <xref:System.Security.PermissionSet> per specificare l'accesso a un membro.</span><span class="sxs-lookup"><span data-stu-id="76035-111">Use the <xref:System.Security.PermissionSet> class to specify access to a member.</span></span>  
  
 <span data-ttu-id="76035-112">Compilare con [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) per elaborare i commenti relativi alla documentazione in un file.</span><span class="sxs-lookup"><span data-stu-id="76035-112">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76035-113">Esempio</span><span class="sxs-lookup"><span data-stu-id="76035-113">Example</span></span>  
 <span data-ttu-id="76035-114">Questo esempio usa il tag `<permission>` per descrivere che la <xref:System.Security.Permissions.FileIOPermission> è richiesta dal metodo `ReadFile`.</span><span class="sxs-lookup"><span data-stu-id="76035-114">This example uses the `<permission>` tag to describe that the <xref:System.Security.Permissions.FileIOPermission> is required by the `ReadFile` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="76035-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="76035-115">See also</span></span>

- [<span data-ttu-id="76035-116">Tag di commento XML</span><span class="sxs-lookup"><span data-stu-id="76035-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
