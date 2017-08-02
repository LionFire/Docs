===================
Class State Machine
===================

GitHub home: https://github.com/lionfire/class-state-machine


.. toctree::
   :titlesonly:
   :maxdepth: 2
   :caption: Topcis
   
   roadmap
   test

Overview
===============

Quick Start
============


.. code-block:: C#

    [Flags]
    enum MyState { 
        [StartingState]
        Uninitialized = 1 << 0, 
        Ready = 1 << 1, 
        Started = 1 << 2, 
        Finished = 1 << 3 
    }; 

    enum MyTransition 
    {
        [Transition(MyState.Uninitialized, MyState.Ready)]
        Initialize, 
        [Transition(MyState.Ready, MyState.Started)]
        Start, 
        [Transition(MyState.Uninitialized, MyState.Finished)]
        Finish 
    };

    [StateMachine]
    public class MyClass
    {

      public void OnInitialize()
      {
      }

      private string mustNotBeNull;
      public bool CanLeaveUninitialized()
      {
	      if(mustNotBeNull == null) return false;

	      return true;
      }

      public void AfterReady(StateChangeContext context)
      {
	      context.Cancel();
      }

      public void OnStart()
      {
      }

      public void OnFinished()
      {
      }

      public void Test()
      {
        Console.WriteLine(stateMachine.CurrentState); // Uninitialized

        mustNotBeNull = "hello";
        Initialize();
        Console.WriteLine(stateMachine.CurrentState); // Ready 
        
        Start();
        Console.WriteLine(stateMachine.CurrentState); // Started
        
        Finish();
        Console.WriteLine(stateMachine.CurrentState); // Finished
      }

      // Members not defined here are generated in obj/.../MyClass.{hashcode}.generated.cs

    }

Design Goals
=============

 - Standardize how typical state machines are made
 - AOT compatible: no Reflection.Emit
 - Harness design-time code generation to eliminate boilerplate and promote standardization.
 - Allow users to create reusable state machine models, and trim them down to a class. (TODO)
 - Support hierarchical state machines (TODO)
 - Efficently and conveniently flexible method handlers
   - OnEntering{State}() or On{State}
   - OnLeaving{State}() or After{State}
   - On{Transition}() 
 - Flexible language
   - On{Transition}(): OnInitialize or OnInitializing
 - Flexible events:
   - StateMachine.StateChanged
   - StateMachine.StateChanging
   - {Transition}
 - Guards
   - Can{Transition} methods
   - CanLeave{State} / CanEnter{State} methods
 - Cancelation
   - StateChangingContext


Roadmap (features under consideration)
===================================

 - Replace more reflection with design-time generated code

 
