---
title: Supporto SqlClient per LocalDB
ms.date: 03/30/2017
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.openlocfilehash: 200db3b1014278e711062bcbdff81be8d27c3351
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780786"
---
# <a name="sqlclient-support-for-localdb"></a><span data-ttu-id="f8fc9-102">Supporto SqlClient per LocalDB</span><span class="sxs-lookup"><span data-stu-id="f8fc9-102">SqlClient Support for LocalDB</span></span>
<span data-ttu-id="f8fc9-103">A partire da SQL Server nome in codice Denali, sarà disponibile una versione semplificata di SQL Server, denominata local DB.</span><span class="sxs-lookup"><span data-stu-id="f8fc9-103">Beginning in SQL Server code name Denali, a lightweight version of SQL Server, called LocalDB, will be available.</span></span> <span data-ttu-id="f8fc9-104">In questo argomento viene illustrato come connettersi a un database di LocalDB.</span><span class="sxs-lookup"><span data-stu-id="f8fc9-104">This topic discusses how to connect to a LocalDB database.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8fc9-105">Note</span><span class="sxs-lookup"><span data-stu-id="f8fc9-105">Remarks</span></span>  
 <span data-ttu-id="f8fc9-106">Per ulteriori informazioni sul database locale, inclusa la modalità di installazione del database locale e la configurazione dell'istanza del database locale, vedere documentazione online di SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f8fc9-106">For more information about LocalDB, including how to install LocalDB and configure your LocalDB instance, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="f8fc9-107">Per riepilogare le operazioni che è possibile eseguire con LocalDB:</span><span class="sxs-lookup"><span data-stu-id="f8fc9-107">To summarize what you can do with LocalDB:</span></span>  
  
- <span data-ttu-id="f8fc9-108">Creare e avviare le istanze di LocalDB con sqllocaldb.exe o il file app.config.</span><span class="sxs-lookup"><span data-stu-id="f8fc9-108">Create and start LocalDB instances with sqllocaldb.exe or your app.config file.</span></span>  
  
- <span data-ttu-id="f8fc9-109">Usare sqlcmd.exe per aggiungere e modificare i database in un'istanza di LocalDB.</span><span class="sxs-lookup"><span data-stu-id="f8fc9-109">Use sqlcmd.exe to add and modify databases in a LocalDB instance.</span></span> <span data-ttu-id="f8fc9-110">Ad esempio `sqlcmd -S (localdb)\myinst`.</span><span class="sxs-lookup"><span data-stu-id="f8fc9-110">For example, `sqlcmd -S (localdb)\myinst`.</span></span>  
  
- <span data-ttu-id="f8fc9-111">Usare la parola chiave della stringa di connessione `AttachDBFilename` per aggiungere un database all'istanza di LocalDB.</span><span class="sxs-lookup"><span data-stu-id="f8fc9-111">Use the `AttachDBFilename` connection string keyword to add a database to your LocalDB instance.</span></span> <span data-ttu-id="f8fc9-112">Quando si usa `AttachDBFilename`, se non si specifica il nome del database con la parola chiave della stringa di connessione `Database` , il database verrà rimosso dall'istanza di LocalDB alla chiusura dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="f8fc9-112">When using `AttachDBFilename`, if you do not specify the name of the database with the `Database` connection string keyword, the database will be removed from the LocalDB instance when the application closes.</span></span>  
  
