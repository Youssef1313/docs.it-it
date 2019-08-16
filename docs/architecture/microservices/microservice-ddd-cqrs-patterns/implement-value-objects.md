---
title: Implementazione di oggetti valore
description: Architettura di microservizi .NET per applicazioni .NET in contenitori | Informazioni su dettagli e opzioni per implementare oggetti valore con le nuove funzionalità di Entity Framework.
ms.date: 10/08/2018
ms.openlocfilehash: b2f7b0f36fea25c25edd47731d9387810bd2b44d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2019
ms.locfileid: "68674148"
---
# <a name="implement-value-objects"></a><span data-ttu-id="e820f-103">Implementare oggetti valore</span><span class="sxs-lookup"><span data-stu-id="e820f-103">Implement value objects</span></span>

<span data-ttu-id="e820f-104">Come descritto nelle sezioni precedenti relative a entità e aggregazioni, l'identità è un elemento fondamentale per le entità.</span><span class="sxs-lookup"><span data-stu-id="e820f-104">As discussed in earlier sections about entities and aggregates, identity is fundamental for entities.</span></span> <span data-ttu-id="e820f-105">Tuttavia, esistono numerosi oggetti ed elementi di dati in un sistema che non richiedono un'identità e la verifica dell'identità, ad esempio gli oggetti valore.</span><span class="sxs-lookup"><span data-stu-id="e820f-105">However, there are many objects and data items in a system that do not require an identity and identity tracking, such as value objects.</span></span>

<span data-ttu-id="e820f-106">Un oggetto valore può fare riferimento ad altre entità.</span><span class="sxs-lookup"><span data-stu-id="e820f-106">A value object can reference other entities.</span></span> <span data-ttu-id="e820f-107">Ad esempio, in un'applicazione che genera una route che descrive come passare da un punto a altro, questa route sarebbe un oggetto valore.</span><span class="sxs-lookup"><span data-stu-id="e820f-107">For example, in an application that generates a route that describes how to get from one point to another, that route would be a value object.</span></span> <span data-ttu-id="e820f-108">Corrisponderebbe a uno snapshot di punti in una route specifica, tuttavia la route suggerita non avrebbe un'identità, anche se internamente potrebbe fare riferimento a entità come City, Road e così via.</span><span class="sxs-lookup"><span data-stu-id="e820f-108">It would be a snapshot of points on a specific route, but this suggested route would not have an identity, even though internally it might refer to entities like City, Road, etc.</span></span>

<span data-ttu-id="e820f-109">La figura 7-13 illustra l'oggetto valore Address all'interno dell'aggregazione Order.</span><span class="sxs-lookup"><span data-stu-id="e820f-109">Figure 7-13 shows the Address value object within the Order aggregate.</span></span>

![Oggetto valore Address all'interno dell'aggregazione Order.](./media/image14.png)

<span data-ttu-id="e820f-111">**Figura 7-13**.</span><span class="sxs-lookup"><span data-stu-id="e820f-111">**Figure 7-13**.</span></span> <span data-ttu-id="e820f-112">Oggetto valore Address all'interno dell'aggregazione Order</span><span class="sxs-lookup"><span data-stu-id="e820f-112">Address value object within the Order aggregate</span></span>

<span data-ttu-id="e820f-113">Come illustrato nella figura 7-13, un'entità è generalmente composta da più attributi.</span><span class="sxs-lookup"><span data-stu-id="e820f-113">As shown in Figure 7-13, an entity is usually composed of multiple attributes.</span></span> <span data-ttu-id="e820f-114">Ad esempio, l'entità `Order` può essere modellata come entità con un'identità, composta internamente da un set di attributi come OrderId, OrderDate, OrderItems e così via. Invece l'indirizzo, che è semplicemente un valore complesso costituito da paese/area geografica, strada, città e così via, e che non ha un'identità in questo dominio, deve essere modellato e gestito come oggetto valore.</span><span class="sxs-lookup"><span data-stu-id="e820f-114">For example, the `Order` entity can be modeled as an entity with an identity and composed internally of a set of attributes such as OrderId, OrderDate, OrderItems, etc. But the address, which is simply a complex-value composed of country/region, street, city, etc. and has no identity in this domain, must be modeled and treated as a value object.</span></span>

## <a name="important-characteristics-of-value-objects"></a><span data-ttu-id="e820f-115">Caratteristiche importanti degli oggetti valore</span><span class="sxs-lookup"><span data-stu-id="e820f-115">Important characteristics of value objects</span></span>

<span data-ttu-id="e820f-116">Esistono due caratteristiche principali proprie degli oggetti valore:</span><span class="sxs-lookup"><span data-stu-id="e820f-116">There are two main characteristics for value objects:</span></span>

- <span data-ttu-id="e820f-117">Non hanno identità.</span><span class="sxs-lookup"><span data-stu-id="e820f-117">They have no identity.</span></span>

- <span data-ttu-id="e820f-118">Non sono modificabili.</span><span class="sxs-lookup"><span data-stu-id="e820f-118">They are immutable.</span></span>

