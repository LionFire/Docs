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