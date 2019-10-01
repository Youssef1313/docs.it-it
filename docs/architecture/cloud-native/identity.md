---
title: identità
description: Architettura di app .NET cloud native per Azure | Identità
ms.date: 09/23/2019
ms.openlocfilehash: 4cc7c04bf323d2589777df466321f6801f511b6f
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183049"
---
# <a name="identity"></a><span data-ttu-id="7c53e-103">identità</span><span class="sxs-lookup"><span data-stu-id="7c53e-103">Identity</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="7c53e-104">Per la maggior parte delle applicazioni software è necessario conoscere l'utente o il processo che li chiama.</span><span class="sxs-lookup"><span data-stu-id="7c53e-104">Most software applications need to have some knowledge of the user or process that is calling them.</span></span> <span data-ttu-id="7c53e-105">L'utente o il processo che interagisce con un'applicazione è noto come entità di sicurezza e il processo di autenticazione e autorizzazione di tali entità è noto come gestione delle identità o semplicemente come *identità*.</span><span class="sxs-lookup"><span data-stu-id="7c53e-105">The user or process interacting with an application is known as a security principal, and the process of authenticating and authorizing these principals is known as identity management, or simply *identity*.</span></span> <span data-ttu-id="7c53e-106">Le applicazioni semplici possono includere tutta la loro gestione delle identità all'interno dell'applicazione, ma questo approccio non si adatta perfettamente a molte applicazioni e a molti tipi di entità di sicurezza.</span><span class="sxs-lookup"><span data-stu-id="7c53e-106">Simple applications may include all of their identity management within the application, but this approach doesn't scale well with many applications and many kinds of security principals.</span></span> <span data-ttu-id="7c53e-107">Windows supporta l'utilizzo di Active Directory per fornire l'autenticazione e l'autorizzazione centralizzate.</span><span class="sxs-lookup"><span data-stu-id="7c53e-107">Windows supports the use of Active Directory to provide centralized authentication and authorization.</span></span>

<!-- (insert figure showing Windows AD auth model) -->

<span data-ttu-id="7c53e-108">Anche se questa soluzione è efficace all'interno delle reti aziendali, non è progettata per l'uso da parte di utenti o applicazioni che si trovano all'esterno del dominio AD.</span><span class="sxs-lookup"><span data-stu-id="7c53e-108">While this solution is effective within corporate networks, it isn't designed for use by users or applications that are outside of the AD domain.</span></span> <span data-ttu-id="7c53e-109">Con la crescita delle applicazioni basate su Internet e l'aumento delle app native del cloud, i modelli di sicurezza si sono evoluti.</span><span class="sxs-lookup"><span data-stu-id="7c53e-109">With the growth of Internet-based applications and the rise of cloud-native apps, security models have evolved.</span></span>

<span data-ttu-id="7c53e-110">Nel modello di identità nativo del cloud odierno, si presuppone che l'architettura sia distribuita.</span><span class="sxs-lookup"><span data-stu-id="7c53e-110">In today's cloud-native identity model, architecture is assumed to be distributed.</span></span> <span data-ttu-id="7c53e-111">Le app possono essere distribuite ovunque e possono comunicare con altre app ovunque.</span><span class="sxs-lookup"><span data-stu-id="7c53e-111">Apps can be deployed anywhere and may communicate with other apps anywhere.</span></span> <span data-ttu-id="7c53e-112">I client possono comunicare con queste app da qualsiasi luogo e, di fatto, i client possono essere costituiti da qualsiasi combinazione di piattaforme e dispositivi.</span><span class="sxs-lookup"><span data-stu-id="7c53e-112">Clients may communicate with these apps from anywhere, and in fact, clients may consist of any combination of platforms and devices.</span></span> <span data-ttu-id="7c53e-113">Le soluzioni di identità native del Cloud sfruttano gli standard aperti per ottenere l'accesso sicuro alle applicazioni dai client.</span><span class="sxs-lookup"><span data-stu-id="7c53e-113">Cloud-native identity solutions leverage open standards to achieve secure application access from clients.</span></span> <span data-ttu-id="7c53e-114">Questi client vanno da utenti umani su PC o telefoni, ad altre app ospitate ovunque online, a set-top box e dispositivi Internet che eseguono qualsiasi piattaforma software ovunque nel mondo.</span><span class="sxs-lookup"><span data-stu-id="7c53e-114">These clients range from human users on PCs or phones, to other apps hosted anywhere online, to set-top boxes and IOT devices running any software platform anywhere in the world.</span></span>

<span data-ttu-id="7c53e-115">Le moderne soluzioni di identità native del cloud usano in genere i token di accesso emessi da un servizio token di sicurezza/server (STS) a un'entità di sicurezza una volta determinata l'identità.</span><span class="sxs-lookup"><span data-stu-id="7c53e-115">Modern cloud-native identity solutions typically leverage access tokens that are issued by a secure token service/server (STS) to a security principal once their identity is determined.</span></span> <span data-ttu-id="7c53e-116">Il token di accesso, in genere un token JSON Web (JWT), include *attestazioni* sull'entità di sicurezza.</span><span class="sxs-lookup"><span data-stu-id="7c53e-116">The access token, typically a JSON Web Token (JWT), includes *claims* about the security principal.</span></span> <span data-ttu-id="7c53e-117">Queste attestazioni includono almeno l'identità dell'utente, ma possono includere anche altre attestazioni che possono essere utilizzate dalle applicazioni per determinare il livello di accesso per concedere l'entità di protezione.</span><span class="sxs-lookup"><span data-stu-id="7c53e-117">These claims will minimally include the user's identity but may also include additional claims that can be used by applications to determine the level of access to grant the principal.</span></span>

<!-- (insert figure showing basic handshake involving a principal, an STS, and an app) -->

<span data-ttu-id="7c53e-118">In genere, il servizio token di protezione è responsabile solo dell'autenticazione dell'entità.</span><span class="sxs-lookup"><span data-stu-id="7c53e-118">Typically, the STS is only responsible for authenticating the principal.</span></span> <span data-ttu-id="7c53e-119">La determinazione del livello di accesso alle risorse viene lasciata ad altre parti dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="7c53e-119">Determining their level of access to resources is left to other parts of the application.</span></span>

## <a name="references"></a><span data-ttu-id="7c53e-120">Riferimenti</span><span class="sxs-lookup"><span data-stu-id="7c53e-120">References</span></span>

- [<span data-ttu-id="7c53e-121">Piattaforma di identità Microsoft</span><span class="sxs-lookup"><span data-stu-id="7c53e-121">Microsoft identity platform</span></span>](https://docs.microsoft.com/azure/active-directory/develop/)

>[!div class="step-by-step"]
><span data-ttu-id="7c53e-122">[Precedente](azure-monitor.md)
>[Successivo](authentication-authorization.md)</span><span class="sxs-lookup"><span data-stu-id="7c53e-122">[Previous](azure-monitor.md)
[Next](authentication-authorization.md)</span></span>