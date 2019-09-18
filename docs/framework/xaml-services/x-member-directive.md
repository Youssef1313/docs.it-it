---
title: Direttiva x:Member
ms.date: 03/30/2017
ms.assetid: 4d8394ef-644c-4331-b6c5-be855d392980
ms.openlocfilehash: d3d023873aab2039913a78108440a2e2d4ea77fb
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053735"
---
# <a name="xmember-directive"></a>Direttiva x:Member
Dichiara un membro XAML nel markup.  
  
## <a name="xaml-object-element-usage"></a>Utilizzo della sintassi XAML per gli elementi oggetto  
  
```xaml  
<object x:Class="className">  
  <x:Members>  
    <x:Member Name="propertyName"/>  
    additionalMembers  
  </x:Members>  
</object>  
```  
  
## <a name="xaml-values"></a>Valori XAML  
  
|||  
|-|-|  
|`className`|Nome della classe sottostante o della classe parziale per la produzione XAML.|  
|`memberName`|Nome membro della proprietà da definire.|  
  
## <a name="remarks"></a>Note  
 Nell'implementazione dei servizi XAML di .NET Framework, `x:Member` non dispone di un supporto del tipo diretto, ma è supportato dalla classe <xref:System.Windows.Markup.MemberDefinition>. In un flusso del nodo XAML, un elemento `x:Member` viene rappresentato come membro denominato `Member`, dallo spazio dei nomi XAML del linguaggio XAML. Il membro `Member` contiene gli attributi dichiarati dal markup.  
  
 I significati di `Name` e di `Type` non vengono assegnati a livello di servizi XAML di .NET Framework. Vengono archiviati nel flusso del nodo XAML iniziale come valori di stringa, da interpretare in seguito in base alle regole che potrebbero essere imposte da framework specifici. Il significato potrebbe allinearsi al significato di un nome XAML e di un tipo XAML o potrebbe essere valido solo in un sistema di tipi di supporto, a seconda dell'implementazione.  
  
 Per supportare un utilizzo pratico di `x:Members` come mezzo per specificare le definizioni dei membri nel markup, i membri devono essere associati a una classe che può essere modificata. Il modello designato prevede che `x:Members` esista come membro di un tipo che specifica un oggetto `x:Class`. Tuttavia, il meccanismo per l'associazione di tipi e membri o per la creazione di definizioni dei membri dinamici non è supportato a livello di servizi XAML di .NET Framework. Questo viene lasciato ai singoli framework che dispongono di modelli di applicazione che supportano le definizioni dei membri da XAML. In genere, le azioni di compilazione MSBUILD, che compilano XAML con il markup e lo integrano con il code-behind o creano veri e propri assembly da XAML, sono necessarie per supportare tale funzionalità.  
  
## <a name="xproperty-for-windows-workflow-foundation"></a>x:Property per Windows Workflow Foundation  
 Per Windows Workflow Foundation, `x:Property` definisce i membri di un'attività personalizzata costituita interamente in XAML o i membri dinamici definiti da XAML per ActivityDesigner con code-behind. `x:Class` deve essere specificato anche nell'elemento radice della produzione XAML. Non è un requisito a livello di servizi XAML di .NET Framework, ma diventa un requisito quando la produzione XAML viene caricata dalle azioni di compilazione MSBUILD che supportano attività personalizzate e il codice XAML di Windows Workflow Foundation in generale. Windows Workflow Foundation non usa il nome di tipo XAML puro come valore previsto per l' `x:Property` `Type` attributo e usa invece una convenzione che non è documentata qui. Per ulteriori informazioni, vedere la pagina relativa alla [creazione di DynamicActivity](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).
