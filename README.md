# Solution Load sample

[![Build status](https://ci.appveyor.com/api/projects/status/s0wahy0lg80gaggm?svg=true)](https://ci.appveyor.com/project/madskristensen/solutionloadsample)

**Applies to Visual Studio 2015 and newer**

This example shows how to listen to solution events when the package might not be initialized until after the solution has loaded.

Clone the repo to test out the sample in Visual Studio 2017 yourself.

## What is the problem?
In Visual Studio 2017 Update 8, packages will no longer be auto-loaded immediately when the following is true:

* Package inherits from AsyncPackage
* Uses `ProvideAutoload` attribute
* Supports background load
* VS is starting up or solution is being loaded 

Instead, the package will be initialized **after** the startup or solution load depending on the `ProvideAutoload` context. This is done for performance reasons and is generally speaking a net benefit to most, if not all users.

The consequence is that the solution might already have been loaded when your package initializes and no solution load events will be fired until the user opens another solution. 

[See full Pakcage class in the source](src/VSPackage.cs)

## Further reading

* [How to use AsyncPackage with background load](https://docs.microsoft.com/en-us/visualstudio/extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background)
* [Use Rule-based UI context for package load](https://docs.microsoft.com/en-us/visualstudio/extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions)

## License
[Apache 2.0](LICENSE)