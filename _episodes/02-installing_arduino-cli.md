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
- "Arduino software uses a serial connection to program the device."

---
Until recently, the best way to program an Arduino was to use an
Integrated Development Environment (IDE). The IDE provides a graphical interface to write programs, compile them, and upload them to the Arduino.

More recently, a command-line application for programming
Arduinos and similar devices has been developed. The [arduino-cli project is hosted at
github](https://github.com/arduino/arduino-cli) and includes [documentation](https://arduino.github.io/arduino-cli/).

You can download an install script (written in bash) and pipe it directly to a script to install it.

~~~
$ curl -fsSL https://raw.githubusercontent.com/arduino/arduino-cli/master/install.sh | sh
~~~
{: .language-bash}

This will install the program in the "bin" directory of your home directory.

When you install it, it make need to create the "bin" directory. If that directory didn't exist when you logged in, your path will not include it. The easiest way to solve this problem is to log out and log back in.

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

Assuming it finds a board it recognizes, you should see the serial port it's on, the name of the board, the Fully Qualified Board Name (FQBN), and the core.

~~~
Downloading missing tool builtin:ctags@5.8-arduino11...
builtin:ctags@5.8-arduino11 downloaded                                          
Installing builtin:ctags@5.8-arduino11...
builtin:ctags@5.8-arduino11 installed
Downloading missing tool builtin:serial-discovery@1.0.0...
builtin:serial-discovery@1.0.0 downloaded                                       
Installing builtin:serial-discovery@1.0.0...
builtin:serial-discovery@1.0.0 installed
Updating index: library_index.json downloaded                                   
Updating index: package_index.json downloaded                                   
Updating index: package_index.json.sig downloaded                               
Port         Type              Board Name  FQBN            Core       
/dev/ttyACM0 Serial Port (USB) Arduino Uno arduino:avr:uno arduino:avr
/dev/ttyAMA0 Serial Port       Unknown                                
~~~
{: .output}

You may need to install the core.  You can check which cores are installed:

~~~
$ arduino-cli core list
~~~
{: .language-bash}

And then, if it's not in the list, install the required core:

~~~
$ arduino-cli core install [core]
~~~
{: .language-bash}

If you're using some other type of Arduino-like board, you may need to do additional configuration of the arduino-cli program.

~~~
Downloading packages...
arduino:avr-gcc@7.3.0-atmel3.6.1-arduino7 already downloaded
arduino:avrdude@6.3.0-arduino17 already downloaded
arduino:arduinoOTA@1.3.0 already downloaded
arduino:avr@1.8.3 already downloaded
Installing arduino:avr-gcc@7.3.0-atmel3.6.1-arduino7...
arduino:avr-gcc@7.3.0-atmel3.6.1-arduino7 installed
Installing arduino:avrdude@6.3.0-arduino17...
arduino:avrdude@6.3.0-arduino17 installed
Installing arduino:arduinoOTA@1.3.0...
arduino:arduinoOTA@1.3.0 installed
Installing arduino:avr@1.8.3...
Configuring platform...
arduino:avr@1.8.3 installed
~~~
{: .output}

~~~
$ arduino-cli config init
~~~
{: .language-bash}

This command will save a "arduino-cli.yaml" file inside an invisible ".arduino15 directory inside your home directory. This file includes a place where you can specify additional URLs for the "board manager" that will ensure the Arduino can recognize and download the necessary core to work with your particular board.

{% include links.md %}
