---
title: Attestazioni e token
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], and tokens
ms.assetid: eff167f3-33f8-483d-a950-aa3e9f97a189
ms.openlocfilehash: 6d148bca56cfa4e28c2d3e6c0d9fcb564861a7cd
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663465"
---
# <a name="claims-and-tokens"></a>Attestazioni e token

Questo argomento descrive i vari tipi di attestazione che Windows Communication Foundation (WCF) Crea dai token predefiniti supportati.

È possibile esaminare le attestazioni di una credenziale client usando le classi <xref:System.IdentityModel.Claims.ClaimSet> e <xref:System.IdentityModel.Claims.Claim>. L'elemento `ClaimSet` contiene una raccolta di oggetti `Claim`. Ogni oggetto `Claim` comprende i membri seguenti:

- La proprietà <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> restituisce un URI (Uniform Resource Identifier) che specifica il tipo di attestazione che viene creato. Ad esempio, un tipo di attestazione può essere un'identificazione personale di un certificato, nel qual caso l'URI è `http://schemas.microsoft.com/ws/20005/05/identity/claims/thumprint`.

- La proprietà <xref:System.IdentityModel.Claims.Claim.Right%2A> restituisce un URI che specifica il diritto dell'attestazione. I diritti predefiniti si trovano nella classe <xref:System.IdentityModel.Claims.Rights> (<xref:System.IdentityModel.Claims.Rights.Identity%2A>, <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>).

- La proprietà <xref:System.IdentityModel.Claims.Claim.Resource%2A> restituisce la risorsa associata all'attestazione.

Ogni classe <xref:System.IdentityModel.Claims.ClaimSet> ha anche una proprietà <xref:System.IdentityModel.Claims.ClaimSet.Issuer%2A> che rappresenta la classe <xref:System.IdentityModel.Claims.ClaimSet> dell'elemento `Issuer`.

## <a name="windows-accounts"></a>Account di Windows

Quando una credenziale client esegue il mapping a un account utente Windows, la classe <xref:System.IdentityModel.Claims.ClaimSet> risultante ha i valori seguenti:

- `Issuer` è il valore restituito dalla proprietà Windows statica della classe <xref:System.IdentityModel.Claims.ClaimSet>.

- Le attestazioni incluse nella raccolta sono:

  - Una classe <xref:System.IdentityModel.Claims.Claim> con un valore SID <xref:System.IdentityModel.Claims.Claim.ClaimType%2A>, un valore <xref:System.IdentityModel.Claims.Claim.Right%2A> della proprietà `Identity` e una proprietà <xref:System.IdentityModel.Claims.Claim.Resource%2A> che restituisce il valore SID effettivo. Un SID è un valore univoco che il controller di dominio invia a ogni utente. Il SID viene usato per identificare l'utente nelle interazioni con la protezione di Windows.

  - Una classe <xref:System.IdentityModel.Claims.Claim> con un valore SID <xref:System.IdentityModel.Claims.Claim.ClaimType%2A>, un valore <xref:System.IdentityModel.Claims.Claim.Right%2A> della proprietà `PossessProperty` e una proprietà <xref:System.IdentityModel.Claims.Claim.Resource%2A> del valore SID.

  - Una classe <xref:System.IdentityModel.Claims.Claim> con una proprietà <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> con valore <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, una proprietà <xref:System.IdentityModel.Claims.Claim.Right%2A> con valore `PossessProperty` e una proprietà <xref:System.IdentityModel.Claims.Claim.Resource%2A> della stringa che contiene il nome utente (ad esempio, "MYMACHINE\Bob").

  - Attestazioni SID aggiuntive con la proprietà <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> per i vari gruppi ai quali appartiene l'utente.

## <a name="certificates"></a>Certificati

Quando la credenziale client è un certificato, la classe <xref:System.IdentityModel.Claims.ClaimSet> risultante ha i valori seguenti:

