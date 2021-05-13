# reimagined-design-patterns

**Observer Pattern**

**When to use?**
The Observer pattern is used when there is a need to notify some objects about a change/update.
Notification systems can be built based on this pattern. 
By using this pattern, it is possible to build a subscription mechanism so that only the subscribed objects receive the notification. Eg: Email newsletter subscriptions.

**Implementation**
There is a publisher class with below contents:
3 methods  - subscribe(), unsubscribe(), notify(). And other business methods if required.
1 Collection - to maintain list of subscribers.

subscribe() - to add to collection of subscribers.
unsubscribe() - to remove from collection of subscribers.
notify() - to send notifications to all subscribers in collection.

**Example**
For a newsletter subscription system, the subscribers click on the subscribe button. The subscription request goes to
Publisher and is added to collection. Once a newsletter edition is released, the publisher notifies all the subscribers 
About it. 

**Advantage**
Possibility to subscribe/unsubscribe optionally.


**Builder Pattern**

**When to use?**
Builder design pattern is useful when we need to build complex objects. That is when the requirement to create objects
Is based on various parameters. Lot of times, in our code base, we have come across constructors in classes having numerous parameters. These parameters represent some functionality of the class, or they enable or disable some functionalities in the class. This pattern helps us optionally add the functionalities to the class and create the object finally.

**Implementation**
Usually, there is builder class that is responsible for the construction of the object. 
The class for which the object is to be created has all its functionalities or parameters as methods.
These methods return the instance of the same object after adding the functionality.

**Example**
Consider a scenario where we need to create an editor with below optional functionalities:
	- Show Line number
	- Undo options
	- Access rights to read/write

Class - TextEditor has three methods:
Public TextEditor showLineNumber(boolean showLineNo);
Public TextEditor addUndoFunctionality();
Public TextEditor giveEditAccess(boolean edit);

And one build() method which is the final operation for object creation.
All these methods return TextEditor instance. 

Usage would be like below,
TextEditor textEditor  = TextEditor.showLineNumber(false).addUndoFunctionality().giveEditAccess(true).build();
Now we have built an object of text editor class that doesn’t show line numbers, has undo functionality and has access 
Right to edit.

**Advantage**
This way of creating objects makes the code more readable and maintainable as the process is step by step.
If a new functionality is added to the class, it's enough to just to call it in as a step during object creation.

In the traditional way of using a constructor, if a new parameter is introduced, it affects all the places where the 
Constructor has been called. This is avoided by using this pattern.


**Decorator pattern**

**When to use it?**

Decorator pattern is used when a new additional functionality needs to be added to existing functionality in such a way that the client code needs no changes.

**Implementation**

Consider an email notification system implemented with interface Inotifier. We have 2 notifiers - EmailNotifier and SMSNotifier. 
The Inotifier class has a method notify(). 

Now , in addition to sending an email notification, there is a requirement to store the content 
Of the email in database. 

To achieve this, we introduce a wrapper class or Decorator class that wraps around the
EmailNotifier functionality and also performs the DB storage activity.

This new decorator will implement Inotifier and also will have an instance of EmailNotifier. 
On calling notify() in decorator class email notification will be sent and new activity of DB persistence will be done. This way the client need not change its code, since the wrapping decorator also implements INotifier  interface.

**Advantage**
We use composition in addition to inheritance in this pattern. Using only inheritance would have resulted in changes in client code to accommodate this new functionality. 
This is avoided now.

**Adapter Pattern**

**When to use?**
Adapter pattern helps to bridge two different interfaces.

**Implementation**
We introduce an adapter class which wraps the interface of one of the
incompatible interface or one of the interfaces that need to communicate to each other and implements the 
other interface.

Consider a file writer functionality thats provided by a library.
The interface IXMLWriter contains a write() method. 
This library helps write content in xml format. 

Now, if the same file needs to be written in json format? The json writer has 
an interface IJsonWriter
One way to implement this would be to introduce a json file writer and use it 
in all the places where the xml writer was used. This would mean a lot of changes.

Let us introduce a new adapter class -> XmlToJsonWriterAdapter implements IXMLWriter
XmlToJsonWriterAdapter contains IJsonWriter.
Now the XmlToJsonWriterAdapter also contains write() method. 
The write() method in adapter class will have the implementation to call the json writer for the same file.

**Advantage**
Since the adapter class uses the same interface as that of the existing library, client code need not change. The adapter can also implement both the interfaces meaning which the clients can use it both ways. It can be used for converter functionalities.

 
















