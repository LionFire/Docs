==========
Templating
==========

The Templating framework assists with structuring template info that is shared with many objects, and parameters that can be used to initialize individual objects. 
 
Core Concepts
=============

`Instance <instance.html>`_
  The object you work with.

`Template <template.html>`_
  A serializable object that can be referenced by several instances at runtime to access common information.  An instance has a type, but it can be further constrained by which Template is assigned to it.
  
`Parameters <parameters.html>`_
  Parameters provide additional information to the instance being created.
    
`Instantiation <instantiation.html>`_
  An instantiation is simply a combination of a Template and optionally Parameters.
  
.. toctree::
   :titlesonly:
   :maxdepth: 2
   :hidden:
   
   self
   instance
   template
   parameters
   instantiation
   future
   