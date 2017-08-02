=============
Core Concepts
=============

`Vos <vos.html>`_ - Virtual Object System
  The Vos is a object system (like a filesystem).  There is one instance per running application.
  
Vob path
  Vos is a hierarchical system for objects in which each object has a path.  Forward slashes are used for path separators.

`Vob <vob.html>`_  - **V**s **Ob**ject Node *(Rename to Von?)*
  At every path, there exists (on demand) one canonical Vob node in an application.  What can be done at each Vob node depends on hos Vos is configured.

`VobHandle <vobhandle.html>`_ - *(Rename to Voh?)*
  A VobHandle has a path and therefore has a corresponding Vob.  It also has a type, which may simply be object, but it is usually a more specific type.  It is used to retrieve an object of the specified type (or a type that can be assigned to the specified type) from the Vos.  It holds a reference to an object and can be used to save the object back to Vos.  VobHandles are often shared within an application so it only has one copy of the object instance. 
  
`Mount <mount.html>`_
  Mounts are what make Vos useful.  Filesystems, databases, in-memory objects can all be mounted into the Vob tree.  Multiple underlying stores can be mounted at the same location, and assigned read and write priorities which are used to determine how objects are persisted to Vos. 
  
Other Terms
===========  
  
Vob root
  The root Vob has a path of /.  There is only one Vob root supported in an AppDomain. 

Vob tree
  There is only one root Vob, and therefore one Vob tree for the currently running application.  
  
Chroot - Change root
  Chroot is the process of assigning another Vob as root and then forcing part of an application to run within that root, as though it was the actual root.  Chroot is not currently available but perhaps it will be considered for some day.  It may be useful in certain scriptable or hosting applications in which limited information should be made available to scripts.
  
.. toctree::
   :titlesonly:
   :maxdepth: 2
   :hidden:
   
   self
   vob
   vobhandle
   mount
   vos
     