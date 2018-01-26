# iButton 1921 Utilities for OWFS

by Ben Oliver for Regenerys Ltd
ben.oliver@regenerys.com

These are bash script wrappers for the owfs - the one wire filesystem.

Use them with DS1921 data loggers. You might be able to adapt them to use other loggers too.

The focus of the project is to be able to provision and extract data from multiple buttons quickly and accurately.

Right now there is only a script for provisioning. More should come soon, however look in the `functions` file to see functions you can re-use.

They are intended for use on a Linux system and rely on a basic UNIX toolkit.

[Make sure OWFS is installed first](http://owfs.org/)

Then just `cd` to this directory and run

    ./provision

It only works for USB but I have left it open to work with other readers.
