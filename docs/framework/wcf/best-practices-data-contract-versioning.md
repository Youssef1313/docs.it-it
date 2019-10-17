---
title: 'Procedure consigliate: controllo delle versioni del contratto dati'
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- service contracts
- best practices [WCF], data contract versioning
- Windows Communication Foundation, data contracts
ms.assetid: bf0ab338-4d36-4e12-8002-8ebfdeb346cb
ms.openlocfilehash: 4d500c37efa4a90e24b06cd2e886147e1f159d4e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320784"
---
# <a name="best-practices-data-contract-versioning"></a>Procedure consigliate: controllo delle versioni del contratto dati
In questo argomento vengono elencate le procedure consigliate per la creazione di contratti dati che possono evolvere facilmente nel tempo. Per ulteriori informazioni sui contratti dati, vedere gli argomenti relativi all' [utilizzo di contratti dati](./feature-details/using-data-contracts.md).  
  
## <a name="note-on-schema-validation"></a>Note sulla convalida dello schema  
 Quando si discute il controllo delle versioni dei contratti dati, è importante notare che lo schema del contratto dati esportato da Windows Communication Foundation (WCF) non dispone di alcun supporto per il controllo delle versioni, tranne per il fatto che gli elementi sono contrassegnati come facoltativi per impostazione predefinita.  
  
 Di conseguenza, anche lo scenario di controllo delle versioni più comune, quale l'aggiunta di un nuovo membro dati, non può essere implementato agevolmente rispetto a un schema specificato. Le versioni più recenti di un contratto dati (ad esempio con un nuovo membro dati) non vengono convalidate usando lo schema obsoleto.  
  
 Esistono tuttavia molti scenari in cui non è richiesta una totale conformità allo schema. Molte piattaforme di servizi Web, tra cui WCF e i servizi Web XML creati tramite ASP.NET, non eseguono la convalida dello schema per impostazione predefinita e pertanto tollerano elementi aggiuntivi non descritti dallo schema. Se si usano tali piattaforme, l'implementazione di molti scenari di controllo delle versioni risulta più semplice.  
  
 Sono pertanto disponibili due set di linee guida per il controllo delle versioni di un contratto dati: un set per gli scenari in cui la rigorosa validità dello schema è importante e un altro set per gli scenari in cui non lo è.  
  
## <a name="versioning-when-schema-validation-is-required"></a>Controllo delle versioni quando la convalida dello schema è necessaria  
 Se la rigorosa validità dello schema è necessaria in tutte le direzioni (da nuovo a vecchio e da vecchio a nuovo), i contratti dati devono essere considerati immutabili. Se occorre eseguire il controllo delle versioni, è necessario creare un nuovo contratto dati, con un nome o uno spazio dei nomi diverso e il contratto di servizio che usa il tipo di dati deve essere sottoposto al controllo delle versioni.  
  
 Ad esempio, un contratto di servizio che elabora un ordine di acquisto denominato `PoProcessing` con un'operazione `PostPurchaseOrder` accetta un parametro basato su un contratto dati `PurchaseOrder`. Se è necessario modificare il contratto `PurchaseOrder`, creare un nuovo contratto dati, ovvero `PurchaseOrder2`, che includa le modifiche. È quindi necessario gestire il controllo delle versioni a livello del contratto di servizio. Ad esempio, creando un'operazione `PostPurchaseOrder2` che accetta il parametro `PurchaseOrder2` o creando un contratto di servizio `PoProcessing2` in cui l'operazione `PostPurchaseOrder` accetta un contratto dati `PurchaseOrder2`.  
  
 Si noti che se altri contratti dati fanno riferimento alle modifiche apportate ai contratti dati, queste si estenderanno anche a livello del modello di servizio. Ad esempio, si supponga che nello scenario precedente il contratto dati `PurchaseOrder` non abbia bisogno di modifiche. Tale contratto tuttavia contiene un membro dati di un contratto dati `Customer` che, a sua volta, contiene un membro dati del contratto dati `Address` che deve essere modificato. In tal caso, è necessario creare un contratto dati `Address2` con le modifiche necessarie, un contratto dati `Customer2` contenente il membro dati `Address2` e un contratto dati `PurchaseOrder2` contenente il membro dati `Customer2`. Come nel caso precedente, anche il contratto di servizio deve essere sottoposto al controllo delle versioni.  
  
 Sebbene in questi esempi i nomi sono stati modificati (aggiungendo "2"), è consigliabile modificare gli spazi dei nomi anziché i nomi, aggiungendo un numero di versione o una data ai nuovi spazi dei nomi. Ad esempio, il contratto dati `http://schemas.contoso.com/2005/05/21/PurchaseOrder` diventerebbe il contratto dati `http://schemas.contoso.com/2005/10/14/PurchaseOrder`.  
  
 Per ulteriori informazioni, vedere procedure consigliate: [controllo delle versioni dei servizi](service-versioning.md).  
  
 In alcuni casi è necessario garantire la rigorosa conformità allo schema per i messaggi inviati dall'applicazione, ma non è possibile basarsi sui messaggi in ingresso per essere rigorosamente conformi allo schema. In questo caso, vi è il rischio che un messaggio in ingresso contenga dati estranei. I valori estranei vengono archiviati e restituiti da WCF e pertanto generano messaggi non validi per lo schema. Per evitare questo problema, è necessario disattivare la funzionalità di creazione di sequenze di andata e ritorno. È possibile ottenere questo risultato in due modi.  
  
