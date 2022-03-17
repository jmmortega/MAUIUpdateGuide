# Register services

First big change, register services change completely, and it's better use the actual system with MauiAppBuilder, this it's allocate in a ServiceProvider and ServiceCollection. If you use DependencyService or another locator service, it's time to change, no make sense use the old one. If you use a abstraction to avoid work with dependency injection service directly (good work) time to change your abstraction to adapt for your injection service.

## Abstraction outside MAUI project

If your abstraction was outside of Forms app, that make sense, you need communicate with ServiceProvider that locates in MAUI project a good practice it's create a static method inside that allow set our ServiceProvider interface

## RegisterLazySingleton

If you need use LazySingleton, IServiceCollection doesn't have a option to do that, anyway we can use solutions like [this](https://stackoverflow.com/a/44936287/2469223) problem solved.