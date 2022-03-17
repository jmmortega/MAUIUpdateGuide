#Known Errors

## Problem with package

**In ios:**

It's quite possible that your app, should be different project references that not require platform specific version from net6.0 (-android, -ios...) when you build should probably receive an error like that: ```error NETSDK1005: Assets file '{0}/obj/project.assets.json' doesn't have a target for 'net6.0-ios'. Ensure that restore has run and that you have included 'net6.0-ios' in the TargetFrameworks for your project.```

**Solution**

Delete all bin and obj folders to allow restore 


 ## ```error MSB4044: The "GetMlaunchArguments" task was not given a value for the required parameter "AppBundlePath"```


## InitializeComponent has error.

https://stackoverflow.com/questions/68639893/maui-project-cannot-add-a-new-page

This is a known issue for tooling MAUI team.

- https://github.com/dotnet/maui/issues/3171
- https://github.com/dotnet/maui/issues/3200


**In android:**
error MSB3072: The "Exec" task needs a command to execute. [{0}}.csproj]