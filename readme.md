# Nancy.EmbeddedContent

A code utility to aid in serving embedded content over a
[Nancy](http://nancyfx.org) application (on .NET 4). An example of what to do with
this is shipping a `dll` containing static files instead of a bunch of static files.
 
**Disclaimer**: i've written this package because i'm stuck on .NET 4 for a
while longer. Instead of using this project, i'd recommend using
[Microsoft.Owin.StaticFiles](https://www.nuget.org/packages/Microsoft.Owin.StaticFiles/)
if your project can use .NET 4.5.

## Usage

This is meant to be downloaded and included in your own source code. To utilize,
clone this code, and import the project into your solution.

Views will be discovered automatically as long as the build action for each
file you want served is set to **Embedded Resource**.

To serve embedded files as static content, you will have to add a static content
convention to your bootstrapper:

```c#
public class Bootstrapper : DefaultNancyBootstrapper
{
    protected override void ConfigureConventions(NancyConventions nancyConventions)
    {
        nancyConventions.StaticContentsConventions.AddEmbeddedDirectory("/Content");
    }
}
```
