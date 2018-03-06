Decorators give you the power to give objects new responsibilities without making code changes to the underlying classes.

## Design Principle

Classes should be open for extension but closed for modification.

Our goal is to allow classes to be easily extended to incorporate new behavior without modifying existing code.

You don't have to apply this principle everywhere. It'll lead to a lot of unnecessary effort and time spent.

# Decorators

Decorators attach additional responsibilities to an object dynamically. They provide a flexible alternative to sub-classing for extending functionality.

Decorators have the following properties:

1. They have the same supertype as the object they decorate meaning they inherit from the same parent class or interface.
2. You can use one or more decorators to wrap an object.
3. Since they have the same parent class as the object they wrap, we can pass them around in place of the original wrapped object.
4. The decorator adds its own behavior before or after it delegates to the object it decorates to do the rest of the job.

## The Different Objects Involved in This Pattern

**Abstract Component**: an abstract class or interface decorators and wrapped objects inherit from.

**Concrete Component**: decorator or wrapped object that inherits from abstract component.

Note: If you have code that relies on concrete component's type, decorators will break that code. As long as you write code against the abstract component type the use decorators remains transparent to the client.

## More Objects Created Using This Pattern

This is certainly true using the Decorator Pattern. That's why other patterns like Factory or Builder are used in conjunction with this pattern.

