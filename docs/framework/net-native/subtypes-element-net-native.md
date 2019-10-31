---
title: Elemento <Subtypes> (.NET Native)
ms.date: 03/30/2017
ms.assetid: fb854070-248b-46cf-9dab-c322e2b4d624
ms.openlocfilehash: 9f090e7d1558d31111345e2c9b8dabb55b7122c1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128100"
---
# <a name="subtypes-element-net-native"></a><span data-ttu-id="7d70c-102">Elemento > di sottotipi \<(.NET Native)</span><span class="sxs-lookup"><span data-stu-id="7d70c-102">\<Subtypes> Element (.NET Native)</span></span>
<span data-ttu-id="7d70c-103">Applica i criteri di runtime a tutte le classi ereditate per il tipo contenitore.</span><span class="sxs-lookup"><span data-stu-id="7d70c-103">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d70c-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="7d70c-104">Syntax</span></span>  
  
```xml  
<Subtypes Activate="policy_type"  
          Browse="policy_type"  
          Dynamic="policy_type"  
          Serialize="policy_type"   
          DataContractSerializer="policy_setting"  
          DataContractJsonSerializer="policy_setting"  
          XmlSerializer="policy_setting"  
          MarshalObject="policy_setting"  
          MarshalDelegate="policy_setting"  
          MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d70c-105">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="7d70c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="7d70c-106">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="7d70c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d70c-107">Attributi</span><span class="sxs-lookup"><span data-stu-id="7d70c-107">Attributes</span></span>  
  
|<span data-ttu-id="7d70c-108">Attributo</span><span class="sxs-lookup"><span data-stu-id="7d70c-108">Attribute</span></span>|<span data-ttu-id="7d70c-109">Tipo di attributo</span><span class="sxs-lookup"><span data-stu-id="7d70c-109">Attribute type</span></span>|<span data-ttu-id="7d70c-110">Descrizione</span><span class="sxs-lookup"><span data-stu-id="7d70c-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="7d70c-111">Reflection</span><span class="sxs-lookup"><span data-stu-id="7d70c-111">Reflection</span></span>|<span data-ttu-id="7d70c-112">Attributo facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7d70c-112">Optional attribute.</span></span> <span data-ttu-id="7d70c-113">Controlla l'accesso in fase di esecuzione ai costruttori per abilitare l'attivazione di istanze.</span><span class="sxs-lookup"><span data-stu-id="7d70c-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="7d70c-114">Reflection</span><span class="sxs-lookup"><span data-stu-id="7d70c-114">Reflection</span></span>|<span data-ttu-id="7d70c-115">Attributo facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7d70c-115">Optional attribute.</span></span> <span data-ttu-id="7d70c-116">Controlla le query per le informazioni sugli elementi di programma, ma non abilita l'accesso in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="7d70c-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="7d70c-117">Reflection</span><span class="sxs-lookup"><span data-stu-id="7d70c-117">Reflection</span></span>|<span data-ttu-id="7d70c-118">Attributo facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7d70c-118">Optional attribute.</span></span> <span data-ttu-id="7d70c-119">Controlla l'accesso in fase di esecuzione a tutti i membri dei tipi, inclusi costruttori, metodi, campi, proprietà ed eventi, per abilitare la programmazione dinamica.</span><span class="sxs-lookup"><span data-stu-id="7d70c-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="7d70c-120">Serializzazione</span><span class="sxs-lookup"><span data-stu-id="7d70c-120">Serialization</span></span>|<span data-ttu-id="7d70c-121">Attributo facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7d70c-121">Optional attribute.</span></span> <span data-ttu-id="7d70c-122">Controlla l'accesso in fase di esecuzione a costruttori, campi e proprietà per abilitare la serializzazione e la deserializzazione delle istanze del tipo da parte di librerie quali il serializzatore JSON di Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="7d70c-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="7d70c-123">Serializzazione</span><span class="sxs-lookup"><span data-stu-id="7d70c-123">Serialization</span></span>|<span data-ttu-id="7d70c-124">Attributo facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7d70c-124">Optional attribute.</span></span> <span data-ttu-id="7d70c-125">Controlla i criteri per la serializzazione che usano la classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7d70c-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="7d70c-126">Serializzazione</span><span class="sxs-lookup"><span data-stu-id="7d70c-126">Serialization</span></span>|<span data-ttu-id="7d70c-127">Attributo facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7d70c-127">Optional attribute.</span></span> <span data-ttu-id="7d70c-128">Controlla i criteri per la serializzazione JSON che usano la classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7d70c-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="7d70c-129">Serializzazione</span><span class="sxs-lookup"><span data-stu-id="7d70c-129">Serialization</span></span>|<span data-ttu-id="7d70c-130">Attributo facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7d70c-130">Optional attribute.</span></span> <span data-ttu-id="7d70c-131">Controlla i criteri per la serializzazione XML che usano la classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7d70c-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="7d70c-132">Interoperabilità</span><span class="sxs-lookup"><span data-stu-id="7d70c-132">Interop</span></span>|<span data-ttu-id="7d70c-133">Attributo facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7d70c-133">Optional attribute.</span></span> <span data-ttu-id="7d70c-134">Controlla i criteri per effettuare il marshalling dei tipi di riferimento a Windows Runtime e COM.</span><span class="sxs-lookup"><span data-stu-id="7d70c-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="7d70c-135">Interoperabilità</span><span class="sxs-lookup"><span data-stu-id="7d70c-135">Interop</span></span>|<span data-ttu-id="7d70c-136">Attributo facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7d70c-136">Optional attribute.</span></span> <span data-ttu-id="7d70c-137">Controlla i criteri per effettuare il marshalling dei tipi delegati come puntatori a funzioni al codice nativo.</span><span class="sxs-lookup"><span data-stu-id="7d70c-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="7d70c-138">Interoperabilità</span><span class="sxs-lookup"><span data-stu-id="7d70c-138">Interop</span></span>|<span data-ttu-id="7d70c-139">Attributo facoltativo.</span><span class="sxs-lookup"><span data-stu-id="7d70c-139">Optional attribute.</span></span> <span data-ttu-id="7d70c-140">Controlla i criteri per il marshalling dei tipi di valore al codice nativo.</span><span class="sxs-lookup"><span data-stu-id="7d70c-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="7d70c-141">Tutti gli attributi</span><span class="sxs-lookup"><span data-stu-id="7d70c-141">All attributes</span></span>  
  
|<span data-ttu-id="7d70c-142">Value</span><span class="sxs-lookup"><span data-stu-id="7d70c-142">Value</span></span>|<span data-ttu-id="7d70c-143">Descrizione</span><span class="sxs-lookup"><span data-stu-id="7d70c-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7d70c-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="7d70c-144">*policy_setting*</span></span>|<span data-ttu-id="7d70c-145">L'impostazione da applicare a questo tipo di criteri.</span><span class="sxs-lookup"><span data-stu-id="7d70c-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="7d70c-146">I valori consentiti sono `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` e `Required All`.</span><span class="sxs-lookup"><span data-stu-id="7d70c-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="7d70c-147">Per altre informazioni, vedere [Runtime Directive Policy Settings](runtime-directive-policy-settings.md) (Impostazioni dei criteri delle direttive di runtime).</span><span class="sxs-lookup"><span data-stu-id="7d70c-147">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7d70c-148">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="7d70c-148">Child Elements</span></span>  
 <span data-ttu-id="7d70c-149">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="7d70c-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7d70c-150">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="7d70c-150">Parent Elements</span></span>  
  
|<span data-ttu-id="7d70c-151">Elemento</span><span class="sxs-lookup"><span data-stu-id="7d70c-151">Element</span></span>|<span data-ttu-id="7d70c-152">Descrizione</span><span class="sxs-lookup"><span data-stu-id="7d70c-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d70c-153">\<Type></span><span class="sxs-lookup"><span data-stu-id="7d70c-153">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="7d70c-154">Applica i criteri di reflection a un tipo e a tutti i membri.</span><span class="sxs-lookup"><span data-stu-id="7d70c-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d70c-155">Note</span><span class="sxs-lookup"><span data-stu-id="7d70c-155">Remarks</span></span>  
 <span data-ttu-id="7d70c-156">L'elemento `<Subtypes>` applica i criteri a tutti i sottotipi del tipo contenitore.</span><span class="sxs-lookup"><span data-stu-id="7d70c-156">The `<Subtypes>` element applies policy to all the subtypes of its containing type.</span></span> <span data-ttu-id="7d70c-157">Viene usato per applicare criteri diversi ai tipi derivati e alle classi base.</span><span class="sxs-lookup"><span data-stu-id="7d70c-157">You use it when you want to apply different policies to derived types and their base classes.</span></span>  
  
 <span data-ttu-id="7d70c-158">Gli attributi di reflection, serializzazione e interoperabilità sono tutti facoltativi, ma è necessario usarne almeno uno.</span><span class="sxs-lookup"><span data-stu-id="7d70c-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d70c-159">Esempio</span><span class="sxs-lookup"><span data-stu-id="7d70c-159">Example</span></span>  
 <span data-ttu-id="7d70c-160">L'esempio seguente definisce una classe denominata `BaseClass` e una sottoclasse denominata `Derived1`.</span><span class="sxs-lookup"><span data-stu-id="7d70c-160">The following example defines a class named `BaseClass` and a subclass named `Derived1`.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#4)]  
  
 <span data-ttu-id="7d70c-161">Come mostrato nel seguente codice, il file di direttive di runtime imposta esplicitamente i criteri `Dynamic` e `Activate` per `BaseClass` su `Excluded`.</span><span class="sxs-lookup"><span data-stu-id="7d70c-161">As shown in the following code, the runtime directives file explicitly sets the `Dynamic` and `Activate` policies for `BaseClass` to `Excluded`.</span></span> <span data-ttu-id="7d70c-162">Di conseguenza, non è possibile creare un'istanza degli oggetti di tipo `BaseClass` dinamicamente o mediante chiamate al costruttore di classi `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="7d70c-162">Because of this, objects of type `BaseClass` cannot be instantiated dynamically or by calls to the `BaseClass` class constructor.</span></span> <span data-ttu-id="7d70c-163">Tuttavia, l'elemento `<Subtypes>` consente di creare un'istanza delle classi derivate da `BaseClass` dinamicamente e mediante chiamate ai relativi costruttori di classi.</span><span class="sxs-lookup"><span data-stu-id="7d70c-163">However, the `<Subtypes>` element allows classes derived from `BaseClass` to be instantiated dynamically and through calls to their class constructors.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
   <Assembly Name="*Application*" Dynamic="Required All" />  
     <Type Name="Examples.Libraries.BaseClass" Activate ="Excluded" Dynamic="Excluded" >  
        <Subtypes Activate="Public" Dynamic ="Public"/>  
     </Type>  
  </Application>  