- Per i certificati autocertificati, l'elemento `Issuer` è la classe <xref:System.IdentityModel.Claims.ClaimSet> stessa. La classe <xref:System.IdentityModel.Claims.ClaimSet> restituisce una proprietà <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> con valore <xref:System.IdentityModel.Claims.ClaimTypes.Thumbprint%2A>, una proprietà <xref:System.IdentityModel.Claims.Claim.Right%2A> con valore `Identity` e un valore della proprietà <xref:System.IdentityModel.Claims.Claim.Resource%2A> che corrisponde a una matrice <xref:System.Byte> contenente l'identificazione personale del certificato.

- Per un certificato emesso da un'autorità di certificazione, l'emittente corrisponde al valore `ClaimSet` che rappresenta il certificato dell'autorità di certificazione.

- Gli elementi `Claims` presenti nella raccolta includono:

  - Un elemento `Claim` con una proprietà `ClaimType` con valore Thumbprint, una proprietà `Right` con valore PossessProperty e una proprietà `Resource` che corrisponde a una matrice di byte contenente l'identificazione personale del certificato.

  - Attestazioni PossessProperty aggiuntive di vario tipo, tra cui X500DistinguishedName, Dns, Name, Upn e Rsa rappresentano le varie proprietà del certificato. La risorsa per l'attestazione Rsa è la chiave pubblica associata al certificato. **Nota** in cui il tipo di credenziale client è un certificato che il servizio esegue il mapping a un Windows dell'account, due `ClaimSet` gli oggetti vengono generati. Il primo contiene tutte le attestazioni relative all'account di Windows e il secondo contiene tutte le attestazioni relative al certificato.

## <a name="user-namepassword"></a>Nome utente/Password

Quando la credenziale client è un nome utente/password (o equivalente) che non esegue il mapping a un account di Windows, l'oggetto `ClaimSet` risultante viene pubblicato dalla proprietà <xref:System.IdentityModel.Claims.ClaimSet.System%2A> statica della classe `ClaimSet`. Il `ClaimSet` contiene un `Identity` di attestazione di tipo <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A> la cui risorsa è il nome utente del client fornito. Un'attestazione corrispondente ha una proprietà `Right` di tipo `PossessProperty`.

## <a name="rsa-keys"></a>Chiavi RSA

Quando viene usata una chiave RSA non associata a un certificato, l'oggetto risultante `ClaimSet` è autocertificato e contiene un `Identity` di attestazione di tipo <xref:System.IdentityModel.Claims.ClaimTypes.Rsa%2A> cui risorsa è la chiave RSA. Un'attestazione corrispondente ha una proprietà `Right` di tipo `PossessProperty`.

## <a name="saml"></a>SAML

Quando il client esegue l'autenticazione con un token SAML (Security Assertions Markup Language), l'oggetto `ClaimSet` risultante viene emesso dall'entità che ha firmato il token SAML, in genere il certificato del servizio token di sicurezza (STS) che ha emesso il token SAML. `ClaimSet` contiene le varie attestazioni presenti nel token SAML. Se il token SAML contiene una classe `SamlSubject` con un nome `null`, verranno create un'attestazione `Identity` di tipo <xref:System.IdentityModel.Claims.ClaimTypes.NameIdentifier%2A> e un tipo di risorsa <xref:System.IdentityModel.Tokens.SamlNameIdentifierClaimResource>.

## <a name="identity-claims-and-servicesecuritycontextisanonymous"></a>Attestazioni d'identità e ServiceSecurityContext.IsAnonymous

Se nessuna del `ClaimSet` gli oggetti risultanti dalle credenziali client contengano un'attestazione con un `Right` dei `Identity,` il <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> restituisce proprietà `true`. Se sono presenti una o più di tali attestazioni, la proprietà `IsAnonymous` restituisce `false`.

## <a name="see-also"></a>Vedere anche

- <xref:System.IdentityModel.Claims.ClaimSet>
- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- [Gestione delle attestazioni e dell'autorizzazione con il modello di identità](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
