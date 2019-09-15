---
title: -target (opzioni del compilatore C#)
ms.date: 07/20/2015
f1_keywords:
- /target
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
ms.openlocfilehash: 073660fa732c04cdc987af5617b894a277ebcc0f
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970120"
---
# <a name="-target-c-compiler-options"></a>-target (opzioni del compilatore C#)
L'opzione del compilatore **-target** può essere specificata in una delle quattro forme seguenti:  
  
 [/target:appcontainerexe](./target-appcontainerexe-compiler-option.md)  
 Per creare un file con estensione exe per le applicazioni [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)].  
  
 [/target:exe](./target-exe-compiler-option.md)  
 Per creare un file con estensione exe.  
  
 [/target:library](./target-library-compiler-option.md)  
 Per creare una libreria di codice.  
  
 [/target:module](./target-module-compiler-option.md)  
 Per creare un modulo.  
  
 [/target:winexe](./target-winexe-compiler-option.md)  
 Per creare un programma di Windows.  
  
 [/target:winmdobj](./target-winmdobj-compiler-option.md)  
 Per creare un file con estensione winmdobj intermedio.  
  
 Se non si specifica **-target:module**, **-target** provoca l'inserimento di un manifesto dell'assembly di .NET Framework in un file di output. Per altre informazioni, vedere [assembly in .NET](../../../standard/assembly/index.md) e [attributi comuni](../../programming-guide/concepts/attributes/common-attributes.md).  
  
 Il manifesto dell'assembly viene inserito nel primo file di output con estensione .exe della compilazione o nel primo DLL, se non esiste alcun file di output .exe. Ad esempio, nella riga di comando seguente il manifesto verrà inserito in `1.exe`:  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 Il compilatore crea solo un manifesto dell'assembly per ogni compilazione. Le informazioni su tutti i file in una compilazione vengono inserite nel manifesto dell'assembly. Tutti i file di output, ad eccezione di quelli creati con **-target:module** possono contenere un manifesto dell'assembly. Quando si generano più file di output nella riga di comando, è possibile creare solo un manifesto e deve essere inseriti nel primo file di output specificato nella riga di comando. Indipendentemente da quale sia il primo file di output ( **-target:exe**, **-target:winexe**, **-target:library** o **-target:module**), tutti gli altri file di output generati nella stessa compilazione devono essere moduli ( **-target:module**).  
  
 Se si crea un assembly, è possibile indicare che tutto o parte del codice è conforme a CLS con l'attributo <xref:System.CLSCompliantAttribute>.  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 Per altre informazioni sull'impostazione di questa opzione del compilatore a livello di codice, vedere <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="see-also"></a>Vedere anche

- [Opzioni del compilatore C#](./index.md)
- [Gestione delle proprietà di progetti e soluzioni](/visualstudio/ide/managing-project-and-solution-properties)
- [-subsystemversion (opzioni del compilatore C#)](./subsystemversion-compiler-option.md)
