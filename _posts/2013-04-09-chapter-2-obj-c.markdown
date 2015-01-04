---
layout: post
title: Obj-C
date: 2013-04-09 08:54:35.000000000 -05:00
---
<h4>Objects</h4>

<ul>
<li>Each instance of a class becomes an object that holds it&#8217;s own data.</li>
<li>An instance of a class, an object, has its <strong>instance variables</strong>.</li>
<li><strong>Methods</strong> are functions associated with objects and they have access to instance variables. Their structure is:

<ul>
<li>Return type</li>
<li>Name</li>
<li>Parameters it expects</li>
<li><ul>
<li>(NSString *) setItemName: (NSString *)str;</li>
</ul></li>
</ul></li>
<li>An instruction that makes an object execute a method is a <strong>message</strong>.</li>
<li>an object (class instance) is declared using a <strong>pointer</strong> that points to a location in the momory where the object is actually stored.

<ul>
<li>Class *classInstance; // Creates a(n instance) variable that point to an Object, but doesn&#8217;t create the object itself.</li>
</ul></li>
<li>To create an object, you send an alloc message to a class.

<ul>
<li>Class *classInstance = [Class alloc]; // This syntax creates a class and then creates a pointer to it with the name &#8220;classInstance&#8221;.</li>
</ul></li>
<li>The first message you always send to a newly allocated instance is an initialization message as an instance isn&#8217;t valid until initialized.

<ul>
<li>Class *classInstance = [[Class alloc] init];</li>
</ul></li>
</ul>

<h4>Anatomy of a Message:</h4>

<ul>
<li>A message is always contained in square brackets.</li>
<li>Parts of a message:

<ul>
<li>Reciever: A pointer to the <em>object</em> recieving the message</li>
<li>Selector: The name of the <em>method</em> that is supposed to be executed</li>
<li>Arguments: The values that are to be supplied as the <em>parameters</em> of the method.</li>
<li>[recievingObject methodName:argument];</li>
</ul></li>
<li>Multiple Arguments: Each argument is paired with a label in the selector, and each label ends with a colon.

<ul>
<li>[recievingObject methodName:argument1 sameMethod:argument2]</li>
<li>For every pair of square brackets, there is only one message being sent. Even if it has two labels, it is still only one message, and sending that message results in <strong>only one method being executed</strong>.</li>
</ul></li>
<li>A <strong>method</strong> is a chunk of code that can be executed, and a <strong>message</strong> is the act of asking a class or object to execute a method.</li>
</ul>

<h4>Destroying Objcts</h4>

<ul>
<li>Objects can be destroyed by setting their pointer to <strong>nil</strong>.

<ul>
<li>classIntance = nil;</li>
</ul></li>
<li>A pointer with the value &#8220;nil&#8221; is used to represent the absence of an object.</li>
</ul>

<h4>Creating Strings</h4>

<ul>
<li>When you want a hard-coded string, you prefix a character string with an @ symbol. This creates an instance of NSString that holds the character string.</li>
<li><strong>Format Strings</strong>: NSLog takes variable number of arguments:

<ul>
<li>The first argument <strong>must</strong> be an NSString <em>format string</em>, followed by arguments that refer to the tokens.</li>
<li>%d: double</li>
<li>%f: float</li>
<li>%c: char</li>
<li><strong>%@</strong>: Any object

<ul>
<li>When %@ is encountered in the format string, instead of the token being replaced by the corresponding argument, that argument is sent the message <em>description</em>. The description method returns an NSString that replaces the token. Because the argument is sent a message, that argument must be an object.</li>
</ul></li>
</ul></li>
</ul>

<h4>NSArray and NSMutableArray</h4>

<ul>
<li>An array is an <strong>ordered</strong> list of objects, which can be accessed using an <strong>index</strong>.</li>
<li>an NSArray is <strong>immutable</strong>, that is nothing can be added/removed once the array has been initialized.</li>
<li><strong>NSMutableArray</strong>, a subclass of NSArray, allows edits.</li>
<li>An array does not actually contain the objects that belong to it; instead it holds a pointer to each object. So array can only hold references to Obj-C objects and can have different types of objects.

<ul>
<li>An array or any other object does hold <strong>static variables</strong> like <em>int</em>, etc in their heap.</li>
</ul></li>
<li><strong>count</strong>: Message to enqire an array of the number of objects it is storing.</li>
<li><strong>NSNull</strong>: You cannot add nil to an array. If you need to add “holes” to an array, you must use NSNull. NSNull is an object that represents nil and is used specifically for this task.

<ul>
<li>[array addObject:[NSNull null]];</li>
</ul></li>
<li><strong>objectAtIndex:</strong>- Used to retrieve object-pointers at specific indices.

<ul>
<li>NSString *objectName = [array objectAtIndex:0]</li>
</ul></li>
</ul>

<h4>Subclasses</h4>

