---
title: Chiamata a una funzione di DLL
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged functions, calling
- unmanaged functions
- COM interop, platform invoke
- platform invoke, calling unmanaged functions
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 113646de-7ea0-4f0e-8df0-c46dab3e8733
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b842f44711d38a996b9d710dbe8bd369d30c5443
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/17/2019
ms.locfileid: "71051877"
---
# <a name="calling-a-dll-function"></a>Chiamata a una funzione di DLL
Anche se le chiamate a funzioni di DLL non gestite sono quasi identiche alle chiamate ad altro codice gestito, esistono alcune differenze che possono rendere apparentemente poco chiaro l'uso delle funzioni di DLL. In questa sezione vengono presentati argomenti che descrivono alcuni aspetti meno comuni delle chiamate.  
  
 Le strutture che vengono restituite dalle chiamate platform invoke devono essere tipi di dati contenenti la stessa rappresentazione in codice gestito e non gestito. Questi tipi sono definiti *tipi copiabili da BLT* perché non richiedono la conversione. Vedere [Tipi copiabili e non copiabili da BLT](blittable-and-non-blittable-types.md). Per chiamare una funzione con una struttura non copiabile da BLT come tipo restituito, è possibile definire un tipo di helper copiabile da BLT della stessa dimensione del tipo non copiabile da BLT e convertire i dati dopo la restituzione della funzione.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Passaggio di strutture](passing-structures.md)  
 Identifica le problematiche relative al passaggio di strutture di dati con un layout predefinito.  
  
 [Funzioni di callback](callback-functions.md)  
 Include informazioni di base sulle funzioni di callback.  
  
 [Procedura: Implementare funzioni di callback](how-to-implement-callback-functions.md)  
 Descrive come implementare funzioni di callback nel codice gestito.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Utilizzo di funzioni di DLL non gestite](consuming-unmanaged-dll-functions.md)  
 Descrive come chiamare funzioni di DLL non gestite con platform invoke.  
  
 [Marshalling dei dati con platform invoke](marshaling-data-with-platform-invoke.md)  
 Descrive come dichiarare i parametri dei metodi e passare gli argomenti alle funzioni esportate dalle librerie non gestite.
