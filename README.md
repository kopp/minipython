![image](https://github.com/mytechnotalent/minipython/blob/master/MiniPython.png?raw=true)

MiniPython for the BBC micro:bit
================================

This is the source code for MiniPython running on the BBC micro:bit with
additional features based on
[the original MicroPython](https://github.com/bbcmicrobit/micropython)
version for the BBC micro:bit!


Goals of MiniPython and Contrast to MicroPython
-----------------------------------------------

***NOTE:*** This is a new fork and in early stages of development.  Please be patient as this develops out.

The goal is to help educators have an active fork to add custom functionality to their curriculum in the form of modules.
This way, a teacher could distribute an hex-file containing all the necessary tools/libraries for his/her course.
To allow for this, a step-by-step guide for how to build your own modules will be published here soon.

The same technique would allow people hacking on MicroPython to easily test out a new module which maybe they would like to have included in an "official release" for a specific HW plattform.

In contrast, [MicroPython](https://micropython.org/) aims to provide a lean implementation of (a subset of) Python 3 with the python standard library, upon which people can build custom projects.

The ultimate goal is to get more people involved with MicroPython nothing more.


Overview and Build instructions
===============================


To get involved with the micro:bit community join the Slack channel by signing up here:
https://tech.microbit.org/get-involved/where-to-find/

Various things are in this repository, including:
- Source code in source/ and inc/ directories.
- Example Python programs in the examples/ directory.
- Tools in the tools/ directory.
- Integrated Friend module chatbot.

The source code is a yotta application and needs yotta to build, along
with an ARM compiler toolchain (eg arm-none-eabi-gcc and friends).

Ubuntu users can install the needed packages using:
```
sudo add-apt-repository -y ppa:team-gcc-arm-embedded
sudo add-apt-repository -y ppa:pmiller-opensource/ppa
sudo apt-get update
sudo apt-get install cmake ninja-build gcc-arm-none-eabi srecord libssl-dev
pip3 install yotta
```

Once all packages are installed, use yotta and the provided Makefile to build.
You might need need an Arm Mbed account to complete some of the yotta commands,
if so, you could be prompted to create one as a part of the process.

- Use target bbc-microbit-classic-gcc-nosd:

  ```
  yotta target bbc-microbit-classic-gcc-nosd
  ```

- Run yotta update to fetch remote assets:

  ```
  yotta up
  ```

- Start the build:

  ```
  make all
  ```

The resulting firmware.hex file to flash onto the device can be
found in the build/ directory from the root of the repository.

The Makefile provided does some extra preprocessing of the source,
adds version information to the UICR region, puts the resulting
firmware at build/firmware.hex, and includes some convenience targets.

How to use
==========

Upon reset you will have a REPL on the USB CDC serial port, with baudrate
115200 (eg picocom /dev/ttyACM0 -b 115200).

Then try:

    >>> import microbit
    >>> microbit.display.scroll('hello!')
    >>> microbit.button_a.is_pressed()
    >>> dir(microbit)

Tab completion works and is very useful!

Read our documentation here:

https://minipython.readthedocs.io/en/latest/

You can also use the tools/pyboard.py script to run Python scripts directly
from your PC, eg:

    $ ./tools/pyboard.py /dev/ttyACM0 examples/conway.py

Be brave! Break things! Learn and have fun!
