==================
Referencing Assets
==================

Usage
=====

Creating an Asset Handle
------------------------

.. code-block:: C#

   var hTower = new HAsset<TCapacitor>("Tower3");
  
Creating an Asset Reference
---------------------------
  
.. code-block:: C#

   var rTower = AssetReference<TCapacitor>.FromName("Tower3");

