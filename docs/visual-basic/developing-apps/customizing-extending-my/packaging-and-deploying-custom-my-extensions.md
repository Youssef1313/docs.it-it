---
title: Packaging and deploying custom My extensions
ms.date: 08/14/2018
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
ms.openlocfilehash: a2e2a6705fb3d8d4424d46d96bbf49b41e1414af
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330253"
---
# <a name="package-and-deploy-custom-my-extensions-visual-basic"></a><span data-ttu-id="5322a-102">Package and deploy custom My extensions (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5322a-102">Package and deploy custom My extensions (Visual Basic)</span></span>

<span data-ttu-id="5322a-103">Visual Basic provides an easy way for you to deploy your custom `My` namespace extensions by using Visual Studio templates.</span><span class="sxs-lookup"><span data-stu-id="5322a-103">Visual Basic provides an easy way for you to deploy your custom `My` namespace extensions by using Visual Studio templates.</span></span> <span data-ttu-id="5322a-104">If you are creating a project template for which your `My` extensions are an integral part of the new project type, you can just include your custom `My` extension code with the project when you export the template.</span><span class="sxs-lookup"><span data-stu-id="5322a-104">If you are creating a project template for which your `My` extensions are an integral part of the new project type, you can just include your custom `My` extension code with the project when you export the template.</span></span> <span data-ttu-id="5322a-105">For more information about exporting project templates, see [How to: Create Project Templates](/visualstudio/ide/how-to-create-project-templates).</span><span class="sxs-lookup"><span data-stu-id="5322a-105">For more information about exporting project templates, see [How to: Create Project Templates](/visualstudio/ide/how-to-create-project-templates).</span></span>

<span data-ttu-id="5322a-106">If your custom `My` extension is in a single code file, you can export the file as an item template that users can add to any type of Visual Basic project.</span><span class="sxs-lookup"><span data-stu-id="5322a-106">If your custom `My` extension is in a single code file, you can export the file as an item template that users can add to any type of Visual Basic project.</span></span> <span data-ttu-id="5322a-107">You can then customize the item template to enable additional capabilities and behavior for your custom `My` extension in a Visual Basic project.</span><span class="sxs-lookup"><span data-stu-id="5322a-107">You can then customize the item template to enable additional capabilities and behavior for your custom `My` extension in a Visual Basic project.</span></span> <span data-ttu-id="5322a-108">Those capabilities include the following:</span><span class="sxs-lookup"><span data-stu-id="5322a-108">Those capabilities include the following:</span></span>

- <span data-ttu-id="5322a-109">Allowing users to manage your custom `My` extension from the **My Extensions** page of the Visual Basic Project Designer.</span><span class="sxs-lookup"><span data-stu-id="5322a-109">Allowing users to manage your custom `My` extension from the **My Extensions** page of the Visual Basic Project Designer.</span></span>

- <span data-ttu-id="5322a-110">Automatically adding your custom `My` extension when a reference to a specified assembly is added to a project.</span><span class="sxs-lookup"><span data-stu-id="5322a-110">Automatically adding your custom `My` extension when a reference to a specified assembly is added to a project.</span></span>

- <span data-ttu-id="5322a-111">Hiding the `My` extension item template in the **Add Item** dialog box so that it is not included in the list of project items.</span><span class="sxs-lookup"><span data-stu-id="5322a-111">Hiding the `My` extension item template in the **Add Item** dialog box so that it is not included in the list of project items.</span></span>

<span data-ttu-id="5322a-112">This topic discusses how to package a custom `My` extension as a hidden item template that can be managed from the **My Extensions** page of the Visual Basic Project Designer.</span><span class="sxs-lookup"><span data-stu-id="5322a-112">This topic discusses how to package a custom `My` extension as a hidden item template that can be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="5322a-113">The custom `My` extension can also be added automatically when a reference to a specified assembly is added to a project.</span><span class="sxs-lookup"><span data-stu-id="5322a-113">The custom `My` extension can also be added automatically when a reference to a specified assembly is added to a project.</span></span>

## <a name="create-a-my-namespace-extension"></a><span data-ttu-id="5322a-114">Create a My namespace extension</span><span class="sxs-lookup"><span data-stu-id="5322a-114">Create a My namespace extension</span></span>

