---
ms.openlocfilehash: d48ced9d0201a33f9149aba155ddd3d8bc04c93f
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71217045"
---
### <a name="serializableattribute-removed-from-some-windows-forms-types"></a><span data-ttu-id="a43de-101">SerializableAttribute rimosso da alcuni tipi di Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a43de-101">SerializableAttribute removed from some Windows Forms types</span></span>

<span data-ttu-id="a43de-102"><xref:System.SerializableAttribute> È stata rimossa da alcune classi Windows Forms che non hanno scenari di serializzazione binaria noti.</span><span class="sxs-lookup"><span data-stu-id="a43de-102">The <xref:System.SerializableAttribute> has been removed from some Windows Forms classes that have no known binary serialization scenarios.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a43de-103">Descrizione della modifica</span><span class="sxs-lookup"><span data-stu-id="a43de-103">Change description</span></span>

<span data-ttu-id="a43de-104">I tipi seguenti sono decorati con <xref:System.SerializableAttribute> in .NET Framework, ma l'attributo è stato rimosso in .NET Core:</span><span class="sxs-lookup"><span data-stu-id="a43de-104">The following types are decorated with the <xref:System.SerializableAttribute> in .NET Framework, but the attribute has been removed in .NET Core:</span></span>

- `System.InvariantComparer`
- <xref:System.ComponentModel.Design.ExceptionCollection?displayProperty=nameWithType>
- <xref:System.ComponentModel.Design.Serialization.CodeDomSerializerException?displayProperty=nameWithType>
- `System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService.CodeDomSerializationStore`
- <xref:System.Drawing.Design.ToolboxItem?displayProperty=nameWithType>
- `System.Resources.ResXNullRef`
- `System.Resources.ResXDataNode`
- `System.Resources.ResXFileRef`
- <xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>
- `System.Windows.Forms.NativeMethods.MSOCRINFOSTRUCT`
- `System.Windows.Forms.NativeMethods.MSG`

<span data-ttu-id="a43de-105">Storicamente, questo meccanismo di serializzazione ha avuto gravi problemi di manutenzione e sicurezza.</span><span class="sxs-lookup"><span data-stu-id="a43de-105">Historically, this serialization mechanism has had serious maintenance and security concerns.</span></span> <span data-ttu-id="a43de-106">La `SerializableAttribute` gestione dei tipi significa che tali tipi devono essere testati per le modifiche di serializzazione da versione a versione e potenzialmente modifiche della serializzazione da Framework a Framework.</span><span class="sxs-lookup"><span data-stu-id="a43de-106">Maintaining `SerializableAttribute` on types means those types must be tested for version-to-version serialization changes and potentially framework-to-framework serialization changes.</span></span> <span data-ttu-id="a43de-107">Ciò rende più difficile l'evoluzione di questi tipi e può essere costoso da gestire.</span><span class="sxs-lookup"><span data-stu-id="a43de-107">This makes it harder to evolve those types and can be costly to maintain.</span></span> <span data-ttu-id="a43de-108">Questi tipi non hanno scenari di serializzazione binari noti, riducendo al minimo l'effetto della rimozione dell'attributo.</span><span class="sxs-lookup"><span data-stu-id="a43de-108">These types have no known binary serialization scenarios, which minimizes the impact of removing the attribute.</span></span>

<span data-ttu-id="a43de-109">Per ulteriori informazioni, vedere [serializzazione binaria](~/docs/standard/serialization/binary-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="a43de-109">For more information, see [Binary serialization](~/docs/standard/serialization/binary-serialization.md).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a43de-110">Versione introdotta</span><span class="sxs-lookup"><span data-stu-id="a43de-110">Version introduced</span></span>

<span data-ttu-id="a43de-111">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="a43de-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a43de-112">Azione consigliata</span><span class="sxs-lookup"><span data-stu-id="a43de-112">Recommended action</span></span>

<span data-ttu-id="a43de-113">Aggiornare qualsiasi codice che può dipendere da questi tipi contrassegnati come serializzabili.</span><span class="sxs-lookup"><span data-stu-id="a43de-113">Update any code that may depend on these types being marked as serializable.</span></span>

#### <a name="category"></a><span data-ttu-id="a43de-114">Category</span><span class="sxs-lookup"><span data-stu-id="a43de-114">Category</span></span>

<span data-ttu-id="a43de-115">Windows Form</span><span class="sxs-lookup"><span data-stu-id="a43de-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a43de-116">API interessate</span><span class="sxs-lookup"><span data-stu-id="a43de-116">Affected APIs</span></span>

- <span data-ttu-id="a43de-117">nessuno</span><span class="sxs-lookup"><span data-stu-id="a43de-117">None</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->