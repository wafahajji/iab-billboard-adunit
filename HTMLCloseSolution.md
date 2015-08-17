# Billboard Unit : HTML / JS Based Close Button Solution #

### Assumptions ###

While logic shown here can be applied across any solution, the technology utilized in the sample files assumes implementation of DoubleClick rich media technology and adherence to standard sizes acceptable through the [IAB](http://www.iab.net/risingstars) for this ad unit.

### Logic ###

**On Page Load**
  1. HTML page completes load.
  1. Javascript function is called to check for cookie existence.

  * **Cookie exists : value is expanded**
    1. Show ad button div display is is hidden
    1. Ad unit div dimensions are defined to 970x250
    1. iframe is created and appended to ad unit div
    1. Ad tag is loaded into iframe (**impression +1**)

  * **Cookie exists : value is collapsed**
    1. Image is appended to show button div
    1. show button div display is set to visible
    1. show button div dimensions are defined to 300x31

  * **Cookie does not exist**
    1. JS sets cookie with value of expanding, expiring at midnight
    1. Ad unit div dimensions are defined to 970x250
    1. Show ad button div display is is hidden
    1. iframe is created and appended to ad unit div
    1. Ad tag is loaded into iframe (**impression +1**)

**On Click to Close Button from Flash**
  1. External interface call is made to JS function on page.
  1. JS function checks cookie : value is expanded, collapse called
  1. Image is appended to show button div
  1. Show button div display is set to visible
  1. Show button div dimensions are defined to 300x31
  1. iframe is removed from ad unit div
  1. Cookie is set to collapsed

**On Click to Show Button from HTML**
  1. JS function is called to check cookie : value is collapsed, expand called
  1. Show ad button div display is is hidden
  1. Ad unit div dimensions are defined to 970x250
  1. iframe is created and appended to ad unit div
  1. Ad tag is loaded into iframe
  1. Cookie is set to expanded

### Source Code ###

  * [AS 3.0](http://code.google.com/p/iab-billboard-adunit/wiki/HTMLCloseSolutionAS)
  * [HTML / JS](http://code.google.com/p/iab-billboard-adunit/wiki/HTMLCloseSolutionHTML)
  * [CSS](http://code.google.com/p/iab-billboard-adunit/wiki/HTMLCloseSolutionCSS)