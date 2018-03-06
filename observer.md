# The Observer Pattern

A one-to-many dependency between objects so that when an object changes state all its dependents are notified and updated automatically.

Subjects and Observers are loosely coupled. The Subject knows about a one-method interface that Observers implement. You can add Observers any time without any change needed to the Subject. When Subject changes state Observers get notified.

Subject and Observers can be used independently of each other in isolation. Changes to one does not affect the other.

## Design Principle

Strive for loose coupling between objects that interact.

## Loose Coupling

When two objects are loosely coupled they can interact but know very little about each other.