<span data-ttu-id="e820f-119">La prima caratteristica è già stata descritta.</span><span class="sxs-lookup"><span data-stu-id="e820f-119">The first characteristic was already discussed.</span></span> <span data-ttu-id="e820f-120">L'immutabilità è un requisito importante.</span><span class="sxs-lookup"><span data-stu-id="e820f-120">Immutability is an important requirement.</span></span> <span data-ttu-id="e820f-121">Dopo aver creato l'oggetto, i valori di un oggetto valore non devono essere modificabili.</span><span class="sxs-lookup"><span data-stu-id="e820f-121">The values of a value object must be immutable once the object is created.</span></span> <span data-ttu-id="e820f-122">Quindi, quando l'oggetto viene costruito, è necessario fornire i valori richiesti, ma non se ne deve consentire la modifica per l'intera durata dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="e820f-122">Therefore, when the object is constructed, you must provide the required values, but you must not allow them to change during the object’s lifetime.</span></span>

<span data-ttu-id="e820f-123">Gli oggetti valore consentono di eseguire alcune operazioni per migliorare le prestazioni, grazie alla loro natura non modificabile.</span><span class="sxs-lookup"><span data-stu-id="e820f-123">Value objects allow you to perform certain tricks for performance, thanks to their immutable nature.</span></span> <span data-ttu-id="e820f-124">Ciò vale soprattutto nei sistemi in cui possono essere presenti migliaia di istanze di un oggetto valore, molte delle quali contengono gli stessi valori.</span><span class="sxs-lookup"><span data-stu-id="e820f-124">This is especially true in systems where there may be thousands of value object instances, many of which have the same values.</span></span> <span data-ttu-id="e820f-125">La natura non modificabile di questi oggetti ne consente il riutilizzo. Sono anche intercambiabili perché i loro valori sono uguali e non hanno alcuna identità.</span><span class="sxs-lookup"><span data-stu-id="e820f-125">Their immutable nature allows them to be reused; they can be interchangeable objects, since their values are the same and they have no identity.</span></span> <span data-ttu-id="e820f-126">A volte, questo tipo di ottimizzazione può fare la differenza tra un software eseguito lentamente e uno con prestazioni ottimali.</span><span class="sxs-lookup"><span data-stu-id="e820f-126">This type of optimization can sometimes make a difference between software that runs slowly and software with good performance.</span></span> <span data-ttu-id="e820f-127">Naturalmente, tutti questi casi dipendono l'ambiente dell'applicazione e dal contesto di distribuzione.</span><span class="sxs-lookup"><span data-stu-id="e820f-127">Of course, all these cases depend on the application environment and deployment context.</span></span>

## <a name="value-object-implementation-in-c"></a><span data-ttu-id="e820f-128">Implementazione dell'oggetto valore in C\#</span><span class="sxs-lookup"><span data-stu-id="e820f-128">Value object implementation in C\#</span></span>

<span data-ttu-id="e820f-129">In termini di implementazione, è possibile avere una classe di base di oggetti valore contenente metodi di utilità di base come l'uguaglianza basata sul confronto tra tutti gli attributi (perché un oggetto valore non deve essere basato sull'identità) e altre caratteristiche fondamentali.</span><span class="sxs-lookup"><span data-stu-id="e820f-129">In terms of implementation, you can have a value object base class that has basic utility methods like equality based on comparison between all the attributes (since a value object must not be based on identity) and other fundamental characteristics.</span></span> <span data-ttu-id="e820f-130">L'esempio seguente mostra una classe di base di oggetti valore usata nel microservizio degli ordini di eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="e820f-130">The following example shows a value object base class used in the ordering microservice from eShopOnContainers.</span></span>

```csharp
public abstract class ValueObject
{
    protected static bool EqualOperator(ValueObject left, ValueObject right)
    {
        if (ReferenceEquals(left, null) ^ ReferenceEquals(right, null))
        {
            return false;
        }
        return ReferenceEquals(left, null) || left.Equals(right);
    }

    protected static bool NotEqualOperator(ValueObject left, ValueObject right)
    {
        return !(EqualOperator(left, right));
    }

    protected abstract IEnumerable<object> GetAtomicValues();

    public override bool Equals(object obj)
    {
        if (obj == null || obj.GetType() != GetType())
        {
            return false;
        }

        ValueObject other = (ValueObject)obj;
        IEnumerator<object> thisValues = GetAtomicValues().GetEnumerator();
        IEnumerator<object> otherValues = other.GetAtomicValues().GetEnumerator();
        while (thisValues.MoveNext() && otherValues.MoveNext())
        {
            if (ReferenceEquals(thisValues.Current, null) ^
                ReferenceEquals(otherValues.Current, null))
            {
                return false;
            }

            if (thisValues.Current != null &&
                !thisValues.Current.Equals(otherValues.Current))
            {
                return false;
            }
        }
        return !thisValues.MoveNext() && !otherValues.MoveNext();
    }

    public override int GetHashCode()
    {
        return GetAtomicValues()
         .Select(x => x != null ? x.GetHashCode() : 0)
         .Aggregate((x, y) => x ^ y);
    }
    // Other utility methods
}
```

