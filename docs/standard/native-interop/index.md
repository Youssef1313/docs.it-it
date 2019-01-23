---
title: Interoperabilità nativa - .NET
description: Informazioni su come interagire con i componenti nativi in .NET.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 85a22394c8c59f51f462bc0a2ba6a11265682db3
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416055"
---
# <a name="native-interoperability"></a><span data-ttu-id="39ddb-103">Interoperabilità nativa</span><span class="sxs-lookup"><span data-stu-id="39ddb-103">Native interoperability</span></span>

<span data-ttu-id="39ddb-104">Gli articoli seguenti illustrano i diversi metodi per implementare l'"interoperabilità nativa" in .NET.</span><span class="sxs-lookup"><span data-stu-id="39ddb-104">The following articles show the various ways of doing "native interoperability" in .NET.</span></span>

<span data-ttu-id="39ddb-105">Vari motivi possono rendere necessaria la chiamata del codice nativo:</span><span class="sxs-lookup"><span data-stu-id="39ddb-105">There are a few reasons why you'd want to call into native code:</span></span>

* <span data-ttu-id="39ddb-106">Sistemi operativi con un volume elevato di API che non sono presenti nelle librerie di classi gestite.</span><span class="sxs-lookup"><span data-stu-id="39ddb-106">Operating systems come with a large volume of APIs that aren't present in the managed class libraries.</span></span> <span data-ttu-id="39ddb-107">Un ottimo esempio di questo scenario è l'accesso alle funzioni di gestione dell'hardware o del sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="39ddb-107">A prime example for this scenario would be access to hardware or operating system management functions.</span></span>
* <span data-ttu-id="39ddb-108">Comunicazione con altri componenti che hanno o possono generare ABI di tipo C (ABI native), ad esempio il codice Java esposto tramite [Java Native Interface (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) o qualsiasi altro linguaggio gestito in grado di creare un componente nativo.</span><span class="sxs-lookup"><span data-stu-id="39ddb-108">Communicating with other components that have or can produce C-style ABIs (native ABIs), such as Java code that is exposed via [Java Native Interface (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) or any other managed language that could produce a native component.</span></span>
* <span data-ttu-id="39ddb-109">In Windows la maggior parte del software installato, ad esempio la suite Microsoft Office, registra componenti COM che rappresentano i programmi corrispondenti e consente agli sviluppatori di automatizzarli o di usarli.</span><span class="sxs-lookup"><span data-stu-id="39ddb-109">On Windows, most of the software that gets installed, such as the Microsoft Office suite, registers COM components that represent their programs and allow developers to automate them or use them.</span></span> <span data-ttu-id="39ddb-110">Anche questo richiede interoperabilità nativa.</span><span class="sxs-lookup"><span data-stu-id="39ddb-110">This also requires native interoperability.</span></span>

<span data-ttu-id="39ddb-111">L'elenco sopra riportato non esaurisce tutti i potenziali scenari e situazioni in cui lo sviluppatore vuole, preferisce o deve definire un'interfaccia con i componenti nativi.</span><span class="sxs-lookup"><span data-stu-id="39ddb-111">The previous list doesn't cover all of the potential situations and scenarios in which the developer would want/like/need to interface with native components.</span></span> <span data-ttu-id="39ddb-112">La libreria di classi .NET, ad esempio, usa il supporto per l'interoperabilità nativa per implementare un numero notevole di API, ad esempio il supporto e la manipolazione della console, l'accesso al file system e altro.</span><span class="sxs-lookup"><span data-stu-id="39ddb-112">.NET class library, for instance, uses the native interoperability support to implement a fair number of its APIs, like console support and manipulation, file system access and others.</span></span> <span data-ttu-id="39ddb-113">Tuttavia è importante ricordare che in caso di necessità è disponibile una soluzione alternativa.</span><span class="sxs-lookup"><span data-stu-id="39ddb-113">However, it's important to note that there's an option if needed.</span></span>

> [!NOTE]
> <span data-ttu-id="39ddb-114">La maggior parte degli esempi riportati in questa sezione viene presentata per tutte e tre le piattaforme supportate in .NET Core (Windows, Linux e macOS).</span><span class="sxs-lookup"><span data-stu-id="39ddb-114">Most of the examples in this section will be presented for all three supported platforms for .NET Core (Windows, Linux and macOS).</span></span> <span data-ttu-id="39ddb-115">Per alcuni esempi brevi e illustrativi, tuttavia, verrà presentata solo la versione che usa nomi file ed estensioni Windows, come "dll" per le librerie.</span><span class="sxs-lookup"><span data-stu-id="39ddb-115">However, for some short and illustrative examples, just one sample is shown that uses Windows filenames and extensions (that is, "dll" for libraries).</span></span> <span data-ttu-id="39ddb-116">Questo non significa che le funzionalità illustrate non siano disponibili in Linux o macOS. La scelta dipende solo da motivi di praticità.</span><span class="sxs-lookup"><span data-stu-id="39ddb-116">This doesn't mean that those features aren't available on Linux or macOS, it was done merely for convenience sake.</span></span>

## <a name="see-also"></a><span data-ttu-id="39ddb-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="39ddb-117">See also</span></span>

- [<span data-ttu-id="39ddb-118">Platform Invoke (P/Invoke)</span><span class="sxs-lookup"><span data-stu-id="39ddb-118">Platform Invoke (P/Invoke)</span></span>](pinvoke.md)
- [<span data-ttu-id="39ddb-119">Marshalling dei tipi</span><span class="sxs-lookup"><span data-stu-id="39ddb-119">Type marshalling</span></span>](type-marshalling.md)