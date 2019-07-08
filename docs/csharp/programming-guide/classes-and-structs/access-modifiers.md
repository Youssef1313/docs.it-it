---
title: Modificatori di accesso - Guida per programmatori C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, access modifiers
- access modifiers [C#], about
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
ms.openlocfilehash: 6622612e927b800e1a4769c99df0e2fa7d99a33d
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/07/2019
ms.locfileid: "67609643"
---
# <a name="access-modifiers-c-programming-guide"></a>Modificatori di accesso (Guida per programmatori C#)
Tutti i tipi e i membri dei tipi hanno un livello di accessibilità, che controlla se possono essere usati da altro codice nell'assembly o in assembly di terze parti. È possibile usare i modificatori di accesso seguenti per specificare l'accessibilità di un tipo o di un membro quando viene dichiarato:  
  
 [public](../../../csharp/language-reference/keywords/public.md)  
 Il tipo o il membro è accessibile da altro codice nello stesso assembly o in un altro assembly che vi fa riferimento. 
  
 [private](../../../csharp/language-reference/keywords/private.md)  
 Il tipo o il membro è accessibile solo dal codice nella stessa classe o struct.  
  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 Il tipo o membro è accessibile solo dal codice nella stessa classe o in una classe derivata da tale classe.  
 [internal](../../../csharp/language-reference/keywords/internal.md)  
 Il tipo o il membro è accessibile dal codice nello stesso assembly ma non da un altro assembly.  
  
 [protected internal](../../../csharp/language-reference/keywords/protected-internal.md) Il tipo o il membro è accessibile da qualsiasi codice dell'assembly in cui viene dichiarato o dall'interno di una classe derivata in un altro assembly. 

 [private protected](../../../csharp/language-reference/keywords/private-protected.md) Il tipo o il membro è accessibile solo dall'interno dell'assembly in cui viene dichiarato, dal codice nella stessa classe o in un tipo derivato da tale classe.
  
 L'esempio seguente illustra come specificare i modificatori di accesso in un tipo e in un membro:  
  
 [!code-csharp[csProgGuideObjects#72](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#72)]  
  
 Non tutti i modificatori di accesso possono essere usati da tutti i tipi o membri in tutti i contesti e in alcuni casi l'accessibilità di un membro del tipo è vincolato all'accessibilità del tipo contenitore. Le sezioni seguenti offrono altre informazioni dettagliate sull'accessibilità.  
  
## <a name="class-and-struct-accessibility"></a>Accessibilità di classi e struct  
 Le classi e gli struct dichiarati direttamente all'interno di uno spazio dei nomi (in altre parole, che non sono annidati all'interno di altre classi o struct) possono essere public o internal. Internal è l'opzione predefinita se non viene specificato nessun modificatore di accesso.  
  
 I membri struct, incluse le classi e gli struct annidati, possono essere dichiarati come public, internal o private. I membri struct, incluse le classi e gli struct annidati, possono essere public, protected internal, protected, internal, private protected o private. Il livello di accesso per i membri di classe e per i membri struct, incluse le classi e gli struct annidati, è private per impostazione predefinita. I tipi annidati private non sono accessibili all'esterno del tipo contenitore.  
  
 Le classi derivate non possono avere un'accessibilità maggiore di quella dei tipi di base. In altre parole, non è possibile avere una classe `B` public che deriva da una classe `A` internal. Se questo fosse consentito, avrebbe l'effetto di rendere `A` pubblic, perché tutti i membri protected e internal di `A` sarebbero accessibili dalla classe derivata.  
  
 È possibile abilitare altri assembly specifici per accedere ai tipi internal usando InternalsVisibleToAttribute. Per altre informazioni, vedere [Friend Assemblies](../../../standard/assembly/friend-assemblies.md) (Assembly friend).  
  
## <a name="class-and-struct-member-accessibility"></a>Accessibilità dei membri struct e di classe  
 I membri di classe (inclusi le classi e gli struct annidati) possono essere dichiarati con uno qualsiasi dei sei tipi di accesso. I membri struct non possono essere dichiarati protected perché struct non supporta l'ereditarietà.  
  
 In genere l'accessibilità di un membro non è maggiore dell'accessibilità del tipo contenitore. Un membro public di una classe internal potrebbe tuttavia essere accessibile dall'esterno dell'assembly se il membro implementa metodi di interfaccia o esegue l'override di metodi virtuali definiti in una classe di base public.  
  
 Il tipo di qualsiasi membro che è un campo, proprietà o evento deve essere accessibile almeno quanto il membro stesso. Analogamente, il tipo restituito e i tipi di parametri di qualsiasi membro, che è un metodo, indicizzatore o delegato, devono essere accessibili almeno quanto il membro stesso. Ad esempio, non è possibile avere un metodo `M` public che restituisce una classe `C` a meno che `C` non sia anche public. Analogamente, non è possibile avere una proprietà protected di tipo `A` se `A` è dichiarato come private.  
  
 Gli operatori definiti dall'utente devono sempre essere dichiarati come public e static. Per altre informazioni, vedere [Overload degli operatori](../../../csharp/language-reference/operators/operator-overloading.md).  
  
 I finalizzatori non possono avere modificatori di accessibilità.  
  
 Per impostare il livello di accesso per un membro struct o di classe, aggiungere la parola chiave appropriata alla dichiarazione del membro, come illustrato nell'esempio seguente.  
  
 [!code-csharp[csProgGuideObjects#73](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#73)]  
  
> [!NOTE]
>  Il livello di accessibilità protected internal significa protected O internal, ma non protected E internal. In altre parole, un membro protected internal è accessibile da qualsiasi classe dello stesso assembly, incluse le classi derivate. Per limitare l'accessibilità solo alle classi derivate dello stesso assembly, dichiarare la classe stessa come internal e dichiarare i relativi membri come protected. A partire da C# 7.2, è anche possibile usare il modificatore di accesso private protected per ottenere lo stesso risultato senza dover impostare come interna la classe che lo contiene.  
  
## <a name="other-types"></a>Altri tipi  
 Le interfacce dichiarate direttamente all'interno di uno spazio dei nomi possono essere dichiarate come public o internal e, analogamente a classi e struct, le interfacce vengono impostate a accesso internal. I membri di interfaccia sono sempre public poiché lo scopo di un'interfaccia è abilitare altri tipi ad accedere a una classe o struct. Nessun modificatore di accesso può essere applicato ai membri di interfaccia.  
  
 I membri di enumerazione sono sempre public e non può essere applicato nessun modificatore di accesso.  
  
 I delegati si comportano come classi e struct. Per impostazione predefinita, hanno accesso internal quando dichiarati direttamente all'interno di uno spazio dei nomi e accesso private se annidati.  
  
## <a name="c-language-specification"></a>Specifiche del linguaggio C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Guida per programmatori C#](../../../csharp/programming-guide/index.md)
- [Classi e struct](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Interfacce](../../../csharp/programming-guide/interfaces/index.md)
- [private](../../../csharp/language-reference/keywords/private.md)
- [public](../../../csharp/language-reference/keywords/public.md)
- [internal](../../../csharp/language-reference/keywords/internal.md)
- [protected](../../../csharp/language-reference/keywords/protected.md)
- [protected internal](../../../csharp/language-reference/keywords/protected-internal.md)
- [private protected](../../../csharp/language-reference/keywords/private-protected.md)
- [class](../../../csharp/language-reference/keywords/class.md)
- [struct](../../../csharp/language-reference/keywords/struct.md)
- [interface](../../../csharp/language-reference/keywords/interface.md)