<span data-ttu-id="5322a-115">The first step in creating a deployment package for a custom `My` extension is to create the extension as a single code file.</span><span class="sxs-lookup"><span data-stu-id="5322a-115">The first step in creating a deployment package for a custom `My` extension is to create the extension as a single code file.</span></span> <span data-ttu-id="5322a-116">For details and guidance about how to create a custom `My` extension, see [Extending the My Namespace in Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="5322a-116">For details and guidance about how to create a custom `My` extension, see [Extending the My Namespace in Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).</span></span>

## <a name="export-a-my-namespace-extension-as-an-item-template"></a><span data-ttu-id="5322a-117">Export a My namespace extension as an item template</span><span class="sxs-lookup"><span data-stu-id="5322a-117">Export a My namespace extension as an item template</span></span>

<span data-ttu-id="5322a-118">After you have a code file that includes your `My` namespace extension, you can export the code file as a Visual Studio item template.</span><span class="sxs-lookup"><span data-stu-id="5322a-118">After you have a code file that includes your `My` namespace extension, you can export the code file as a Visual Studio item template.</span></span> <span data-ttu-id="5322a-119">For instructions on how to export a file as a Visual Studio item template, see [How to: Create Item Templates](/visualstudio/ide/how-to-create-item-templates).</span><span class="sxs-lookup"><span data-stu-id="5322a-119">For instructions on how to export a file as a Visual Studio item template, see [How to: Create Item Templates](/visualstudio/ide/how-to-create-item-templates).</span></span>

> [!NOTE]
> <span data-ttu-id="5322a-120">If your `My` namespace extension has a dependency on a particular assembly, you can customize your item template to automatically install your `My` namespace extension when a reference to that assembly is added.</span><span class="sxs-lookup"><span data-stu-id="5322a-120">If your `My` namespace extension has a dependency on a particular assembly, you can customize your item template to automatically install your `My` namespace extension when a reference to that assembly is added.</span></span> <span data-ttu-id="5322a-121">As a result, you will want to exclude that assembly reference when you export the code file as a Visual Studio item template.</span><span class="sxs-lookup"><span data-stu-id="5322a-121">As a result, you will want to exclude that assembly reference when you export the code file as a Visual Studio item template.</span></span>

## <a name="customize-the-item-template"></a><span data-ttu-id="5322a-122">Customize the item template</span><span class="sxs-lookup"><span data-stu-id="5322a-122">Customize the item template</span></span>

<span data-ttu-id="5322a-123">You can enable your item template to be managed from the **My Extensions** page of the Visual Basic Project Designer.</span><span class="sxs-lookup"><span data-stu-id="5322a-123">You can enable your item template to be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="5322a-124">You can also enable the item template to be added automatically when a reference to a specified assembly is added to a project.</span><span class="sxs-lookup"><span data-stu-id="5322a-124">You can also enable the item template to be added automatically when a reference to a specified assembly is added to a project.</span></span> <span data-ttu-id="5322a-125">To enable these customizations, you will add a new file, called the CustomData file, to your template, and then add a new element to the XML in your .vstemplate file.</span><span class="sxs-lookup"><span data-stu-id="5322a-125">To enable these customizations, you will add a new file, called the CustomData file, to your template, and then add a new element to the XML in your .vstemplate file.</span></span>

### <a name="add-the-customdata-file"></a><span data-ttu-id="5322a-126">Add the CustomData file</span><span class="sxs-lookup"><span data-stu-id="5322a-126">Add the CustomData file</span></span>

<span data-ttu-id="5322a-127">The CustomData file is a text file that has a file name extension of .CustomData (the file name can be set to any value meaningful to your template) and that contains XML.</span><span class="sxs-lookup"><span data-stu-id="5322a-127">The CustomData file is a text file that has a file name extension of .CustomData (the file name can be set to any value meaningful to your template) and that contains XML.</span></span> <span data-ttu-id="5322a-128">The XML in the CustomData file instructs Visual Basic to include your `My` extension when users use the **My Extensions** page of the Visual Basic Project Designer.</span><span class="sxs-lookup"><span data-stu-id="5322a-128">The XML in the CustomData file instructs Visual Basic to include your `My` extension when users use the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="5322a-129">You can optionally add the <`AssemblyFullName>` attribute to your CustomData file XML.</span><span class="sxs-lookup"><span data-stu-id="5322a-129">You can optionally add the <`AssemblyFullName>` attribute to your CustomData file XML.</span></span> <span data-ttu-id="5322a-130">This instructs Visual Basic to automatically install your custom `My` extension when a reference to a particular assembly is added to the project.</span><span class="sxs-lookup"><span data-stu-id="5322a-130">This instructs Visual Basic to automatically install your custom `My` extension when a reference to a particular assembly is added to the project.</span></span> <span data-ttu-id="5322a-131">You can use any text editor or XML editor to create the CustomData file, and then add it to your item template's compressed folder (.zip file).</span><span class="sxs-lookup"><span data-stu-id="5322a-131">You can use any text editor or XML editor to create the CustomData file, and then add it to your item template's compressed folder (.zip file).</span></span>

<span data-ttu-id="5322a-132">For example, the following XML shows the contents of a CustomData file that will add the template item to the My Extensions folder of a Visual Basic project when a reference to the Microsoft.VisualBasic.PowerPacks.Vs.dll assembly is added to the project.</span><span class="sxs-lookup"><span data-stu-id="5322a-132">For example, the following XML shows the contents of a CustomData file that will add the template item to the My Extensions folder of a Visual Basic project when a reference to the Microsoft.VisualBasic.PowerPacks.Vs.dll assembly is added to the project.</span></span>

```xml
<VBMyExtensionTemplate
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"
    Version="1.0.0.0"
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"
/>
```

<span data-ttu-id="5322a-133">The CustomData file contains a <`VBMyExtensionTemplate>` element that has attributes as listed in the following table.</span><span class="sxs-lookup"><span data-stu-id="5322a-133">The CustomData file contains a <`VBMyExtensionTemplate>` element that has attributes as listed in the following table.</span></span>

|<span data-ttu-id="5322a-134">Attributo</span><span class="sxs-lookup"><span data-stu-id="5322a-134">Attribute</span></span>|<span data-ttu-id="5322a-135">Descrizione</span><span class="sxs-lookup"><span data-stu-id="5322a-135">Description</span></span>|
|---|---|
|`ID`|<span data-ttu-id="5322a-136">Obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="5322a-136">Required.</span></span> <span data-ttu-id="5322a-137">A unique identifier for the extension.</span><span class="sxs-lookup"><span data-stu-id="5322a-137">A unique identifier for the extension.</span></span> <span data-ttu-id="5322a-138">If the extension that has this ID has already been added to the project, the user will not be prompted to add it again.</span><span class="sxs-lookup"><span data-stu-id="5322a-138">If the extension that has this ID has already been added to the project, the user will not be prompted to add it again.</span></span>|
|`Version`|<span data-ttu-id="5322a-139">Obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="5322a-139">Required.</span></span> <span data-ttu-id="5322a-140">A version number for the item template.</span><span class="sxs-lookup"><span data-stu-id="5322a-140">A version number for the item template.</span></span>|
|`AssemblyFullName`|<span data-ttu-id="5322a-141">Parametro facoltativo.</span><span class="sxs-lookup"><span data-stu-id="5322a-141">Optional.</span></span> <span data-ttu-id="5322a-142">Nome dell'assembly.</span><span class="sxs-lookup"><span data-stu-id="5322a-142">An assembly name.</span></span> <span data-ttu-id="5322a-143">When a reference to this assembly is added to the project, the user will be prompted to add the `My` extension from this item template.</span><span class="sxs-lookup"><span data-stu-id="5322a-143">When a reference to this assembly is added to the project, the user will be prompted to add the `My` extension from this item template.</span></span>|

### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a><span data-ttu-id="5322a-144">Add the \<CustomDataSignature> element to the .vstemplate file</span><span class="sxs-lookup"><span data-stu-id="5322a-144">Add the \<CustomDataSignature> element to the .vstemplate file</span></span>

<span data-ttu-id="5322a-145">To identify your Visual Studio item template as a `My` namespace extension, you must also modify the .vstemplate file for your item template.</span><span class="sxs-lookup"><span data-stu-id="5322a-145">To identify your Visual Studio item template as a `My` namespace extension, you must also modify the .vstemplate file for your item template.</span></span> <span data-ttu-id="5322a-146">You must add a `<CustomDataSignature>` element to the `<TemplateData>` element.</span><span class="sxs-lookup"><span data-stu-id="5322a-146">You must add a `<CustomDataSignature>` element to the `<TemplateData>` element.</span></span> <span data-ttu-id="5322a-147">The `<CustomDataSignature>` element must contain the text `Microsoft.VisualBasic.MyExtension`, as shown in the following example.</span><span class="sxs-lookup"><span data-stu-id="5322a-147">The `<CustomDataSignature>` element must contain the text `Microsoft.VisualBasic.MyExtension`, as shown in the following example.</span></span>

```xml
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>
```

<span data-ttu-id="5322a-148">You cannot modify files in a compressed folder (.zip file) directly.</span><span class="sxs-lookup"><span data-stu-id="5322a-148">You cannot modify files in a compressed folder (.zip file) directly.</span></span> <span data-ttu-id="5322a-149">You must copy the .vstemplate file from the compressed folder, modify it, and then replace the .vstemplate file in the compressed folder with your updated copy.</span><span class="sxs-lookup"><span data-stu-id="5322a-149">You must copy the .vstemplate file from the compressed folder, modify it, and then replace the .vstemplate file in the compressed folder with your updated copy.</span></span>

<span data-ttu-id="5322a-150">The following example shows the contents of a .vstemplate file that has the `<CustomDataSignature>` element added.</span><span class="sxs-lookup"><span data-stu-id="5322a-150">The following example shows the contents of a .vstemplate file that has the `<CustomDataSignature>` element added.</span></span>

```xml
<VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">
  <TemplateData>
    <DefaultName>MyCustomExtensionModule.vb</DefaultName>
    <Name>MyPrinterInfo</Name>
    <Description>Custom My Extensions Item Template</Description>
    <ProjectType>VisualBasic</ProjectType>
    <SortOrder>10</SortOrder>
    <Icon>__TemplateIcon.ico</Icon>
    <CustomDataSignature      >Microsoft.VisualBasic.MyExtension</CustomDataSignature>
  </TemplateData>
  <TemplateContent>
    <References />
    <ProjectItem SubType="Code"
                 TargetFileName="$fileinputname$.vb"
                 ReplaceParameters="true"
     >MyCustomExtensionModule.vb</ProjectItem>
  </TemplateContent>
</VSTemplate>
```

## <a name="install-the-template"></a><span data-ttu-id="5322a-151">Install the template</span><span class="sxs-lookup"><span data-stu-id="5322a-151">Install the template</span></span>

<span data-ttu-id="5322a-152">To install the template, you can copy the compressed folder ( *.zip* file) to the Visual Basic item templates folder.</span><span class="sxs-lookup"><span data-stu-id="5322a-152">To install the template, you can copy the compressed folder (*.zip* file) to the Visual Basic item templates folder.</span></span> <span data-ttu-id="5322a-153">By default, user item templates are located in *%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ItemTemplates\Visual Basic*.</span><span class="sxs-lookup"><span data-stu-id="5322a-153">By default, user item templates are located in *%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ItemTemplates\Visual Basic*.</span></span> <span data-ttu-id="5322a-154">Alternatively, you can publish the template as a Visual Studio Installer ( *.vsi*) file.</span><span class="sxs-lookup"><span data-stu-id="5322a-154">Alternatively, you can publish the template as a Visual Studio Installer (*.vsi*) file.</span></span>

## <a name="see-also"></a><span data-ttu-id="5322a-155">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5322a-155">See also</span></span>

- [<span data-ttu-id="5322a-156">Estensione dello spazio dei nomi My in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5322a-156">Extending the My Namespace in Visual Basic</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)
- [<span data-ttu-id="5322a-157">Estensione del modello di applicazione Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5322a-157">Extending the Visual Basic Application Model</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
- [<span data-ttu-id="5322a-158">Personalizzazione degli oggetti disponibili in My</span><span class="sxs-lookup"><span data-stu-id="5322a-158">Customizing Which Objects are Available in My</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [<span data-ttu-id="5322a-159">Pagina Estensioni My, Creazione progetti</span><span class="sxs-lookup"><span data-stu-id="5322a-159">My Extensions Page, Project Designer</span></span>](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
