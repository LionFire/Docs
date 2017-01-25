====
Core
====

A collection of minimalistic utilities and nano-frameworks that are too small to have their own framework.

LionFire.Extensions.Runtime
---------------------------
 
 * Small set of commonly used augmentations to BCL
 * Some miscellaneous classes that are alternatives to BCL classes or fill common gaps.
 * Trying to strike a balance of keeping this small, while collecting some commonly used small items, while avoiding larger and opinionated items that are likely to not be used at some point in the future.    

 * Structures
   - `Singletons <runtime/structures/singletons.html>`_
     - Singleton<T>
     - ManualSingleton<T>
   - `Applications <applications/applications.html>`_

 * `MessageBus <messagebus/index.rst>`_
   - MBus.Publish("Hello")
   - IObserver<T> sub = MBus.Subscribe<T>();

 * `DependencyInjection <dependencyinjection/index.rst>`_

LionFire.Environment
--------------------

  * Commonly used variables used for environment, similar to System.Environment but with some helpers and additions commonly used in LionFire applications.

LionFire.Annotations.Compilation
--------------------------------

  * Attributes used at compile time, for use with weavers such as Fody
    

1st-Gen
=======

1st-Gen LionFire.Utility.dll
----------------------------

A large assortment of things I have found useful.  I plan to refactor this into smaller executables.

* Application/Shell framework - facilitates UI/application separation.  (Separate shell implementations for WPF and console apps exist.)
* Serialization
* Logging
* ...

Planned
=======

LionFire.Core.Abstractions
--------------------------

This will be a small collection of common abstractions:

* Logging abstraction
* IOC abstraction (TinyIOC)
* EventAggregation abstraction

LionFire.Core
-------------

Default implementations for the abstractions in LionFire.Core.Abstractions

LionFire.Typing
---------------

Support for multi-type objects.
