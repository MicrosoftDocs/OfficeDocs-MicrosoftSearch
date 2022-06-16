---
title: "Graph connectors SDK Sample Hosting"
ms.author: rchanda
author: rchanda
manager: harshkum
ms.audience: Admin
ms.topic: article
ms.service: mssearch
description: "Graph connectors SDK Sample Hosting"
---

# Host the connector as a windows service

The connector executable must be always running so that the connector platform can make requests to it during the crawls or to perform any connection management operations. The executable won’t be actively consuming any resources except for the times when the connector is being crawled. The rest of the time, the connector executable will just be idle.
One possible way to make the connector executable run always is to host it as a windows service. If the executable is registered as a windows service, the OS will take care of starting the process and re-spawning it in case of crashes.

Follow the instructions below for hosting the connector as a windows service:

1. Right click on the solution containing the custom connector project and select Add > New project
<\image>

2. Search for “Worker service” template, select the Worker Service template and click Next
<\image>

3. Name the project as CustomConnectorWorkerService and click Next
<\image>

4. Choose .Net core 3.1 as target framework and click on Create
<\image>

5. Right click on the project and select “Open in Terminal”
<\image>

6. Run the following commands in the terminal

    ```dotnetcli
    dotnet add package Microsoft.Extensions.Hosting --version 6.0.0
    dotnet add package Microsoft.Extensions.Hosting.WindowsServices --version 6.0.0

    ```

7. Right click on the worker service project and select Add -> Project Reference

8. Select the CustomConnector project and click Ok

9. Replace the code in Worker.cs file with the following code

    ```csharp
    using CustomConnector.Server;
    
    using Microsoft.Extensions.Hosting;
    using Microsoft.Extensions.Logging;
    
    using System.Threading;
    using System.Threading.Tasks;
    
    namespace CustomConnectorWorkerService
    {
        public class Worker : BackgroundService
        {
            public Worker(ILogger<Worker> logger)
            {
                var server = new ConnectorServer();
                server.Start();
            }
    
            protected override async Task ExecuteAsync(CancellationToken stoppingToken)
            {
                while (!stoppingToken.IsCancellationRequested)
                {
                    await Task.Delay(1000);
                }
            }
        }
    }

    ```

10. Replace the code in Program.cs with the following

    ```csharp
    using Microsoft.Extensions.DependencyInjection;
    using Microsoft.Extensions.Hosting;
    
    namespace CustomConnectorWorkerService
    {
        public class Program
        {
            public static void Main(string[] args)
            {
                CreateHostBuilder(args).Build().Run();
            }
    
            public static IHostBuilder CreateHostBuilder(string[] args) =>
                Host.CreateDefaultBuilder(args)
                .UseWindowsService()
                    .ConfigureServices((hostContext, services) =>
                    {
                        services.AddHostedService<Worker>();
                    });
        }
    }

    ```

11. Select Release configuration for build and build the CustomConnectorWorkerService project

12. Run the following script to register and start the custom connector as windows service

    ```powershell
    $ServiceName = "CustomConnector"
    $ExePath = "<Full path of CustomConnectorWorkerService.exe from above build>"
    # Create a service with the given executable. This just creates an entry for this service.
    sc.exe create $ServiceName binPath="$ExePath" start="delayed-auto"
    # Set the service to run under a virtual account NT Service\<ServiceName>. Optionally skip this step to run the service under LOCAL SERVICE account
    sc.exe config $ServiceName obj="NT Service\$ServiceName"
    # Restarts service after 5 minutes on first, second and third failures and resets error after 1 day
    sc.exe failureflag $ServiceName 1
    sc.exe failure $ServiceName reset= 86400 actions= restart/300000/restart/300000/restart/300000
    sc.exe start $ServiceName

    ```

13. Open services.msc and check that the service is in running state

## Troubleshooting

### Starting service failed due to Access denied error

Make sure the path of the executable is accessible to Local System account.

1. Right click on the folder containing the executable and choose Properties.

2. Open Security tab and click on Edit under Group or user names

3. Click on Add

4. Enter LOCAL SERVICE as the object name and click on Check Names

5. Click OK in all the dialog boxes.

### Starting service fails with any error

Check the error logs from event viewer. Search for event viewer app and open it. Check for error logs under **Windows logs > Application** and **Windows logs > System**
