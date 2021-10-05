---
title: "Using Arduino Libraries"
teaching: 20
exercises: 10
questions:
- "How can Arduino programming be extended?"
objectives:
- "Don't re-invent the wheel."
keypoints:
- "Libraries can provide additional functionality, especially for hardware, but also for functionality."
---

The Arduino programming language provides a lot of basic, low-level functionality, but there are many libraries that can provide higher-level functions that can simplify interacting with specialized hardware or information.

It's feasible to search for libraries using arduino-cli directly

~~~
$ arduino-cli lib search [keyword]
~~~
{: .language-bash}

But you can also [browse the libraries](https://www.arduinolibraries.info/) to more readily see what's available.

When you've identified a library you want to use, you can install it from the command line:

~~~
$ arduino-cli lib install [name_of_library]
~~~
{: .language-bash}

When programming, you reference a library you want to use with an "#include" statement in your code, and then use the defined elements it provides. In this example, we're using the TimedBlink library, which keeps track of when a pin should be turned on and off.

~~~
// include the library
#include <TimedBlink.h>
int led=6;

TimedBlink monitor(led);

void setup() {
  pinMode(led, OUTPUT);
  // Configure the function with times to stay on and off
  monitor.blink(500,500);
}

void loop() {
  // call frequently to blink at scheduled times.
  monitor.blink();
}
~~~
{: .source}

If you try to compile without installing the library, compilation will fail. Install the library and compile again.

> ## Question
> Why might this function be useful? How you imagine the function is operationalized? Are there any limitations to this approach?
{: .discussion}

Finally, under some circumstances, you might want to [create a library of your own](https://www.arduino.cc/en/Hacking/LibraryTutorial).

{% include links.md %}
