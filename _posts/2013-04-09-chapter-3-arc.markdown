---
layout: post
title: ARC
date: 2013-04-09 08:55:25.000000000 -05:00
---
<h4>The Heap</h4>

<ul>
<li><strong>The Heap</strong>: All Obj-C objects are stored in a <em>part of memory</em> called the heap.

<ul>
<li><em>alloc</em> allocates space in the heap to store instance vars.</li>
</ul></li>
<li><strong>NSDate</strong>: Has 2 instance vars <strong>12 bytes</strong>:

<ul>
<li><em>isa</em>: stores a pointer to the class of the NSDate instance. <strong>4 bytes</strong></li>
<li><em>double</em>: Stores the numer of seconds elapsed since initialization. <strong>8 bytes</strong></li>
</ul></li>
<li>Pointers are 4 bytes.</li>
<li>Objects never live inside one another; they exist separately on the heap. Instead, objects keep references to other objects as needed.</li>
</ul>

<h4>The Stack</h4>

<ul>
<li><strong>Frame</strong>: When a method or function is executed, it allocates a chunk of memory from the stack. That chunk is called a frame.

<ul>
<li>It <strong>stores the values for vars declared inside the method</strong>.</li>
<li>A var declared inside a method is called a <strong>local variable</strong>.</li>
<li>when a method calls another menthod, a frame is created for the target method, <strong><em>stacked</em></strong> on top on the original method.</li>
</ul></li>
</ul>

<h4>Pointer Variables and Object Ownership</h4>

<ul>
<li>Pointer vars convey <strong>ownership</strong>

<ul>
<li>When a method (or function) has a local variable that points to an object, that method is said to own the object being pointed to.</li>
<li>When an object has an instance variable that points to another object, the object with the pointer is said to own the object being pointed to.</li>
</ul></li>
</ul>

<h4>Memory Management</h4>

<ul>
<li>Heap memeory is limited. Hence, unused objects must be destroyed and the heap must be freed for other runtime objects.

<ul>
<li><strong>Memeory Leak</strong>: An object that has <strong><em>no owners</em></strong> cannot be sent messages to and hence, is useless. It should be destroyed.</li>
<li><strong>Premature Dellocation</strong>: If an object with atleast one owner is destroyed, when the owner sends a message to the non-existent object, the app will crash.</li>
</ul></li>
</ul>

<h4>ARC</h4>

<ul>
<li><strong>ARC</strong> = <strong>A</strong>utomatic <strong>R</strong>eference <strong>C</strong>ounting.</li>
<li>Destroys objects without owners. Which can happen when:

<ul>
<li>A var that pointed to the object now points to another object</li>
<li>The var is ser to <em>nil</em> (whi stands for the absence of an object)</li>
<li>The var itself is destroyed.</li>
</ul></li>
</ul>

<h4>Strong and Weak References</h4>

<ul>
<li>When a var points to an object, whether as an instance var or a local var within a method/function, it&#8217;s called an <strong>strong reference</strong>.</li>
<li>A var that <strong>does not take ownership of the object it points to</strong> is said to <strong>weak reference</strong> the object.</li>
<li><strong>Retain Cycle</strong>: When two or more objects own eachother, they will never be destroyed and will be retained in the heap even when every other object releases its ownership of these objects.

<ul>
<li>A retain cycle is a memory leak that cannot be managed by ARC.</li>
<li><a href="https://dl.dropbox.com/u/3698938/Screen%20Shot%202013-03-26%20at%2011.08.25%20AM.png">Retain Cycle</a></li>
</ul></li>
<li>To address a retain cycle, one of the pointers between the objects has to be a <em>weak reference</em>.

<ul>
<li>To decide between the pointers, construct a parent-child relationship between the objects.</li>
<li>The parent has a strong reference to the child, while the child has a weak refernce for the parent.</li>
</ul></li>
<li>To declare a variable as a weak reference, use the <strong>__weak</strong> <em>attribute</em> in the declaration of the var in the header file.

<ul>
<li>__weak BNRItem *container;</li>
</ul></li>
<li>Weak references know when the object they reference to are destroyed and automatically set the pointer to <em>nil</em>.</li>
<li><strong>__unsafe_unretained</strong> attribute: Creates weak references without the ability of setting pointers to destroyed objects to <em>nil</em>.</li>
</ul>

<h4>Properties</h4>

<ul>
<li>Properties are concise alternatives to accessor methods.</li>
<li>A property is declared in the interface of a class (.h).</li>
<li>*<strong>@property NSString <em>itemName;</em></strong> is equivalent to:

<ul>
<li>*-(void) setItemName: (NSString <em>) str;</em></li>
<li>*(NSString <em>) itemName;</em></li>
</ul></li>
<li>When a property is declared, it implicitly declares the corresponding setter and getter methods.</li>
</ul>

<h5>Attributes</h5>

<ul>
<li><strong>Attributes</strong> are used in property declarations to alter the behavior of accessor methods.</li>
<li>The attributes are declared in parentheses after the @property directive.

<ul>
<li>@property (nonatomic, readwrite, strong) NSString *itemName;</li>
</ul></li>
<li>There are <strong>three attributes</strong> with each having 2/3 options.</li>
<li><strong>First Attribute</strong>: Concerns itself with multithreaded applications. Has 2 options

<ul>
<li><strong>atomic</strong>: <strong>Default</strong>.</li>
<li><strong>nonatomic</strong>: Most often used. <strong>NOT the default</strong>, so have to explicitly declare everytime.</li>
</ul></li>
<li><strong>Second Attribute</strong>: For deciding whether both the accessor methods are needed or just the getter.</li>
<li><strong>readwrite</strong>: <strong><em>Default</em></strong> Declares both, the setter and the getter, mothods.

<ul>
<li><strong>readonly</strong>: Declares only the getter method. So, when only a getter method is needed, like with NSDate, etc., the second property is declared &#8220;readonly&#8221;.</li>
</ul></li>
<li><strong>Third Attribute</strong>: Describes <strong>memeory management</strong>.

<ul>
<li><strong>assign</strong>: <strong><em>default</em></strong>, used for properties which are not pointers but int, double, etc.</li>
<li><strong>strong</strong>: Creates a strong reference to the objec the pointer points to.</li>
<li><strong>weak</strong>: Creates a weak reference to the object the pointer points to.</li>
</ul></li>
</ul>

<h4>Synthesizing properties</h4>

<ul>
<li>Properties can be synthesized in the <em>implementation</em> file to generate the code for accessor methods.</li>
<li><strong>@synthesize</strong> directive is used to synthesize the properties in the implementation files.</li>
<li>Any implementation added after synthesizing a property, overrides the synthesized version.</li>
<li><strong>If no instance vars are declared, synthesizing the property will create vars of the same name. Thus, declaring instance vars is redundant.</strong></li>
</ul>
