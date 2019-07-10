---
title: 'Procedura: Eseguire il mapping di gerarchie di ereditarietà'
ms.date: 03/30/2017
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
ms.openlocfilehash: e0ff3fe98fcd9ced0063d2bec85928504ea19bab
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743197"
---
# <a name="how-to-map-inheritance-hierarchies"></a><span data-ttu-id="933eb-102">Procedura: Eseguire il mapping di gerarchie di ereditarietà</span><span class="sxs-lookup"><span data-stu-id="933eb-102">How to: Map Inheritance Hierarchies</span></span>
<span data-ttu-id="933eb-103">Per implementare il mapping di ereditarietà in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)], è necessario specificare gli attributi e le relative proprietà sulla classe radice della gerarchia di ereditarietà, come descritto nei passaggi seguenti.</span><span class="sxs-lookup"><span data-stu-id="933eb-103">To implement inheritance mapping in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)], you must specify the attributes and attribute properties on the root class of the inheritance hierarchy as described in the following steps.</span></span> <span data-ttu-id="933eb-104">Gli sviluppatori che usano Visual Studio è possono usare Progettazione relazionale oggetti per eseguire il mapping delle gerarchie di ereditarietà.</span><span class="sxs-lookup"><span data-stu-id="933eb-104">Developers using Visual Studio can use the Object Relational Designer to map inheritance hierarchies.</span></span> <span data-ttu-id="933eb-105">Vedere [Procedura: Configurare l'ereditarietà usando Object Relational Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).</span><span class="sxs-lookup"><span data-stu-id="933eb-105">See [How to: Configure inheritance by using the O/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="933eb-106">Non sono richiesti attributi o proprietà speciali sulle sottoclassi.</span><span class="sxs-lookup"><span data-stu-id="933eb-106">No special attributes or properties are required on the subclasses.</span></span> <span data-ttu-id="933eb-107">Notare, in particolare, che le sottoclassi non dispongono dell'attributo <xref:System.Data.Linq.Mapping.TableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="933eb-107">Note especially that subclasses do not have the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span>  
  
### <a name="to-map-an-inheritance-hierarchy"></a><span data-ttu-id="933eb-108">Per eseguire il mapping di una gerarchia di ereditarietà</span><span class="sxs-lookup"><span data-stu-id="933eb-108">To map an inheritance hierarchy</span></span>  
  
1. <span data-ttu-id="933eb-109">Aggiungere l'attributo <xref:System.Data.Linq.Mapping.TableAttribute> alla classe radice.</span><span class="sxs-lookup"><span data-stu-id="933eb-109">Add the <xref:System.Data.Linq.Mapping.TableAttribute> attribute to the root class.</span></span>  
  
2. <span data-ttu-id="933eb-110">Aggiungere inoltre alla classe radice un attributo <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> per ogni classe nella struttura gerarchica.</span><span class="sxs-lookup"><span data-stu-id="933eb-110">Also to the root class, add an <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute for each class in the hierarchy structure.</span></span>  
  
3. <span data-ttu-id="933eb-111">Per ogni attributo <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> definire una proprietà <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>.</span><span class="sxs-lookup"><span data-stu-id="933eb-111">For each <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute, define a <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> property.</span></span>  
  
     <span data-ttu-id="933eb-112">Questa proprietà contiene un valore che viene visualizzato nella colonna <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> della tabella di database per indicare la classe o sottoclasse a cui appartiene questa riga di dati.</span><span class="sxs-lookup"><span data-stu-id="933eb-112">This property holds a value that appears in the database table in the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> column to indicate which class or subclass this row of data belongs to.</span></span>  
  
4. <span data-ttu-id="933eb-113">Per ogni attributo <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> aggiungere inoltre una proprietà <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A>.</span><span class="sxs-lookup"><span data-stu-id="933eb-113">For each <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute, also add a <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> property.</span></span>  
  
     <span data-ttu-id="933eb-114">Questa proprietà contiene un valore che specifica a quale classe o sottoclasse corrisponde il valore della chiave.</span><span class="sxs-lookup"><span data-stu-id="933eb-114">This property holds a value that specifies which class or subclass the key value signifies.</span></span>  
  
5. <span data-ttu-id="933eb-115">Aggiungere una proprietà <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> solo a uno degli attributi <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A>.</span><span class="sxs-lookup"><span data-stu-id="933eb-115">On only one of the <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attributes, add an <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> property.</span></span>  
  
     <span data-ttu-id="933eb-116">Questa proprietà viene usata per definire un *fallback* mapping quando il valore discriminante dalla tabella di database non corrisponde a Nessuno <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> valore nel mapping di ereditarietà.</span><span class="sxs-lookup"><span data-stu-id="933eb-116">This property serves to designate a *fallback* mapping when the discriminator value from the database table does not match any <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> value in the inheritance mappings.</span></span>  
  
6. <span data-ttu-id="933eb-117">Aggiungere una proprietà <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> per un attributo <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="933eb-117">Add an <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> property for a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
     <span data-ttu-id="933eb-118">Questa proprietà indica che la colonna specificata contiene il valore <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>.</span><span class="sxs-lookup"><span data-stu-id="933eb-118">This property signifies that this is the column that holds the <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="933eb-119">Esempio</span><span class="sxs-lookup"><span data-stu-id="933eb-119">Example</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="933eb-120">Se si usa Visual Studio, è possibile utilizzare Object Relational Designer per configurare l'ereditarietà.</span><span class="sxs-lookup"><span data-stu-id="933eb-120">If you are using Visual Studio, you can use the Object Relational Designer to configure inheritance.</span></span> <span data-ttu-id="933eb-121">Vedere [Procedura: Configurare l'ereditarietà usando Object Relational Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)</span><span class="sxs-lookup"><span data-stu-id="933eb-121">See [How to: Configure inheritance by using the O/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)</span></span>  
  
 <span data-ttu-id="933eb-122">Nell'esempio di codice seguente `Vehicle` viene definita come classe radice e i passaggi precedenti sono stati implementati per descrivere la gerarchia per [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="933eb-122">In the following code example, `Vehicle` is defined as the root class, and the previous steps have been implemented to describe the hierarchy for [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span>  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="933eb-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="933eb-123">See also</span></span>

- [<span data-ttu-id="933eb-124">Supporto dell'ereditarietà</span><span class="sxs-lookup"><span data-stu-id="933eb-124">Inheritance Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md)
- [<span data-ttu-id="933eb-125">Procedura: Personalizzare le classi di entità usando l'Editor di codice</span><span class="sxs-lookup"><span data-stu-id="933eb-125">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
