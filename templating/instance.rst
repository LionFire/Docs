========
Instance
========

Overview
========

Defining an Instance Type
-------------------------

Everything in the LionFire Templating framework ultimately exists to support the instance. An instance is simply whatever type of object you want to work with.  

Here are some ways of defining an instance:   

POCO Instance
^^^^^^^^^^^^^

.. code-block:: C#

  public class MyClass 
  { 
    // ...
  }
  
ITemplateInstance Instance
^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: C#

  public class MyClass : ITemplateInstance 
  { 
    // ...
  }
  
ITemplateInstance Instance
^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: C#

  public class MyClass : ITemplateInstance 
  { 
    // ...
  }
  