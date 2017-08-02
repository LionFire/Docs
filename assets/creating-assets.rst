====================
Creating Asset Types
====================

POCO
====

.. code-block:: C#

  public class MyAsset
  {
    // ...
  }
 
Implements IAsset
=================
  
.. code-block:: C#

  public class MyAsset : IAsset
  {
    // ...
  }
  
Subclass of AssetBase
=====================

.. code-block:: C#

  public class MyAsset : AssetBase
  {
  }
  
Subclass of AssetBase<AssetType> (Concrete)
===========================================

.. code-block:: C#

  public class MyAsset : AssetBase<MyAsset>
  {
  }
  
Subclass of AssetBase<AssetType> (Interface)
===========================================

.. code-block:: C#

  public interface IMyAsset { }
  
  public class MyAsset : AssetBase<IMyAsset>, IMyAsset
  {
  }