<ul>
<li>Every class in Obj-C has exactly one superclass.</li>
<li><strong>Root Class: NSObject</strong>. Every object inherits 3 methods from NSObject:

<ul>
<li>alloc</li>
<li>init</li>
<li>description</li>
</ul></li>
<li>A subclass adds methods and instance variables to extend the behavior of its superclass.</li>
<li>A subclass can also overide the methods of its superclass.

<ul>
<li>Subclasses override the default behavior of description method, which is to return the name of the object&#8217;s class and its address in memory. They make description supply more relevant information about their instances.

<ul>
<li>NSString returns the string itself</li>
<li>NSArray returns the description of every object in the instance as a string.</li>
</ul></li>
</ul></li>
<li><strong>Header File</strong>: (.h) Starts with <strong>@interface</strong> Classnae and superclass name</li>
<li>@interface ClassName : SuperClassName</li>
<li>Used to declare

<ul>
<li>The name of the new class</li>
<li>Its superclass</li>
<li>Instance variables</li>
<li>Methods</li>
</ul></li>
<li><strong>Implementation File</strong>: (.m) Contains the code for the methods of the class.

<ul>
<li>At the top, the associated headr file is imported</li>
<li><strong>#import &#8220;ClassName.h&#8221;</strong></li>
</ul></li>
<li>Objective-C retains all the keywords of the C language, and additional <strong>keywords specific to Objective-C are distinguishable by the @ prefix</strong>.</li>
<li>To declare a class in Objective-C,

<ul>
<li>Use the keyword <strong>@interface</strong> followed by the name of this new class. After a colon comes the name of the superclass.</li>
<li>@interface NewClass: SuperClass</li>
<li>The @end directive indicates that the class has been fully declared.</li>
</ul></li>
<li><strong>Instance Variables</strong>

<ul>
<li>Declared inside of curly braces immediately after class declaration</li>
<li>Non-pointer instance variables are stored inside the object itself.</li>
</ul></li>
</ul>

<h4>Accessor Methods:</h4>

<ul>
<li>Accessor methods are needed to interact with instance variables in messages.</li>
<li>Methods that <strong>set and get</strong> instance variables are called Accessor Methods.

<ul>
<li><strong>Setters</strong></li>
<li><strong>Getters</strong></li>
</ul></li>
<li>The name of a setter method is set plus the name of the instance variable it is changing.</li>
<li>The name of the getter method is just the name of the instance variable.</li>
<li>Impleemting Accessors:

<ul>
<li>In the implementation file, the header file is imported.</li>
<li>Implementation block begins with <strong>@implementation</strong> keyword followed by the name of the class that is being implemented.</li>
<li>All of the method definitions in the implementation file are inside the implementation block, terminated by the @end keyword.</li>
<li>The setter methods assign the appropriate instance variable to point at the incoming object.</li>
<li>The getter methods return a pointer to the object the instance variable points at.</li>
</ul></li>
<li>-(void) setInstanceVarName: (NSString *) name { instanceVarName = name; }</li>
<li>-(NSString *) instanceVarName { return instanceVarName; }</li>
</ul>

<h4>Instance Methods</h4>

<ul>
<li>When a method is overidden, it doesn&#8217;t need to be declared in the header file as it&#8217;s imported with the superclass.

<ul>
<li>To override a method, just implement it in the implemenation file.</li>
</ul></li>
<li>Remember, an NSLog with %@ as the token will print the description of the corresponding argument