- Non implementare l'interfaccia <xref:System.Runtime.Serialization.IExtensibleDataObject> sui tipi usati.  
  
- Applicare un attributo <xref:System.ServiceModel.ServiceBehaviorAttribute> al contratto di servizio con la proprietà <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> impostata su `true`.  
  
 Per ulteriori informazioni sul round trip, vedere [contratti dati compatibili con](./feature-details/forward-compatible-data-contracts.md)le versioni successive.  
  
## <a name="versioning-when-schema-validation-is-not-required"></a>Controllo delle versioni quando la convalida dello schema non è necessaria  
 La rigorosa conformità allo schema è richiesta raramente. Molte piattaforme tollerano elementi aggiuntivi non descritti da un schema. Fino a quando questo è tollerato, è possibile usare il set completo di funzionalità descritte nei contratti dati di [controllo delle versioni](./feature-details/data-contract-versioning.md) dei contratti dati e di [dati compatibili con](./feature-details/forward-compatible-data-contracts.md) le versioni successive. Di seguito sono riportate alcune linee guida consigliate.  
  
 È necessario attenersi esattamente ad alcune linee guida per inviare versioni nuove di un tipo quando ne è previsto uno precedente o inviare un tipo obsoleto quando ne è previsto uno nuovo. Altre linee guida non sono strettamente necessarie, ma sono elencate perché potrebbero essere interessate dagli sviluppi futuri del controllo delle versioni sullo schema.  
  
1. Non controllare le versioni dei contratti dati in base all'ereditarietà del tipo. Per creare versioni più recenti, modificare il contratto dati su un tipo esistente o creare un nuovo tipo non correlato.  
  
2. L'utilizzo dell'ereditarietà insieme ai contratti dati è consentito, purché l'ereditarietà non venga usata come un meccanismo di controllo delle versioni e vengano seguite determinate regole. Se un tipo deriva da un determinato tipo di base, non è possibile fare in modo che derivi da un tipo di base diverso in una versione futura (a meno che abbia lo stesso contratto dati). Esiste un'unica eccezione a questa condizione: è possibile inserire un tipo nella gerarchia tra un tipo di contratto dati e il relativo tipo di base, ma solo se non contiene membri dati con nomi identici a quelli di altri membri in qualsiasi possibile versione degli altri tipi nella gerarchia. In generale, l'uso di membri dati con nomi identici a livelli diversi della stessa gerarchia di ereditarietà può causare gravi problemi di controllo delle versioni e deve essere evitato.  
  
