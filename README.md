linuxcncSubs
============

Collection of custom and stolen subroutines and m/g codes for linuxcnc
designed for use in NGCGUI unless otherwise stated.  Not guarenteed to be functional or safe but I will do my best to keep accurate notes but do not trust blindly.

Summary of subroutines and files contained within.  Note this readme may not always be perfectly up to date so check sub for extra info in comments or commits, and always test in air and sim before running on your machine!

====================
****** Tips ********
====================

In my bizzare brain, the following conventions make sense and are followed as well as possible:
* MACHINE STATE MUST BE AS SIMILAR BEFORE AND AFTER AS POSSIBLE!
    > Passing a 0 to a setting that does not make sense causes it to be ignored
        * tool
        * feedrate
        * spindle speed
        * ??????
    > avoid G91 in subs 
* routines ending in "cut" are for tracing the edge of a feature, ie cutting it out
* routines ending in "mill" are for pocketing and will cut down
* avoid _ in var names, makes code harder to read
* generally vars like <rad> or some kind of location are where the cut will be upon completion of that iteration, NOT the current location
* code is formatted for pretty folding in sublime text to keep it readable
* standalone NGCs that resemble subroutines are from testing as subs do not return usefull line numbers, any such files are vestigal or in testing, unlikely to serve a purpose
* if you don't use sublime text as an editor, you should.  If you do,  I have a very simple syntax file on github you should snag to color your code all pretty like. also flags a few errors I am prone to making
* dates are formatted yyyy-mm-dd

=====================
*** Specific Subs ***
=====================

annulusmill.ngc : will incrementally mill an annulus (doughnut) starting from Z safe, centers over feature, drops to z start which should be just above the material, can be same as z safe.  depending on dimensions it is cut with three distinct routines in 1, 2 or multiple passes.  only multipass has a finish cut.

boxcut: simply creates a box edge of the dimensions given.  Any corner can be used with proper sign for edge length.  will likely be renamed boxcut to match my convention.

trimstock: takes a first corner, closest to origin, and a raw stock width in Y and part length in X, and both angles measured to the right of the edge, and will trim/true up part in one pass.  Currently fails on Negative lenghts

===========================
******    TO DO     *******
===========================

* remove G91 from annulus mill
* make mill functions have an inverse, given a stock size, remove all material outside feature
* optimize stepover such that there is no mini final pass prior to finish passes
* create images for each sub
* autocomplete syntax?
* "standardize" input layout for readability
* check all subs are cutting full depth always, strange results seen w/ boxcut 2014-01

annulusmill: optimize plunge
  re-configure mooltipass to look ahead and select best stepover
  more aggressive spiral out could save 1/2 turn
  two pass wastes a ton of rotation

boxcut
    renamed from boxedge

===========================
******  KNOWN BUGS  *******
===========================

* may not always cut to full depth?
* trim stock can not handle negative length for Y, will not clear edge of material
*