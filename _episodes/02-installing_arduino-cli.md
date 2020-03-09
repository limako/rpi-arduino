---
title: "Installing arduino-cli"
teaching: 20
exercises: 0
questions:
- "How can you program an Arduino board?"
objectives:
- "Install and configure arduino-cli."
keypoints:
- "There are graphical and command-line packages to program Arduinos"
---
Until recently, the best way to program an Arduino was to use an
Integrated Development Environment (IDE). The IDE provides a graphical interface to write programs, compile them, and upload them to the Arduino.

More recently, a command-line application for programming
Arduinos and similar devices has been developed. The [arduino-cli project is hosted at
github](https://github.com/arduino/arduino-cli)

You can download an install script (written in bash) and pipe it directly to a script to install it.

~~~
$ curl -fsSL https://raw.githubusercontent.com/arduino/arduino-cli/master/install.sh | sh
~~~
{: .language-bash}

This will install the program in the "bin" directory of your home directory.

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

Assuming it finds a board it recognizes, you should see the type of board and the serial port it's on. Using this, you can construct the commands you need to compile and upload a program.

If you're using some other type of Arduino-like board, you may need to do additional configuration of the arduino-cli program.
~~~
$ arduino-cli config init
~~~
{: .language-bash}

This command will save a "arduino-cli.yaml" file inside an invisible ".arduino15 directory inside your home directory. This file includes a place where you can specify additional URLs for the "board manager" that will ensure the Arduino can recognize and interact with your particular board.


{% include links.md %}