- <span data-ttu-id="f8fc9-113">Specificare un'istanza di LocalDB nella stringa di connessione.</span><span class="sxs-lookup"><span data-stu-id="f8fc9-113">Specify a LocalDB instance in your connection string.</span></span> <span data-ttu-id="f8fc9-114">Ad esempio, se il nome dell'istanza è `myInstance`, la stringa di connessione includerà:</span><span class="sxs-lookup"><span data-stu-id="f8fc9-114">For example, your instance name is `myInstance`, the connection string would include:</span></span>  
  
    ```  
    server=(localdb)\\myInstance  
    ```  
  
 <span data-ttu-id="f8fc9-115">`User Instance=True` non è consentito quando ci si connette a un database di LocalDB.</span><span class="sxs-lookup"><span data-stu-id="f8fc9-115">`User Instance=True` is not allowed when connecting to a LocalDB database.</span></span>  
  
 <span data-ttu-id="f8fc9-116">È possibile scaricare LocalDB da [Microsoft SQL Server 2012 Feature Pack](https://www.microsoft.com/download/en/details.aspx?id=29065).</span><span class="sxs-lookup"><span data-stu-id="f8fc9-116">You can download LocalDB from [Microsoft SQL Server 2012 Feature Pack](https://www.microsoft.com/download/en/details.aspx?id=29065).</span></span> <span data-ttu-id="f8fc9-117">Se si utilizza sqlcmd. exe per modificare i dati nell'istanza del database locale, è necessario disporre di sqlcmd da SQL Server 2012, che è possibile ottenere anche dal Feature Pack SQL Server 2012.</span><span class="sxs-lookup"><span data-stu-id="f8fc9-117">If you will use sqlcmd.exe to modify data in your LocalDB instance, you will need sqlcmd from SQL Server 2012, which you can also get from the SQL Server 2012 Feature Pack.</span></span>  
  
## <a name="programmatically-create-a-named-instance"></a><span data-ttu-id="f8fc9-118">Creare un'istanza denominata a livello di codice</span><span class="sxs-lookup"><span data-stu-id="f8fc9-118">Programmatically Create a Named Instance</span></span>  
 <span data-ttu-id="f8fc9-119">Un'applicazione può creare un'istanza denominata e specificare un database come segue:</span><span class="sxs-lookup"><span data-stu-id="f8fc9-119">An application can create a named instance and specify a database as follows:</span></span>  
  
- <span data-ttu-id="f8fc9-120">Specificare le istanze di LocalDB da creare nel file app.config, come illustrato di seguito.</span><span class="sxs-lookup"><span data-stu-id="f8fc9-120">Specify the LocalDB instances to create in the app.config file, as follows.</span></span>  <span data-ttu-id="f8fc9-121">Il numero di versione dell'istanza deve essere uguale al numero di versione dell'installazione di LocalDB.</span><span class="sxs-lookup"><span data-stu-id="f8fc9-121">The version number of the instance should be the same as the version number of your LocalDB installation.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <configSections>  
        <section  
        name="system.data.localdb"  
        type="System.Data.LocalDBConfigurationSection,System.Data,Version=4.0.0.0,Culture=neutral,PublicKeyToken=b77a5c561934e089"/>  
      </configSections>  
      <system.data.localdb>  
        <localdbinstances>  
          <add name="myInstance" version="11.0" />  
        </localdbinstances>  
      </system.data.localdb>  
    </configuration>  
    ```  
  
- <span data-ttu-id="f8fc9-122">Specificare il nome dell'istanza mediante la parola chiave della stringa di connessione `server` .</span><span class="sxs-lookup"><span data-stu-id="f8fc9-122">Specify the name of the instance using the `server` connection string keyword.</span></span>  <span data-ttu-id="f8fc9-123">Il nome dell'istanza specificato nella parola chiave della stringa di connessione `server` deve corrispondere a quello specificato nel file app.config.</span><span class="sxs-lookup"><span data-stu-id="f8fc9-123">The instance name specified in the `server` connection string keyword must match the name specified in the app.config file.</span></span>  
  
- <span data-ttu-id="f8fc9-124">Usare la parola chiave della stringa di connessione `AttachDBFilename` per specificare il file con estensione MDF.</span><span class="sxs-lookup"><span data-stu-id="f8fc9-124">Use the `AttachDBFilename` connection string keyword to specify the .MDF file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8fc9-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f8fc9-125">See also</span></span>

- [<span data-ttu-id="f8fc9-126">Funzionalità di SQL Server e ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f8fc9-126">SQL Server Features and ADO.NET</span></span>](sql-server-features-and-adonet.md)
- [<span data-ttu-id="f8fc9-127">Panoramica di ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f8fc9-127">ADO.NET Overview</span></span>](../ado-net-overview.md)
