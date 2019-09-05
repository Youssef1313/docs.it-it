---
title: 'Procedura: Usare EdmGen.exe per convalidare file di modello e di mapping'
ms.date: 03/30/2017
ms.assetid: 2641906a-971a-4d0b-8aee-13fabc02a1cc
ms.openlocfilehash: 4495ff3c5d55779e9db113a2a59361b643841382
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251384"
---
# <a name="how-to-use-edmgenexe-to-validate-model-and-mapping-files"></a><span data-ttu-id="514d6-102">Procedura: Usare EdmGen.exe per convalidare file di modello e di mapping</span><span class="sxs-lookup"><span data-stu-id="514d6-102">How to: Use EdmGen.exe to Validate Model and Mapping Files</span></span>
<span data-ttu-id="514d6-103">In questo argomento viene illustrato come utilizzare lo strumento [Generatore EDM (EdmGen. exe)](edm-generator-edmgen-exe.md) per convalidare i file di modello e di mapping.</span><span class="sxs-lookup"><span data-stu-id="514d6-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md) tool to validate the model and mapping files.</span></span> <span data-ttu-id="514d6-104">Per ulteriori informazioni, vedere [Entity Data Model](../entity-data-model.md).</span><span class="sxs-lookup"><span data-stu-id="514d6-104">For more information, see [Entity Data Model](../entity-data-model.md).</span></span>  
  
### <a name="to-validate-the-school-model-using-edmgenexe"></a><span data-ttu-id="514d6-105">Per convalidare il modello School usando EdmGen.exe</span><span class="sxs-lookup"><span data-stu-id="514d6-105">To validate the School model using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="514d6-106">Creare il database School.</span><span class="sxs-lookup"><span data-stu-id="514d6-106">Create the School database.</span></span> <span data-ttu-id="514d6-107">Per ulteriori informazioni, vedere [la pagina relativa alla creazione del database di esempio School](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="514d6-107">For more information, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="514d6-108">Generare il modello School.</span><span class="sxs-lookup"><span data-stu-id="514d6-108">Generate the School model.</span></span> <span data-ttu-id="514d6-109">Per altre informazioni, vedere [Procedura: Utilizzare EdmGen. exe per generare i file](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)di modello e di mapping.</span><span class="sxs-lookup"><span data-stu-id="514d6-109">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="514d6-110">Al prompt dei comandi eseguire il comando seguente senza interruzioni di riga:</span><span class="sxs-lookup"><span data-stu-id="514d6-110">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:ValidateArtifacts /inssdl:.\School.ssdl /inmsl:.\School.msl /incsdl:.\School.csdl  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="514d6-111">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="514d6-111">See also</span></span>

- <span data-ttu-id="514d6-112">[Procedura: Configurare manualmente un progetto di Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="514d6-112">[How to: Manually Configure an Entity Framework Project](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span></span>
- <span data-ttu-id="514d6-113">[Strumenti Entity Data Model ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="514d6-113">[ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
- <span data-ttu-id="514d6-114">[Procedura: Pre-genera viste per migliorare le prestazioni delle query](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="514d6-114">[How to: Pre-Generate Views to Improve Query Performance](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span></span>
- [<span data-ttu-id="514d6-115">Procedura: Usare EdmGen. exe per generare il codice del livello oggetti</span><span class="sxs-lookup"><span data-stu-id="514d6-115">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>](how-to-use-edmgen-exe-to-generate-object-layer-code.md)
