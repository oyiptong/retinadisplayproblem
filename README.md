Retina Mac External Display Problem
===================================

#### Warning: This may cause your external monitor to stop displaying. Be prepared to close the browser tab for your monitor to function

What
----

There seems to be a problem where if a 1st-gen Retina Macbook Pro is attached to an external display, when a certain image pattern is attempted to be drawn, the external monitor will shut off.

The monitor will start to show some artifacting patterns, then shut off, unable to draw the screen.

How
---

Using a browser:

1. Pick any browser, make it full-screen, or at least full-width
2. Open the index.html page in the browser
3. Wait until the monitor shows artifacting and/or shuts off

Using preview:

1. Open [display_problems.png](https://raw.github.com/oyiptong/retinadisplayproblem/master/display_problem.png) in Preview.app or using a web browser
2. Make sure the image viewer renders the image unscaled
3. Wait until the monitor shows artifacting and/or shuts off

Web pages:

* [Dan Fraser](http://www.capybara.org/~andrew/noise/)'s 1px reproduction of the bug.
* [Olivier Yiptong](https://people.mozilla.com/~oyiptong/retinadisplayproblem/index.html)

Affected gear
-------------

Computer:

* MacbookPro10,1

Monitors:

* Dell U2410
* Samsung S27B350
* LG W2442PA

OS:

* Mac OS X 10.8
* Windows 7 via bootcamp

Note: Could not reproduce on fedora via bootcamp

Footage
-------

* [Dell U2410](https://vimeo.com/68238157)
