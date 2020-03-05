---
title: "Installing arduino-cli"
teaching: 0
exercises: 0
questions:
- "What is the Arduino platform?"
objectives:
- "First learning objective. (FIXME)"
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---
Until recently, the best way to program an arduino was to use an
Integrated Development Environment (IDE). Recently, they've developed
a command-line application for programming
arduinos and similar devices. The [arduino-cli project is hosted at
github](https://github.com/arduino/arduino-cli)

You can download an install script (written in bash) and pipe it directly to a script to install it.

~~~
$ curl -fsSL https://raw.githubusercontent.com/arduino/arduino-cli/master/install.sh | sh
~~~
{: .language-bash}

This will install the program in your "bin" directory.

You can check by running the "which" command:

~~~
$ which arduino-cli
~~~
{: .language-bash}

which should show you where the program is installed.

If you run the program with no arguments:

~~~
$ arduino-cli
~~~
{: .language-bash}

It should emit a "help" message that shows the available options and commands. We should be able to use the arduino-cli program to see the Arduino board you have connected to the Pi.

~~~
$ arduino-cli board list
~~~
{: .language-bash}

Assuming it finds a board it recognizes, you should see the type of board and the serial port its on. Using this, you can construct the commands you need to compile and upload a program.



{% include links.md %}
