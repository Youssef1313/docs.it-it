---
title: Interfaccia ISymUnmanagedMethod
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod
helpviewer_keywords:
- ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: f204d74c-cc79-4092-83bb-60654be95649
topic_type:
- apiref
ms.openlocfilehash: 1d3ccb2265f056d5776199d997dc067c8d5513e5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448793"
---
# <a name="isymunmanagedmethod-interface"></a>Interfaccia ISymUnmanagedMethod
Rappresenta un metodo all'interno dell'archivio dei simboli. Questa interfaccia consente di accedere solo agli attributi relativi ai simboli di un metodo, anziché agli attributi correlati al tipo.  
  
## <a name="methods"></a>Metodi  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Metodo GetNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getnamespace-method.md)|Ottiene lo spazio dei nomi in cui è definito il metodo.|  
|[Metodo GetOffset](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getoffset-method.md)|Restituisce l'offset all'interno di questo metodo che corrisponde a una posizione specificata all'interno di un documento.|  
|[Metodo GetParameters](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getparameters-method.md)|Ottiene i parametri per questo metodo.|  
|[Metodo GetRanges](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getranges-method.md)|Data una posizione in un documento, restituisce una matrice di coppie di offset di inizio e di fine che corrispondono agli intervalli di MSIL (Microsoft Intermediate Language) che la posizione copre all'interno di questo metodo.|  
|[Metodo GetRootScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getrootscope-method.md)|Ottiene l'ambito lessicale radice all'interno di questo metodo. Questo ambito racchiude l'intero metodo.|  
|[Metodo GetScopeFromOffset](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getscopefromoffset-method.md)|Ottiene l'ambito lessicale di maggiore inclusione all'interno di questo metodo che racchiude l'offset specificato.|  
|[Metodo GetSequencePointCount](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepointcount-method.md)|Ottiene il conteggio dei punti di sequenza all'interno di questo metodo.|  
|[Metodo GetSequencePoints](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepoints-method.md)|Ottiene tutti i punti di sequenza all'interno di questo metodo.|  
|[Metodo GetSourceStartEnd](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsourcestartend-method.md)|Ottiene le posizioni del documento iniziale e finale per l'origine di questo metodo.|  
|[Metodo GetToken](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-gettoken-method.md)|Restituisce il token di metadati per questo metodo.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Vedere anche

- [Interfacce dell'archivio simboli di diagnostica](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
