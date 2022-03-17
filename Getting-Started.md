# **Now what?**

 MAUI isn't prepare for production. (If you use this in production you are a real problem of sanity...)

MAUI can be change, a great point from Xamarin team, it's all the time hear the community and continue progress and change taking dev feedback very serious.

So you have three options in this moment:

- Come back with this issue the next year.
- Create a POC to start to testing MAUI, focusing in issues that are similar for your application.
- Create a experimental branch for your application and migrate your app to MAUI. 

We continue thinking in this point:

## **Let's do it**

Why you create a POC? When you can create a experimental branch and try to mantain a bit every month or every quarter to prepare for new changes?

So let's do it!

### 1) Migrating to experimental

You have a good guide to migrate to MAUI [here](https://docs.microsoft.com/en-gb/dotnet/maui/get-started/migrate) take for sure, must be appear a lot of issues when you migrate, but you can do it!

### 2) Migrate your renderers to handlers

That you show before, you can map your renderers to use in MAUI, but, it's better if you change this renderers and effects for the new system for handlers.

If you use third party controls libraries, move too. 

### 3) Change your startup system

Change your Startup system, to use MAUI host. 

### 4) Try to remove the rest of references related with Xamarin Forms

In this moment, probably you can't remove Xamarin Forms package from your application, only for the fact you use third party libraries that should use Xamarin Forms. 

However, we talk about your code, try to isolate Xamarin Forms usage inside of your application, remove things related such as Command, BindableObject, DependencyService, MessengerService. If there something that you can't remove, a good practice is create an interface to isolate this usages.

### 5) Rinse and repeat

Come back to this branch, everytime that you could. Merge your new changes from your production branch to take updated about your domain and then update to try to maintain for the new MAUI changes.

## **More things to do (or things would do to prepare to MAUI instead of create a POC)**

- If you create a new renderers, try to rethink to avoid to do it
	- In a near future you need to move to handlers, so less work to update.
- Try to refactor your Views to small chunks
	- Although you can use MVVM in MAUI, when you migrate your application. IMO, MAUI will focus to MVU architecture, so if you refactor your view to small chunks your project can be more prepare
	to migrate to MVU
- Try to refactor your ViewModels to small chunks
	- When you "chop" your views, your ViewModels make sense to convert to small ViewModels and separate more and more your logic.
- Isolate your use from Xamarin Forms
	- When you migrate to MAUI we lost all Xamarin Forms support. So you will isolate all Xamarin Forms dependencies to help for your migration. A good start it's isolate all your logic outside in another project and remove all reference from Xamarin Forms.



