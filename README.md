linuxcncSubs
============

Collection of custom and stolen subroutines and m/g codes for linuxcnc
designed for use in NGCGUI unless otherwise stated.  Not guarenteed to be functional or safe but I will do my best to keep accurate notes but do not trust blindly.

Summary of subroutines and files contained within.  Note this readme may not always be perfectly up to date so check sub for extra info in comments or commits, and always test in air and sim before running on your machine!

====================
****** Tips ********
====================

In my bizzare brain, the following conventions make sense and are followed as well as possible:
* avoid _ in var names, makes code harder to read
* generally vars like <rad> or some kind of location are where the cut will be upon completion of that iteration, current location
* code is formatted for pretty folding in sublime text to keep it readable
* standalone NGCs that resemble subroutines are from testing as subs do not return usefull line numbers, any such files are vestigal or in testing, unlikely to serve a purpose
* if you don't use sublime text as an editor, you should.  If you do,  I have a very simple syntax file on github you should snag to color your code all pretty like. also flags a few errors I am prone to

=====================
*** Specific Subs ***
=====================

annulusmill.ngc : will incrementally mill an annulus (doughnut) starting from Z safe, centers over feature, drops to z start which should be just above the material, can be same as z safe.  depending on dimensions it is cut with three distinct routines in 1, 2 or multiple passes.  only multipass has a finish cut.

boxedge: simply creates a box edge of the dimensions given.  Any corner can be used with proper sign for edge length.  will likely be renamed boxcut to match my convention.

===========================
******    TO DO     *******
===========================

annulusmill: optimize plunge
  re-configure mooltipass to look ahead and select best stepover
  more aggressive spiral out could save 1/2 turn
  two pass wastes a ton of rotation

boxedge
