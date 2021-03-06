# Worker As Windows Service DotNetCore

# Add Nuget dependencies
`dotnet add package Microsoft.Extensions.Hosting.WindowsServices`

# Config the program class

`` .UseWindowsService(options =>
    {
        options.ServiceName = ".NET Joke Service";
    })``

# Publish the worker

`dotnet publish -c Release -o ./publish/workerService`

# Create the Windows service

`sc.exe create ".NET Joke Service" binpath="C:\Path\To\App.WindowsService.exe"`

If you need to change the content root of the host configuration, you can pass it as a command-line argument when specifying the binpath:

`sc.exe create "Svc Name" binpath="C:\Path\To\App.exe --contentRoot C:\Other\Path"`

# Start the Windows service

`sc.exe start ".NET Joke Service"`

# Stop the Windows service

`sc.exe stop ".NET Joke Service"`

# Delete the Windows service

`sc.exe delete ".NET Joke Service"`