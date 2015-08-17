# IAB Billboard Ad Unit #

<img src='http://www.johnpaulkelly.me/iab/demo/billboard.png' />

## Introduction ##

This project utilizes javascript and browser cookies to control loading of ad tag or Flash display state of the [Billboard](http://www.youtube.com/watch?v=rZZKQQAvjVw) ad unit. Two versions exist, depending on preference of publisher hosted show ad button or advertiser created Flash button. Full sample files exist here, along with all coding required to achieve the desired result.

Sample files and coding existing in this project utilize DoubleClick rich media and Studio technology. Flash, JavaScript and all HTML and CSS assets will give you a good idea how to set up your execution regardless of technology used.

Please note that this solution is simply a suggested example of what can be done to achieve this result. Other options exist and it is at the publisher or site owner discretion on how to implement the functionality to collapse the ad unit.

## Projects ##

Project overviews on the Wiki will demonstrate the coding involved with setting up two different implementations of communication between a Flash unit and site hosted JavaScript. Using similar methods and logic, this project will focus on communication between a Flash file and site hosted JavaScript. This script will set or receive browser cookie values, which will be returned to Flash and/or JavaScript to determine the appropriate display state and/or HTML display settings via CSS attributes.

**IAB Billboard : Flash Close Button Implementation** | [logic](http://code.google.com/p/iab-billboard-adunit/wiki/FlashCloseSolution)

This solution will trigger an ad request and impression increment on every visit to the page. Visibility defaults to the full Billboard execution on first visit of the day, while setting a cookie with the current state, expiring at midnight. On revisit to the page, users will receive either the full Billboard or the unbranded show button, depending on the state they last selected. Show button exists in the Flash execution.

**IAB Billboard : HTML Close Button Implementation** | [logic](http://code.google.com/p/iab-billboard-adunit/wiki/HTMLCloseSolution)

This solution will only trigger an ad request and impression increment on first visit to the page and any subsequent visits when last page visit was set to the expanded state. Visibility defaults to the full Billboard execution on first visit of the day, while setting a cookie with the current state, expiring at midnight. On revisit to the page, users will receive either the full Billboard or the unbranded show button, depending on the state they last selected. Show button exists within the HTML page content.

## Demos ##

[Flash Version](http://johnpaulkelly.me/iab/flash_branded/index.html)

[HTML Version](http://johnpaulkelly.me/iab/js_nobranded/index.html)

## Source Code ##

Flash Solution : [AS 3.0](http://code.google.com/p/iab-billboard-adunit/wiki/FlashCloseSolutionAS) | [HTML / JS](http://code.google.com/p/iab-billboard-adunit/wiki/FlashCloseSolutionHTML) | [CSS](http://code.google.com/p/iab-billboard-adunit/wiki/FlashCloseSolutionCSS)

HTML Solution : [AS 3.0](http://code.google.com/p/iab-billboard-adunit/wiki/HTMLCloseSolutionAS) | [HTML / JS](http://code.google.com/p/iab-billboard-adunit/wiki/HTMLCloseSolutionHTML) | [CSS](http://code.google.com/p/iab-billboard-adunit/wiki/HTMLCloseSolutionCSS)

