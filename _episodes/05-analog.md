---
title: "Using Analog Pins"
teaching: 0
exercises: 0
questions:
- "Key question (FIXME)"
objectives:
- "First learning objective. (FIXME)"
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---

The Arduino Uno includes 6 pins that can accept "analog" input. These pins can measure the resistance between the pin and ground, perform an "analog to digital" conversion, and will output an integer value between 0 and 1023. Many sensors work using this principal but we can start by using a potentiometer.

A potentiometer is a device that changes resistance depending on how it's adjusted. It has three pins. The middle pin should be connected to the analog

The analog pins are designated with a letter A (A0-A5) and are found on the opposite side of the Arduino from the digital pins. Connect A5 to the middle pin of the potentiometer.

Connect one side of the potentiometer to ground and the other side to 3.3V. (Note: it's not a bad idea to do this two jumpers: one to the red conductor running the length of the breadboard and another between the red conductor and the side of the potentiometer).

This sketch is just the blink-two sketch from before, with a variable standing in for the LED pin and another variable (pot) defined to receive the value from the analog pin.

~~~
int led = 13;
void setup() {
 pinMode(led, OUTPUT);
}

void loop() {
  int pot;
  digitalWrite(led, HIGH);
  pot = analogRead(A5);
  delay(pot);
  digitalWrite(led, LOW);
  delay(pot);
}
~~~
{: .language-arduino}

Why is one variable (led) defined above the setup function and another (pot) defined inside the loop function?

What do you think will happen if you reverse which side is ground and which side is power? Make a prediction and try it out.

{% include links.md %}
