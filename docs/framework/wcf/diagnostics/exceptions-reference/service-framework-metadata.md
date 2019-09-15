---
title: Metadati del framework dei servizi
ms.date: 03/30/2017
ms.assetid: 76afc73a-0770-4084-93f3-6701a757911e
ms.openlocfilehash: f3e73df54b3389b2c9f27001953be147b27eb6f8
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991208"
---
# <a name="service-framework-metadata"></a>Metadati del framework dei servizi
In questo argomento vengono elencate tutte le eccezioni generate dai metadati del framework dei servizi.  
  
## <a name="exception-list"></a>Elenco delle eccezioni  
  
|Codice risorsa|Stringa di risorsa|  
|-------------------|---------------------|  
|AsyncEndCalledOnWrongChannel|Il metodo End asincrono è stato chiamato sul canale errato.|  
|AsyncEndCalledWithAnIAsyncResult|Il metodo End asincrono è stato chiamato con un IAsyncResult di un metodo Begin diverso.|  
|AttemptedToGetContractTypeForButThatTypeIs1|Tentativo di ottenere il tipo di contratto per l'oggetto specificato. Il tipo non è un ServiceContract e non eredita un ServiceContract.|  
|CannotHaveTwoOperationsWithTheSameName3|Nello stesso contratto non possono essere presenti due operazioni aventi lo stesso nome. I metodi specificati contenuti nel tipo specificato violano questa regola. È possibile cambiare il nome di una delle operazioni modificando il nome del metodo o utilizzando la proprietà Name di OperationContractAttribute.|  
|CannotInheritTwoOperationsWithTheSameName3|Impossibile ereditare due diverse operazioni aventi lo stesso nome. Le operazioni specificate appartenenti ai contratti specificati violano questa regola. È possibile cambiare il nome di una delle operazioni modificando il nome del metodo o utilizzando la proprietà Name di OperationContractAttribute.|  
|CantCreateChannelWithManualAddressing|Impossibile creare il canale per un contratto che richiede un request/reply e un'associazione che a sua volta richiede l'indirizzamento manuale ma supporta solo la comunicazione duplex.|  
|DuplicateBehavior1|Impossibile aggiungere il valore alla raccolta perché quest'ultima contiene già un elemento dello stesso tipo specificato. Questa raccolta supporta solo un'istanza di ogni tipo.|  
|InAContractInheritanceHierarchyIfParentHasCallbackChildMustToo|Poiché per il contratto del servizio di base specificato è stato definito un determinato tipo di contratto di callback, anche per il contratto del servizio derivato specificato occorre definire lo stesso tipo di contratto di callback o un tipo derivato.|  
|InvalidAsyncBeginMethodSignatureForMethod2|Firma non valida del metodo Begin asincrono per il metodo specificato nel ServiceContract del tipo specificato. Il metodo Begin deve accettare un AsyncCallback e un oggetto come ultimi due argomenti e restituire un IAsyncResult.|  
|InvalidAsyncEndMethodSignatureForMethod2|Firma non valida del metodo End asincrono per il metodo specificato nel ServiceContract del tipo specificato. Il metodo End deve accettare un IAsyncResult come ultimo argomento.|  
|MessagePropertiesArraySize0|La matrice passata non dispone di spazio sufficiente per contenere tutte le proprietà incluse nella raccolta.|  
|OneWayAndFaultsIncompatible2|Il metodo specificato nel tipo specificato è contrassegnato IsOneWay=true e dichiara uno o più attributi FaultContractAttribute. I metodi One-way non possono dichiarare attributi FaultContractAttribute. Per risolvere il problema, impostare IsOneWay su False o rimuovere gli attributi FaultContractAttribute.|  
|UnsupportedWSDLOnlyOneMessage|Web Services Description Language non supportato. È supportata solo una parte messaggio per i messaggi di errore. Il messaggio di errore fa riferimento a più di una parte del messaggio. Se si dispone di accesso in modifica al file Web Services Description Language, è possibile risolvere il problema rimuovendo le parti del messaggio in eccesso in modo tale che il messaggio di errore faccia riferimento solo a una parte.|  
|UnsupportedWSDLTheFault|Web Services Description Language non supportato. La parte del messaggio di errore deve far riferimento a un elemento. Questo messaggio di errore non fa riferimento ad alcun elemento. Se si dispone di accesso in modifica al documento Web Services Definition Language, è possibile risolvere il problema facendo riferimento a un elemento dello schema utilizzando l'attributo "element".|  
|WsdlImportErrorDependencyDetail|Errore durante l'importazione dell'entità specificata da cui dipende l'altro valore specificato. Viene specificato anche il valore Xpath.|  
|XsdMissingRequiredAttribute1|L'attributo obbligatorio specificato è mancante.|
