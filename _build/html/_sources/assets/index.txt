==========
Vos Assets
==========

Assets are referenced by type and a name (or path) that is unique to that type.  This provides a conveneint way to access instances of a type by name without worrying about where they are in a Vos tree.  

Assets will be stored in a location configured once by the application, and the location for each type can be configured independently.

This is a child project of Vos.

Overview
========

Creating an Asset
-----------------

.. code-block:: C#

   var hTower = new HAsset<TCapacitor>("Tower3");
  
  
.. code-block:: C#

   var rTower = AssetReference<TCapacitor>.FromName("Tower3");

