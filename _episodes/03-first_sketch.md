---
title: "First Sketch"
teaching: 20
exercises: 10
questions:
- "How do you program the Arduino?"
- "What is the structure of an Arduino program?"
objectives:
- "Install software for programming the Arduino."
- "Explore the structure of a 'sketch' or Arduino program."
- "Configure the settings necessary to program an Arduino."
keypoints:
- "Arduino programs are called 'sketches' with a program file inside a directory."
- "Arduino programs have two functions: a 'setup' function that is run once, and a 'loop' function that runs forever."
---

The classic "hello world" program in the Arduino world is "blink".

This command will create a new sketch:

~~~
$ arduino-cli sketch new blink
~~~
{: .language-bash}

This creates a directory named "blink" and a file inside named "blink.ino" which contains the program.  Go into directory (i.e. "cd blink") and then edit the blink.ino file.  The file will already contain "setup" and "loop functions" but you can delete everything and replace with this:

~~~
void setup() {
  pinMode(LED_BUILTIN, OUTPUT);
}

void loop() {
  digitalWrite(LED_BUILTIN, HIGH);
  delay(500);
  digitalWrite(LED_BUILTIN, LOW);
  delay(500);
}
~~~
{: .source}

> ## Case Sensitive:
>
> Using arduino-cli, programs are case-sensitive. On some platforms, computer programs are not case sensitive: it doesn't matter whether letters are capital or lower case. But using arduino-cli, case matters.
{: .callout}


Once you've saved the sketch, you can try to compile the program. Note that to compile, you need to specify the board you identified in the previous section.

~~~
$ arduino-cli -b=arduino:avr:uno compile
~~~
{: .language-bash}

You should get a message with info about how much memory the sketch will require. Or an error message with information for debugging the problem.

Once you successfully compile the program, you can upload it to the Arduino. As above, you need to also identify the serial port where the board is connected.

~~~
$ arduino-cli -b arduino:avr:uno -p /dev/ttyACM0 upload
~~~
{: .language-bash}

> ## Working efficiently:
>
> If you have to type out these entire commands each time you do anything,
> it would be a lot of effort. Luckily you can use the shell history to reuse
> commands. It's perhaps useful to open two terminal windows:
> one where you are editing your sketch and another where you compile and upload the sketch.
>
> You can also create aliases that make short versions of the commands
> to save keystrokes. You can add these to a .bash_aliases files.
>
> ~~~
> alias compile='arduino-cli -b=arduino:avr:uno compile'
> alias upload='arduino-cli -b arduino:avr:uno -p /dev/ttyACM0 upload'
> ~~~
> {: .source}
{: .callout}

While uploading, you should see the LEDs on the Arduino blink rapidly for a moment and then one LED will begin to blink regularly.

> ## Questions
> How long is the LED on? How long is it off. What are the units?
{: .Discussion}

By changing the delays, you can vary how long the LED is on or off.

> ## Try This
>
> Try programming a pattern, like S-O-S in Morse code (". . . — — — . . ."). Consider using a "for" loop to simplify coding.
{: .challenge}

{% include links.md %}
