---
layout: post
title: MapKit
date: 2013-04-09 08:56:09.000000000 -05:00
---
<h4>MapKit Framework</h4>

<ul>
<li>The MapKit framework is responsible for the UI and interactions of the map.</li>
<li>Instances of <code>MKMapView</code> display a map, track touches and display annotations.</li>
<li><strong>IBOutlet</strong> means you will create objects in a XIB file.</li>
</ul>

<h4>MapView Delegate</h4>

<ul>
<li><code>MKMapView</code>&#8217;s instances know how to use Core Location to determine user&#8217;s location.

<ul>
<li>Set <code>showsUserLocation</code> property of <code>MKMapView</code> to <code>YES</code></li>
</ul></li>
<li><p>After the interface is loaded, the ViewController is sent the message <code>viewDidLoad</code>, following which, <code>MKMapView</code> can be asked to update its location.</p>

<pre><code>-(void) viewDidLoad
{
  [worldView setShowsUserLocation:YES];
}
</code></pre></li>
</ul>

<h4>Documentation</h4>

<ul>
<li>The documentation is divided into 4 parts:

<ul>
<li>API Reference</li>
<li>System guides</li>
<li>Tools Guides</li>
<li>Sample Code</li>
</ul></li>
<li><p>In the <code>mapView:didUpdateUserLocation:</code> method, a pointer to an <code>MKUserLocation</code> instance is available.</p>

<h5>Zooming In</h5></li>
<li><code>MKMapView</code> has a <code>region</code> property that zooms in on the coordinates supplied: <code>setRegion:animated</code>.

<ul>
<li><code>region</code> is an <code>MKCoordinateRegion</code> <strong>structure</strong> holding:

<ul>
<li><code>CLLocationCoordinate2D</code></li>
<li><code>MKCoordinateSpan</code></li>
</ul></li>
<li>The function <code>MKCoordinateRegionMakeWithDistance ();</code> takes in <code>CLLocationCoordinate2D</code> and 2 <code>CLLocationDistance</code> distances (m) to set the region.</li>
<li>To find the coordinates, we use <code>MKUserLocation</code> returned by <code>mapView:didUpdateUserLocation:</code>.

<ul>
<li><code>MKUserLocation</code> has a <code>location</code> property that returns <code>CLLocation</code>.</li>
<li><code>CLLocation</code> has a <code>coordinate</code> property that returns an <code>CLLocationCoordinate2D</code>.

<ul>
<li>So, to get coordinates and set a <code>region</code>:
~~~
-(void) mapView:(MKMapView *)mapView didUpdateUserLocation:(MKUserLocation *)userLocation
{
CLLocation loc = [userLocation location];
CLLocationCoordinate2D coordinates =[loc coordinate];
}
~~~
~~~
MKCoordinateRegion MKCoordinateRegionMakeWithDistance(coordinates, 250, 250);
~~~</li>
</ul></li>
</ul></li>
</ul></li>
<li><strong>Alternatively</strong>

<ul>
<li><code>MKUserLocation</code> conforms to the <code>MKAnnotation</code> protocol.</li>
<li><code>MKAnnotation</code> declares a <code>coordinate</code> property that returns a <code>CLLocationCoordinate2d</code> structure, which can be used directly in `MKCoordinateRegionMakeWithDistance&#8217; function. Like:
~~~
-(void) mapView:(MKMapView *)mapView didUpdateUserLocation:(MKUserLocation *)userLocation
{
CLLocationCoordinate2D coordinates = [userLocation coordinate];
MKCoordinateRegion MKCoordinateRegionMakeWithDistance (coordinates, 250, 250);
[worldView setRegion:region animated:YES];
}
~~~</li>
</ul></li>
</ul>

<h4>MKNotation</h4>

<ul>
<li><code>MKNotation</code> is not a delegate protocol.</li>
<li><strong>It declares a set of methods that are useful to any class that wants to display instances of itself on a map view.</strong></li>
<li>When an object conforming to <code>MKAnnotation</code> is added to an <code>MKMapView</code>, an instance of <code>MKAnnotationView</code> (or one of its subclasses) is created and added to the map view.</li>
<li>The <code>MKAnnotation</code> protocol, like all protocols, <strong>only dictates method signatures</strong>. As long as the signatures match exactly, the conforming class can implement them however it wants.</li>
</ul>

<h4>Text Editing</h4>

<ul>
<li><code>UIResponder</code> is a class in the <code>UIKit</code> framework.</li>
<li>A <strong>responder</strong> is responsible for receiving and handling events that are associated with it.</li>
<li><code>UIView</code> is a subclass of UIResponder and can receive events.</li>
<li><strong>First Responder</strong> handles events which are not associated with a position on the screen. Like shakes.</li>
<li><code>UITextField</code> is a responder.

<ul>
<li>When a <code>UITextfield</code> is tapped, it becomes the first responder.</li>
<li>As long as the text field is the first responder, a keyboard stays on the screen.</li>
<li>When a <code>resignFirstResponder</code> message is sent to it, it gives up its first responder status and the keyboard goes away.</li>
</ul></li>
<li>Note that <strong>when importing files, you put quotation marks around header files</strong> you create and <strong>angled brackets around header files from frameworks</strong>.

<ul>
<li><p>Angled brackets tell the compiler, “Only look in the system libraries for this file.”</p></li>
<li><p>Quotation marks say, “Look in the directory for this project first, and if you don’t find something, then look in the system libraries.”</p></li>
</ul>
*</li>
</ul>