<span data-ttu-id="e820f-131">È possibile usare questa classe quando si implementa l'oggetto valore effettivo, ad esempio l'oggetto valore Address mostrato nell'esempio seguente:</span><span class="sxs-lookup"><span data-stu-id="e820f-131">You can use this class when implementing your actual value object, as with the Address value object shown in the following example:</span></span>

```csharp
public class Address : ValueObject
{
    public String Street { get; private set; }
    public String City { get; private set; }
    public String State { get; private set; }
    public String Country { get; private set; }
    public String ZipCode { get; private set; }

    private Address() { }

    public Address(string street, string city, string state, string country, string zipcode)
    {
        Street = street;
        City = city;
        State = state;
        Country = country;
        ZipCode = zipcode;
    }

    protected override IEnumerable<object> GetAtomicValues()
    {
        // Using a yield return statement to return each element one at a time
        yield return Street;
        yield return City;
        yield return State;
        yield return Country;
        yield return ZipCode;
    }
}
```

<span data-ttu-id="e820f-132">Si può vedere come questa implementazione dell'oggetto valore di Address non abbia alcuna identità, e quindi alcun campo ID, né a livello della classe Address, né a livello della classe ValueObject.</span><span class="sxs-lookup"><span data-stu-id="e820f-132">You can see how this value object implementation of Address has no identity and therefore, no ID field, neither at the Address class not even at the ValueObject class.</span></span>

<span data-ttu-id="e820f-133">L'assenza di un campo ID in una classe usata da Entity Framework non era possibile fino a EF Core 2.0, che consente invece di implementare migliori oggetti valore senza ID.</span><span class="sxs-lookup"><span data-stu-id="e820f-133">Having no ID field in a class to be used by Entity Framework was not possible until EF Core 2.0, which greatly helps to implement better value objects with no ID.</span></span> <span data-ttu-id="e820f-134">Tutto ciò viene illustrato nella prossima sezione.</span><span class="sxs-lookup"><span data-stu-id="e820f-134">That is precisely the explanation of the next section.</span></span>

<span data-ttu-id="e820f-135">Si potrebbe sostenere che gli oggetti valore, essendo non modificabili, debbano essere di sola lettura (ovvero, proprietà di solo richiamo) e in effetti è vero.</span><span class="sxs-lookup"><span data-stu-id="e820f-135">It could be argued that value objects, being immutable, should be read-only (i.e. get-only properties), and that’s indeed true.</span></span> <span data-ttu-id="e820f-136">Tuttavia, gli oggetti valore vengono in genere serializzati e deserializzati per passare attraverso le code di messaggi e il fatto che siano di sola lettura impedisce al deserializzatore di assegnare valori. Vengono pertanto lasciati come "set privato", con proprietà di sola lettura sufficienti a garantirne la praticità.</span><span class="sxs-lookup"><span data-stu-id="e820f-136">However, value objects are usually serialized and deserialized to go through message queues, and being read-only stops the deserializer from assigning values, so we just leave them as private set which is read-only enough to be practical.</span></span>

## <a name="how-to-persist-value-objects-in-the-database-with-ef-core-20"></a><span data-ttu-id="e820f-137">Come rendere persistenti gli oggetti valore nel database con EF Core 2.0</span><span class="sxs-lookup"><span data-stu-id="e820f-137">How to persist value objects in the database with EF Core 2.0</span></span>

<span data-ttu-id="e820f-138">È stato appena descritto come definire un oggetto valore nel modello di dominio.</span><span class="sxs-lookup"><span data-stu-id="e820f-138">You just saw how to define a value object in your domain model.</span></span> <span data-ttu-id="e820f-139">Ma come si può rendere effettivamente persistente un oggetto valore nel database con Entity Framework (EF) Core, che in genere usa entità con identità?</span><span class="sxs-lookup"><span data-stu-id="e820f-139">But, how can you actually persist it into the database through Entity Framework (EF) Core which usually targets entities with identity?</span></span>

### <a name="background-and-older-approaches-using-ef-core-11"></a><span data-ttu-id="e820f-140">Approcci generali e precedenti con l'uso di EF Core 1.1</span><span class="sxs-lookup"><span data-stu-id="e820f-140">Background and older approaches using EF Core 1.1</span></span>

