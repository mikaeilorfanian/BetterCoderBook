# Template Method

It defines the sketch of an algorithm in a method deferring the implementation of some steps to sub-classes.

It is a method that defines an algorithm as a set of steps where each step is a method call. One or more of these methods is "abstract" and should be implemented by sub-classes.

### Types of Methods in the Abstract Class of the Template Method

* The Abstract Method: final and cannot be changed by sub-classes
* Abstract Methods: must be implemented by sub-classes.
* Final Concrete Methods: can't be changed by sub-classes, but they or the Template Method can use them.
* Hooks: the are concrete \(meaning they have a default implementation\), but sub-classes can override them but they don't have to.

### Hooks

They let sub-classes hook into an algorithm at various points if they wish to. Sub-classes can also ignore these hooks.

Hooks vs. Abstract Methods

Abstract Methods must be implemented by sub-classes. This means they're not optional. Hooks, however, are for the optional steps of an algorithm.

#### Why Hooks?

* To let sub-classes implement or skip optional steps in an algorithm.
* They give sub-classes the chance to react to a step in the Template Method that is about to happen or already happened.
* They give sub-classes the ability to make a decision for the abstract class.

This pattern shows up everywhere because it's a great design for creating framework where the framework decides how something gets done, but leaves it to you \(the user of the framework\) to decide what happens in each step the framework takes.

## Hollywood Principle

Don't call us \(the high-level component\), we'll call you \(the low-level component\).

This principle lets low-level components to hook into a high-level. High-level components decide when the low-level ones are needed and how.

This principle helps avoid dependency rot where high-level components depend on low-level ones which depend on high-levels ones which depend on sideway components, etc.

This principle is a technique for building frameworks or components so that lower-level components can hook into higher-level ones without creating a dependency between them.

Question: Can low-level components call high-level component's methods?

Yes, this often happen when low-level components inherit behavior by inheriting from the high-level components.

But, you must be careful not to create explicit circular dependencies between these components.

#### Flask

Template method's Hollywood Principle lets you hook into a high-level system where the high-level system decides when the low-level components are needed and how they're used.

In Flask, the low-level components are request handlers and the high-level components belong to the Flak framework.

In Flask decorators are used as hooks so that there's no need for request handlers to inherit anything. The decorators are not used for the Decorator Pattern. The beauty of Pythonic code here is that it allows you to use advanced techniques without writing advanced-looking code.

#### unittest

The test-runner of the unittest library allows you to hook into it.

There's a certain algorithm that unittest follows when it discovers and runs your tests. By inheriting from TestCase you get to introduce hooks into this algorithm.

For example, you can add methods that are treated as tests and others that are not. Or, you can create setup and tear down procedures for each or all tests within a class.

Or, you can use convenient methods such as asserEqual which become available through inheritance. This creates a soft circular dependency: the test-runner depends on your code and your code depends on the test-runner. However, your code's dependency on unittes is much stronger, i.e. you cannot change the algorithm that unittest uses to set, tear down, and execute tests.

Strategy vs. Template Method

Strategy: define a family of algorithms and make them interchangeable. Each algorithm is encapsulated meaning a client can use any of those algorithms without having to make any code changes.

Template Method: the intent is to define the outline o an algorithm but let sub-classes do some of the work. It has several implementations of a step, but has control over the structure of the whole algorithm.

Strategy uses composition, but T.M. uses inheritance.

Strategy is better when all steps except one in an algorithm are the same. Also, the sub-classes can use code from the super class.

