# Understanding logging

All logging change in MAUI, probably you use a log system (I hope you do) all log system should be set inside of MAUI builder using ConfigureLogging method. 

If you have your own log system, to include this log system, you need implement ILogger interface from Microsoft.Extension.Logging.Abstractions in any case there several implementations that should be included like Microsoft.Extensions.Logging.Console|Debug...

When implement *ILogger* we have three methods to implement:
- Log
- IsEnabled
- BeginScope

When configure Logging in MAUI app, it's a slightly different from ASP.NET core samples, when check documentation usually use *ConfigureLogging* method inside builder, however inside of MAUI app we use Logging property and it's the same setup like you can check in documentation.

If you need add your own provider we recommend use a extension methods that explain [here](https://docs.microsoft.com/en-us/dotnet/core/extensions/custom-logging-provider) at the end of document.