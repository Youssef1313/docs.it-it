---
title: Programmazione con i domini applicazione e gli assembly
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
- application domains, programming
- programming application domains
ms.assetid: 96d3b8e3-bef8-4da0-9a81-9841e23a94e9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b4f0c2ad1290a7f9cf8d0c43c504a3e0a9628b86
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971918"
---
# <a name="programming-with-application-domains-and-assemblies"></a>Programmazione con i domini applicazione e gli assembly
Gli host come Microsoft Internet Explorer, ASP.NET e la shell di Windows caricano Common Language Runtime in un processo, creano un [dominio dell'applicazione](../../../docs/framework/app-domains/application-domains.md) in tale processo e quindi caricano ed eseguono codice dell'utente in tale dominio dell'applicazione quando eseguono un'applicazione .NET Framework. Nella maggior parte dei casi, non è necessario occuparsi della creazione dei domini dell'applicazione e del caricamento di assembly all'interno degli stessi, perché è l'host di runtime a eseguire tali attività.  
  
 Tuttavia, se si sta creando un'applicazione che ospita Common Language Runtime, strumenti o codice che si vogliono scaricare a livello di codice o componenti modulari che possono essere scaricati e ricaricati in tempo reale, si creano anche domini dell'applicazione personalizzati. Anche se non si sta creando un host di runtime, questa sezione fornisce importanti informazioni su come utilizzare i domini dell'applicazione e gli assembly caricati al loro interno.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Argomenti relativi alle procedure per domini applicazione e assembly](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)  
 Fornisce i collegamenti a tutte le procedure contenute nella documentazione sui concetti relativi alla programmazione con domini dell'applicazione e assembly.  
  
 [Uso dei domini dell'applicazione](../../../docs/framework/app-domains/use.md)  
 Fornisce esempi di creazione, configurazione e uso dei domini dell'applicazione.  
  
 [Programmazione con gli assembly](../../standard/assembly/program.md)  
 Descrive come creare, firmare e impostare attributi sugli assembly.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Creazione di assembly e metodi dinamici](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 Descrive come creare gli assembly dinamici.  
  
 [Assembly in .NET](../../standard/assembly/index.md)  
 Viene fornita una panoramica sui concetti di base relativi agli assembly.  
  
 [Domini dell'applicazione](../../../docs/framework/app-domains/application-domains.md)  
 Viene fornita una panoramica sui concetti di base relativi ai domini applicazione.  
  
 [Panoramica della reflection](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Descrive come usare la classe **Reflection** per ottenere informazioni su un assembly.
