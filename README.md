watched till "Asp net core appsettings json file"

# dotnetcore-kudvenkat

Taken from YouTube [playlist](https://www.youtube.com/watch?v=4IgC2Q5-yDE&list=PL6n9fhu94yhVkdrusLaQsfERmL_Jh4XmU)

- Both MVC controller class and web API controller class inherit from the same `Controller` base class and returns `IActionResult`
- IActionResult

  - ViewResult
  - JsonResult

- CreateDefaultBuilder() method calls UseIIS() method and host the app inside of the IIS worker process w3wp.exe or iisexpress.exe
  `<AspNetCoreHostingModel>InProcess</AspNetCoreHostingModel>`
- InProcess hosting gives higher request throughput than OutOfProcess hosting

| IIS Express                    | IIS                      |
| :----------------------------- | :----------------------- |
| Lightweight                    | For Production           |
| process name is iisexpress.exe | process name is w3wp.exe |

| OutOfProcess                         | InProcess                                                             |
| :----------------------------------- | :-------------------------------------------------------------------- |
| 2 web servers: Internal and external | Only one web server, Only internal???                                 |
| Process name is dotnet.exe           | w3wp.exe, iisexpress.exe                                              |
| internal: Kestrel                    |                                                                       |
| external: IIS, Nginx, Apache         |                                                                       |
| better performance                   | penalty of proxying requests between internal and external web server |

- Kestrel
  - cross platform
  - process: dotnet.exe

| commandName | AspNetCoreHostingModel                                              | Internal Web Server | External Web Server |
| ----------- | ------------------------------------------------------------------- | ------------------- | ------------------- |
| Project     | Hosting Setting Ignored <td colspan=2>Only one web server - Kestrel |
| IISExpress  | InProcess <td colspan=2>Only one web server - IISExpress            |
| IISExpress  | OutOfProcess                                                        | Kestrel             | IISExpress          |
| IIS         | InProcess <td colspan=2>Only one web server - IIS                   |
| IIS         | OutOfProcess                                                        | Kestrel             | IIS                 |

### Configuration sources

- Files (appsettings.json, appsettings.{Environment}.json)
- User secrets
- Environment variables
- Command-line arguments
