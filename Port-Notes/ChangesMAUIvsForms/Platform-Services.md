## Platform services

A common practice in forms when need specific code in our platform is create different services one per platform and add the specific code here and then in the common part use interface to communicate with the current platform.

Well, this ends, we will continue with this way to work, however no makes more sense, there are best ways to work in MAUI with that. If you analyze your specific services, most of them, almost duplicate the code that use or there are parts of code that duplicate. In this moment, a best way to works with this type of services is use conditional approach or a best way, to avoid spaghetti code, create different partial classes.

In this scenario, a common class that implement service and every specific partial class that implement custom code for this service.

Another good aproach it's create a similar implementation like [Essentials library](https://github.com/xamarin/Essentials/tree/main/Xamarin.Essentials) another way to use of partial classes.

IMO, I prefer use the first approach, because we implement a interface and then we have the possibility to mock when test or change the implementation when needed. So we take the first approach.

**Please don't use conditional compilation approach**. Yes, could be easy to use, yes, sounds really good in a first way. However, you will be a spaghetti code in any moment. Yes, when this will happen, you will refactor, bla, bla. We will know you don't do that and spaghetti code will be grow. So please, try don't use conditional compilation. Partial classes approach will be more legibility and reduce your tech debt for sure.

A good practice to use partial classes are [Monogame](https://github.com/MonoGame/MonoGame) take a look to Texture2D years ago when use [conditional compilation](https://github.com/MonoGame/MonoGame/blob/2d33bbdf9dbfeeefe8bc55ed3849c6926a7a75c7/MonoGame.Framework/Graphics/Texture2D.cs) and take a look now. 

There a problem related with this aproach because, you can't use partial methods and return values, this is because a compiler issue you can know more about this [here] (https://stackoverflow.com/a/9600649/2469223)

So we need to perform a good way to achieve that, to avoid IMO the best choice that use conditional compilations. 

If you can create this API using static methods, you can use the aproach that use [Essentials library](https://github.com/dotnet/maui/tree/main/src/Essentials) I don't like using this way to try to share all the code, because you can't use interfaces to create service pattern and then code add more difficult for testing.

So in this case, only should leave one way to share code, the Xamarin way. Creating a file for each platform implementation and locate in platform folder. Then register using an extension method inside MauiAppBuilder.