<span data-ttu-id="e820f-141">Una limitazione generale di EF Core 1.0 e 1.1 impediva l'uso dei [tipi complessi](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) come definito in EF 6.x nella piattaforma .NET Framework tradizionale.</span><span class="sxs-lookup"><span data-stu-id="e820f-141">As background, a limitation when using EF Core 1.0 and 1.1 was that you could not use [complex types](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) as defined in EF 6.x in the traditional .NET Framework.</span></span> <span data-ttu-id="e820f-142">Quindi, se si usava EF Core 1.0 o 1.1, era necessario archiviare l'oggetto di valore come entità EF con un campo ID.</span><span class="sxs-lookup"><span data-stu-id="e820f-142">Therefore, if using EF Core 1.0 or 1.1, you needed to store your value object as an EF entity with an ID field.</span></span> <span data-ttu-id="e820f-143">Successivamente, per farlo somigliare di più a un oggetto valore senza identità, era possibile nascondere l'ID per indicare che l'identità di un oggetto valore non è importante nel modello di dominio.</span><span class="sxs-lookup"><span data-stu-id="e820f-143">Then, so it looked more like a value object with no identity, you could hide its ID so you make clear that the identity of a value object is not important in the domain model.</span></span> <span data-ttu-id="e820f-144">L'ID poteva essere nascosto trasformandolo in una [proprietà shadow](https://docs.microsoft.com/ef/core/modeling/shadow-properties ).</span><span class="sxs-lookup"><span data-stu-id="e820f-144">You could hide that ID by using the ID as a [shadow property](https://docs.microsoft.com/ef/core/modeling/shadow-properties ).</span></span> <span data-ttu-id="e820f-145">Dal momento che la configurazione per nascondere l'ID del modello viene configurata nel livello di infrastruttura di EF, risulterebbe trasparente per il modello di dominio.</span><span class="sxs-lookup"><span data-stu-id="e820f-145">Since that configuration for hiding the ID in the model is set up in the EF infrastructure level, it would be kind of transparent for your domain model.</span></span>

<span data-ttu-id="e820f-146">Nella versione iniziale di eShopOnContainers (.NET Core 1.1), l'ID nascosto necessario per l'infrastruttura EF Core era implementato nel modo seguente nel livello DbContext, usando l'API Fluent nel progetto di infrastruttura.</span><span class="sxs-lookup"><span data-stu-id="e820f-146">In the initial version of eShopOnContainers (.NET Core 1.1), the hidden ID needed by EF Core infrastructure was implemented in the following way in the DbContext level, using Fluent API at the infrastructure project.</span></span> <span data-ttu-id="e820f-147">Quindi, l'ID risultava nascosto per il modello di dominio, ma era ancora presente nell'infrastruttura.</span><span class="sxs-lookup"><span data-stu-id="e820f-147">Therefore, the ID was hidden from the domain model point of view, but still present in the infrastructure.</span></span>

```csharp
// Old approach with EF Core 1.1
// Fluent API within the OrderingContext:DbContext in the Infrastructure project
void ConfigureAddress(EntityTypeBuilder<Address> addressConfiguration)
{
    addressConfiguration.ToTable("address", DEFAULT_SCHEMA);

    addressConfiguration.Property<int>("Id")  // Id is a shadow property
        .IsRequired();
    addressConfiguration.HasKey("Id");   // Id is a shadow property
}
```

<span data-ttu-id="e820f-148">La persistenza dell'oggetto valore nel database era comunque assicurata usando un'entità normale in un'altra tabella.</span><span class="sxs-lookup"><span data-stu-id="e820f-148">However, the persistence of that value object into the database was performed like a regular entity in a different table.</span></span>

<span data-ttu-id="e820f-149">In EF Core 2.0 vengono forniti modi nuovi e ottimizzati per rendere persistenti gli oggetti valore.</span><span class="sxs-lookup"><span data-stu-id="e820f-149">With EF Core 2.0, there are new and better ways to persist value objects.</span></span>

## <a name="persist-value-objects-as-owned-entity-types-in-ef-core-20"></a><span data-ttu-id="e820f-150">Rendere persistenti gli oggetti valore come tipi di entità di proprietà in EF Core 2.0</span><span class="sxs-lookup"><span data-stu-id="e820f-150">Persist value objects as owned entity types in EF Core 2.0</span></span>

<span data-ttu-id="e820f-151">Anche se ci sono alcune discrepanze tra lo schema dell'oggetto valore canonico in DDD e il tipo di entità di proprietà in EF Core, questo è attualmente il modo migliore per rendere persistenti gli oggetti valore con EF Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="e820f-151">Even with some gaps between the canonical value object pattern in DDD and the owned entity type in EF Core, it's currently the best way to persist value objects with EF Core 2.0.</span></span> <span data-ttu-id="e820f-152">È possibile vedere le limitazioni alla fine di questa sezione.</span><span class="sxs-lookup"><span data-stu-id="e820f-152">You can see limitations at the end of this section.</span></span>

<span data-ttu-id="e820f-153">La funzionalità dei tipi di entità di proprietà è stata aggiunta a EF Core a partire dalla versione 2.0.</span><span class="sxs-lookup"><span data-stu-id="e820f-153">The owned entity type feature was added to EF Core since version 2.0.</span></span>

<span data-ttu-id="e820f-154">Un tipo di entità di proprietà consente di eseguire il mapping dei tipi che non hanno un'identità definita in modo esplicito nel modello di dominio e che vengono usati come proprietà, ad esempio un oggetto valore, all'interno di qualsiasi entità.</span><span class="sxs-lookup"><span data-stu-id="e820f-154">An owned entity type allows you to map types that do not have their own identity explicitly defined in the domain model and are used as properties, such as a value object, within any of your entities.</span></span> <span data-ttu-id="e820f-155">Un tipo di entità di proprietà condivide lo stesso tipo CLR con un altro tipo di entità, ovvero si tratta di una classe normale.</span><span class="sxs-lookup"><span data-stu-id="e820f-155">An owned entity type shares the same CLR type with another entity type (that is, it’s just a regular class).</span></span> <span data-ttu-id="e820f-156">L'entità contenente la navigazione che lo definisce è l'entità del proprietario.</span><span class="sxs-lookup"><span data-stu-id="e820f-156">The entity containing the defining navigation is the owner entity.</span></span> <span data-ttu-id="e820f-157">Quando si esegue una query sul proprietario, i tipi di proprietà vengono inclusi per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="e820f-157">When querying the owner, the owned types are included by default.</span></span>

