watched till "Asp net core project file"

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

| OutOfProcess                         | InProcess        |
| :----------------------------------- | :--------------- |
| 2 web servers: Internal and external | Only internal??? |
| internal: Kestrel                    | only IIS         |
| external: IIS, Nginx, Apache         |

- Kestrel
  - cross platform
  - process: dotnet.exe
