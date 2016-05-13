========
Overview
========

Jared Thirsk and LionFire Games are making available various open source software packages.  Software is all C# so far, with some Aurelia-based web apps potentially coming at some point. 

Repository locations:
 * http://github.com/lionfire
 * http://github.com/jaredthirsk

Current Status
--------------

Although I intend to put up several open source projects, not (m)any are up yet.  My priority right now is to start collecting documentation for my own purposes, to capture the design for some more complex bits.

My other priority right now is to ship some (closed-source) software, but if you stumble upon this site and think some of my software may be useful, let me know by email (jared+public at thirsk.ca) and I'll see if I have time to upload these projects.

Overview of Projects
====================

VOS
---

Vos (Virtual object system) is an ambitious attempt to create a multi-purpose virtual filesystem, except centered around objects.  As with other virtual filesystems, the underlying data store could be files on a disk, hierarchical data provided by some sort of plugin, or virtual in-memory objects (like the linux /sys filesystem.)  

Child Projects
^^^^^^^^^^^^^^
* ObjectBus - data abstraction layer
* Assets - a microframework to flatten

Dependency Projects
^^^^^^^^^^^^^^^^^^^
  
* LionFire Core 
  * LionFire.Utility - an assortment of assorted things, to be refactored.
  * LionFire Serialization - abstraction of serialization (currently has a focus on JSON)
  

Templating
----------

Templates are classes that can be serialized and deserialized, and then used to create instances.  Optionally, a Parameters object can be used to set the state of the instance.

Object State
^^^^^^^^^^^^

A microframework useful for saving and loading the state of an object.
