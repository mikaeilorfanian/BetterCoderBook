# Composition

## Introducing Design Principles

You can think of design principles as easy to remember rules that will guide you to write code that's easy to read and maintain. The design principles you'll find in this chapter are from Head First Design Patterns. But, since these principles are more like best practices, you'll often see them referred to by other names.

### Design Principle

#### Identify aspects of your application that vary and separate them from what stays the same.

What varies should not affect what does not vary. This way you minimize unintended consequences.

This single principle is the basis of all design patterns and good practices.

The goal of good practices and patterns is to let you build parts of your application that vary independently of other parts of your application.

### Design Principle

#### Program to an interface not an implementation.

This principle is not that big of a deal in weakly-typed languages like Python where almost everything is programmed to interfaces by the design of the language itself.

An Example

`Dog d = new Dog(); d.bark(); <-- we're coding to a specific class and its implementation`

`Animal a = new Dog(); a.makeSound(); <-- we know we have an Animal, but we still make a specific one`

`Animal a = getAnimal(); a.makeSound(); <-- we don't care what type of animal we have, but only that it makes a sound.`

### Design Principle

Favor composition over inheritance.

Each Duck has a FlyBehavior and QuackBehavior to which it delegates to for flying and quacking behavior. It does not inherit flying or quacking behavior from another class. FlyBehavior and QuackBehavior are actually interfaces. They can be used by clients other than a Duck. Here, we say that Duck is composed with the right FlyBehavior or QuackBehavior object so it can have extended responsibilities.

**Composition is used in many design patterns.**

