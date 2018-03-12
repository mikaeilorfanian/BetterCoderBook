# Command Pattern

This pattern lets you decouple the requester of an action from the object that performs the action.

A Command Object encapsulates a request to do something on a specific object. The Command Object can be passed around and has a method that encapsulates the actions that need to happen. It also has a reference to the Receiver object\(the object that gets operated on\).

## Components

Client: creates the Command object

Command: this object knows which actions should be takes on which objects. It has an `execute` method that is invoked by the Invoker object on the Receiver object.

Invoker: Client calls the `SetCommand` method of this object and passes the Command object to it. At some point in future, Invoker calls `execute` on the Command object.

Receiver: this is the object on which actions take place. Usually this happens within the body of the Command object's \`execute\` method.

All Command objects implement the same interface: it consists of one method called \`execute\`. Command usually takes the Receiver in its constructor and saves it as an instance variable. Later on when execute is invoked this instance variable is acted upon.

### Macro Command

A Command that executes one or more Commands.

### HTTP Request as Command Object

How does a HTTP \`GET\` request decouple a client from the server? 

* Client and server can be anywhere on earth.
* They can be on different types of machines \(e.g. phone and a server in a server farm\).
* They can be implemented using any desired set of technologies\(e.g. phone uses Android whereas server uses PHP\).

In this context, the Command object is the HTTP request. It knows the receiver and what action should be taken. In this case though the logic of the action taken is in the Receiver object.

### Dumb vs. Smart Command Objects

Can we put the logic of the action taken right into the Command object? Do we always have to have a reference to the Receiver and have the Receiver implement the logic related to an action? In general, it's better to have dumb Commands. You could put the Receiver's logic in a Command\(sacrificing decoupling and forcing you to have a reference to the Receiver\) to make it "smart".







