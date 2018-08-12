* How does using actors work better than just having functions that return
futures?
  - they help when you need to keep some form of state
  - they also *scale* into a cluster very easily
* The main `QuickStartServer` is runnable because it `extends App`
* you should split all the routes into their own files, and then use the
  `concat` directive to combine them
  - `val routes: Route = concat(userRoutes, configRoutes, ...)`

Creating a route file
------------------------
* routes that are rejected move up the hierarchy until they reach the root route
  - you should use `concat` over `~`, but they both work
* the `entity(as[User])` converts the request body into the `T` object (here
  it's `User`)

Binding HTTP Server
--------------------
* `ActorSystem`: can be used by Akka Streams too
* `Materializer`: basically the thread pool for Akka Streams

Marshalling
------------------
* they use Spray JSON in the example
* you have to provide a format instance for a type, if you plan on returning it
  with `complete(MyType)`
  - this is so you don't expose some type by accident
