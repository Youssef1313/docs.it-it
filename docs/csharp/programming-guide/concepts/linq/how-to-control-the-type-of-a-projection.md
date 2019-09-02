---
title: 'Procedura: Controllare il tipo di una proiezione (C#)'
ms.date: 07/20/2015
ms.assetid: e4db6b7e-4cc9-4c8f-af85-94acf32aa348
ms.openlocfilehash: a44f7616beba3e07f6e44cc279c67468abc779e3
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204098"
---
# <a name="how-to-control-the-type-of-a-projection-c"></a><span data-ttu-id="6557a-102">Procedura: Controllare il tipo di una proiezione (C#)</span><span class="sxs-lookup"><span data-stu-id="6557a-102">How to: Control the Type of a Projection (C#)</span></span>
<span data-ttu-id="6557a-103">Per proiezione si intende il processo in cui un unico set di dati viene accettato e filtrato, ne viene cambiata la forma e persino il tipo.</span><span class="sxs-lookup"><span data-stu-id="6557a-103">Projection is the process of taking one set of data, filtering it, changing its shape, and even changing its type.</span></span> <span data-ttu-id="6557a-104">Le proiezioni vengono eseguite nella maggior parte delle espressioni di query.</span><span class="sxs-lookup"><span data-stu-id="6557a-104">Most query expressions perform projections.</span></span> <span data-ttu-id="6557a-105">Quasi tutte le espressioni di query illustrate in questa sezione restituiscono il tipo <xref:System.Collections.Generic.IEnumerable%601> di <xref:System.Xml.Linq.XElement>, tuttavia è possibile controllare il tipo della proiezione per creare raccolte di altri tipi.</span><span class="sxs-lookup"><span data-stu-id="6557a-105">Most of the query expressions shown in this section evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, but you can control the type of the projection to create collections of other types.</span></span> <span data-ttu-id="6557a-106">In questo argomento viene illustrato come eseguire questa operazione.</span><span class="sxs-lookup"><span data-stu-id="6557a-106">This topic shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6557a-107">Esempio</span><span class="sxs-lookup"><span data-stu-id="6557a-107">Example</span></span>  
 <span data-ttu-id="6557a-108">Nell'esempio seguente viene definito un nuovo tipo `Customer`.</span><span class="sxs-lookup"><span data-stu-id="6557a-108">The following example defines a new type, `Customer`.</span></span> <span data-ttu-id="6557a-109">L'espressione di query crea quindi un'istanza per nuovi oggetti `Customer` nella clausola `Select`.</span><span class="sxs-lookup"><span data-stu-id="6557a-109">The query expression then instantiates new `Customer` objects in the `Select` clause.</span></span> <span data-ttu-id="6557a-110">Il tipo dell'espressione di query diventa quindi <xref:System.Collections.Generic.IEnumerable%601> di `Customer`.</span><span class="sxs-lookup"><span data-stu-id="6557a-110">This causes the type of the query expression to be <xref:System.Collections.Generic.IEnumerable%601> of `Customer`.</span></span>  
  
 <span data-ttu-id="6557a-111">Nell'esempio viene usato il documento XML seguente: [File XML di esempio: clienti e ordini (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="6557a-111">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
```csharp  
public class Customer  
{  
    private string customerID;  
    public string CustomerID{ get{return customerID;} set{customerID = value;}}  
  
    private string companyName;  
    public string CompanyName{ get{return companyName;} set{companyName = value;}}  
  
    private string contactName;  
    public string ContactName { get{return contactName;} set{contactName = value;}}  
  
    public Customer(string customerID, string companyName, string contactName)  
    {  
        CustomerID = customerID;  
        CompanyName = companyName;  
        ContactName = contactName;  
    }  
  
    public override string ToString()  
    {  
        return $"{this.customerID}:{this.companyName}:{this.contactName}";
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        XElement custOrd = XElement.Load("CustomersOrders.xml");  
        IEnumerable<Customer> custList =  
            from el in custOrd.Element("Customers").Elements("Customer")  
            select new Customer(  
                (string)el.Attribute("CustomerID"),  
                (string)el.Element("CompanyName"),  
                (string)el.Element("ContactName")  
            );  
        foreach (Customer cust in custList)  
            Console.WriteLine(cust);  
    }  
}  
```  
  
 <span data-ttu-id="6557a-112">L'output del codice è il seguente:</span><span class="sxs-lookup"><span data-stu-id="6557a-112">This code produces the following output:</span></span>  
  
```output  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="6557a-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6557a-113">See also</span></span>

- <xref:System.Linq.Enumerable.Select%2A>
