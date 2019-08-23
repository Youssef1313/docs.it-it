---
title: Traccia del flusso di lavoro
ms.date: 03/30/2017
ms.assetid: 18737989-0502-4367-b5f6-617ebfb77c96
ms.openlocfilehash: 7bca78b24963d94bfa0f2e2245a677b7dce455c9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933435"
---
# <a name="workflow-tracing"></a><span data-ttu-id="c6103-102">Traccia del flusso di lavoro</span><span class="sxs-lookup"><span data-stu-id="c6103-102">Workflow Tracing</span></span>
<span data-ttu-id="c6103-103">La traccia del flusso di lavoro consente di acquisire informazioni diagnostiche usando i listener di traccia di .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c6103-103">Workflow tracing offers a way to capture diagnostic information using .NET Framework trace listeners.</span></span> <span data-ttu-id="c6103-104">La traccia può essere abilitata in seguito al rilevamento di un problema con l'applicazione, quindi nuovamente disabilitata quando il problema viene risolto.</span><span class="sxs-lookup"><span data-stu-id="c6103-104">Tracing can be enabled if a problem is detected with the application and then disabled again once the problem is resolved.</span></span> <span data-ttu-id="c6103-105">Sono disponibili due modi per abilitare la traccia di debug per i flussi di lavoro:</span><span class="sxs-lookup"><span data-stu-id="c6103-105">There are two ways you could enable debug tracing for workflows.</span></span> <span data-ttu-id="c6103-106">è possibile configurarla usando il visualizzatore di Traccia eventi oppure usare l'oggetto <xref:System.Diagnostics> per inviare eventi di traccia a un file.</span><span class="sxs-lookup"><span data-stu-id="c6103-106">You can configure it using the Event Trace viewer or you can use <xref:System.Diagnostics> to send trace events to a file.</span></span>  
  
## <a name="enabling-debug-tracing-in-etw"></a><span data-ttu-id="c6103-107">Abilitazione della traccia di debug in ETW</span><span class="sxs-lookup"><span data-stu-id="c6103-107">Enabling Debug Tracing in ETW</span></span>  
 <span data-ttu-id="c6103-108">Per abilitare la traccia tramite ETW, abilitare il canale Debug in Visualizzatore eventi:</span><span class="sxs-lookup"><span data-stu-id="c6103-108">To enable tracing using ETW, enable the Debug channel in Event Viewer:</span></span>  
  
1. <span data-ttu-id="c6103-109">Passare al nodo dei registri analitici e di debug in Visualizzatore eventi.</span><span class="sxs-lookup"><span data-stu-id="c6103-109">Navigate to analytic and debug logs node in Event Viewer.</span></span>  
  
2. <span data-ttu-id="c6103-110">Nella visualizzazione struttura ad albero di Visualizzatore eventi passare a **Visualizzatore eventi-> registri applicazioni e servizi-> Microsoft-> Windows-> server applicazioni-applicazioni**.</span><span class="sxs-lookup"><span data-stu-id="c6103-110">In the tree view in Event Viewer, navigate to **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications**.</span></span> <span data-ttu-id="c6103-111">Fare clic con il pulsante destro del mouse su **server applicazioni-applicazioni** e selezionare visualizza **-> Visualizza log analitici e di debug**.</span><span class="sxs-lookup"><span data-stu-id="c6103-111">Right-click **Application Server-Applications** and select **View->Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="c6103-112">Fare clic con il pulsante destro del mouse su **debug** e selezionare **Abilita log**.</span><span class="sxs-lookup"><span data-stu-id="c6103-112">Right-click **Debug** and select **Enable Log**.</span></span>  
  
3. <span data-ttu-id="c6103-113">Quando un flusso di lavoro esegue il debug e le tracce vengono create nel canale di debug ETW, queste ultime possono essere visualizzate in Visualizzatore eventi.</span><span class="sxs-lookup"><span data-stu-id="c6103-113">When a workflow runs the debug and traces are emitted to ETW debug channel, they can be viewed in the Event Viewer.</span></span> <span data-ttu-id="c6103-114">Passare a **Visualizzatore eventi-> registri applicazioni e servizi-> Microsoft-> Windows-> server applicazioni-applicazioni**.</span><span class="sxs-lookup"><span data-stu-id="c6103-114">Navigate to **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications**.</span></span> <span data-ttu-id="c6103-115">Fare clic con il pulsante destro del mouse su **debug** e selezionare **Aggiorna**.</span><span class="sxs-lookup"><span data-stu-id="c6103-115">Right-click **Debug** and select **Refresh**.</span></span>  
  
