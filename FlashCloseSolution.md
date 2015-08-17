# Billboard Unit : Flash Based Close Button Solution #

### Assumptions ###

While logic shown here can be applied across any solution, the technology utilized in the sample files assumes implementation of DoubleClick rich media technology and adherence to standard sizes acceptable through the [IAB](http://www.iab.net/risingstars) for this ad unit.

### Logic ###

**On Page Load**
  1. HTML page completes load.
  1. iframe is created and appended to ad unit div.
  1. Ad tag is loaded into iframe (**impression +1**).
  1. External interface call is made from Flash to JS function on page requesting cookie value.
  1. JS function checks for cookie existence / value and returns to Flash.

  * **Cookie exists : value is expanded**
    1. Rich media Flash unit is set to expanded 970x250 state
    1. Full billboard creative assets are loaded into ad tag through Flash parent file
    1. Ad unit div dimensions are defined to 970x250

  * **Cookie exists : value is collapsed**
    1. Rich media Flash unit is set to collapsed 196x31 state
    1. Collapsed show ad button creative assets are loaded into ad tag through Flash parent file
    1. Ad unit div dimensions are defined to 300x31 and positioned to the right of the page

  * **Cookie does not exist**
    1. JS sets cookie with value of expanding, expiring at midnight
    1. Rich media Flash unit is set to expanded 970x250 state
    1. Full billboard creative assets are loaded into ad tag through Flash parent file
    1. Ad unit div dimensions are defined to 970x250

**On Click to Close Button from Flash**
  1. External interface call is made to JS to collapse.
  1. JS resets cookie value to collapsed.
  1. Rich media Flash unit is set to collapsed 196x31 state
  1. Collapsed show ad button creative assets are loaded into ad tag through Flash parent file
  1. Ad unit div dimensions are defined to 300x31 and positioned to the right of the page

**On Click to Show Button from Flash**
  1. External interface call is made to JS to expand.
  1. JS resets cookie value to expanded.
  1. Rich media Flash unit is set to expanded 970x250 state
  1. Full billboard creative assets are loaded into ad tag through Flash parent file
  1. Ad unit div dimensions are defined to 970x250

### Source Code ###

  * [AS 3.0](http://code.google.com/p/iab-billboard-adunit/wiki/FlashCloseSolutionAS)
  * [HTML / JS](http://code.google.com/p/iab-billboard-adunit/wiki/FlashCloseSolutionHTML)
  * [CSS](http://code.google.com/p/iab-billboard-adunit/wiki/FlashCloseSolutionCSS)