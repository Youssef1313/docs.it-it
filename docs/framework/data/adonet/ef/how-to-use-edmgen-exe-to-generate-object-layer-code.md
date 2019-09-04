---
title: 'Procedura: Usare EdmGen.exe per generare codice a livello oggetti'
ms.date: 03/30/2017
ms.assetid: c44d2ebe-f66f-42cb-9741-4a3f0c2dcffb
ms.openlocfilehash: b85bacff093c268cd35dca2ede36e6ceb74ca4d1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251400"
---
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a><span data-ttu-id="b24f6-102">Procedura: Usare EdmGen.exe per generare codice a livello oggetti</span><span class="sxs-lookup"><span data-stu-id="b24f6-102">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>
<span data-ttu-id="b24f6-103">In questo argomento viene illustrato come utilizzare lo strumento [Generatore EDM (EdmGen. exe)](edm-generator-edmgen-exe.md) per generare il codice del livello oggetti in base al file con estensione csdl.</span><span class="sxs-lookup"><span data-stu-id="b24f6-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md) tool to generate object-layer code  based on the .csdl file.</span></span>  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a><span data-ttu-id="b24f6-104">Per generare il codice del livello oggetti per il modello School per un progetto di Visual Basic usando EdmGen.exe</span><span class="sxs-lookup"><span data-stu-id="b24f6-104">To generate object-layer code for the School model for a Visual Basic project using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="b24f6-105">Creare il database School.</span><span class="sxs-lookup"><span data-stu-id="b24f6-105">Create the School database.</span></span> <span data-ttu-id="b24f6-106">Per ulteriori informazioni, vedere [la pagina relativa alla creazione del database di esempio School](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="b24f6-106">For more information, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="b24f6-107">Generare il modello School o ottenere il file School.csdl.</span><span class="sxs-lookup"><span data-stu-id="b24f6-107">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="b24f6-108">Per altre informazioni, vedere [Procedura: Utilizzare EdmGen. exe per generare i file](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)di modello e di mapping.</span><span class="sxs-lookup"><span data-stu-id="b24f6-108">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="b24f6-109">Al prompt dei comandi eseguire il comando seguente senza interruzioni di riga:</span><span class="sxs-lookup"><span data-stu-id="b24f6-109">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a><span data-ttu-id="b24f6-110">Per generare il codice del livello oggetti per il modello School per un progetto di C# usando EdmGen.exe</span><span class="sxs-lookup"><span data-stu-id="b24f6-110">To generate object-layer code for the School model for a C# project using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="b24f6-111">Creare il database School.</span><span class="sxs-lookup"><span data-stu-id="b24f6-111">Create the School database.</span></span> <span data-ttu-id="b24f6-112">Per ulteriori informazioni, vedere [la pagina relativa alla creazione del database di esempio School](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="b24f6-112">For more information, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="b24f6-113">Generare il modello School o ottenere il file School.csdl.</span><span class="sxs-lookup"><span data-stu-id="b24f6-113">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="b24f6-114">Per altre informazioni, vedere [Procedura: Utilizzare EdmGen. exe per generare i file](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)di modello e di mapping.</span><span class="sxs-lookup"><span data-stu-id="b24f6-114">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="b24f6-115">Al prompt dei comandi eseguire il comando seguente senza interruzioni di riga:</span><span class="sxs-lookup"><span data-stu-id="b24f6-115">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration   
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b24f6-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b24f6-116">See also</span></span>

- [<span data-ttu-id="b24f6-117">Modellazione e mapping</span><span class="sxs-lookup"><span data-stu-id="b24f6-117">Modeling and Mapping</span></span>](modeling-and-mapping.md)
- <span data-ttu-id="b24f6-118">[Procedura: Configurare manualmente un progetto di Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b24f6-118">[How to: Manually Configure an Entity Framework Project](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span></span>
- <span data-ttu-id="b24f6-119">[Strumenti di ADO.NET Entity Data Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b24f6-119">[ADO.NET Entity Data Model  Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
- <span data-ttu-id="b24f6-120">[Procedura: Pre-genera viste per migliorare le prestazioni delle query](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b24f6-120">[How to: Pre-Generate Views to Improve Query Performance](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span></span>
- [<span data-ttu-id="b24f6-121">Procedura: Usare EdmGen. exe per generare i file di modello e di mapping</span><span class="sxs-lookup"><span data-stu-id="b24f6-121">How to: Use EdmGen.exe to Generate the Model and Mapping Files</span></span>](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
