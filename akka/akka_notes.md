Basics
===========
* The actor API uses messages.
  - there is no shared state between actors. If you want the state of an actor,
    you must use the messaging API to ask its state

* Messages can by of arbitrary type
* Actors should have a `props` method that describes how to contruct the actor
* An Actor can have state. Accessing or mutating the internal state of an Actor is fully thread safe since it is protected by the Actor model.
  - meaning you can store `var`s.

* you get `sender()` within the body of an actor for free

Creating Actors
-----------------
* you **cannot** create actors with the `new` keyword
  - you must use a factory. This is the `actorOf` method that belongs to
    `ActorSystem`.
  - this factory doesn't return an instance of the Actor, it returns an ActorRef
  - **Important**: This is what they mean by "location transparency"

Communicating with Actors
--------------------------
* Actors have message queues called "mailboxes"
  - these are ordered as FIFO
