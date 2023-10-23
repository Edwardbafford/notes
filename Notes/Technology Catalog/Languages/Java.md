
# General

**Java** is an object oriented, statically typed programming language defined by a specification, **JLS**.

The **JVM** is a runtime and environment that is defined by a specification, **VMSpec**, which ensures consist behavior but flexibility for different vendors to develop their own versions.

`.java` files are compiled by `javac` into `.class` files that consist of bytecode and loaded into the JVM.

New Java releases happen every six months with a long term release every three years.

# New Features

## Var

Added type inference to reduce boilerplate

 `var varName = ...`

Should be used for simple initializers where the scope is limited.

## Collection Factories

A simple way to declare collection literals. 

`List.of(...)`
`Map.of(...)`

## Removed Libraries

Explicit imports are needed for following libraries
- JAXB
- JAX-WS
- SE

## HTTP 2

New library to support HTTP 2 to allow for
- low overhead binary headers
- multiple connections per socket
- multiple requests per connection
- enforce TLS

## Streams

Stream is an interface that has funcational methods such as `map()`, `filter()`, `reduce()`, etc.

Create a stream from a collection using `stream()` method.

`collect()` method returns a collection from the stream object.

This framework allows for functional programming.

Avoid parallel methods unless you can prove they improve performance.

## Text Blocks

Allow for string literals that extend over multiple lines without escaping.

Start and end the sequence with `"""`

## Switch Expressions

Similar to switch statements.

Use `yield` to pass back value to a variable.

Functional form exists that can compress multiple cases into a single "switch".

Must handle every possible case for your input type or it won't compile. Because of this, it works well with enums.

## Records

New type of Java class for POJO where the class is nothing but it's fields.

Compiler automatically creates necessary methods and a constructor.

```
public record recordType(
	int intValue,
	String stringValue,
	...
)
```

Created equals method simply compares all fields.

Data is immutable.

Similar to tuple in other languages.

Can create custom constructor or static methods within the record, usually to transform something into a record.

## Sealed Types

A class can be extended but only by a known list of subtypes.

Subtypes are defined as inner classes.

```
public abstract sealed class Pet {
	...

	public static final class Cat extends Pet {
		...
	}
}
```

# Modules

A new way of packaging and deploying code.

Collection of packages and classes that are loaded as a single entity.

Benefits
- Detect dependency problems at compile time
- Proper encapsulation

Dependencies are explicit which allows hard guarantees that can be used by the compiler to catch issues early on.

Modules can choose to protect their internal code, giving them the option to change it in the future without destabilizing other code bases.

Two new formats introduced
- JMOD is similar to JARs
- JIMAGE represents a runtime image

`jimage` can be used to show metadata about a Java runtime image.

Stack frames are now qualified with module name: `at java.base/java.lang.Integer.parseInt (Integer.java:652)`

`module-info.java` file at root of project defines
- module name
- module dependencies
- publicly available packages
- relfective access permissions
- services provided
- services consumed

`export` keyword defines publicly available package.

`export ... to ...` package is available to a specific other package

`requires` defines a module dependency.

`requires transitive` to define other module/s needed to use the current module.

`open` keyword to provide reflective-only access to an otherwise internal package.

`opens ... to ...` for specific package reflective access.

Module names are global.

Modules are loaded through module path variable, similar to classpath.

JVM creates module graph based on dependencies.

Module types
- Platform - come from the JDK itself
- Application - modularized application
- Automatic - come from JAR files on module path
	- automatic name
	- all packages are exporte
	- depends on every module in the module path
- Unnamed - classes and JAR on the classpath
	- depends on every module in the module path

Command-line switches can be used to adjust module behavior at compile time.

Run main class of a module: `java --module-path ... -m ...`

`jlink` can be used to create a small java runtime out of modules.
# Classes

`javap` CLI can be used to dissect Java class files.

`.class` file components
- type descriptors to describe methods
- constant pools are class elements that reference each other

## Class Loading

At runtime `.class` files are loaded and processed by the JVM.

Steps
- Verification - syntax checks
- Preparation - memory allocation
- Resolution - resolve dependencies
- Initialization - run static blocks and create `Class` Java object representing the class

Class loaders are used to load class files and other resources. There are built in implementations but custom ones can be created as well.

Class loader use cases
- Load from unusual places
- Dynamically load classes (like in dependency injection)

## Runtime

**call stack** is the stack of methods within a thread.

**evaluation stack** is where operations interact.

Each type of operation is defined by an **opcode** within the byte code. Each opcode manipulates the evaluation stack.

## Reflection

Manipulation of class objects at runtime.

- Get classes
- Get methods
- Get modules

# Concurrency

## Block Structure

Original tools for implementing concurrency

`synchronized` keyword is used to lock a method or an object, preventing other threads from entering that method or using a synchronized block of that object.

Locks used by `synchronized` can cause deadlocks!

`private synchronized boolean withdraw(int amount) { ... }`

`synchronized (object) { ... }`

After synchronized sections run all changes are flushed to main memory.

`volatile` keyword is used to define a field. It ensures that main memory is read before using the field and any operation flushes the result to main memory. 

Acts like a mini synchronized block but without locks.

## Threads

Java objects that are abstractions of an actual OS thread.

States
- New - thread on OS does not exist yet
- Runnable - while running
- Waiting - indefinitely waiting based on some system instruction 
- Timed waiting - waiting based on a timer
- Blocked - waiting on a resource
- Terminated - thread has been stopped forever

Threads are implemented by Runnable objects and can be interacted with through their methods.

```java
Runnable r = () -> { ... }
var t = new Thread(r);
t.start(); // starts thread
t.join(); // waits for thread to exit
```

`t.interrupt()` tells the thread to exit but the thread must check for the interrupt signal internally using `Thread.interrupted()`.

Threads can have custom exception handlers set through `t.setUncaughtExceptionHandler((t,e) -> { ... })`.

`t.stop()`, `t.suspend()`, and `t.resumes()` should never be used as they are dangerous and can lead to deadlocks and inconsistent states.


## Library

New `java.util.cncurrent` library for high level functionality.

**Atomic** classes provide atomic operations as a wrapper for Java primitives.

**Lock** classes provide options for blocking sections of code between threads.

**CountDownLatch** is a type of lock that can be counted down and block threads until the value equals zero.

**ConcurrentHashMap** thread safe version of a map.

**CopyOnWriteArrayList** is a list that returns a copy of the list anytime a change operation is called.

**BlockingQueue** is used to can force threads to wait when trying to put and take items from the queue.

**Futures** represent an asynchronous task that allows you to wait for the response.

**Completable Future** is an implementation of the Future interface that can be shared between threads and can pass in and receive a value.

**Tasks** are a new way to represent a thread.

**Executors** are used to help developers work with thread pools.

Fixed thread pools can be created with a fixed number of threads. Tasks are submitted to the executor as a queue and processed by one of the threads.

Cached thread pool will create and delete threads as needed by the number of tasks.

Scheduled thread pool will allow for scheduled tasks to be run.

