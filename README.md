# iButton 1921 Utilities for OWFS

_by Ben Oliver for Regenerys Ltd_
_ben.oliver@regenerys.com_

These are bash script wrappers for owfs - the one wire filesystem.

Use them with DS1921 data loggers. You might be able to adapt them to use other loggers too.

The focus of the project is to be able to provision and extract data from multiple buttons quickly and accurately. We have used it to provision 100 loggers in under 5 minutes.

It borrows a little from [this project](https://github.com/clemens-it/tcibm), particularly the data handling, but I have written the workflow from scratch with a goal to make it easy to provision large numbers of thermocrons.

Right now there is only a script for provisioning, but it does dump the data before doing so. More should come soon, however look in the `functions` file to see functions you can re-use.

They are intended for use on a Linux system and rely on a basic UNIX toolkit.

It only works for USB (the DS9490 I think) but I have left it open to work with other readers.

## Installation

- [Make sure OWFS is installed first](http://owfs.org/)
- Clone this repo to somewhere nice

## Usage

`cd` to this directory and:

    cp config.sample config

Then pick your favourite editor and edit the config. See below for more details.

Once the config is how you want it, run (from inside the cloned directory):

    ./provision

It will:

1. Dump the data into a txt file (optional)
1. Clear the memory
1. Set the clock
1. Set the new parameters according to the config
1. Provision the button logger
1. Write the logger ID to a log (optional)
1. Wait for your input before repeating the previous steps over and over again or your signal to quit

## Configuration

A sample config file is provided. Make sure you copy it and name it `config`.

| Name       | Data Type | Notes                                                                                                                                                       |
|------------|-----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| MOUNTPOINT | directory | Where OWFS will mount. I like ~/owfs1                                                                                                                       |
| BUSDIR     | string    | The bus OWFS sees your probes on. Mine is bus.0. My colleague is bus.1, so mount owfs (`owfs -u -m /mount/point`) and check (`cd /mount/point/bus.X`).      |
| FAMILY     | string    | Usually a number. `1921` data loggers all have the same family number of 21, and so the directory owfs creates for it is always called `21.xxxx`            |
| ROLLOVER   | boolean   | Dictates whether the mission stops when the memory is full, or just overwrites the oldest data points.                                                      |
| FREQUENCY  | integer   | The sample frequency, in minutes, up to 255                                                                                                                 |
| DELAY      | integer   | The delay before the mission starts, in minutes, up to 255                                                                                                  |
| ISUSB      | boolean   | Keep this true for now. This is present in order to potentially expand the usage to non-USB readers (which would require a different OWFS command to mount) |
| OUTPUTDIR  | directory | This is where the data goes                                                                                                                                 |
| LOGGING    | boolean   | write a log of events, includes config and a list of probes used                                                                                            |
| DUMPDATA   | boolean   | Applies to provisioning only. Dump the data before provisioning the logger (and therefore wiping the current memory)                                        |
| MEMORY     | string    | 512 bytes of memory to write some text. The sample config puts the date of provisioning in there.                                                           |
