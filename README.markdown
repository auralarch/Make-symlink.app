Make-SymLink.app: an OSX droplet for creating Symbolic Links
============================================================

A GUI-based symbolic link (symlink, soft link, unix alias) maker for OS X 10.6+.

While the Finder does not perceptibly differentiate between aliases and symbolic
links (calling them both aliases), the underlying file system & operating
system does denote the difference which is evident by its behavior.  Both
aliases and symbolic links each have their own pros and cons making one of them
more suited to certain applications. In general symbolic links are more
universally compatible, and will be recognized by other operating systems and
more apps within OS X.
But aliases are more resilient to breaking and continue to work if you move the
target. More detailed information is available online.

Installation
------------

Copy Make-SymLink.app somewhere sensible (perhaps Library/Scripts or Applications
in your home folder). From that folder in the Finder, drag the Make-SymLink.app
icon onto the toolbar of the Finder window for convenient usage.

Usage
-----

Drag the file or directory you want to link to (the source/target your link will
point to) onto the the icon you placed in the toolbar.
Enter a new filename if you would like your link to have a different name than
the source/target.
Select the folder where to create the link.

Thanks to
---------

* [rusto](http://forums.macosxhints.com/archive/index.php/t-3017.html) for the
  start.
