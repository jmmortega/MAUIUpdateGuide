- Install .Net SDK 6

- To start MAUI require run:
    - ```dotnet workload install maui```
    - ```dotnet tool install -g redth.net.MAUI.check```
    - ```maui-check```
        - Install all that suggests maui check
            - There are things that can't be update automatically like Xcode


- Install MAUI template 
    - ```dotnet new maui --search```


- Run in your favourite platform to test
    - ```dotnet build -t:Run -f net6.0-android```
    - ```dotnet build -t:Run -f net6.0-ios```
    - ```dotnet build -t:Run -f net6.0-maccatalyst```

- If you receive an error like this: "error NETSDK1139: The target platform identifier ios was not recognized"
    Run this commands: (Maybe MAUI check don't his work correctly)
        - dotnet workload install maui
        - dotnet workload install ios
        
- There a tool called upgrade-assistant in MAUI documentation. Problem is, this tool only works in Windows machine

- ¡Let's update!

# Visual studio version

If you start to work to update is better if you use the last version of Visual Studio 2022, in this moment are in preview version however works better with MAUI. We allow change the platform, anyway for the moment there few things that can improve, such as platform selector or when create a new method if there partial classes asks where want to place.

## Mac scenario

If you working with Mac the best way for the moment, is use Visual Studio Code. 

Visual studio for Mac preview support works really well too.