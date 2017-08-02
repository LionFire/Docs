===============
Messaging: MBus
===============

A pub/sub facade and nano-framework for strongly-typed messages.  It follows the same interface as the `Caliburn.Micro EventAggregator<https://caliburnmicro.codeplex.com/wikipage?title=The%20Event%20Aggregator>`_.

Used by LionFire code to generate ambient messages.  Applications can choose to ignore these messages, feed them through to another event bus (such as Caliburn Micro's EventAggregator), or Subscribe to them via the default implementation. 

Usage: Publishing
=================

using LionFire.Messaging;

Publish
=======

object myMessage = ...;
EventBus.Publish(myMessage);

Publish in Context
==================

EventContext ctx = ...;
EventBus.Publish(myMessage, ctx);

Subscribe
=========

object myMessage = ...;
EventBus.Subscribe(myMessage);

Use Own Broker Implementation
=============================

Default Instance
----------------
LionFire.Structures.ManualSingleton<IMessageBroker>.Instance = myBroker;

Injection Context
-----------------
(Not implemented yet but see DependencyInjection code for how it could be done.)