<span data-ttu-id="e820f-158">Osservando semplicemente il modello di dominio, un tipo di proprietà sembra non avere alcuna identità,</span><span class="sxs-lookup"><span data-stu-id="e820f-158">Just by looking at the domain model, an owned type looks like it doesn’t have any identity.</span></span> <span data-ttu-id="e820f-159">invece la ha, ma la proprietà di navigazione del proprietario fa parte di questa identità.</span><span class="sxs-lookup"><span data-stu-id="e820f-159">However, under the covers, owned types do have identity, but the owner navigation property is part of this identity.</span></span>

<span data-ttu-id="e820f-160">L'identità delle istanze dei tipi di proprietà non è del tutto esclusiva,</span><span class="sxs-lookup"><span data-stu-id="e820f-160">The identity of instances of owned types is not completely their own.</span></span> <span data-ttu-id="e820f-161">ma è costituita da tre componenti:</span><span class="sxs-lookup"><span data-stu-id="e820f-161">It consists of three components:</span></span>

- <span data-ttu-id="e820f-162">L'identità del proprietario</span><span class="sxs-lookup"><span data-stu-id="e820f-162">The identity of the owner</span></span>

- <span data-ttu-id="e820f-163">La proprietà di navigazione che punta alle istanze</span><span class="sxs-lookup"><span data-stu-id="e820f-163">The navigation property pointing to them</span></span>

- <span data-ttu-id="e820f-164">Per le raccolte di tipi di proprietà, un componente indipendente (non ancora supportato in EF Core 2.0, lo sarà nella versione 2.2).</span><span class="sxs-lookup"><span data-stu-id="e820f-164">In the case of collections of owned types, an independent component (not yet supported in EF Core 2.0, coming up on 2.2).</span></span>

<span data-ttu-id="e820f-165">Ad esempio, nel modello di dominio degli ordini in eShopOnContainers, all'interno dell'entità Order, l'oggetto valore Address viene implementato come un tipo di entità di proprietà all'interno dell'entità del proprietario, ovvero l'entità Order.</span><span class="sxs-lookup"><span data-stu-id="e820f-165">For example, in the Ordering domain model at eShopOnContainers, as part of the Order entity, the Address value object is implemented as an owned entity type within the owner entity, which is the Order entity.</span></span> <span data-ttu-id="e820f-166">Address è un tipo la cui proprietà identità non è definita nel modello di dominio.</span><span class="sxs-lookup"><span data-stu-id="e820f-166">Address is a type with no identity property defined in the domain model.</span></span> <span data-ttu-id="e820f-167">Viene usato come proprietà del tipo Order per specificare l'indirizzo di spedizione per uno specifico ordine.</span><span class="sxs-lookup"><span data-stu-id="e820f-167">It is used as a property of the Order type to specify the shipping address for a particular order.</span></span>

<span data-ttu-id="e820f-168">Per convenzione viene creata una chiave primaria shadow per il tipo di proprietà e ne viene eseguito il mapping alla stessa tabella del proprietario usando la suddivisione di tabelle.</span><span class="sxs-lookup"><span data-stu-id="e820f-168">By convention, a shadow primary key is created for the owned type and it will be mapped to the same table as the owner by using table splitting.</span></span> <span data-ttu-id="e820f-169">Ciò consente di usare i tipi di proprietà in modo simile ai tipi complessi in EF6 in .NET Framework tradizionale.</span><span class="sxs-lookup"><span data-stu-id="e820f-169">This allows to use owned types similarly to how complex types are used in EF6 in the traditional .NET Framework.</span></span>

<span data-ttu-id="e820f-170">È importante notare che, per convenzione, i tipi di proprietà non vengono mai individuati in EF Core, quindi è necessario dichiararli in modo esplicito.</span><span class="sxs-lookup"><span data-stu-id="e820f-170">It is important to note that owned types are never discovered by convention in EF Core, so you have to declare them explicitly.</span></span>

<span data-ttu-id="e820f-171">Nel metodo OnModelCreating() di OrderingContext.cs in eShopOnContainers vengono applicate più configurazioni dell'infrastruttura.</span><span class="sxs-lookup"><span data-stu-id="e820f-171">In eShopOnContainers, at the OrderingContext.cs, within the OnModelCreating() method, there are multiple infrastructure configuration being applied.</span></span> <span data-ttu-id="e820f-172">Una di esse è correlata all'entità Order.</span><span class="sxs-lookup"><span data-stu-id="e820f-172">One of them is related to the Order entity.</span></span>

