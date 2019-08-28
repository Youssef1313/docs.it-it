---
title: -refonly (opzioni del compilatore C#)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: eb62f98c5d548fe3583d3422eb7b6020a82c296a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606479"
---
# <a name="-refonly-c-compiler-options"></a>-refonly (opzioni del compilatore C#)

L'opzione **-refonly** indica che l'output primario deve essere un assembly di riferimento, anziché un assembly di implementazione. Il parametro `-refonly` disabilita automaticamente l'output dei file PDB poiché non è possibile eseguire gli assembly di riferimento. Questa opzione corrisponde alla proprietà del progetto [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) di MSBuild.

## <a name="syntax"></a>Sintassi

```console
-refonly
```

## <a name="remarks"></a>Osservazioni

Per gli assembly di soli metadati i corpi di metodo vengono sostituiti con un singolo corpo `throw null`, ma sono inclusi tutti i membri, tranne i tipi anonimi. L'utilizzo di corpi `throw null`, a differenza di nessun corpo, è giustificato dal fatto che PEVerify può essere eseguito e avere esito positivo convalidando la completezza dei metadati.

Gli assembly di riferimento includono un attributo `ReferenceAssembly` al livello assembly. Questo attributo può essere specificato nell'origine, quindi non è necessaria la sintesi da parte del compilatore. A causa di questo attributo, i runtime non caricheranno gli assembly di riferimento per l'esecuzione, che tuttavia possono essere caricati in modalità sola reflection. Gli strumenti che eseguono la reflection sugli assembly devono garantire che vengano caricati gli assembly di riferimento come sola reflection; in caso contrario il runtime visualizzerà un errore di caricamento del tipo.

Gli assembly di riferimento rimuovono ulteriormente i metadati (membri privati) dagli assembly di soli metadati:

- Un assembly di riferimento include solo i riferimenti per i requisiti nella superficie dell'API. L'assembly reale può includere riferimenti aggiuntivi relativi a implementazioni specifiche. Ad esempio, l'assembly di riferimento per `class C { private void M() { dynamic d = 1; ... } }` non fa riferimento ai tipi necessari per `dynamic`.
- I membri-funzione privati (metodi, proprietà ed eventi) vengono rimossi quando la rimozione non impatta in maniera visibile sulla compilazione. Se non esistono attributi <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>, eseguire la stessa operazione per i membri-funzione interni.
- Negli assembly di riferimento vengono tuttavia mantenuti tutti i tipi, inclusi i tipi privati o nidificati. Vengono mantenuti tutti gli attributi, persino quelli interni.
- Vengono mantenuti tutti i metodi virtuali. Vengono mantenute le implementazioni esplicite di interfacce. Vengono mantenuti gli eventi e le proprietà implementati in modo esplicito poiché le relative funzioni di accesso sono virtuali.
- Vengono mantenuti tutti i campi di uno struct. È un candidato per la rifinitura post-C#-7.1.

Le opzioni `-refonly` e [`-refout`](refout-compiler-option.md) si escludono reciprocamente.

## <a name="see-also"></a>Vedere anche

- [Opzioni del compilatore C#](./index.md)
- [Gestione delle proprietà di progetti e soluzioni](/visualstudio/ide/managing-project-and-solution-properties)