4. <span data-ttu-id="c6103-116">La dimensione del buffer di traccia analitica predefinita è solo 4 kilobyte (KB). Si consiglia di aumentare la dimensione a 32 KB.</span><span class="sxs-lookup"><span data-stu-id="c6103-116">The default analytic trace buffer size is only 4 kilobytes (KB); it is recommended to increase the size to 32 KB.</span></span> <span data-ttu-id="c6103-117">A tale scopo, eseguire i passaggi seguenti.</span><span class="sxs-lookup"><span data-stu-id="c6103-117">To do this, perform the following steps.</span></span>  
  
    1. <span data-ttu-id="c6103-118">Eseguire il comando seguente nella directory del framework corrente (ad esempio, C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`</span><span class="sxs-lookup"><span data-stu-id="c6103-118">Execute the following command in the current framework directory (for example, C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`</span></span>  
  
    2. <span data-ttu-id="c6103-119">Modificare il \<valore di > bufferSize nel file Windows. ApplicationServer. Applications. Man in 32.</span><span class="sxs-lookup"><span data-stu-id="c6103-119">Change the \<bufferSize> value in the Windows.ApplicationServer.Applications.man file to 32.</span></span>  
  
        ```xml  
        <channel name="Microsoft-Windows-Application Server-Applications/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" >  
                    <publishing>  
                      <bufferSize>32</bufferSize>  
                    </publishing>  
                  </channel>  
        ```  
  
    3. <span data-ttu-id="c6103-120">Eseguire il comando seguente nella directory del framework corrente (ad esempio, C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`</span><span class="sxs-lookup"><span data-stu-id="c6103-120">Execute the following command in the current framework directory (for example, C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c6103-121">Se si usa il .NET Framework 4 Client Profile, è necessario prima registrare il manifesto ETW eseguendo il comando seguente dalla directory .NET Framework 4:`ServiceModelReg.exe –i –c:etw`</span><span class="sxs-lookup"><span data-stu-id="c6103-121">If you are using the .NET Framework 4 Client Profile, you must first register the ETW manifest by running the following command from the .NET Framework 4 directory: `ServiceModelReg.exe –i –c:etw`</span></span>  
  
## <a name="enabling-debug-tracing-using-systemdiagnostics"></a><span data-ttu-id="c6103-122">Abilitazione della traccia di debug tramite l'oggetto System.Diagnostics</span><span class="sxs-lookup"><span data-stu-id="c6103-122">Enabling Debug Tracing using System.Diagnostics</span></span>  
 <span data-ttu-id="c6103-123">Questi listener possono essere configurati nel file App.config dell'applicazione flusso di lavoro o nel file Web.config per un servizio flusso di lavoro.</span><span class="sxs-lookup"><span data-stu-id="c6103-123">These listeners can be configured in the App.config file of the workflow application, or the Web.config for a workflow service.</span></span> <span data-ttu-id="c6103-124">In questo esempio, un oggetto [TextWriterTraceListener](https://go.microsoft.com/fwlink/?LinkId=165424) è configurato per salvare le informazioni di traccia nel file nel MyTraceLog. txt nella directory corrente.</span><span class="sxs-lookup"><span data-stu-id="c6103-124">In this example, a [TextWriterTraceListener](https://go.microsoft.com/fwlink/?LinkId=165424) is configured to save tracing information to the MyTraceLog.txt file in the current directory.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="System.Activities" switchValue="Information">  
        <listeners>  
          <add name="textListener" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"  
           type="System.Diagnostics.TextWriterTraceListener"  
           initializeData="MyTraceLog.txt"  
           traceOutputOptions="ProcessId, DateTime" />  
    </sharedListeners>  
    <trace autoflush="true" indentsize="4">  
      <listeners>  
        <add name="textListener" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c6103-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c6103-125">See also</span></span>

- [<span data-ttu-id="c6103-126">Monitoraggio di Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="c6103-126">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)
- [<span data-ttu-id="c6103-127">Monitoraggio delle applicazioni con l'infrastruttura di app</span><span class="sxs-lookup"><span data-stu-id="c6103-127">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
