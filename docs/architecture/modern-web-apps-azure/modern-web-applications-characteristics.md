---
title: Caratteristiche delle applicazioni Web moderne
description: Progettare applicazioni Web moderne con ASP.NET Core e Azure | Caratteristiche delle applicazioni Web moderne
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: f4fe18d7361f7d67c29fb7dab53132237f709280
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2019
ms.locfileid: "68672908"
---
# <a name="characteristics-of-modern-web-applications"></a>Caratteristiche delle applicazioni Web moderne

> "… con la progettazione adeguata, i costi delle funzionalità risultano competitivi. Questo approccio è complesso, ma continua a dare risultati positivi".  
> _\- Dennis Ritchie_

Le applicazioni Web moderne devono soddisfare esigenze e aspettative degli utenti sempre più importanti. Oggi le app Web devono essere disponibili 24 ore al giorno, ogni giorno e in qualsiasi parte del mondo e devono poter essere usate su qualsiasi dispositivo o su uno schermo di qualsiasi dimensione. Le applicazioni Web devono essere sicure, flessibili e scalabili, per soddisfare i picchi di richiesta. Scenari sempre più complessi devono essere gestiti con esperienze utente complete, app compilate nel client con JavaScript e in grado di comunicare adeguatamente tramite le API Web.

ASP.NET Core è ottimizzato per le applicazioni Web moderne e gli scenari di hosting nel cloud. Grazie al design modulare della soluzione, le applicazioni dipendono solo dalle funzionalità che effettivamente usano, migliorando la sicurezza e le prestazioni e riducendo i requisiti per la risorsa host.

## <a name="reference-application-eshoponweb"></a>Applicazione di riferimento: eShopOnWeb

Questa guida include un'applicazione di riferimento, _eShopOnWeb_, che dimostra alcune idee e suggerimenti. L'applicazione è un semplice negozio online, nel quale gli utenti possono consultare un catalogo di T-shirt, tazze da caffè e altri articoli di marketing. L'applicazione di riferimento è volutamente semplice, perché sia facile comprenderne il funzionamento.

**Figura 2-1.** eShopOnWeb

![](./media/image2-1.png)

> ### <a name="reference-application"></a>Applicazione di riferimento
>
> - **eShopOnWeb**  
>   <https://github.com/dotnet/eShopOnWeb>

## <a name="cloud-hosted-and-scalable"></a>Ospitato nel cloud e scalabile

Il framework ASP.NET Core è ottimizzato per il cloud (sia pubblico che privato) perché fa un uso ridotto della memoria e garantisce velocità effettive elevate. Il footprint ridotto delle applicazioni ASP.NET Core significa che è possibile ospitarne di più nello stesso componente hardware e ridurre i costi quando si usano servizi di hosting su cloud con il modello di pagamento a consumo. La velocità effettiva superiore consente di raggiungere più clienti da un'applicazione residente in un determinato componente hardware, riducendo ulteriormente gli investimenti in server e infrastrutture di hosting.

## <a name="cross-platform"></a>Multipiattaforma

ASP.NET Core è multipiattaforma e può essere eseguito in Linux, macOS e Windows. Ciò apre molte nuove opzioni per lo sviluppo e la distribuzione di app compilate con ASP.NET Core. I contenitori Docker sia Linux che Windows possono ospitare applicazioni ASP.NET Core e avvalersi così dei vantaggi offerti da [contenitori e microservizi](../microservices/index.md).

## <a name="modular-and-loosely-coupled"></a>Modulare e loosely coupled

I pacchetti NuGet sono perfettamente compatibili in .NET Core e la struttura con molte librerie delle app ASP.NET Core dipende da NuGet. La granularità delle funzionalità garantisce che le app eseguano e distribuiscano solo le funzionalità necessarie, riducendo la superficie di attacco per le vulnerabilità di sicurezza.

ASP.NET Core offre anche il supporto completo per l'[inserimento delle dipendenze](https://deviq.com/dependency-injection/), sia internamente che a livello di applicazione. Le interfacce possono avere più implementazioni, intercambiabili in base alle esigenze. L'inserimento delle dipendenze consente l'accoppiamento debole delle app a tali interfacce, anziché a implementazioni specifiche, semplificandone l'estensione, la gestione e il test.

## <a name="easily-tested-with-automated-tests"></a>Test automatizzati

