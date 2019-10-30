---
title: <bindingExtensions>
ms.date: 03/30/2017
ms.assetid: 8373f94d-d095-486f-8f1e-4ac2f72b58c7
ms.openlocfilehash: bd6aeb32e0994bceb9e56bcb1c6267f4cb64a5a4
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039149"
---
# <a name="bindingextensions"></a><span data-ttu-id="dae6d-101">\<bindingExtensions ></span><span class="sxs-lookup"><span data-stu-id="dae6d-101">\<bindingExtensions></span></span>

<span data-ttu-id="dae6d-102">Questa sezione consente l'uso di un'associazione definita dall'utente dal file di configurazione di un computer o di un'applicazione.</span><span class="sxs-lookup"><span data-stu-id="dae6d-102">This section enables the use of a user defined binding from a machine or application configuration file.</span></span> <span data-ttu-id="dae6d-103">È possibile aggiungere un binding definito dall'utente a questa raccolta usando la parola chiave `add` e impostando l'attributo `type` dell'elemento su un'associazione definita dall'utente e anche l'attributo `name` sul nome dell'associazione definita dall'utente.</span><span class="sxs-lookup"><span data-stu-id="dae6d-103">You can add a user defined binding to this collection by using the `add` keyword, and setting the `type` attribute of the element to a user defined binding, as well as the `name` attribute to the name of the user defined binding.</span></span>

<span data-ttu-id="dae6d-104">Le estensioni dell'associazione consentono di creare associazioni definite dall'utente da usare come parte di una configurazione di endpoint.</span><span class="sxs-lookup"><span data-stu-id="dae6d-104">Binding extensions enable the user to create user-defined bindings for use as part an endpoint configuration.</span></span> <span data-ttu-id="dae6d-105">A livello di programmazione, un'estensione di associazione è un tipo che implementa la classe astratta <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="dae6d-105">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.Binding>.</span></span>

<span data-ttu-id="dae6d-106">Nell'esempio seguente viene utilizzato l'elemento `add`, nonché l'attributo `name` per aggiungere un'estensione di associazione alla sezione `bindingExtensions` del file di configurazione:</span><span class="sxs-lookup"><span data-stu-id="dae6d-106">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingExtensions` section of the configuration file:</span></span>

```xml
<system.serviceModel>
  <extensions>
    <bindingExtensions>
      <add name="MyBinding"
           type="Microsoft.ServiceModel.Samples.MyBinding, MyBinding,
                 Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
    </bindingExtensions>
  </extensions>
</system.serviceModel>
```

<span data-ttu-id="dae6d-107">Per aggiungere capacità di configurazione all'elemento, è necessario scrivere e registrare un elemento `bindingSection`.</span><span class="sxs-lookup"><span data-stu-id="dae6d-107">To add configuration abilities to the element, the user needs to write and register a `bindingSection` element.</span></span> <span data-ttu-id="dae6d-108">Per altre informazioni a tal proposito, vedere la documentazione di <xref:System.Configuration>.</span><span class="sxs-lookup"><span data-stu-id="dae6d-108">For more information on this, see the <xref:System.Configuration> documentation.</span></span>

<span data-ttu-id="dae6d-109">Dopo la definizione dell'elemento e del relativo tipo di configurazione, l'estensione può essere usata come parte di un endpoint, come illustrato nell'esempio seguente:</span><span class="sxs-lookup"><span data-stu-id="dae6d-109">After the element and its configuration type are defined, the extension can be used as part of an endpoint as shown in the following example:</span></span>

```xml
<services>
  <service name="MyService">
    <endpoint address="myAddress"
              binding="MyBinding" />
  </service>
</services>
```

## <a name="see-also"></a><span data-ttu-id="dae6d-110">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="dae6d-110">See also</span></span>

- [<span data-ttu-id="dae6d-111">Estensione delle associazioni</span><span class="sxs-lookup"><span data-stu-id="dae6d-111">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
