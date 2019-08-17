# Loose Coupling

## What is Loose Coupling

This is what happens when you have tight coupling: you change a function's internals, then you need to look up all the places where that function is used and that leads you to changing the clients of that function.

This happens because the client code is tightly coupled to the function you modified.

To avoid having to make all those changes you need to make the client and the function loosely coupled.

Many good coding techniques like design principles and patterns are made to avoid tight coupling of code. Design principles and patterns are used everywhere not just in programming. For example, once you learn how to drive a car you can drive any car. Or, you go to the same postal service branch for sending all kinds of letters or packages. Imagine how painful it would be if every couple of years you'd have re-learn driving a car because a manufacturer has "improved" the internals of the car.

With loose coupling the goal is to "code to interfaces not implementation". This means that ideally the client of a function should know only the signature of that function. Changes in how that function does what it does should affect its clients.

## Loose Coupling with Python Decorators

Take the implementation of decorators in Python. Python's ingenious design and implementation of functions in the language enables you to write code that doesn't even depend on the signature of a function. This is why decorators are so flexible in Python.

A decorator does not know the name of the function it decorates and the parameters it takes. The function being decorated knows nothing about it. All these are reasons why decorators are such a great tool for writing loosely coupled code in Python.

For some amazing use of decorators take a look at [Flask](http://flask.pocoo.org/) and [pytest](https://docs.pytest.org/en/latest/).