3. A partire dalla prima versione di un contratto dati, implementare sempre <xref:System.Runtime.Serialization.IExtensibleDataObject> per attivare le sequenze di andata e ritorno. Per altre informazioni, vedere [Contratti di dati compatibili con versioni successive](./feature-details/forward-compatible-data-contracts.md). Se sono state rilasciate una o più versioni di un tipo senza implementare questa interfaccia, è necessario implementarla nella prossima versione del tipo.  
  
4. Nelle versioni più recenti, non modificare il nome o lo spazio dei nomi del contratto dati. Se si modifica il nome o lo spazio dei nomi del tipo sottostante il contratto dati, assicurarsi di mantenere il nome e lo spazio dei nomi del contratto dati usando i meccanismi adatti, ad esempio la proprietà <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> di <xref:System.Runtime.Serialization.DataContractAttribute>. Per ulteriori informazioni sulla denominazione, vedere [nomi di contratto dati](./feature-details/data-contract-names.md).  
  
5. Nelle versioni più recenti, non modificare i nomi di qualsiasi membro dati. Se si modifica il nome del campo, della proprietà o dell'evento sottostante il membro dati, usare la proprietà `Name` di <xref:System.Runtime.Serialization.DataMemberAttribute> per mantenere il nome del membro dati esistente.  
  
6. Nelle versioni più recenti, non modificare il tipo di qualsiasi campo, proprietà o evento sottostante un membro dati in modo tale che il contratto dati risultante per quel membro dati venga modificato. Tenere presente che i tipi di interfaccia sono equivalenti a <xref:System.Object> per l'identificazione del contratto dati previsto.  
  
7. Nelle versioni più recenti, non modificare l'ordine dei membri dati esistenti impostando la proprietà <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> dell'attributo <xref:System.Runtime.Serialization.DataMemberAttribute>.  
  
8. Nelle versioni più recenti, possono essere aggiunti nuovi membri dati. Questa operazione deve essere eseguita osservando le regole seguenti:  
  
    1. La proprietà <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> deve essere sempre impostata sul valore predefinito `false`.  
  
    2. Se un valore predefinito pari a `null` o a zero per il membro non è accettabile, è necessario fornire un metodo di callback mediante <xref:System.Runtime.Serialization.OnDeserializingAttribute> per garantire un'impostazione predefinita adeguata qualora il membro non sia presente nel flusso in ingresso. Per altre informazioni sul callback, vedere [callback di serializzazione a tolleranza di versione](./feature-details/version-tolerant-serialization-callbacks.md).  
  
    3. È necessario utilizzare la proprietà <xref:System.Runtime.Serialization.DataMemberAttribute.Order?displayProperty=nameWithType> per assicurarsi che tutti i membri dati appena aggiunti vengano visualizzati dopo i membri dati esistenti. La procedura consigliata per eseguire questa operazione consiste nel verificare che la proprietà `Order` non sia impostata per alcun membro dati nella prima versione del contratto dati. La proprietà `Order` di tutti i membri dati aggiunti nella versione 2 del contratto dati deve essere impostata su 2. La proprietà `Order` di tutti i membri dati aggiunti nella versione 3 del contratto dati deve essere impostata su 3 e così via. È consentito avere più membri dati impostati sullo stesso numero di `Order`.  
  
9. Non rimuovere i membri dati nelle versioni più recenti, anche se per la proprietà <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> è stato lasciato il valore predefinito `false` nelle versioni precedenti.  
  
10. Non modificare la proprietà `IsRequired` di qualsiasi membro dati esistente nel passaggio da una versione all'altra.  
  
11. Per i membri dati richiesti (dove `IsRequired` è `true`), non modificare la proprietà `EmitDefaultValue` nel passaggio da una versione all'altra.  
  
