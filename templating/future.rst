============
Future Ideas
============

Use Multi-type framework instead of templating and parameters
  * obj.AsType<TMyClass>(), and obj.SetType(myTemplate, frozen: true)
  * obj.AsType<PMyClass>(), and obj.SetType(myParams, frozen: true)
  * POCO relationship: [Template(typeof(TMyClass)] [Params(typeof(PMyClass))] class MyClass { } // And use generator to create public TMyClass Template { get; }
    - or Template base class: class TMyClass : Template<MyClass, PMyClass> { }