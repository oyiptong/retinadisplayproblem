Retina Mac External Display Problem
===================================

#### Warning: This may cause your external monitor to stop displaying. Be prepared to close the browser tab for your monitor to function

What
----

There seems to be a problem where if a 1st-gen Retina Macbook Pro is attached to an external display, when a certain image pattern is attempted to be drawn, the external monitor will shut off.

The monitor will start to show some artifacting patterns, then shut off, unable to draw the screen.

How
---

Either get the code:

1. Clone the repository
2. Pick any browser, make it full-screen, or at least full-width
3. Open the index.html page from your local repo in the browser
4. Wait until the monitor shows artifacting and/or shuts off

Or open one of these web pages:

* [Dan Fraser](http://www.capybara.org/~andrew/noise/)'s reproduction of the bug.
* [My version](https://people.mozilla.com/~oyiptong/retinadisplayproblem/index.html) with progressive animation to find the "breaking point"

Dan's will make the screen go blank faster, (instantly in my case). Mine will progressively add the repeating pattern on-screen until the problem occurs.

Affected gear
-------------

Computer:

* MacbookPro10,1

Monitors:

* Dell U2410
* Samsung S27B350
* LG 23EN43
* LG W2442PA
* LG W2240V
* Apple 23" Cinema Display
* Samsung SyncMaster P2770

Monitors not affected:

* Apple 27" Cinema

OS:

* Mac OS X 10.8
* Windows 7 via bootcamp

Footage
-------

* [Dell U2410](https://vimeo.com/68238157)
* [LG Flatron W2240V](https://vimeo.com/68255631) courtesy of [unr](https://github.com/unr)
* [LG W2442PA](https://vimeo.com/68274344) courtesy of [Byron Jones](https://github.com/globau)

Causation
---------

Here are some plausible theories on the cause:

1. mbell over at [hacker news](https://news.ycombinator.com/item?id=5870720):
    
    > Just a guess:  
    > The patterns in the examples seem to be horizontal, meaning the raw (pre 'cable encoding', usually 8b/10b) bit pattern of the display output would be repetitive . It wouldn't be out of the question that a slightly improperly electrically balanced or terminated output could cause signal integrity issues, including ringing (voltage exceeds spec on rising / falling edges) which could trigger safeguard circuitry in a display (shut it off).  
    >
    > If my guess is correct, it would be a problem in the design of the output transceiver circuit on the RMP's motherboard, assuming the cable and receiver in the display are built to spec.  
    > Could be an IC issue, could be the impedance control of the connector, could be the impedance control of the traces on the circuit board, could be poorly chosen passives, could be interference from nearby circuits, etc.  
    >
    > I wish I could give you a better answer but high speed signal integrity is one of the most obtuse and most black art aspects of electronics design, there's a fair amount of non-intuitive physics going on, e.g. signals going down a wire don't just go, they 'ricochet' off impedance differences. It's far too large a topic to treat in a HN comment and its whole system encompassing so 'what it could be' is a large set.  
    >
    > These types of things are not uncommon in hardware development, especially with high speed signaling. The interactivity of such systems can be high and hard to predict fully at times.  
    >
    > EDIT: Simply put - display outputs scan top to bottom, left to right. The fact that the pattern that triggers the issue appears to be horizontal means it would occur in the raw bit stream of the output in a periodic way. That means there is some low order frequency in the system caused by this pattern (maybe it repeats every 500khz or something like that). If there is something in the electronics of the output of the RMBp that resonates at that frequency (easier than you think), then it could possibly cause the described failure.  
    
    mbell's alternate take:
    
    > I thought of a simpler, or at least more relatable, analogy:  
    >
    > Most people have been around a cell phone which was near an audio speaker and heard it make those awful snap and pop sounds.  
    >
    > It doesn't make sense initially that you would hear anything like that from a phone, after all they operate at very high frequency, 900 - 2400 Mhz, definitely not audible frequencies. But, the system works by breaking up radio time into chunks, several hundred chunks a second. The relative spacing of the chunks, a few hundred a second, creates noise that is easily picked up by the speaker and turned into audible sound.  
    >
    > In the same way with the laptop you've got this high frequency signal: HDMI / DVI but when there are particular patterns of bits being carried you can get lower frequency content, similar to the chunks being used by the cell phone. Just like the coil in the speaker gets excited by the radio chunks, you could have a problem where the output circuitry of the RMBp gets excited by these rare low frequency patterns leading to problems with the display.  

3. [elmood](http://www.capybara.org/) from freenode on the topic:
    
    > &lt;oyiptong_&gt; so here's a possible explanation: https://news.ycombinator.com/item?id=5870720  
    > &lt;oyiptong_&gt; i don't understand it =/  
    > &lt;elmood&gt; the ringing makes sense i suppose  
    > &lt;elmood&gt; but i wonder how much ringing there is in an HDMI cable really  
    > &lt;elmood&gt; and why it only happens with certain models  
    > &lt;elmood&gt; maybe improper termination in the adapter  
    > &lt;oyiptong_&gt; what's ringing?  
    > &lt;elmood&gt; video and high speed signals travel down transmission lines  
    > &lt;elmood&gt; which means that the signal has to be matched to the wire, circuit board, connector all the way along  
    > &lt;elmood&gt; for a constant impedance  
    > &lt;elmood&gt; incorrect impedances cause the signal to reflect back and forth, or get distorted  
    > &lt;elmood&gt; you can mostly see it on VGA if you use a bad cable or put a few cables together  
    > &lt;elmood&gt; you can see little ghosts  
    > &lt;elmood&gt; like echos that extend to the right of sharp edges  
    > &lt;oyiptong_&gt; i see  
    > &lt;elmood&gt; that is impedance mismatch in the cables  
    > &lt;elmood&gt; and what you see is the time it takes for the signal to bounce back and forth  
    > &lt;elmood&gt; about 1ns per metre of cable or less  
    > &lt;elmood&gt; err 1ns per foot i think  
    > &lt;elmood&gt; a pixel on a high res screen is <10ns usually  
    > &lt;oyiptong_&gt; why does it occur only on retina macs so far then?  
    > &lt;elmood&gt; i don't know  
    > &lt;oyiptong_&gt; hmmm interesting  
    > &lt;elmood&gt; perhaps the driver chip used in these adapters is not very good  
    > &lt;elmood&gt; or the board is not designed correctly  
    > &lt;elmood&gt; i did a lot of video stuff some years ago so learned all about this  
    > &lt;elmood&gt; i was measuring the length of CAT5 cables and stuff electrically  
    > &lt;elmood&gt; quite fun!  
    > &lt;oyiptong_&gt; that sounds fun!   
