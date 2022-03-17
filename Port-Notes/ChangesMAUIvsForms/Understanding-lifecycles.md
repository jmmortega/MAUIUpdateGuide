# Understanding lifecycle

Say goodbye to old lifecycle system that works with Application. With MAUI we can register all that lifecycle that we need, even create our lifecycle events. 

With new lifecycle system, we can register native lifecycles directly to our events that require, this new way to register lifecycle, sounds really 'hacky' and obviously we have a better resolutions of all lifecycle. 

We could configure LifecycleEvents, we use **ConfigureLifecycleEvents** method from MauiAppBuilder, this method have an Action like parameter and then, we use an extension method for every platform (AddAndroid, AddIos, AddWindows...) that receive another Action like parameter, there are two interesting thing here.

- There are different extension methods with the common platform native lifecycle events.
- The most interesting point, it's we could create our lifecycle events (really cool IMO), please don't use this lifecycle events like a MessageCenter, his use it's related with lifecycle and the way to call this lifecycle custom events it's use. 

All lifecycle system we handle with the [ILifecycleEventService](https://github.com/dotnet/maui/tree/main/src/Core/src/LifecycleEvents) so then we could resolve this dependency in any moment and invoke own events or check which event are active. 

## How handle this lifecycle methods events?

We have thinking a lot related how handle lifecycle, when run an application there are two types of lifecycle events:

- Specific lifecycle events
- Common lifecycle events

In a Xamarin Forms perspective, we call all we need in platform events, then run all common things we need in the App lifecycle, however this track inside of App events. So we need replicate the same scenario.

I think the best way to handle this, it's like another thing that require common and specific code, using partial classes. The good point here is we can add any handlers that we want, so we can add two handlers for the same lifecycle event, one for the specific code and another for the common one.

**My recommendation** add first specific and then common, because specific code must be run after common one.

Don't worry to repeat methods names, specific lifecycle methods has specific parameters, i.e Activity for Android parameters and common methods should be parameterless.

We take care when place several events, i.e. common Start in iOS, in this cases is better call FinishedLaunching from iOS and when finish call common OnStart.