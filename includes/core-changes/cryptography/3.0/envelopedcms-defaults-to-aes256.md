---
ms.openlocfilehash: f9000b19997201c2d3de0643669f9029ff1ca31c
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567983"
---
### <a name="envelopedcms-defaults-to-aes-256-encryption"></a>Il valore predefinito di EnvelopedCms è AES-256 Encryption

L'algoritmo di crittografia simmetrica predefinito usato da `EnvelopedCms` è stato modificato da TripleDES ad AES-256.

#### <a name="change-description"></a>Descrizione della modifica

In .NET Core Preview 7 e versioni precedenti, quando <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> viene usato per crittografare i dati senza specificare un algoritmo di crittografia simmetrico tramite un overload del costruttore, i dati sono stati crittografati con l'algoritmo TripleDES/3DES/3DEA/DES3-EDE.

A partire da .NET Core 3,0 Preview 8 (tramite la versione 4.6.0 del pacchetto NuGet [System. Security. Cryptography. Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) ), l'algoritmo predefinito è stato modificato in AES-256 per la modernizzazione dell'algoritmo e per migliorare la sicurezza delle opzioni predefinite. Se un certificato del destinatario del messaggio ha una chiave pubblica Diffie-Hellman (non EC), l'operazione di crittografia potrebbe non riuscire con una <xref:System.Security.Cryptography.CryptographicException> a causa delle limitazioni della piattaforma sottostante.

Nell'esempio di codice seguente i dati vengono crittografati con TripleDES se in esecuzione in .NET Core 3,0 Preview 7 o versioni precedenti. Se è in esecuzione in .NET Core 3,0 Preview 8 o versione successiva, viene crittografato con AES-256.

```csharp
EnvelopedCms cms = new EnvelopedCms(content);
cms.Encrypt(recipient);
return cms.Encode();
```

#### <a name="version-introduced"></a>Versione introdotta

3,0 Anteprima 8

#### <a name="recommended-action"></a>Azione consigliata

Se la modifica ha un impatto negativo, è possibile ripristinare la crittografia TripleDES specificando in modo esplicito l'identificatore dell'algoritmo di crittografia in un costruttore <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> che include un parametro di tipo <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>, ad esempio:

```csharp
Oid tripleDesOid = new Oid("1.2.840.113549.3.7", null);
AlgorithmIdentifier tripleDesIdentifier = new AlgorithmIdentifier(tripleDesOid);
EnvelopedCms cms = new EnvelopedCms(content, tripleDesIdentifier);

cms.Encrypt(recipient);
return cms.Encode()l
```

#### <a name="category"></a>Category

Crittografia

#### <a name="affected-apis"></a>API interessate

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.ContentInfo)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor(System.Security.Cryptography.Pkcs.ContentInfo)`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)`

-->
