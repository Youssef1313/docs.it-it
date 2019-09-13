---
title: 'Procedura: Personalizzare criteri di cache basati sul tempo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- customizing time-based cache policies
- cache [.NET Framework], time-based policies
ms.assetid: 8d84f936-2376-4356-9264-03162e0f9279
ms.openlocfilehash: 5df070bb2cfef42d60247cad39f2a2f76963bae8
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894739"
---
# <a name="how-to-customize-a-time-based-cache-policy"></a><span data-ttu-id="3b9ac-102">Procedura: Personalizzare criteri di cache basati sul tempo</span><span class="sxs-lookup"><span data-stu-id="3b9ac-102">How to: Customize a Time-Based Cache Policy</span></span>
<span data-ttu-id="3b9ac-103">Quando si creano criteri di cache basati sul tempo, è possibile personalizzare il comportamento di memorizzazione nella cache specificando i valori per durata massima, validità minima, obsolescenza massima o data di sincronizzazione della cache.</span><span class="sxs-lookup"><span data-stu-id="3b9ac-103">When creating a time-based cache policy, you can customize caching behavior by specifying values for maximum age, minimum freshness, maximum staleness, or cache synchronization date.</span></span> <span data-ttu-id="3b9ac-104">L'oggetto <xref:System.Net.Cache.HttpRequestCachePolicy> fornisce più costruttori che consentono di specificare le combinazioni valide di questi valori.</span><span class="sxs-lookup"><span data-stu-id="3b9ac-104">The <xref:System.Net.Cache.HttpRequestCachePolicy> object provides several constructors that allow you to specify valid combinations of these values.</span></span>  
  
### <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a><span data-ttu-id="3b9ac-105">Per creare un criterio di cache basato sul tempo che usa una data di sincronizzazione della cache</span><span class="sxs-lookup"><span data-stu-id="3b9ac-105">To create a time-based cache policy that uses a cache synchronization date</span></span>  
  
- <span data-ttu-id="3b9ac-106">Creare un criterio di cache basato sul tempo che usa una data di sincronizzazione della cache passando un oggetto <xref:System.DateTime> al costruttore <xref:System.Net.Cache.HttpRequestCachePolicy>.</span><span class="sxs-lookup"><span data-stu-id="3b9ac-106">Create a time-based cache policy that uses a cache synchronization date by passing a <xref:System.DateTime> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor.</span></span>  
  
    ```csharp  
    public static HttpRequestCachePolicy CreateLastSyncPolicy(DateTime when)  
    {  
        HttpRequestCachePolicy policy =   
            new HttpRequestCachePolicy(when);  
        Console.WriteLine("When: {0}", when);  
        Console.WriteLine(policy.ToString());  
        return policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Function CreateLastSyncPolicy([when] As DateTime) As HttpRequestCachePolicy  
        Dim policy As New HttpRequestCachePolicy([when])  
        Console.WriteLine("When: {0}", [when])  
        Console.WriteLine(policy.ToString())  
        Return policy  
    End Function  
    ```  
  
 <span data-ttu-id="3b9ac-107">L'output è simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="3b9ac-107">The output is similar to the following:</span></span>  
  
