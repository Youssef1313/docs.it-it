---
title: "Procedura: Creare eccezioni definite dall'utente con messaggi di eccezione localizzati"
description: Informazioni su come creare eccezioni definite dall'utente con messaggi di eccezione localizzati
author: Youssef1313
ms.date: 09/13/2019
ms.openlocfilehash: 453e332541628770932da2a6802fdcaee5211a84
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141530"
---
# <a name="how-to-create-user-defined-exceptions-with-localized-exception-messages"></a>Procedura: Creare eccezioni definite dall'utente con messaggi di eccezione localizzati

In questo articolo si apprenderà come creare eccezioni definite dall'utente ereditate dalla classe <xref:System.Exception> di base con messaggi di eccezione localizzati tramite assembly satellite.

## <a name="create-custom-exceptions"></a>Creare eccezioni personalizzate

.NET contiene molte eccezioni diverse che è possibile usare. Tuttavia, in alcuni casi in cui nessuno soddisfa le proprie esigenze, è possibile creare eccezioni personalizzate.

Si supponga di voler creare un `StudentNotFoundException` contenente una proprietà `StudentName`.
Per creare un'eccezione personalizzata, attenersi alla procedura seguente:

1. Creare una classe serializzabile che erediti da <xref:System.Exception>. Il nome della classe deve terminare con "Exception":

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception { }
    ```

1. Aggiungere i costruttori predefiniti:

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception
    {
        public StudentNotFoundException() { }

        public StudentNotFoundException(string message)
            : base(message) { }

        public StudentNotFoundException(string message, Exception inner)
            : base(message, inner) { }
    }
    ```

1. Definire le proprietà e i costruttori aggiuntivi:

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception
    {
        public string StudentName { get; }

        public StudentNotFoundException() { }

        public StudentNotFoundException(string message)
            : base(message) { }

        public StudentNotFoundException(string message, Exception inner)
            : base(message, inner) { }

        public StudentNotFoundException(string message, string studentName)
            : this(message)
        {
            StudentName = studentName;
        }
    }
    ```

## <a name="create-localized-exception-messages"></a>Creare messaggi di eccezione localizzati

È stata creata un'eccezione personalizzata, che può essere generata ovunque con codice simile al seguente:

```csharp
throw new StudentNotFoundException("The student cannot be found.", "John");
```

Il problema con la riga precedente è che `"The student cannot be found."` è semplicemente una stringa costante. In un'applicazione localizzata è necessario avere messaggi diversi a seconda delle impostazioni cultura dell'utente.
Gli [assembly satellite](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) sono un modo efficace per eseguire questa operazione. Un assembly satellite è un file con estensione dll che contiene risorse per una lingua specifica. Quando si richiede una specifica risorsa in fase di esecuzione, CLR trova tale risorsa a seconda delle impostazioni cultura dell'utente. Se non viene trovato alcun assembly satellite per tali impostazioni cultura, vengono utilizzate le risorse delle impostazioni cultura predefinite.

Per creare i messaggi di eccezione localizzati:

1. Creare una nuova cartella denominata *Resources* per conservare i file di risorse.
1. Aggiungere un nuovo file di risorse. Per eseguire questa operazione in Visual Studio, fare clic con il pulsante destro del mouse sulla cartella **Esplora soluzioni**e scegliere **Aggiungi** > **nuovo elemento** > **file di risorse**. Denominare il file *ExceptionMessages. resx*. Questo è il file di risorse predefinito.
1. Aggiungere una coppia nome/valore per il messaggio di eccezione, come illustrato nella figura seguente:

   ![Aggiungere risorse alle impostazioni cultura predefinite](media/add-resources-to-default-culture.jpg)

1. Aggiungere un nuovo file di risorse per il francese. Denominarlo *ExceptionMessages.fr-fr. resx*.
1. Aggiungere nuovamente una coppia nome/valore per il messaggio di eccezione, ma con un valore francese:

   ![Aggiungere risorse alle impostazioni cultura fr-FR](media/add-resources-to-fr-culture.jpg)

1. Dopo aver compilato il progetto, la cartella di output di compilazione deve contenere la cartella *fr-fr* con un file con estensione *dll* , ovvero l'assembly satellite.
1. L'eccezione viene generata con codice simile al seguente:

    ```csharp
    var resourceManager = new ResourceManager("FULLY_QIALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly());
    throw new StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John");
    ```

  > [!NOTE]
  > Se il nome del progetto è `TestProject` e il file di risorse *ExceptionMessages. resx* risiede nella cartella *Resources* del progetto, il nome completo del file di risorse viene `TestProject.Resources.ExceptionMessages`.

## <a name="see-also"></a>Vedere anche

- [Come creare eccezioni definite dall'utente](how-to-create-user-defined-exceptions.md)
- [Creazione di assembly satellite per le applicazioni desktop](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [base (C# riferimento)](../../csharp/language-reference/keywords/base.md)
- [Questo (C# riferimento)](../../csharp/language-reference/keywords/this.md)