<ul>
<li>NSLog(@&#8220;%@&#8221;, objectName);</li>
<li>A string could be declared using just the @ keyword

<ul>
<li>[p setSerialNumber:@&#8220;A1B2C&#8221;];</li>
</ul></li>
</ul></li>
</ul>

<h4>Initializers</h4>

<ul>
<li><strong>alloc</strong>: Allocates memeory and creates an instance(object), returning it&#8217;s pointer.</li>
<li><strong>init</strong>: Gives instance varaibles their initial values.</li>
<li><strong>Initializers</strong>: Initialization methods that take arguments to initialize their objects&#8217; instance vars.</li>
<li><p><strong>Each initializer name, conventionally, begins with the word <em>init</em>.</strong></p>

<h5>Designated Initializer:</h5></li>
<li>An initializer method, of the multiple ones which a class can have, that makes sure every instance var of an object is valid.</li>
<li>Designated initializers have parameters for the most important and frequently used instance vars of a class.</li>
<li><ul>
<li>(id) initWithItemName: (NSString *)name valueInDollars: (int) value serialNumber: (NSString *)sNumber;</li>
</ul>

<ul>
<li>Name of the method (Selector): initWithItemName:valueInDollars:serialNumber</li>
<li>Labels of the selector: initWithItemName, valueInDollars, serialNumber</li>
<li>three parameters : name, value, sNumber.</li>
</ul></li>
<li><strong>- (id)</strong> : The return type <em>id</em> is a <strong>POINTER to any object</strong>. Returns a pointer to the appropriate object.

<ul>
<li><strong>init</strong> methods are always declared to return id.</li>
</ul></li>
<li><strong>isa pointer</strong>: Stores the class of the bobject, thus making it aware of what

<ul>
<li>Every object (class instance) has the <em>isa</em> instance var.</li>
<li>When an instance is created by sending a class the <em>[alloc]</em> message, the class sets the <em>isa</em> var of the onstance(object) to point back to the class.</li>
</ul></li>
<li><strong>Implementing the designated initializer</strong>:

<ul>
<li>First thing: Call the superclass&#8217;s designated initializer using <em>super</em>.</li>
<li>Last thing: Return a pointer to the successfully initialied object using <em>self</em>.</li>
</ul></li>
<li><strong>self</strong>: Self is an <strong>implicit local var</strong>.

<ul>
<li>It doesn&#8217;t need declaration</li>
<li>It&#8217;s automatically pointed to <em>the object that was sent the message</em>.

<ul>
<li>[self methodName]; //self points to the object within which it was sent the message.</li>
</ul></li>
<li>It&#8217;s used so that <em>an object can send a message to itself</em>.</li>
</ul></li>
<li><strong>super</strong>: A compiler directive in Obj-C

<ul>
<li>Usually when you send a message to an object, the search for a method of that name starts in the object’s class. If there is no such method, the search continues in the superclass of the object. The search will continue up the inheritance hierarchy until a suitable method is found. (If it gets to the top of the hierarchy and no method is found, an exception is thrown.)</li>
<li>When you send a message to <em>super</em>, you are sending a message to self, but <strong>the search for the method skips the object’s class and starts at the superclass.</strong></li>
</ul></li>
<li>Check with <em>if (self) { }</em> that the superclass&#8217; initializer succeeded.</li>
<li>Rules about initializers:

<ul>
<li>A class inherits all initializers from its superclass and can add as many as it wants for its own purposes.</li>
<li>Each class picks one initializer as its designated initializer.</li>
<li>The designated initializer calls the superclass’s designated initializer.

<ul>
<li>self = [super init]</li>
</ul></li>
<li>Any other initializer a class has calls the class’s designated initializer.</li>
<li><strong>If a class declares a designated initializer that is different from its superclass, the superclass’s designated initializer must be overridden to call the new designated initializer.</strong></li>
</ul></li>
</ul>

<h4>Class Methods</h4>

<ul>
<li>There are 2 kinds of methods:

<ul>
<li><strong>Classs methods</strong>: are sent to classes, like <em>alloc</em></li>
<li><strong>Instance Methods</strong>: are sent to class instances (objects), like <em>init</em></li>
</ul></li>
<li>Class methods typically either <strong>create new instances of the class</strong> or <strong>retrieve some global property of the class</strong>.</li>
<li>Class methods do not operate on an instance or have any access to instance vars.</li>
<li><strong>An instance method uses the - character just before the return type, and a class method uses the + character.</strong></li>
<li>The order of the declarations for the methods:

<ul>
<li><strong>Class methods</strong></li>
<li><strong>Initializers</strong></li>
<li><strong>other methods</strong></li>
</ul></li>
<li>rand() % [arrayName count] // would generate random indices for the array.</li>
<li><strong>NSInteger</strong> is not a class or object but a type definition for <strong>long</strong>.

<ul>
<li>NSInteger vs int: http://stackoverflow.com/questions/4445173/when-to-use-nsinteger-vs-int</li>
</ul></li>
<li><strong>Generaring random chars</strong>:

<ul>
<li>&#8216;0&#8217; + rand() % 10 //generates numbers as chars</li>
<li>&#8216;A&#8217; + rand() % 26, //generates alphabet as chars</li>
</ul></li>
<li><strong>Convenience methods</strong>: Class methods which return an object of the type of the class itself.

<ul>
<li><em>self</em> used in class methods refers to the class itself instead of an instance.</li>
<li>Convinience methods should use <em>self</em> instead of the Class name to allow reuse in subclasses.</li>
</ul></li>
</ul>

<h4>Exceptions and Unrecognized Selectors</h4>

<ul>
<li>When a message is sent to an object that doesn&#8217;t respond to the message, the application will throw an <strong>exception</strong>.</li>
<li><strong>Exceptions</strong> are also known as <strong>run-time errors</strong> because they occur once your application is running</li>
<li><strong>Compile-time errors</strong> show up when your application is being built, or compiled.</li>
</ul>

<h4>Fast Enumeration</h4>

<pre><code>for (BNRItem *item in items)
    {
    NSLog(@&quot;%@&quot;, item);
    }
</code></pre>

<h4>More</h4>

<ul>
<li><strong>Namespace collision</strong>: Error when two classes have the smae name.</li>
</ul>
