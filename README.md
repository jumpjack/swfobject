Live:  [link](https://jumpjack.github.io/swfobject/swfobject/index.html) 

= --- IMPORTANT UPDATE ---

SWFObject is no longer in active development. Flash Player is on the decline, and the authors of SWFObject have moved on to other projects. This project is being left on GitHub for historical purposes.

= SWFObject

SWFObject is a free, open-source tool for embedding swf content in websites.

This GitHub edition of SWFObject is our 2.3 beta. The current release -- 2.2 -- is still available for download at http://code.google.com/p/swfobject/


== CHANGES
SWFObject 2.3 introduces many small changes under the hood (almost exclusively aimed at fixing bugs), but the public API is mostly unchanged and completely backwards compatible with SWFObject 2.2.  The only two significant changes to the API: 

1. You may now pass an element as an argument in embedSWF (in place of an ID)
2. You may now use integers in place of number strings in embedSWF (e.g. 9 instead of "9").

Example:

OLD:
    swfobject.embedSWF("myContent.swf", "my-target-element", "300", "120", "10.0.0");

NEW:
    var el = document.getElementById("my-target-element");
    swfobject.embedSWF("myContent.swf", el, 300, 120, 10);


Another significant change: SWFObject's approach to dynamic embedding in Internet Explorer has been updated to use a more W3C-friendly way of creating the <object>. Because this is Internet Explorer, a few hacks were required, but the end result is code generated by W3C techniques (document.createElement). This means, among other things, that nodes generated  for XHTML documents should properly self close:

OLD:
    <object><param></object>

NEW: 
    <object><param /></object>

Similarly, since the <param> elements are all generated using the same W3C techniques, encoding flashvars should be less troublesome. Developers will no longer need to create separate flashvars encoding workflows for IE and non-IE browsers.
