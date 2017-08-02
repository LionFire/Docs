============
Applications
============

Takes the kind of approach used in composing ASP.NET Core apps and makes it generic to all .NET Core (nothing ASP.NET-specific.)

Features:
 - ServiceCollection
 - Components can be 

Extensibility
 - Override AppHost to replace
   - IServiceCollection NewServiceCollection

Usage
 - Create an AppHost
 - Add components via Add()
 - IsInitialized will be true
 - Initialize()
    - Bootstrap()
        - IReadHandle components will be replaced with their targets
        - ITemplate components will be replaced with instantiations
        - IConfigures<IAppHost> components will configure the AppHost
        - IConfigures<IServiceCollection> components will configure services 
        - ServiceProvider will be built from ServicesCollections (uses Microsoft.Extensions.DependencyInjection by default, but overridable)
        - IRequiresServices components will have ServiceProvider injected
        - Properties marked [Dependency], or specified by IHasDependencyProperties will be injected from IServiceProvider
    - IInitializable components will be initialized
      - Initialize will be repeatedly invoked on components until they all return true.  (If no progress is made, an exception is thrown.)

  


 