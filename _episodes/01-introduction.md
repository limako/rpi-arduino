---
title: "Introduction"
teaching: 15
exercises: 10
questions:
- "What is the Arduino platform?"
- "Why do we use the Arduino platform?"
objectives:
- "Understand what Arduinos can do."
- "Understand when Arduinos are a good choice."
keypoints:
- "Arduinos are very simple devices for physical computing."
- "Arduinos are at the center of a universe of resources for making projects."

---
The Arduino is a hardware platform that has an open specification that has been widely deployed for prototyping embedded computing and interfacing with sensors and devices. As with a model system in biology, the main advantage of using it is the vast library of existing resources you can draw from for building your project.

There are many many versions of Arduino devices that have been developed for particular applications, but this guide will assume you're using an Arduino Uno, which is a basic device that works well for prototyping.

<a href="{{ page.root }}/fig/arduino_med.jpg">
  <img src="{{ page.root }}/fig/arduino_full.jpg" alt="Formatting Rules" />
</a>

A program for an Arduino is called a "sketch" and is written in a subset of the C++ programming language.

Arduinos only do two things. When they start, they run a function called "setup" that is executed only once. Then they run a function called "loop" which runs over and over again forever. That's it.

Along the sides of an Arduino are sockets that can be used to connect with little wires, or "jumpers", to a breadboard. (Or directly to a component).

> ## Important:
>
> Although Arduinos are generally forgiving, it's possible to damage the electronics by shorting connections among pins. Use guidance when making connections and double check everything before plugging things in.
{: .callout}

You should connect your Arduino to your Raspberry Pi and notice that an LED is lit to show that it is powered. The rest of this guide will assume you have an Arduino attached to a Raspberry Pi via USB.

<a href="{{ page.root }}/fig/pi_and_arduino_med.jpg">
  <img src="{{ page.root }}/fig/pi_and_arduino_full.jpg" alt="Formatting Rules" />
</a>

{% include links.md %}
