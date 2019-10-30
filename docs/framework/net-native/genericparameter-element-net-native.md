---
title: Elemento <GenericParameter> (.NET Native)
ms.date: 03/30/2017
ms.assetid: cbd49732-3615-49a5-a900-f96947cdc3e6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf2b06b14252f152c1eece6f9c0d317482a24b27
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039521"
---
# <a name="genericparameter-element-net-native"></a><span data-ttu-id="255d7-102">\<elemento GenericParameter > (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="255d7-102">\<GenericParameter> Element (.NET Native)</span></span>
<span data-ttu-id="255d7-103">Applica i criteri al tipo di parametro di un tipo o di un metodo generico.</span><span class="sxs-lookup"><span data-stu-id="255d7-103">Applies policy to the parameter type of a generic type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="255d7-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="255d7-104">Syntax</span></span>  
  
```xml  
<GenericParameter Name="generic_parameter_name"  
                  Activate="policy_type"  
                  Browse="policy_type"  
                  Dynamic="policy_type"  
                  Serialize="policy_type"  
                  DataContractSerializer="policy_type"  
                  DataContractJsonSerializer="policy_type"  
                  XmlSerializer="policy_type"  
                  MarshalObject="policy_type"  
                  MarshalDelegate="policy_type"  
                  MarshalStructure="policy_type" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="255d7-105">Attributi ed elementi</span><span class="sxs-lookup"><span data-stu-id="255d7-105">Attributes and Elements</span></span>  
 <span data-ttu-id="255d7-106">Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.</span><span class="sxs-lookup"><span data-stu-id="255d7-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="255d7-107">Attributi</span><span class="sxs-lookup"><span data-stu-id="255d7-107">Attributes</span></span>  
  
|<span data-ttu-id="255d7-108">Attributo</span><span class="sxs-lookup"><span data-stu-id="255d7-108">Attribute</span></span>|<span data-ttu-id="255d7-109">Tipo di attributo</span><span class="sxs-lookup"><span data-stu-id="255d7-109">Attribute type</span></span>|<span data-ttu-id="255d7-110">Descrizione</span><span class="sxs-lookup"><span data-stu-id="255d7-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="255d7-111">Generale</span><span class="sxs-lookup"><span data-stu-id="255d7-111">General</span></span>|<span data-ttu-id="255d7-112">Attributo obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="255d7-112">Required attribute.</span></span> <span data-ttu-id="255d7-113">Il nome del parametro generico.</span><span class="sxs-lookup"><span data-stu-id="255d7-113">The name of the generic parameter.</span></span> <span data-ttu-id="255d7-114">Ad esempio, per il delegato generico <xref:System.Func%603>, il valore dell'attributo `Name` è "TResult" per applicare i criteri di runtime al valore restituito del delegato.</span><span class="sxs-lookup"><span data-stu-id="255d7-114">For example, for the generic delegate <xref:System.Func%603>, the value of the `Name` attribute is "TResult" to apply runtime policy to the delegate's return value.</span></span>|  
|`Activate`|<span data-ttu-id="255d7-115">Reflection</span><span class="sxs-lookup"><span data-stu-id="255d7-115">Reflection</span></span>|<span data-ttu-id="255d7-116">Attributo facoltativo.</span><span class="sxs-lookup"><span data-stu-id="255d7-116">Optional attribute.</span></span> <span data-ttu-id="255d7-117">Controlla l'accesso in fase di esecuzione ai costruttori per abilitare l'attivazione di istanze.</span><span class="sxs-lookup"><span data-stu-id="255d7-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="255d7-118">Reflection</span><span class="sxs-lookup"><span data-stu-id="255d7-118">Reflection</span></span>|<span data-ttu-id="255d7-119">Attributo facoltativo.</span><span class="sxs-lookup"><span data-stu-id="255d7-119">Optional attribute.</span></span> <span data-ttu-id="255d7-120">Controlla le query per le informazioni sugli elementi di programma, ma non abilita l'accesso in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="255d7-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="255d7-121">Reflection</span><span class="sxs-lookup"><span data-stu-id="255d7-121">Reflection</span></span>|<span data-ttu-id="255d7-122">Attributo facoltativo.</span><span class="sxs-lookup"><span data-stu-id="255d7-122">Optional attribute.</span></span> <span data-ttu-id="255d7-123">Controlla l'accesso in fase di esecuzione a tutti i membri dei tipi, inclusi costruttori, metodi, campi, proprietà ed eventi, per abilitare la programmazione dinamica.</span><span class="sxs-lookup"><span data-stu-id="255d7-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="255d7-124">Serializzazione</span><span class="sxs-lookup"><span data-stu-id="255d7-124">Serialization</span></span>|<span data-ttu-id="255d7-125">Attributo facoltativo.</span><span class="sxs-lookup"><span data-stu-id="255d7-125">Optional attribute.</span></span> <span data-ttu-id="255d7-126">Controlla l'accesso in fase di esecuzione a costruttori, campi e proprietà per abilitare la serializzazione e la deserializzazione delle istanze del tipo da parte di librerie quali il serializzatore JSON di Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="255d7-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="255d7-127">Serializzazione</span><span class="sxs-lookup"><span data-stu-id="255d7-127">Serialization</span></span>|<span data-ttu-id="255d7-128">Attributo facoltativo.</span><span class="sxs-lookup"><span data-stu-id="255d7-128">Optional attribute.</span></span> <span data-ttu-id="255d7-129">Controlla i criteri per la serializzazione che usano la classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="255d7-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="255d7-130">Serializzazione</span><span class="sxs-lookup"><span data-stu-id="255d7-130">Serialization</span></span>|<span data-ttu-id="255d7-131">Attributo facoltativo.</span><span class="sxs-lookup"><span data-stu-id="255d7-131">Optional attribute.</span></span> <span data-ttu-id="255d7-132">Controlla i criteri per la serializzazione JSON che usano la classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="255d7-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="255d7-133">Serializzazione</span><span class="sxs-lookup"><span data-stu-id="255d7-133">Serialization</span></span>|<span data-ttu-id="255d7-134">Attributo facoltativo.</span><span class="sxs-lookup"><span data-stu-id="255d7-134">Optional attribute.</span></span> <span data-ttu-id="255d7-135">Controlla i criteri per la serializzazione XML che usano la classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="255d7-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="255d7-136">Interoperabilità</span><span class="sxs-lookup"><span data-stu-id="255d7-136">Interop</span></span>|<span data-ttu-id="255d7-137">Attributo facoltativo.</span><span class="sxs-lookup"><span data-stu-id="255d7-137">Optional attribute.</span></span> <span data-ttu-id="255d7-138">Controlla i criteri per effettuare il marshalling dei tipi di riferimento a Windows Runtime e COM.</span><span class="sxs-lookup"><span data-stu-id="255d7-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="255d7-139">Interoperabilità</span><span class="sxs-lookup"><span data-stu-id="255d7-139">Interop</span></span>|<span data-ttu-id="255d7-140">Attributo facoltativo.</span><span class="sxs-lookup"><span data-stu-id="255d7-140">Optional attribute.</span></span> <span data-ttu-id="255d7-141">Controlla i criteri per effettuare il marshalling dei tipi delegati come puntatori a funzioni al codice nativo.</span><span class="sxs-lookup"><span data-stu-id="255d7-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="255d7-142">Interoperabilità</span><span class="sxs-lookup"><span data-stu-id="255d7-142">Interop</span></span>|<span data-ttu-id="255d7-143">Attributo facoltativo.</span><span class="sxs-lookup"><span data-stu-id="255d7-143">Optional attribute.</span></span> <span data-ttu-id="255d7-144">Controlla i criteri per il marshalling dei tipi di valore al codice nativo.</span><span class="sxs-lookup"><span data-stu-id="255d7-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="255d7-145">Name (attributo)</span><span class="sxs-lookup"><span data-stu-id="255d7-145">Name attribute</span></span>  
  
|<span data-ttu-id="255d7-146">Value</span><span class="sxs-lookup"><span data-stu-id="255d7-146">Value</span></span>|<span data-ttu-id="255d7-147">Descrizione</span><span class="sxs-lookup"><span data-stu-id="255d7-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="255d7-148">*generic_parameter_name*</span><span class="sxs-lookup"><span data-stu-id="255d7-148">*generic_parameter_name*</span></span>|<span data-ttu-id="255d7-149">Attributo obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="255d7-149">Required attribute.</span></span> <span data-ttu-id="255d7-150">Il nome del parametro di tipo generico.</span><span class="sxs-lookup"><span data-stu-id="255d7-150">The name of the generic type parameter.</span></span> <span data-ttu-id="255d7-151">Ad esempio, per il delegato generico <xref:System.Func%603>, un valore "TResult" per *generic_parameter_name* consente di applicare i criteri di runtime al valore restituito del delegato.</span><span class="sxs-lookup"><span data-stu-id="255d7-151">For example, for the generic delegate <xref:System.Func%603>, a *generic_parameter_name* value of "TResult" applies runtime policy to the delegate's return value.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="255d7-152">Tutti gli altri attributi</span><span class="sxs-lookup"><span data-stu-id="255d7-152">All other attributes</span></span>  
  
|<span data-ttu-id="255d7-153">Value</span><span class="sxs-lookup"><span data-stu-id="255d7-153">Value</span></span>|<span data-ttu-id="255d7-154">Descrizione</span><span class="sxs-lookup"><span data-stu-id="255d7-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="255d7-155">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="255d7-155">*policy_setting*</span></span>|<span data-ttu-id="255d7-156">L'impostazione da applicare a questo tipo di criteri.</span><span class="sxs-lookup"><span data-stu-id="255d7-156">The setting to apply to this policy type.</span></span> <span data-ttu-id="255d7-157">I valori consentiti sono `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` e `Required All`.</span><span class="sxs-lookup"><span data-stu-id="255d7-157">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="255d7-158">Per altre informazioni, vedere [Runtime Directive Policy Settings](runtime-directive-policy-settings.md) (Impostazioni dei criteri delle direttive di runtime).</span><span class="sxs-lookup"><span data-stu-id="255d7-158">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="255d7-159">Elementi figlio</span><span class="sxs-lookup"><span data-stu-id="255d7-159">Child Elements</span></span>  
 <span data-ttu-id="255d7-160">Nessuna.</span><span class="sxs-lookup"><span data-stu-id="255d7-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="255d7-161">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="255d7-161">Parent Elements</span></span>  
  
|<span data-ttu-id="255d7-162">Elemento</span><span class="sxs-lookup"><span data-stu-id="255d7-162">Element</span></span>|<span data-ttu-id="255d7-163">Descrizione</span><span class="sxs-lookup"><span data-stu-id="255d7-163">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="255d7-164">\<Method></span><span class="sxs-lookup"><span data-stu-id="255d7-164">\<Method></span></span>](method-element-net-native.md)|<span data-ttu-id="255d7-165">Applica i criteri di reflection di runtime a un costruttore o a un metodo.</span><span class="sxs-lookup"><span data-stu-id="255d7-165">Applies runtime reflection policy to a constructor or method.</span></span>|  
|[<span data-ttu-id="255d7-166">\<Type></span><span class="sxs-lookup"><span data-stu-id="255d7-166">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="255d7-167">Applica i criteri di reflection di runtime a un determinato tipo, ad esempio una classe o una struttura.</span><span class="sxs-lookup"><span data-stu-id="255d7-167">Applies runtime reflection policy to a particular type, such as a class or structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="255d7-168">Note</span><span class="sxs-lookup"><span data-stu-id="255d7-168">Remarks</span></span>  
 <span data-ttu-id="255d7-169">L'elemento `<GenericParameter>` è figlio dell'elemento [\<Method>](method-element-net-native.md) o [\<Type>](type-element-net-native.md) ed è usato per applicare i criteri a un determinato parametro di tipo generico, specificato mediante il nome nella firma del tipo o del metodo generico.</span><span class="sxs-lookup"><span data-stu-id="255d7-169">The `<GenericParameter>` element is a child of either the [\<Method>](method-element-net-native.md) or [\<Type>](type-element-net-native.md) element and is used to apply policy to a particular generic type parameter, which is specified by its name in the generic type or method signature.</span></span>  
  
 <span data-ttu-id="255d7-170">L'elemento `<GenericParameter>` è molto utile se usato con i serializzatori.</span><span class="sxs-lookup"><span data-stu-id="255d7-170">The `<GenericParameter>` element is most useful when used with serializers.</span></span> <span data-ttu-id="255d7-171">L'esempio seguente usa l'elemento `<GenericParameter>` per applicare i criteri al tipo `T` nelle chiamate agli overload del metodo [JsonConvert.DeserializeObject\<T>(String)](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) del serializzatore JSON NewtonSoft.</span><span class="sxs-lookup"><span data-stu-id="255d7-171">The following example uses the `<GenericParameter>` element to apply policy to the type `T` in calls to the NewtonSoft JSON serializer's [JsonConvert.DeserializeObject\<T>(String)](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) method overloads.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject{T}">  
         <GenericParameter Name="T" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="255d7-172">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="255d7-172">See also</span></span>

- [<span data-ttu-id="255d7-173">Elemento \<Method></span><span class="sxs-lookup"><span data-stu-id="255d7-173">\<Method> Element</span></span>](method-element-net-native.md)
- [<span data-ttu-id="255d7-174">\<tipo > elemento</span><span class="sxs-lookup"><span data-stu-id="255d7-174">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="255d7-175">Informazioni di riferimento sul file di configurazione delle direttive di runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="255d7-175">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="255d7-176">Impostazioni dei criteri delle direttive di runtime</span><span class="sxs-lookup"><span data-stu-id="255d7-176">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="255d7-177">Elementi direttiva di runtime</span><span class="sxs-lookup"><span data-stu-id="255d7-177">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