Le applicazioni ASP.NET Core supportano gli unit test, l'accoppiamento libero e l'inserimento delle dipendenze, pertanto risulta facile sostituire le sezioni dell'infrastruttura che causano problemi con implementazioni fittizie per l'esecuzione di test. ASP.NET Core include anche un TestServer che può essere usato per l'hosting delle app in memoria. I test funzionali possono quindi inoltrare richieste a questo server in memoria, usando l'intero stack dell'applicazione (middleware, routing, binding dei modelli, filtri e così via) e ricevendo una risposta, il tutto in una frazione del tempo che sarebbe necessario per impostare l'hosting dell'app in un server reale e inoltrare richieste attraverso il layer di rete. Questi test sono facili da scrivere e particolarmente utili per le API, che sono sempre più importanti nelle applicazioni Web moderne.

## <a name="traditional-and-spa-behaviors-supported"></a>Supporto di comportamenti tradizionali e delle applicazioni a pagina singola

Le applicazioni Web tradizionali includono comportamenti lato client limitati, ma si basano sul server per tutte le attività di navigazione, query e aggiornamento. Ogni nuova operazione eseguita dall'utente diventa una nuova richiesta Web e richiede un nuovo caricamento completo della pagina nel browser dell'utente finale. I framework Model-View-Controller (MVC , Modello-Visualizzazione-Controller) classici seguono in genere questo approccio, in cui ogni nuova richiesta corrisponde a un'azione del controller diversa che a sua volta interagisce con un modello e restituisce una visualizzazione. Alcune operazioni singole su una determinata pagina possono essere migliorate con la funzionalità AJAX (Asynchronous JavaScript and XML), ma l'architettura complessiva dell'app usa molte visualizzazioni MVC e molti endpoint URL diversi. ASP.NET Core MVC supporta anche Razor Pages, un modo più semplice per organizzare le pagine in stile MVC.

Le applicazioni a pagina singola, al contrario, richiedono un numero molto limitato di caricamenti pagina generati dinamicamente sul lato server. Molte applicazioni a pagina singola vengono inizializzate all'interno di un file HTML statico, che carica le librerie JavaScript necessarie per avviare ed eseguire l'app. Queste app usano in modo intensivo le API Web per ottenere i dati necessari e possono offrire esperienze utente molto più complete.

Molte applicazioni Web presentano una combinazione di comportamenti dell'applicazione Web tradizionale (in genere per il contenuto) e applicazioni a pagina singola (per l'interattività). ASP.NET Core supporta sia MVC (Viste e Pagine) sia le API Web nella stessa applicazione, usando lo stesso set di strumenti e librerie del framework sottostanti.

## <a name="simple-development-and-deployment"></a>Sviluppo e distribuzione facili

È possibile creare applicazioni ASP.NET Core con editor di testo e interfacce della riga di comando semplici oppure con ambienti di sviluppo completi come Visual Studio. In genere le applicazioni monolitiche vengono distribuite a un singolo endpoint. Le distribuzioni possono essere facilmente automatizzate e incluse in una pipeline di integrazione continua (CI, Continuous Integration) e recapito continuo (CD, Continuous Delivery). Windows Azure dispone di supporto integrato sia per gli strumenti CI/CD tradizionali sia per i repository git integrati ed è in grado di distribuire automaticamente gli aggiornamenti completati a un ramo git o un tag specificato.

## <a name="traditional-aspnet-and-web-forms"></a>ASP.NET tradizionale e Web Form

Oltre ad ASP.NET Core, anche ASP.NET 4.x continua a rappresentare una piattaforma solida e affidabile per la compilazione di applicazioni Web. Oltre ai modelli di sviluppo MVC e API Web, ASP.NET supporta Web Form, ideale per lo sviluppo di applicazioni complesse basate sulla pagina e dispone di un ecosistema di componenti di terze parti completo. Windows Azure offre da tempo il supporto completo delle applicazioni ASP.NET 4.x e molti sviluppatori conoscono a fondo questa piattaforma.

> ### <a name="references--modern-web-applications"></a>Riferimenti: applicazioni Web moderne
>
> - **Introduzione a ASP.NET Core**  
>   <https://docs.microsoft.com/aspnet/core/>
> - **Six Key Benefits of ASP.NET Core which make it Different and Better** (Sei vantaggi chiave che fanno di ASP.NET Core una soluzione migliore)  
>   <https://blog.trigent.com/six-key-benefits-of-asp-net-core-1-0-which-make-it-different-better/>
> - **Test e debug in ASP.NET Core**  
>   <https://docs.microsoft.com/aspnet/core/testing/>

>[!div class="step-by-step"]
>[Precedente](index.md)
>[Successivo](choose-between-traditional-web-and-single-page-apps.md)
