=======================
Core (and dependencies)
======================= 

[Overhaul / refactor in progress as of Oct 2017]

A core set of infrastructure and mini-frameworks to support the LionFire.Core Framework's information architecture strategy.

To use:
 * Via nuget, reference the metapackage 'LionFire.Standard' (TODO)

DLLs from lower levels to higher:

LionFire.Base
--------------
 * Augmentations to the .NET Base Class Library
 * (FUTURE: Consider making these single .cs file nuget includes)

 * LionFire.Execution.AutoRetry
  

LionFire.Structures
-------------------
 * Various collection classes that are used frequently and useful on their own.
 * (FUTURE: Consider merging with LionFire.Base)
 * IComposable
   * Standardized interface for composition: adding and accessing children
 * IKeyed
   * Allows keys for dictionaries to be extracted from within an object

LionFire.Referencing.Abstractions
-----------------------------------

References to objects!  References can change, so references can be synced.  Since things can get out of sync, there can be version control and automatic and manual merge conflict resolution.

 * Handles
   * IReadHandle<T> - lazily loadable reference to an object
   * IHandle<T> - combination of IReadHandle<T> and IWriteHandle<T>
   * Idea for prefixes:
     * RSomething - readonly handle
     * HSomething - readwrite handle.
     * WSomething - writeonly handle.
 * References
 * Lit (version control)

LionFire.Referencing
---------------------
 * ReferenceFactory
   * IReference ToReference(this string uri);
 * TODO - HandleResolver 

LionFire.Core(.Abstractions)
--------------------------------

TODO: Figure out how much of this to spin out into separate DLLs.

 Core frameworks that provide cohesion points among LionFire Libraries:
 * Ambience
   * Context-oriented programming: 
     * Simple apps: use statics
     * Complex apps: use ThreadStatic data
     * Example uses: InjectionContext, PersistenceContext, LogContext
 * Events: PubSub/Logging/Alerting/Notifying
 * Dependency Injection / service location
   * Defaults
   * Singleton
 * MultiTyping
 * Type Resolution
 * Validation


 * Structures
   - `Singletons <runtime/structures/singletons.html>`_
     - Singleton<T>
     - ManualSingleton<T>
   - `Applications <applications/applications.html>`_

 * `MessageBus <messagebus/index.rst>`_
   - MBus.Publish("Hello")
   - IObserver<T> sub = MBus.Subscribe<T>();

 * `DependencyInjection <dependencyinjection/index.rst>`_
   - Defaults class: Get/Set methods

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
