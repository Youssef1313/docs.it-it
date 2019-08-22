---
title: L'uso dell'istanza predefinita di una classe nel costruttore della classe potrebbe generare una chiamata ricorsiva infinita
ms.date: 07/20/2015
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
ms.openlocfilehash: cec3d3d462822ca571cab59a2e4d7e730d2aec46
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664374"
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a><span data-ttu-id="abe20-102">L'uso dell'istanza predefinita di una classe nel costruttore della classe potrebbe generare una chiamata ricorsiva infinita</span><span class="sxs-lookup"><span data-stu-id="abe20-102">Use of Default Instance of a class in the class constructor could lead to infinite recursive call</span></span>
<span data-ttu-id="abe20-103">Nel costruttore della classe è stata usata un'istanza predefinita di una classe.</span><span class="sxs-lookup"><span data-stu-id="abe20-103">A default instance of a class has been used in the constructor of the class.</span></span> <span data-ttu-id="abe20-104">Questo può causare una chiamata ricorsiva infinita, detta anche ciclo infinito.</span><span class="sxs-lookup"><span data-stu-id="abe20-104">This can lead to an infinite recursive call, also known as an infinite loop.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="abe20-105">Per correggere l'errore</span><span class="sxs-lookup"><span data-stu-id="abe20-105">To correct this error</span></span>  
  
- <span data-ttu-id="abe20-106">Rimuovere l'istanza predefinita dal costruttore della classe.</span><span class="sxs-lookup"><span data-stu-id="abe20-106">Remove the default instance from the class constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abe20-107">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="abe20-107">See also</span></span>

- [<span data-ttu-id="abe20-108">Costruttori</span><span class="sxs-lookup"><span data-stu-id="abe20-108">Constructors</span></span>](../programming-guide/concepts/object-oriented-programming.md#constructors)