```csharp
// Part of the OrderingContext.cs class at the Ordering.Infrastructure project
//
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
    modelBuilder.ApplyConfiguration(new ClientRequestEntityTypeConfiguration());
    modelBuilder.ApplyConfiguration(new PaymentMethodEntityTypeConfiguration());
    modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
    modelBuilder.ApplyConfiguration(new OrderItemEntityTypeConfiguration());
    //...Additional type configurations
}
```

<span data-ttu-id="e820f-173">Nel codice seguente l'infrastruttura di persistenza è definita per l'entità Order:</span><span class="sxs-lookup"><span data-stu-id="e820f-173">In the following code, the persistence infrastructure is defined for the Order entity:</span></span>

```csharp
// Part of the OrderEntityTypeConfiguration.cs class
//
public void Configure(EntityTypeBuilder<Order> orderConfiguration)
{
    orderConfiguration.ToTable("orders", OrderingContext.DEFAULT_SCHEMA);
    orderConfiguration.HasKey(o => o.Id);
    orderConfiguration.Ignore(b => b.DomainEvents);
    orderConfiguration.Property(o => o.Id)
        .ForSqlServerUseSequenceHiLo("orderseq", OrderingContext.DEFAULT_SCHEMA);

    //Address value object persisted as owned entity in EF Core 2.0
    orderConfiguration.OwnsOne(o => o.Address);

    orderConfiguration.Property<DateTime>("OrderDate").IsRequired();

    //...Additional validations, constraints and code...
    //...
}
```

<span data-ttu-id="e820f-174">Nel codice precedente il metodo `orderConfiguration.OwnsOne(o => o.Address)` specifica che la proprietà `Address` è un'entità di proprietà del tipo `Order`.</span><span class="sxs-lookup"><span data-stu-id="e820f-174">In the previous code, the `orderConfiguration.OwnsOne(o => o.Address)` method specifies that the `Address` property is an owned entity of the `Order` type.</span></span>

<span data-ttu-id="e820f-175">Per impostazione predefinita, le convenzioni di EF Core nome le colonne del database per le proprietà del tipo di entità di proprietà come `EntityProperty_OwnedEntityProperty`.</span><span class="sxs-lookup"><span data-stu-id="e820f-175">By default, EF Core conventions name the database columns for the properties of the owned entity type as `EntityProperty_OwnedEntityProperty`.</span></span> <span data-ttu-id="e820f-176">Quindi, le proprietà interne di `Address` verranno visualizzate nella tabella `Orders` con i nomi `Address_Street`, `Address_City` (e così via per `State`, `Country` e `ZipCode`).</span><span class="sxs-lookup"><span data-stu-id="e820f-176">Therefore, the internal properties of `Address` will appear in the `Orders` table with the names `Address_Street`, `Address_City` (and so on for `State`, `Country` and `ZipCode`).</span></span>

<span data-ttu-id="e820f-177">È possibile aggiungere il metodo Fluent `Property().HasColumnName()` per rinominare le colonne.</span><span class="sxs-lookup"><span data-stu-id="e820f-177">You can append the `Property().HasColumnName()` fluent method to rename those columns.</span></span> <span data-ttu-id="e820f-178">Se `Address` è una proprietà pubblica, i mapping sono simili ai seguenti:</span><span class="sxs-lookup"><span data-stu-id="e820f-178">In the case where `Address` is a public property, the mappings would be like the following:</span></span>

```csharp
orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.Street).HasColumnName("ShippingStreet");

orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.City).HasColumnName("ShippingCity");
```

<span data-ttu-id="e820f-179">È possibile concatenare il metodo `OwnsOne` in un mapping Fluent.</span><span class="sxs-lookup"><span data-stu-id="e820f-179">It is possible to chain the `OwnsOne` method in a fluent mapping.</span></span> <span data-ttu-id="e820f-180">Nell'esempio ipotetico seguente `OrderDetails` è proprietario di `BillingAddress` e `ShippingAddress`, che sono entrambi tipi `Address`.</span><span class="sxs-lookup"><span data-stu-id="e820f-180">In the following hypothetical example, `OrderDetails` owns `BillingAddress` and `ShippingAddress`, which are both `Address` types.</span></span> <span data-ttu-id="e820f-181">Quindi `OrderDetails` è di proprietà del tipo `Order`.</span><span class="sxs-lookup"><span data-stu-id="e820f-181">Then `OrderDetails` is owned by the `Order` type.</span></span>

```csharp
orderConfiguration.OwnsOne(p => p.OrderDetails, cb =>
    {
        cb.OwnsOne(c => c.BillingAddress);
        cb.OwnsOne(c => c.ShippingAddress);
    });
//...
//...
public class Order
{
    public int Id { get; set; }
    public OrderDetails OrderDetails { get; set; }
}

public class OrderDetails
{
    public Address BillingAddress { get; set; }
    public Address ShippingAddress { get; set; }
}

public class Address
{
    public string Street { get; set; }
    public string City { get; set; }
}
```

### <a name="additional-details-on-owned-entity-types"></a><span data-ttu-id="e820f-182">Altre informazioni sui tipi di entità di proprietà</span><span class="sxs-lookup"><span data-stu-id="e820f-182">Additional details on owned entity types</span></span>

