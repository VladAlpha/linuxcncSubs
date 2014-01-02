linuxcncSubs
============

Collection of custom and stolen subroutines and m/g codes for linuxcnc
designed for use in NGCGUI unless otherwise stated.  Not guarenteed to be functional or safe but I will do my best to keep accurate notes but do not trust blindly.

Summary of subroutines and files contained within.  Note this readme may not always be perfectly up to date so check sub for extra info in comments or commits, and always test in air and sim before running on your machine!

annulusmill.ngc : will incrementally mill an annulus (doughnut) starting from Z safe, centers over feature, drops to z start which should be just above the material, can be same as z safe.  depending on dimensions it is cut with three distinct routines in 1, 2 or multiple passes.  only multipass has a finish cut.


===========================
******    TO DO     *******
===========================

annulusmill: optimize plunge
  re-configure mooltipass to look ahead and select best stepover
  more aggressive spiral out could save 1/2 turn