</Directives>  
```  
  
 <span data-ttu-id="7d70c-164">Grazie alla direttiva `<Subtypes>`, il seguente codice che crea dinamicamente un'istanza `Derived1` chiamando il metodo <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> viene eseguito correttamente.</span><span class="sxs-lookup"><span data-stu-id="7d70c-164">Because of the `<Subtypes>` directive, the following code that instantiates a `Derived1` instance dynamically by calling the <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> method executes successfully.</span></span>  <span data-ttu-id="7d70c-165">Questa variabile del blocco corrisponde a un oggetto <xref:System.Windows.Controls.TextBlock> in un'app di Windows Store vuota.</span><span class="sxs-lookup"><span data-stu-id="7d70c-165">The block variable here is a <xref:System.Windows.Controls.TextBlock> object in a blank Windows Store app.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="7d70c-166">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7d70c-166">See also</span></span>

- [<span data-ttu-id="7d70c-167">\<tipo > elemento</span><span class="sxs-lookup"><span data-stu-id="7d70c-167">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="7d70c-168">Informazioni di riferimento sul file di configurazione delle direttive di runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="7d70c-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="7d70c-169">Elementi direttiva di runtime</span><span class="sxs-lookup"><span data-stu-id="7d70c-169">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="7d70c-170">Impostazioni dei criteri delle direttive di runtime</span><span class="sxs-lookup"><span data-stu-id="7d70c-170">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