- <span data-ttu-id="e820f-183">I tipi di proprietà vengono definiti quando si configura una proprietà di navigazione su un tipo particolare usando l'API Fluent OwnsOne.</span><span class="sxs-lookup"><span data-stu-id="e820f-183">Owned types are defined when you configure a navigation property to a particular type using the OwnsOne fluent API.</span></span>

- <span data-ttu-id="e820f-184">La definizione di un tipo di proprietà nel modello di metadati è composta da: tipo di proprietario, proprietà di navigazione e tipo CLR del tipo di proprietà.</span><span class="sxs-lookup"><span data-stu-id="e820f-184">The definition of an owned type in our metadata model is a composite of: the owner type, the navigation property, and the CLR type of the owned type.</span></span>

- <span data-ttu-id="e820f-185">L'identità (chiave) di un'istanza del tipo di proprietà in questo stack è composta dall'identità del tipo di proprietario e dalla definizione del tipo di proprietà.</span><span class="sxs-lookup"><span data-stu-id="e820f-185">The identity (key) of an owned type instance in our stack is a composite of the identity of the owner type and the definition of the owned type.</span></span>

#### <a name="owned-entities-capabilities"></a><span data-ttu-id="e820f-186">Funzionalità delle entità di proprietà:</span><span class="sxs-lookup"><span data-stu-id="e820f-186">Owned entities capabilities:</span></span>

- <span data-ttu-id="e820f-187">I tipi di proprietà possono fare riferimento ad altre entità, sia di proprietà (tipi di proprietà annidati) che non (proprietà di navigazione con normale riferimento ad altre entità).</span><span class="sxs-lookup"><span data-stu-id="e820f-187">Owned types can reference other entities, either owned (nested owned types) or non-owned (regular reference navigation properties to other entities).</span></span>

- <span data-ttu-id="e820f-188">È possibile eseguire il mapping dello stesso tipo CLR come tipi di proprietà diversi nella stessa entità del proprietario usando proprietà di navigazione distinte.</span><span class="sxs-lookup"><span data-stu-id="e820f-188">You can map the same CLR type as different owned types in the same owner entity through separate navigation properties.</span></span>

- <span data-ttu-id="e820f-189">La suddivisione di tabelle è configurata per convenzione, ma è possibile rifiutare esplicitamente eseguendo il mapping del tipo di proprietà in una tabella diversa usando ToTable.</span><span class="sxs-lookup"><span data-stu-id="e820f-189">Table splitting is setup by convention, but you can opt out by mapping the owned type to a different table using ToTable.</span></span>

- <span data-ttu-id="e820f-190">Il caricamento eager viene eseguito automaticamente sui tipi di proprietà, ovvero non è necessario chiamare Include() nella query.</span><span class="sxs-lookup"><span data-stu-id="e820f-190">Eager loading is performed automatically on owned types, i.e. no need to call Include() on the query.</span></span>

- <span data-ttu-id="e820f-191">Possono essere configurate con l'attributo \[Owned\], a partire da EF Core 2.1</span><span class="sxs-lookup"><span data-stu-id="e820f-191">Can be configured with attribute \[Owned\], as of EF Core 2.1</span></span>

#### <a name="owned-entities-limitations"></a><span data-ttu-id="e820f-192">Limitazioni delle entità di proprietà:</span><span class="sxs-lookup"><span data-stu-id="e820f-192">Owned entities limitations:</span></span>

- <span data-ttu-id="e820f-193">Non è possibile creare un elemento DbSet\<T\> di un tipo di proprietà (per impostazione predefinita).</span><span class="sxs-lookup"><span data-stu-id="e820f-193">You cannot create a DbSet\<T\> of an owned type (by design).</span></span>

- <span data-ttu-id="e820f-194">Non è possibile chiamare ModelBuilder.Entity\<T\>() nei tipi di proprietà (attualmente per impostazione predefinita).</span><span class="sxs-lookup"><span data-stu-id="e820f-194">You cannot call ModelBuilder.Entity\<T\>() on owned types (currently by design).</span></span>

- <span data-ttu-id="e820f-195">Le raccolte di tipi di proprietà non sono ancora supportate (in EF Core 2.1, ma lo saranno nella versione 2.2).</span><span class="sxs-lookup"><span data-stu-id="e820f-195">No collections of owned types yet (as of EF Core 2.1, but they will be supported in 2.2).</span></span>

- <span data-ttu-id="e820f-196">Nessun supporto per i tipi di proprietà facoltativi (ovvero, nullable) di cui viene eseguito il mapping con il proprietario nella stessa tabella, ad esempio tramite la suddivisione di tabelle.</span><span class="sxs-lookup"><span data-stu-id="e820f-196">No support for optional (that is, nullable) owned types that are mapped with the owner in the same table (i.e. using table splitting).</span></span> <span data-ttu-id="e820f-197">Ciò è dovuto al fatto che il mapping viene eseguito per ogni proprietà e non è disponibile un valore sentinel separato per l'intero valore complesso Null.</span><span class="sxs-lookup"><span data-stu-id="e820f-197">This is because mapping is done for each property, we don't have a separate sentinel for the null complex value a as whole.</span></span>

