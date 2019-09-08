---
title: Esecuzione di SqlCommand con SqlNotificationRequest
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1776f48f-9bea-41f6-83a4-c990c7a2c991
ms.openlocfilehash: 3115bfb80d4e5e61ed49da11e36eaa37bc24334f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791540"
---
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a><span data-ttu-id="9bdff-102">Esecuzione di SqlCommand con SqlNotificationRequest</span><span class="sxs-lookup"><span data-stu-id="9bdff-102">SqlCommand Execution with a SqlNotificationRequest</span></span>

<span data-ttu-id="9bdff-103">È possibile configurare <xref:System.Data.SqlClient.SqlCommand> per generare una notifica quando i dati vengono modificati dopo essere stati recuperati dal server, nel qual caso il set di risultati sarebbe diverso se venisse eseguita nuovamente la query.</span><span class="sxs-lookup"><span data-stu-id="9bdff-103">A <xref:System.Data.SqlClient.SqlCommand> can be configured to generate a notification when data changes after it has been fetched from the server and the result set would be different if the query were executed again.</span></span> <span data-ttu-id="9bdff-104">Questa funzione risulta utile per le situazioni in cui si desidera usare code di notifiche personalizzate sul server o quando non si desidera mantenere oggetti attivi.</span><span class="sxs-lookup"><span data-stu-id="9bdff-104">This is useful for scenarios where you want to use custom notification queues on the server or when you do not want to maintain live objects.</span></span>

## <a name="creating-the-notification-request"></a><span data-ttu-id="9bdff-105">Creazione della richiesta di notifica</span><span class="sxs-lookup"><span data-stu-id="9bdff-105">Creating the Notification Request</span></span>

<span data-ttu-id="9bdff-106">È possibile usare un oggetto <xref:System.Data.Sql.SqlNotificationRequest> per creare la richiesta di notifica associandolo a un oggetto `SqlCommand`.</span><span class="sxs-lookup"><span data-stu-id="9bdff-106">You can use a <xref:System.Data.Sql.SqlNotificationRequest> object to create the notification request by binding it to a `SqlCommand` object.</span></span> <span data-ttu-id="9bdff-107">Una volta creata la richiesta, l'oggetto `SqlNotificationRequest` non è più necessario.</span><span class="sxs-lookup"><span data-stu-id="9bdff-107">Once the request is created, you no longer need the `SqlNotificationRequest` object.</span></span> <span data-ttu-id="9bdff-108">È possibile eseguire una query sulla coda per rilevare eventuali notifiche e rispondere nel modo appropriato.</span><span class="sxs-lookup"><span data-stu-id="9bdff-108">You can query the queue for any notifications and respond appropriately.</span></span> <span data-ttu-id="9bdff-109">Le notifiche possono essere generate anche se l'applicazione viene arrestata e successivamente riavviata.</span><span class="sxs-lookup"><span data-stu-id="9bdff-109">Notifications can occur even if the application is shut down and subsequently restarted.</span></span>

<span data-ttu-id="9bdff-110">Quando viene eseguito il comando con la notifica associata, le eventuali modifiche apportate al set di risultati originale attivano l'invio di un messaggio alla coda di SQL Server configurata nella richiesta di notifica.</span><span class="sxs-lookup"><span data-stu-id="9bdff-110">When the command with the associated notification is executed, any changes to the original result set trigger sending a message to the SQL Server queue that was configured in the notification request.</span></span>

<span data-ttu-id="9bdff-111">Il polling della coda di SQL Server e l'interpretazione del messaggio sono specifici dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="9bdff-111">How you poll the SQL Server queue and interpret the message is specific to your application.</span></span> <span data-ttu-id="9bdff-112">Il polling della coda e la reazione in base al contenuto del messaggio dipendono interamente dall'applicazione.</span><span class="sxs-lookup"><span data-stu-id="9bdff-112">The application is responsible for polling the queue and reacting based on the contents of the message.</span></span>

> [!NOTE]
> <span data-ttu-id="9bdff-113">Quando si usano le richieste di notifica di SQL Server con <xref:System.Data.SqlClient.SqlDependency>, creare un nome per la coda anziché usare il nome del servizio predefinito.</span><span class="sxs-lookup"><span data-stu-id="9bdff-113">When using SQL Server notification requests with <xref:System.Data.SqlClient.SqlDependency>, create your own queue name instead of using the default service name.</span></span>

<span data-ttu-id="9bdff-114">Non esistono nuovi elementi di sicurezza sul lato client per <xref:System.Data.Sql.SqlNotificationRequest>.</span><span class="sxs-lookup"><span data-stu-id="9bdff-114">There are no new client-side security elements for <xref:System.Data.Sql.SqlNotificationRequest>.</span></span> <span data-ttu-id="9bdff-115">Si tratta principalmente di una funzionalità del server, che ha creato privilegi speciali di cui gli utenti devono disporre per richiedere una notifica.</span><span class="sxs-lookup"><span data-stu-id="9bdff-115">This is primarily a server feature, and the server has created special privileges that users must have to request a notification.</span></span>

### <a name="example"></a><span data-ttu-id="9bdff-116">Esempio</span><span class="sxs-lookup"><span data-stu-id="9bdff-116">Example</span></span>

<span data-ttu-id="9bdff-117">Nel frammento di codice seguente viene illustrato come creare un oggetto <xref:System.Data.Sql.SqlNotificationRequest> e associarlo a <xref:System.Data.SqlClient.SqlCommand>.</span><span class="sxs-lookup"><span data-stu-id="9bdff-117">The following code fragment demonstrates how to create a <xref:System.Data.Sql.SqlNotificationRequest> and associate it with a <xref:System.Data.SqlClient.SqlCommand>.</span></span>

```vb
' Assume connection is an open SqlConnection.
' Create a new SqlCommand object.
Dim command As New SqlCommand( _
  "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", connection)

' Create a SqlNotificationRequest object.
Dim notifcationRequest As New SqlNotificationRequest()
notificationRequest.id = "NotificationID"
notificationRequest.Service = "mySSBQueue"

' Associate the notification request with the command.
command.Notification = notificationRequest
' Execute the command.
command.ExecuteReader()
' Process the DataReader.
' You can use Transact-SQL syntax to periodically poll the
' SQL Server queue to see if you have a new message.
```

```csharp
// Assume connection is an open SqlConnection.
// Create a new SqlCommand object.
SqlCommand command=new SqlCommand(
 "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", connection);

// Create a SqlNotificationRequest object.
SqlNotificationRequest notificationRequest=new SqlNotificationRequest();
notificationRequest.id="NotificationID";
notificationRequest.Service="mySSBQueue";

// Associate the notification request with the command.
command.Notification=notificationRequest;
// Execute the command.
command.ExecuteReader();
// Process the DataReader.
// You can use Transact-SQL syntax to periodically poll the
// SQL Server queue to see if you have a new message.
```

## <a name="see-also"></a><span data-ttu-id="9bdff-118">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9bdff-118">See also</span></span>

- [<span data-ttu-id="9bdff-119">Notifiche di query in SQL Server</span><span class="sxs-lookup"><span data-stu-id="9bdff-119">Query Notifications in SQL Server</span></span>](query-notifications-in-sql-server.md)
- [<span data-ttu-id="9bdff-120">Panoramica di ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9bdff-120">ADO.NET Overview</span></span>](../ado-net-overview.md)