12. Non tentare di creare gerarchie di controlli delle versioni sottoposte a branching. Ovvero, deve esistere sempre un percorso, in almeno una direzione, da una qualsiasi versione a un'altra usando solo le modifiche consentite dalle presenti linee guida.  
  
     Ad esempio, se la versione 1 di un contratto dati Person contiene solo il membro dati Name, non è necessario creare la versione 2a del contratto aggiungendo solo il membro Age e la versione 2b aggiungendo solo il membro Address. Il passaggio dalla versione 2a alla versione 2b coinvolgerebbe la rimozione di Age e l'aggiunta di Address; nella direzione opposta sarebbe necessario rimuovere Address e aggiungere Age. La rimozione di membri non è consentita dalle presenti linee guida.  
  
13. In genere, è sconsigliabile creare nuovi sottotipi dei tipi di contratto dati esistenti in una nuova versione dell'applicazione. Analogamente, non è consigliabile creare nuovi contratti dati da usare al posto dei membri dati dichiarati come Object o come tipi di interfaccia. La creazione di queste nuove classi è consentita solo quando si è sicuri di poter aggiungere i tipi nuovi all'elenco dei tipi noti di tutte le istanze dell'applicazione precedente. Ad esempio, nella versione 1 dell'applicazione è possibile avere il tipo di contratto dati LibraryItem con i sottotipi del contratto dati Book e Newspaper. Pertanto, nell'elenco dei tipi noti di LibraryItem sarebbero presenti Book e Newspaper. Si supponga di aggiungere un tipo Magazine alla versione 2 che è un sottotipo di LibraryItem. Se si invia un'istanza di Magazine dalla versione 2 alla versione 1, il contratto dati di Magazine non sarà presente nell'elenco dei tipi noti e verrà generata un'eccezione.  
  
14. Non è consigliabile aggiungere o rimuovere membri di enumerazione tra diverse versioni. È inoltre sconsigliabile rinominare i membri di enumerazione, a meno che non si utilizzi la proprietà Name sull'attributo `EnumMemberAttribute` per mantenere gli stessi nomi nel modello del contratto dati.  
  
15. Le raccolte sono intercambiabili nel modello del contratto dati, come descritto in [tipi di raccolta nei contratti dati](./feature-details/collection-types-in-data-contracts.md). Ciò assicura un elevato grado di flessibilità. Tuttavia, accertarsi di non modificare inavvertitamente un tipo di raccolta in modo non intercambiabile da una versione all'altra. Ad esempio, non modificare una raccolta non personalizzata (ovvero senza l'attributo `CollectionDataContractAttribute`) in una raccolta personalizzata o una raccolta personalizzata in una non personalizzata. Inoltre, non impostare le proprietà su `CollectionDataContractAttribute` da versione a versione. L'unica modifica consentita consiste nell'aggiunta di una proprietà Name o Namespace se il nome o lo spazio dei nomi del tipo di raccolta sottostante sono stati modificati ed è necessario uniformare il nome e lo spazio dei nomi del contratto dati a quelli di una versione precedente.  
  
 Alcune delle linee guida elencate possono essere ignorate senza conseguenze se si verificano alcune circostanze speciali. Accertarsi di aver compreso tutti gli aspetti della serializzazione, della deserializzazione e dei meccanismi dello schema coinvolti prima di allontanarsi dalle linee guida.  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>
- <xref:System.Runtime.Serialization.IExtensibleDataObject>
- <xref:System.ServiceModel.ServiceBehaviorAttribute>
- <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A>
- <xref:System.Runtime.Serialization.ExtensionDataObject>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- [Uso di contratti di dati](./feature-details/using-data-contracts.md)
- [Controllo delle versioni dei contratti di dati](./feature-details/data-contract-versioning.md)
- [Nomi di contratto di dati](./feature-details/data-contract-names.md)
- [Contratti di dati compatibili con versioni successive](./feature-details/forward-compatible-data-contracts.md)
- [Callback di serializzazione a tolleranza di versione](./feature-details/version-tolerant-serialization-callbacks.md)