- <span data-ttu-id="e820f-198">Nessun supporto del mapping di ereditarietà per i tipi di proprietà, ma è possibile eseguire il mapping di due tipi di foglia delle stesse gerarchie di ereditarietà come tipi di proprietà diversi.</span><span class="sxs-lookup"><span data-stu-id="e820f-198">No inheritance mapping support for owned types, but you should be able to map two leaf types of the same inheritance hierarchies as different owned types.</span></span> <span data-ttu-id="e820f-199">EF Core non considera il fatto che fanno parte della stessa gerarchia.</span><span class="sxs-lookup"><span data-stu-id="e820f-199">EF Core will not reason about the fact that they are part of the same hierarchy.</span></span>

#### <a name="main-differences-with-ef6s-complex-types"></a><span data-ttu-id="e820f-200">Principali differenze rispetto ai i tipi complessi di EF6</span><span class="sxs-lookup"><span data-stu-id="e820f-200">Main differences with EF6's complex types</span></span>

- <span data-ttu-id="e820f-201">La suddivisione di tabelle è facoltativa, ossia si può scegliere di eseguirne il mapping a una tabella separata mantenendo lo stato di tipi di proprietà.</span><span class="sxs-lookup"><span data-stu-id="e820f-201">Table splitting is optional, i.e. they can optionally be mapped to a separate table and still be owned types.</span></span>

- <span data-ttu-id="e820f-202">Possono fare riferimento ad altre entità, ovvero possono fungere da lato dipendente nelle relazioni con altri tipi non di proprietà.</span><span class="sxs-lookup"><span data-stu-id="e820f-202">They can reference other entities (i.e. they can act as the dependent side on relationships to other non-owned types).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="e820f-203">Risorse aggiuntive</span><span class="sxs-lookup"><span data-stu-id="e820f-203">Additional resources</span></span>

- <span data-ttu-id="e820f-204">**Martin Fowler. Modello ValueObject** </span><span class="sxs-lookup"><span data-stu-id="e820f-204">**Martin Fowler. ValueObject pattern** </span></span>\
  <https://martinfowler.com/bliki/ValueObject.html>

- <span data-ttu-id="e820f-205">**Eric Evans. Domain-Driven Design (Progettazione basata su domini): Tackling Complexity in the Heart of Software.** (Gestire le complessità nel software)</span><span class="sxs-lookup"><span data-stu-id="e820f-205">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software.**</span></span> <span data-ttu-id="e820f-206">(Libro. Include una trattazione sugli oggetti valore) </span><span class="sxs-lookup"><span data-stu-id="e820f-206">(Book; includes a discussion of value objects) </span></span>\
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- <span data-ttu-id="e820f-207">**Vaughn Vernon. Implementing Domain-Driven Design (Implementazione della progettazione basata su domini).**</span><span class="sxs-lookup"><span data-stu-id="e820f-207">**Vaughn Vernon. Implementing Domain-Driven Design.**</span></span> <span data-ttu-id="e820f-208">(Libro. Include una trattazione sugli oggetti valore) </span><span class="sxs-lookup"><span data-stu-id="e820f-208">(Book; includes a discussion of value objects) </span></span>\
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- <span data-ttu-id="e820f-209">**Proprietà shadow** </span><span class="sxs-lookup"><span data-stu-id="e820f-209">**Shadow Properties** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/shadow-properties](/ef/core/modeling/shadow-properties)

- <span data-ttu-id="e820f-210">**Complex types and/or value objects (Tipi complessi e/o oggetti valore)** .</span><span class="sxs-lookup"><span data-stu-id="e820f-210">**Complex types and/or value objects**.</span></span> <span data-ttu-id="e820f-211">Discussione nel repository GitHub di EF Core (scheda Issues) </span><span class="sxs-lookup"><span data-stu-id="e820f-211">Discussion in the EF Core GitHub repo (Issues tab) </span></span>\
  <https://github.com/aspnet/EntityFramework/issues/246>

- <span data-ttu-id="e820f-212">**ValueObject.cs.**</span><span class="sxs-lookup"><span data-stu-id="e820f-212">**ValueObject.cs.**</span></span> <span data-ttu-id="e820f-213">Classe oggetti valore di base in eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="e820f-213">Base value object class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs>

- <span data-ttu-id="e820f-214">**Address class (Classe di indirizzi).**</span><span class="sxs-lookup"><span data-stu-id="e820f-214">**Address class.**</span></span> <span data-ttu-id="e820f-215">Classe oggetti valore di esempio in eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="e820f-215">Sample value object class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs>

> [!div class="step-by-step"]
> <span data-ttu-id="e820f-216">[Precedente](seedwork-domain-model-base-classes-interfaces.md)
> [Successivo](enumeration-classes-over-enum-types.md)</span><span class="sxs-lookup"><span data-stu-id="e820f-216">[Previous](seedwork-domain-model-base-classes-interfaces.md)
[Next](enumeration-classes-over-enum-types.md)</span></span>