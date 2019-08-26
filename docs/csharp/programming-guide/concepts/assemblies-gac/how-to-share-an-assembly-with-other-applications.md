---
title: 'Procedura: Condividere un assembly con altre applicazioni (C#)'
ms.date: 07/20/2015
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: 954db3fe139ff307386fc182dbf16c60ce86bd30
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595739"
---
# <a name="how-to-share-an-assembly-with-other-applications-c"></a>Procedura: Condividere un assembly con altre applicazioni (C#)
Gli assembly possono essere privati o condivisi. Per impostazione predefinita, i programmi più semplici sono costituiti da un assembly privato perché non sono destinati ad essere usati in altre applicazioni.  
  
 Per condividerlo con altre applicazioni, un assembly deve essere inserito nella [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).  
  
### <a name="sharing-an-assembly"></a>Condivisione di un assembly  
  
1. Creare l'assembly. Per altre informazioni, vedere [Creazione degli assembly](../../../../framework/app-domains/create-assemblies.md).  
  
2. Assegnare all'assembly un nome sicuro. Per altre informazioni, vedere [Procedura: Firmare un assembly con un nome sicuro](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
3. Assegnare all'assembly le informazioni sulla versione. Per altre informazioni, vedere [Controllo delle versioni degli assembly](../../../../framework/app-domains/assembly-versioning.md).  
  
4. Aggiungere l'assembly alla Global Assembly Cache. Per altre informazioni, vedere [Procedura: Installare un assembly nella Global Assembly Cache](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).  
  
5. Accedere ai tipi contenuti nell'assembly da altre applicazioni. Per altre informazioni, vedere [Procedura: Aggiungere un riferimento a un assembly con nome sicuro](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md).  
  
## <a name="see-also"></a>Vedere anche

- [Guida per programmatori C#](../../index.md)
- [Programmazione con gli assembly](../../../../framework/app-domains/programming-with-assemblies.md)
