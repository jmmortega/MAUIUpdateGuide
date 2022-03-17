## Avoid use namespaces with Compability.*

There a lot of code inside Compability namespace, all this code, sooner or later become to deprecated for sure and then you need refactor all. 

## MasterDetailPage not longer exists

You can't use MasterDetailPage is completed removed for FlyoutPage. Maybe it's time to use Shell navigation page system, that seems continue and will have a strong support [1](https://github.com/davidortinau/WeatherTwentyOne/blob/main/src/WeatherTwentyOne/App.xaml#L13) and [2](https://github.com/microsoft/dotnet-podcasts/blob/f04f9db3109fdb2280a39ae6dbbb555c7f89cf62/src/Mobile/Pages/MobileShell.xaml#L2)

## Color and Colors

Sound small, however I think it's a small pain. MAUI changes the default color palette class name to Colors besides Color. When develop apps and create my own color palette, I used to Colors class, so, enter in ambigous declaration. Easy fix, use a using statement. 

## Ouch what is my OutputType?

Take care in your .csproj project with the tag called OutputType. Check if Exe and not Library or another thing.

## External libraries 

If your project use external libraries, you need upgrade this libraries too. You need move all the source code from your external libraries to the new MAUI template library
