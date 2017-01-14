==========
Singletons
==========


 * Singleton<T>

   - lazily instantiate an instance of a concrete type

 * ManualSingleton<T>

   - Instance property will not lazily instantiate.  It will return null if it has not been initialized.

   - GuaranteedInstance will lazily instantiate.
   
     - If T is an interface type, and the interface has the [DefaultImplementationType], it will look to ManualSingleton<DefaultImplementationType>.Instance. 