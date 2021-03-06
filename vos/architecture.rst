======================
Architectural Overview
======================

External
========

* LionFire.Utility (to be refactored)
  - Multitype - Tools for manipulating objects with one or more types (decorator pattern)
  - Overlay - tools for overlaying and merging objects
  - Serialization

Foundation
==========

* `ObjectBus <../objectbus/index.html>`_ (aka OBus)

Sophistication
==============

* Vos - OBases including Vos OBases can be mounted at a Vos path.  Multiple OBases can be mounted at the same path with different read/write precedence.
  - Packages - Load/unload packages of data into the Vos tree.  Can be used to load expansion packs for games.
  - Overlays - When there are objects at multiple layers, this supports merging behavior.

Convenience Frameworks
======================

* Assets - a simple convention mini-frameowrk for providing convenient access to instances of a particular data type based on a key specific to the type. (Effectively provides a flat alternative to the Vos hierarchy, similar to RDBMS with tables and primary keys, although subpaths are still supported.)

* Templating - Templates provide data that is shared by many instances.  Instantiation parameters are applied to a template to create an instance.

Tools
=====

* Vos explorer
* Hopefully more coming soon

External Dependencies
=====================

* JsonExSerializer (may be replaced with another, such as Json.NET)