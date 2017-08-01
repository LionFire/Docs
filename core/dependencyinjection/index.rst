============================
LionFire.DependencyInjection
============================


Convenience
-----------

 - Defaults (namespace: LionFire)
   - Set<T>() 
     - Sets in ManualSingleton<T>.Instance
   - Get<T>()
     - Tries ManualSingleton<T>.Instance
     - Tries result from ManualSingleton<IServiceProvider>.Instance?.GetService();
   
   FUTURE: Allow Get/Set methods to be swapped out for custom ones.
 
 - TryResolveDependencies(IEnumerable<object> objects, IServiceProvider serviceProvider)
   - Resolves dependencies on each object
     - object can specify which properties explicitly via IHasDependencyProperties
     - otherwise, it will look for properties marked [Dependency]