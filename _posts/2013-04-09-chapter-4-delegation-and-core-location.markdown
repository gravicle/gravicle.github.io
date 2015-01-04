---
layout: post
title: Delegation and Core Location
date: 2013-04-09 08:57:29.000000000 -05:00
---
<h4>Projects, Targets and Framework</h4>

<ul>
<li><strong>Project (.xcodeproj)</strong>: A project is a file that contains a list of references to other files as well as a number of settings that lay out the rules for items within the project.</li>
<li><strong>Target</strong>: A project always has atleast one target. A target uses the files in the project to build a product.</li>
<li>Essential <strong>build phases</strong>:

<ul>
<li>Complie sources</li>
<li>Link binary with libraries</li>
<li>Copy bundle resources</li>
</ul></li>
</ul>

<h5>Framework</h5>

<ul>
<li>A framework is a collection of related classes.</li>
<li>Cocoa-Touch is a collection of frameworks that add various functions to a target and can be added individually as needed.</li>
<li><code>FrameworkName.framework</code></li>
</ul>

<h4>Core Location</h4>

<ul>
<li>The Core Location framework contains classes that help a device determine its geographical location.</li>
<li>Using Core Location framework

<ul>
<li>Add the framework to Target</li>
<li><strong>Import framework header file</strong> into files that need to know about the framework</li>
<li><code>#import &lt;CoreLocation/CoreLocation.h&gt;</code></li>
</ul></li>
<li><strong>FrameworkName.h</strong>: Every framework has a header file that imports the header file of all the classses in the framework.</li>
<li><strong>CLLocationManager</strong>: Class that interfaces with the location hardware and returns the location of the device.

<ul>
<li><strong>desiredAccuracy</strong> property: Tells the location manager of the required accuracy of locaion.

<ul>
<li><code>[locationManagerObject setDesiredAccuracy: kCLLocationAccuracyBest]</code>
<code>[ startUpdatingLocation]</code></li>
</ul></li>
</ul></li>
<li><code>CLLocationManager</code> sends the message <code>locationManager:didUpdateToLocation:fromLocation:</code> to its <strong><em>delegate</em></strong>.</li>
<li><strong>Delegate</strong> is an object that can be set to recieve messages from another class.

<ul>
<li><code>[locationManager setDelegate: self];</code></li>
</ul></li>
<li>When a <code>CLLocationManager</code> has enough data to produce a new location, it creates an instance of <code>CLLocation</code>, which contains the latitude and longitude of the device. It also contains the accuracy of its reading and, depending on the device, the elevation above sea level.</li>
<li>The method that <code>CLLocatationManager</code> sends its delegate, <code>locationManager:didUpdateToLocation:fromLocation:</code>, must also be implemented in the delegate.</li>
<li>When <code>CLLocationManager</code> fails to find the location, it sends the method <code>locationManager:didFailWithError</code></li>
</ul>

<h4>Delegation</h4>

<ul>
<li><strong>Delegation</strong> is an object-oriented approach to <strong><em>call-backs</em></strong>.</li>
<li>A <strong>Callback</strong> is a function(method) that is called everytime an event occurs.

<ul>
<li><strong>A delegate is set to recieve all the callbacks from an object</strong> and it can then store, display, act-on these messages.</li>
</ul></li>
</ul>

<h5>Target- Action vs Delegation</h5>

<ul>
<li>A new target-action pair must be created for every distinct event, while a delegate can be set once and be sent varied events.

<ul>
<li>A delegate implements corresponding methods to handle the call-backs.</li>
</ul></li>
<li>In delegation, an object can only send its delegate messages from a specific set listed in a protocol.</li>
</ul>

<h4>Protocols</h4>

<ul>
<li>Every object with a delegate property has a corresponding <strong>protocol</strong>.</li>
<li>The delegate implements methods from the protocol for events which it is interested in.</li>
<li>When the delegate object implements methods from the protocol, it&#8217;s said to <strong>conform to the protocol</strong>.</li>
<li><strong>Declaration</strong>:

<ul>
<li><code>@protocol</code> keyword</li>
<li>name of the protocol</li>
<li>Angled brackets to import methods from other protocols</li>
<li><code>@protocol ProtocolName &lt;ImportedProtocolName&gt;</code></li>
</ul></li>
<li>A protocol is not a class but <strong>a collection of methods</strong>.

<ul>
<li>These methods aren&#8217;t implemented in the protocol or elsewhere, but in the clsses that conforms to the protocol (delegate).</li>
<li>Protocol methods either provide information to the delegate or request directives from the delegate.</li>
</ul></li>
<li><strong>Delegate Protocols</strong>: Protocols used for delegation.

<ul>
<li>Naming: Delegation class name followed by <code>Delegate</code>.</li>
</ul></li>
<li>Methods declared in a protocol can be optional or required (default).

<ul>
<li>Optional methods are preceeded by the <code>@optional</code> directive.</li>
</ul></li>
<li>Before sending an optional message to a deligate, the object first asks the delegate whether it implements the said method by sending the <code>respondsToSelector:</code> method.

<ul>
<li>Every object implements <code>respondsToSlector:</code> method.</li>
</ul></li>
<li>For required methods, messages are sent without checking, and thus, the complier insisists that every required method from the protocol be implemeted in the delegate.

<ul>
<li>For this check to work, a delegate must explicitly states that it conforms to the relevant protocols.</li>
<li><strong>The protocols that a class conforms to are added to a comma-delimited list inside angled brackets in the interface declaration following the superclass</strong>.</li>
<li><code>@interface ClassName: SuperClassName</code><br/>
<code>&lt;CLLocationManagerDelegate, ClassNameDelegate&gt;</code></li>
<li>Conforming to the protocol allows for XCode to utocomplete the method names as well as check for required methods.</li>
</ul></li>
</ul>

<h4>Delegation, Controllers and Memory Management</h4>

<ul>
<li>Typically, <strong>delegates are controller objects</strong> in the MVC design.</li>
<li><strong>Controller objects, typically, own the objects that are delegating to it.</strong></li>
<li><strong>Delegate property is an</strong> <code>__unsafe_unretained</code> <strong>reference</strong> (for compatibility with non-ARC versions of iOS) while, the delegate has a strong reference.

<ul>
<li><a href="https://dl.dropbox.com/u/3698938/00066.jpg">References in delegation</a></li>
</ul></li>
<li>Bacuase a delegate is an <code>__unsafe_unretained</code>, instead of <code>weak</code>, it&#8217;s pointer cannot be set to <code>nil</code>. Hence, <strong>a delegate has to be manually deallocated</strong> by sending it <code>setdelegate:nil</code> message in its <code>dealloc</code> method.

<ul>
<li><code>-(void) dealloc</code>
<code>{</code>
<code>// Tell the location manager to stop sending it messages</code>
<code>[locationManager setDelegate:nil];</code>
<code>}</code></li>
</ul></li>
</ul>

<h4>Debugger</h4>

<ul>
<li>Setting a breakpoint on a line of code pauses the execution of the application at that line (before it executes).</li>
<li>A <strong>stack trace</strong> shows you the methods and functions whose frames were in the stack when the application broke.

<ul>
<li>The method where the break occurred is at the top of the stack trace. It was called by the method just below it, which was called by the method just below it, and so on.</li>
<li>This chain of method calls continues all the way back to main.</li>
<li>The methods implemented by the user are in black text and the methods belonging to Apple are in gray.</li>
</ul></li>
</ul>
