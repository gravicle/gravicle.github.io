---
layout: post
title: First App
date: 2013-04-09 08:51:13.000000000 -05:00
---
<p>Two basic questions when writing an app:
1. Creating objects and configuring them
2. Managing user interaction.</p>

<h3>Terms and ideas:</h3>

<ul>
<li>Anything that can appear to the user is a <strong>view</strong>.</li>
<li>The iOS SDK is an object-oriented library, and views are represented by objects.</li>
<li>Each view is an instance of one of several subclasses of the <strong>UIView</strong> class.</li>
<li>Xcode’s interface builder is different. It is an <strong>object editor</strong>: you create and configure view objects and then save them into an archive. The archive is a <strong>XIB</strong> (pronounced “zib”) file.</li>
<li><strong>A XIB file is an XML representation of the archived objects</strong>. When you build a project, the <strong>XIB file is compiled into a NIB file</strong>. Developers work with XIB files (they’re easier to edit), and applications use NIB files (they’re smaller and easier to parse). However, most iOS developers use the words XIB and NIB interchangeably.</li>
<li>The <strong>bundle</strong> is a directory containing the application’s executable and any resources the executable uses.</li>
<li>Objects are archived into XIB files → coplied into NIB files → copied into the application bundle on Build → Loaded and read on execution.</li>
<li><strong>VeiwController</strong>: Object responsible for managing the events that occur on the interfce.</li>
<li>Model-View-Controller pattern: every object you create is exactly one of the following: a <strong>model object</strong>, a <strong>view object</strong>, or a <strong>controller object</strong>.

<ul>
<li>View objects are visible to the user.</li>
<li>Model objects hold data and know nothing about the user interface. Model objects typically use standard collection classes (<strong>NSArray</strong>, <strong>NSDictionary</strong>, <strong>NSSet</strong>) and standard value types (<strong>NSString</strong>, <strong>NSDate</strong>, <strong>NSNumber</strong>).</li>
<li>Controllers are the managers in an application. They keep the view and model objects in sync, control the “flow” of the application, and save the model objects out to the filesystem.</li>
</ul></li>
<li><strong>IBAction</strong> and <strong>IBOutlet</strong> allow to connect controller and view objects in the XIB file.

<ul>
<li>the pointers that appear in the connections panel are the ones that you decorated with IBOutlet in QuizViewController.h.</li>
</ul></li>
<li>A <strong>connection</strong> lets one object know where another object is in memory so that the two objects can work together.</li>
<li>The object that is sent the message is called the <strong>target</strong>.</li>
<li>The message is called the <strong>action</strong>, and it is the name of the method that tapping the button should trigger</li>
<li>Methods and instance variables are declared in the header file (.h), but the actual code for the methods is placed in the implementation file (.m)</li>
<li>View objects are typically created in XIB files, and model objects are always created programmatically.</li>
</ul>
