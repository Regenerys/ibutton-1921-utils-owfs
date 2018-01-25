# iButton 1921 Utilities for OWFS

by Ben Oliver for Regenerys Ltd
ben.oliver@regenerys.com

These are bash script wrappers for the owfs - the one wire filesystem.

Use them with DS1921 data loggers. You might be able to adapt them to use other loggers too.

They are intended for use on a Linux system and rely on a basic UNIX toolkit.

[Make sure OWFS is installed first](http://owfs.org/)

To get started, plug in your USB reader and do

    mkdir ~/owfs
    owfs -u -m ~/owfs

Then your reader and button should be mounted as a filesystem in `~/owfs`
