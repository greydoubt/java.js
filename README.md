# java.js
• Future features




Running applets with the Applet Viewer
--------------------------------------
Here are two examples of using the Applet Viewer:

  bin/appletviewer demo/GraphLayout/example1.html
  bin/appletviewer http://java.sun.com/applets/applets/NervousText/example1.html 
  (On the PC, use "bin\appletviewer" instead of "bin/appletviewer".)

The argument is a filename or URI that refers to an HTML file that
contains one or more APPLET tags.  The Applet Viewer finds the APPLET
tags in the HTML file and runs the applets as specified by the tags
(in separate windows).


The APPLET tag
--------------
The APP tag of previous releases is gone, replaced by the APPLET tag. 
Here is an example of a simple APPLET tag:

  <applet code="MyApplet.class" width=100 height=140></applet>

This tells the viewer or browser to load the applet whose compiled
code is in MyApplet.class (in the same directory as the current HTML
document), and to set the initial size of the applet to 100 pixels
wide and 140 pixels high.

Here's a more complex example of an APPLET tag:

  <applet codebase="http://java.sun.com/applets/applets/NervousText"
	code="NervousText.class" width=400 height=75 align=center >
  <param name="text" value="This is the Applet Viewer.">
  <blockquote>
  <hr>
  If you were using a Java-enabled browser,
  you would see dancing text instead of this paragraph.
  <hr>
  </blockquote>
  </applet>

This tells the viewer or browser to load the applet whose compiled
code is at the URI
http://java.sun.com/applets/applets/NervousText/NervousText.class,
to set the initial size of the applet to 400x75 pixels, and to align
the applet in the center of the line.  The viewer/browser must also
set the applet's "text" attribute (which customizes the text this
applet displays) to be "This is the Applet Viewer."  If the page is
viewed by a browser that can't execute Java applets, then the browser
will ignore the APPLET and PARAM tags, displaying the HTML between
the <blockquote> and </blockquote> tags.  Java-enabled browsers
*ignore* that HTML.

Here's the complete syntax for the APPLET tag:

    '<' 'APPLET'
        ['CODEBASE' '=' codebaseURI]
        'CODE' '=' appletFile
	['ALT' '=' alternateText]
	['NAME' '=' appletInstanceName]
	'WIDTH' '=' pixels 'HEIGHT' '=' pixels
	['ALIGN' '=' alignment]
	['VSPACE' '=' pixels] ['HSPACE' '=' pixels]
    '>'
    ['<' 'PARAM' 'NAME' '=' appletAttribute1 'VALUE' '=' value '>']
    ['<' 'PARAM' 'NAME' '=' appletAttribute2 'VALUE' '=' value '>']
    . . .
    [alternateHTML]
    '</APPLET>'

'CODEBASE' '=' codebaseURI
    This optional attribute specifies the base URI of the applet --
    the directory that contains the applet's code.  If this attribute
    is not specified, then the document's URI is used.

'CODE' '=' appletFile
    This required attribute gives the name of the file that contains
    the applet's compiled Applet subclass.  This file is relative to
    the base URI of the applet.  It cannot be absolute.
    
'ALT' '=' alternateText
    This optional attribute specifies any text that should be
    displayed if the browser understands the APPLET tag but can't
    run Java applets.

'NAME' '=' appletInstanceName
    This optional attribute specifies a name for the applet instance,
    which makes it possible for applets on the same page to find (and
    communicate with) each other.

'WIDTH' '=' pixels 'HEIGHT' '=' pixels
    These required attributes give the initial width and height (in
    pixels) of the applet display area, not counting any windows or
    dialogs that the applet brings up.  

'ALIGN' '=' alignment
    This required attribute specifies the alignment of the applet.
    The possible values of this attribute are the same as those for
    the IMG tag: left, right, top, texttop, middle, absmiddle,
    baseline, bottom, absbottom.

'VSPACE' '=' pixels 'HSPACE' '=' pixels
    These option attributes specify the number of pixels above and
    below the applet (VSPACE) and on each side of the applet (HSPACE).
    They're treated the same way as the IMG tag's VSPACE and HSPACE
    attributes.

'<' 'PARAM' 'NAME' '=' appletAttribute1 'VALUE' '=' value '>' . . .
    This tag is the only way to specify an applet-specific attribute.
    Applets access their attributes with the getParameter() method.


Debugging programs with JDB
---------------------------
This release contains the Java Debugger (JDB), an alpha-quality
prototype of a command-line debugger for Java classes.  It is
designed to test the Java Debugger API, which is in the package
java.tools.debug.  We look forward to getting your feedback on
the debugger API.

You can debug applets using the -debug option of appletviewer.
When debugging applets, it's best to invoke appletviewer from
the directory that contains the applet's HTML file.  For example,
on Solarix:

    cd demo/TicTacToe
    ../../bin/appletviewer -debug example1.html 

On the PC:

    cd demo\TicTacToe
    ..\..\bin\appletviewer -debug example1.html 
    
