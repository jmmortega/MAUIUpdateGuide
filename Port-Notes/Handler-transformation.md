## Transform renderers to handlers

For a better approach, you can need remove all Forms, renderers to Maui handlers.

## Avoid use handlers inline for App

Official documentation from Microsoft [show how use Maui handlers](https://docs.microsoft.com/en-us/dotnet/maui/user-interface/handlers/customize) IMO, this it's a bad approach to create complete Handlers. It's really cool to create small tweaks, also avoid, use compile directives inside App class, better to use partial classes aproach like show after.

## How create a entire Handler

You can check all the process related with a Maui Picker here:

First create a interface with required control implementation like [here](https://github.com/dotnet/maui/blob/ff2cfe059c9b16790caab5d0c8125fd45c61996f/src/Core/src/Core/IPicker.cs)

Then create Handlers like [this](https://github.com/dotnet/maui/tree/4f77ac8668a86c91104ec2304d84ec5a487352d0/src/Core/src/Handlers/Picker) if you see, all handler inherit from ViewHandler with two generics, the interface and the implementation.

If you see i.e. Android or iOS implementation, you can check there an another class called [MauiPicker](https://github.com/dotnet/maui/blob/b09979d93ac544d4b0dd9fd0df5c25da7e91392c/src/Core/src/Platform/iOS/MauiPicker.cs) it's a similar idea than we had in Xamarin Forms.

With a Extensions class you can map all Maui control to Platform control like you can check in this [file](https://github.com/dotnet/maui/blob/4f77ac8668a86c91104ec2304d84ec5a487352d0/src/Core/src/Platform/iOS/PickerExtensions.cs#L17)

This extension class it's a helper for mappers inside of Handlers, to map properties from common control to native view.

Create a control class like we create in Xamarin Forms, like [this](https://github.com/dotnet/maui/blob/4f77ac8668a86c91104ec2304d84ec5a487352d0/src/Controls/src/Core/Picker.cs)



So, recapitulate:

- Create a common implementation with a interface
- Create all the handlers, a common one and one per platform. Use partial classes strategy to reuse code.
- Create extensions methods to get a easy way to map all platforms.
- Create a control like Forms control.

IMO, sound really complex create a Handler instead of Render in Forms. However, the design determine gains more perfomance, the renderers system are really heavy and have several steps.