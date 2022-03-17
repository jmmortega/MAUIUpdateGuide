## **Locator**

I really love DependencyService from XamarinForms, it's a really simple locator, in my experience few times we need more or that to control dependencies inside of my application.

Sadly, we need to say goodbye to DependencyService to start to use HostBuilder. You have a good explanation for specific Startup from MAUI [here](https://docs.microsoft.com/en-gb/dotnet/maui/fundamentals/app-startup) and you can learn more about GenericHost [here](https://docs.microsoft.com/en-us/dotnet/core/extensions/generic-host)

The Generic host have more functions than a locator, it's here where register our Handlers and Renderers, also include Fonts.

I think, it's better this way to initialize our app, besides of Xamarin Forms, because include all related with Fonts and Renderers.

When working with a Xamarin Forms app, we locate a lot of *assembly* statements for all our code, this point add confusion.

## **Messenger Service**

MessagingCenter it's included inside of MAUI in Microsoft.Maui.Controls. Anyway, my advice it's use a abstraction for Messenger pattern, to avoid use directly to avoid mark like obsolete and lose. Also you will include more security inside of Messaging

IMO, try to avoid a Messenger pattern is a good practice, because an abuse provoke an event hell. 

Maybe, this change allow change this part of your architecture and use a better practice, like Observables.


## **Behaviors**

We can't use Behaviors, because the main functionality to behaviors it's remove code behind and then
we can add this functionality inside of View.

## **Converters**

We don't use converters like we know, we should to change controls properties when create our view. 

```
[State]
readonly bool Enabled;

[Body]
View body() => new VStack(spacing:20)
{
    new Text("Hello World)
            .Color(() => Enabled ? Color.White : Color.Silver);
            
}

```

If state have more two values like a enum

```

[State]
readonly int Options;

[Body]
View body() => new VStack(spacing:20)
{
    new Text("Hello world")
        .Color(() => 
        {
            switch(Options)
                case 1:
                    return Color.Red;
                case 2:
                    return Color.Green;
                case 3:
                    return Color.Black;
        })
}

```

If you like converters concept you can create extension methods to get the same example

```

public static T ColorEnabled<T>(this T view, bool enabledState) where T : View
    => view.Color(enabledState ? Color.White : Color.Silver);

```

And use

```
[State]
readonly bool Enabled;

[Body]
View body() => new VStack(spacing:20)
{
    new Text("Hello World)
            .ColorEnabled(Enabled);    
            
}

```

