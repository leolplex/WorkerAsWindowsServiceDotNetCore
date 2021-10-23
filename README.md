# Worker As Windows Service DotNetCore


`dotnet add package Microsoft.Extensions.Hosting.WindowsServices`

Add this in program.cs 
`` .UseWindowsService(options =>
    {
        options.ServiceName = ".NET Joke Service";
    })``


`dotnet publish -c Release -o ./publish/workerService`

`sc.exe create ".NET Joke Service" binpath="C:\Path\To\App.WindowsService.exe"`

If you need to change the content root of the host configuration, you can pass it as a command-line argument when specifying the binpath:

`sc.exe create "Svc Name" binpath="C:\Path\To\App.exe --contentRoot C:\Other\Path"`

# Start the Windows service

`sc.exe start ".NET Joke Service"`

# Stop the Windows service

`sc.exe stop ".NET Joke Service"`

# Delete the Windows service

`sc.exe delete ".NET Joke Service"`