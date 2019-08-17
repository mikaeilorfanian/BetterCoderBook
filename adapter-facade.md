# Adapter, Facade

An Adapter sits between a client and a vendor. It receives messages from a client and translates them so they make sense to the vendor.

## The Flow

The Client sends a request to the Adapter by calling a method on it using the Target Interface.

The Adapter translates the request into one or more calls on the Adaptee using the Adapter interface.

The Client receives the results and never knows of the work done by the Adapter.

The Client and Adapter are decoupled. They don't know about each other's existence.

**Is it possible for one Adaptor to work with multiple Adaptees?**

Yes, because it's possible that you need to use multiple classes to provide the interface that the Client expects. The intent here is to alter the interface of the multiple Adaptees to something the Client expects.

### Two-way Adaptor

An Adapter that implements two interfaces. Each is used by a different client, but the Adaptee is the same.

## The OO Design of the Adapter Pattern

Object composition is used to wrap the Adaptee so we can also wrap any sub-class of the Adaptee as they have the same interface.

The Client is bound to an interface not an implementation. This means the client can use other Adapters that implement the Target Interface. It also means that in future we can make more Adaptors which will work with this or other Clients relying on the Target Interface.

#### Class Adapter

It requires multiple inheritance. Instead of using composition we using inheritance. You inherit from the Interface Target and the Adaptee.

## The Facade

To simplify the interface, it hides the complexity of one or more classes behind a clean interface. It doesn't encapsulate sub-system classes. It's just a simplified interface over the systems' functionality.

The low-level API of the sub-systems is still available and can be used.

A Facade doesn't have to just a pass-through. It can have some logic to organize the work between subsystems

The sub-systems can be covered by more than one Facade.

A Facade decouples client code from sub-systems. Changes to sub-systems don't affect the client.

To use the Facade pattern we create a class or function that simplifies and unifies a set of more complex classes or functions that belong to a sub-system. The difference between Facade and Adapter is the intent. Facade intends to simplify the use of a sub-system.

## Decorators vs. Adapters

**Decorator**

Adds new responsibilities or behavior. Decorators can be nested and they don't know about each other.

They never convert the interface of the object they wrap.

**Adapters**

They allow clients to make use of new libraries and subsets without changing any code.

They always convert the interface of what they wrap.

## The Principle of Least Knowledge

Reduce the interactions of objects to a few "close" friends in order to reduce coupling between objects and classes so that changes don't cascade globally but locally.

### Guidelines for the Least Knowledge Principle

Given an object A, its methods should invoke only those methods that belong to

* the object A itself
* objects passed in as parameters to this object A's methods
* the objects created by this object A
* objects that are saved as instance variables of object A

These rules disallow calling methods of objects \(let's say C\) that are returned from calling other methods \(B's methods\). Otherwise, A would be making requests of C object's sub-parts meaning A has knowledge of C's logic.Instead, we should ask B to make those requests for us.

Below is a class that adheres to the above rules:

```python
class Car:
    def __init__(self, engine):
        self.engine = engine

    def start(self, key):
        doors = Doors()
        authorized = key.turns()

        if authorized:
            self.engine.start()
            self.update_dash_display()
            doors.lock()

    def update_dash_display(self):
        pass
```

### Facade and the Least Knowledge Principle

The client has only one friend: the facade object.

