===================
Class State Machine
===================

GitHub home: https://github.com/lionfire/class-state-machine


.. toctree::
   :titlesonly:
   :maxdepth: 2
   :caption: Topics
   

Overview
========

A convention-oriented state machine for typical C# classes.  

Status
------

Pre-alpha preview ready.  Give it a shot and give me feedback.

Working:
 - Transitions
 - States
 - Event handlers

See the unit tests for examples. 

Design Goals
------------

 - Make it easy to turn typical C# classes into state machines 
 - Make it easy to enforce conventions and state machine logic
 - Augment existing common coding style, with minimal imposition
 - Unintrusive on target codebase
   - No dependencies (aside from .NET Standard)
   - No base class
   - Optional code generation (separate DLL)
 - Harness Roslyn to generate design-time code that offers Intellisense and reduces the need for reflection during run-time startup  
 - AOT compatible in order to run on iOS: no Reflection.Emit
 - Harness design-time code generation to eliminate boilerplate and promote standardization.
 - Allow users to create comprehensive state machine models, and have them autommatically trimmed down to the used states and transitions.
 - Support hierarchical state machines (FUTURE)

Features
--------

 - Efficent and conveniently flexible method handlers
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
 - Allow user to override all conventions (FUTURE)

Requirements and impositions
----------------------------

 - Generated state machine code must be on a partial class with the [GenerateStateMachine] attribute.
 - States and transitions are defined as enum flags.  
   - FUTURE: Allow arbitrary objects as long as they are IEquatable?
 - Transition flags have attributes that define from and to states. 
   - FUTURE: Allow specification of transition info provider via provider type provided to [GenerateStateMachine] attribute
 - [StartingState] attribute on a member of the state enum indicates initial state 
   - FUTURE: Allow specification of starting state via [GenerateStateMachine] attribute

Roadmap (features under consideration)
======================================

 - Hierachical state machine support
   - Sub-state machine example: paused/unpaused under running
   - Sub-state machine example: limited exit states from substate machine
 - Replace more reflection with design-time generated code
 
 - Extension DLL: Tools for state machines:
   - IStateMachine and IHas<IStateMachine>
   - IStateMachine members:
     - CurrentState
     - StateChanging event

  - Optional extensibility / lightweightness features:
    - Optionally parameterized state changes
    - Optionally remember previous transition
    - Optional zero meomory allocation (can be helpful in games)
  - Wrapper/Adapter for goal-seeking, if the desired state change is only possible with multiple steps.


Quick Start Sample
==================

Reference these 2 nuget packages:
 * LionFire.StateMachines.Class.Generation
 * CodeGeneration.Roslyn.BuildTime

Nuget.config:

.. code-block::
 
    <?xml version="1.0" encoding="utf-8"?>
    <configuration>
      <packageSources>
        <add key="api.nuget.org" value="https://api.nuget.org/v3/index.json" />
        <add key="corefxlab" value="https://dotnet.myget.org/F/dotnet-corefxlab/api/v3/index.json" />
      </packageSources>
    </configuration>

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

    // NOTE: Due to a limitation at the moment the State and Transition types have to be in a separate assembly. (Pull-requests welcome.)

    [StateMachine(typeof(MyState), typeof(MyTransition)]
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