```output
When: 1/14/2004 8:07:30 AM  
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a><span data-ttu-id="3b9ac-108">Per creare un criterio di cache basato sul tempo con impostazione della validità minima</span><span class="sxs-lookup"><span data-stu-id="3b9ac-108">To create a time-based cache policy that is based on minimum freshness</span></span>  
  
- <span data-ttu-id="3b9ac-109">Creare un criterio di cache basato sul tempo con impostazione della validità minima specificando <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> come valore del parametro `cacheAgeControl` e passando un oggetto <xref:System.TimeSpan> al costruttore <xref:System.Net.Cache.HttpRequestCachePolicy>.</span><span class="sxs-lookup"><span data-stu-id="3b9ac-109">Create a time-based cache policy that is based on minimum freshness by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> as the `cacheAgeControl` parameter value and passing a <xref:System.TimeSpan> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor.</span></span>  
  
    ```csharp  
    public static HttpRequestCachePolicy CreateMinFreshPolicy(TimeSpan span)  
    {  
        HttpRequestCachePolicy policy =   
            new HttpRequestCachePolicy(HttpCacheAgeControl.MinFresh, span);  
        Console.WriteLine(policy.ToString());  
        return policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Function CreateMinFreshPolicy(span As TimeSpan) As HttpRequestCachePolicy  
        Dim policy As New HttpRequestCachePolicy(HttpCacheAgeControl.MinFresh, span)  
        Console.WriteLine(policy.ToString())  
        Return policy  
    End Function  
    ```  
  
 <span data-ttu-id="3b9ac-110">Per la chiamata seguente:</span><span class="sxs-lookup"><span data-stu-id="3b9ac-110">For the following invocation:</span></span>  
  
```csharp
CreateMinFreshPolicy(new TimeSpan(1,0,0));  
```  

 <span data-ttu-id="3b9ac-111">L'output è:</span><span class="sxs-lookup"><span data-stu-id="3b9ac-111">The output is:</span></span>
  
```output
Level:Default MinFresh:3600  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a><span data-ttu-id="3b9ac-112">Per creare un criterio di cache basato sul tempo con impostazione della validità minima e della durata massima</span><span class="sxs-lookup"><span data-stu-id="3b9ac-112">To create a time-based cache policy that is based on minimum freshness and maximum age</span></span>  
  
- <span data-ttu-id="3b9ac-113">Creare un criterio di cache basato sul tempo con impostazione della validità minima e della durata massima specificando <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> come valore del parametro `cacheAgeControl` e passando due oggetti <xref:System.TimeSpan> al costruttore <xref:System.Net.Cache.HttpRequestCachePolicy>, uno per specificare la durata massima delle risorse e il secondo per specificare la validità minima consentita per un oggetto restituito dalla cache.</span><span class="sxs-lookup"><span data-stu-id="3b9ac-113">Create a time-based cache policy that is based on minimum freshness and maximum age by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> as the `cacheAgeControl` parameter value and passing two <xref:System.TimeSpan> objects to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor, one to specify the maximum age for resources and a second to specify the minimum freshness permitted for an object returned from the cache.</span></span>  
  
    ```csharp  
    public static HttpRequestCachePolicy CreateFreshAndAgePolicy(TimeSpan freshMinimum, TimeSpan ageMaximum)  
    {  
        HttpRequestCachePolicy policy =   
        new HttpRequestCachePolicy(HttpCacheAgeControl.MaxAgeAndMinFresh, ageMaximum, freshMinimum);  
        Console.WriteLine(policy.ToString());  
        return policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Function CreateFreshAndAgePolicy(freshMinimum As TimeSpan, ageMaximum As TimeSpan) As HttpRequestCachePolicy  
        Dim policy As New HttpRequestCachePolicy(HttpCacheAgeControl.MaxAgeAndMinFresh, ageMaximum, freshMinimum)  
        Console.WriteLine(policy.ToString())  
        Return policy  
    End Function  
    ```  
  
 <span data-ttu-id="3b9ac-114">Per la chiamata seguente:</span><span class="sxs-lookup"><span data-stu-id="3b9ac-114">For the following invocation:</span></span>  
  
```csharp
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  

<span data-ttu-id="3b9ac-115">L'output è:</span><span class="sxs-lookup"><span data-stu-id="3b9ac-115">The output is:</span></span>
  
```output
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a><span data-ttu-id="3b9ac-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3b9ac-116">See also</span></span>

- [<span data-ttu-id="3b9ac-117">Gestione della cache per le applicazioni di rete</span><span class="sxs-lookup"><span data-stu-id="3b9ac-117">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [<span data-ttu-id="3b9ac-118">Criteri di cache</span><span class="sxs-lookup"><span data-stu-id="3b9ac-118">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)
- [<span data-ttu-id="3b9ac-119">Criteri di cache basati sulla posizione</span><span class="sxs-lookup"><span data-stu-id="3b9ac-119">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)
- [<span data-ttu-id="3b9ac-120">Criteri di cache basati sull'ora</span><span class="sxs-lookup"><span data-stu-id="3b9ac-120">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)
- [<span data-ttu-id="3b9ac-121">Elemento \<requestCaching> (impostazioni di rete)</span><span class="sxs-lookup"><span data-stu-id="3b9ac-121">\<requestCaching> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
