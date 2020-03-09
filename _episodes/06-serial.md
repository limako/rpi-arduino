---
title: "Using Serial Connections"
teaching: 30
exercises: 10
questions:
- "How can Arduino programs use the serial interace?"
objectives:
- "Receive data from the Arduino."
- "Send data to the Arduino."
keypoints:
- "A serial connection is birectional."
- "Serial connections exchange individual bytes."
- "Higher-level functions can help parse serial input."
---

The Arduino uses a serial connection to receive the uploaded programs from the Raspberry Pi. But it can also exchange data via the serial connection while programs are running. The basic serial functions are [well documented](https://www.arduino.cc/reference/en/language/functions/communication/serial/).

The serial connection is bi-directional, so you can both receive data from the Arduino and send information to it.  By adding just a couple of lines, we can see what the potentiometer is actually set to.

~~~
int led = 13;
void setup() {
 pinMode(led, OUTPUT);
 // This turns on the serial connection
 Serial.begin(9600);
}

void loop() {
  int pot;
  digitalWrite(led, HIGH);
  pot = analogRead(A5);
  // this prints a line with the potentiometer reading
  Serial.println(pot);
  delay(pot);
  digitalWrite(led, LOW);
  delay(pot);
}
~~~
{: .language-arduino}

To see the readings on the Pi, we can use the "screen" command which can communicate via the serial ports.

~~~
$ screen /dev/ttyACM0 9600
~~~
{: .language-bash}

You should see a series of values received. As long as "screen" has the serial port open, arduino-cli won't be able to upload, so once you're done looking at the connection, you need to shut down screen.

> ## Discussion Questions
> How variable are the readings? What is the full range of the potentiometer?
{: .discussion}

Everything you type, gets sent to the Arduino, with one exception: when you type <kbd>Ctrl</kbd>+<kbd>A</kbd> (while pressing the control key, type "a"), screen will listen for you to type a command. A backslash (<kbd>\</kbd>) will get screen to ask you if you want to" "Really quit and kill all your windows [y/n]". Press <kbd>Y</kbd> to close the connection.

A useful way to send data is as "comma separated values". An easy way to format the output is to use the "Serial.print" command to output individual elements on the line (values or commas) and then use "Serial.println" for the last element, which will send the line ending.

~~~
int led = 13;
void setup() {
 pinMode(led, OUTPUT);
 // This turns on the serial connection
 Serial.begin(9600);
}

void loop() {
  int pot;
  digitalWrite(led, HIGH);
  pot = analogRead(A5);
  // The Serial.print command doesn't issue a new line
  Serial.print(pot);
  delay(pot);
  // so we can print a comma
  Serial.print(",");
  // then make a new reading
  pot = analogRead(A5);
  // And print another value with a newline
  Serial.println(pot);
  digitalWrite(led, LOW);
  delay(pot);
}
~~~
{: .language-arduino}

You should now see pairs of values. If you rotate the potentiometer between readings, you should see the two values change independently.

~~~
int led = 13;
void setup() {
 pinMode(led, OUTPUT);
 // This turns on the serial connection
 Serial.begin(9600);
}

void loop() {
  int pot;
  digitalWrite(led, HIGH);
  pot = analogRead(A5);
  // The Serial.print command doesn't issue a new line
  Serial.print(pot);
  delay(pot);
  // so we can print a comma
  Serial.print(",");
  // then make a new reading
  pot = analogRead(A5);
  // And print another value with a newline
  Serial.println(pot);
  digitalWrite(led, LOW);
  delay(pot);
}
~~~
{: .language-arduino}

The Arduino Serial library can read data submitted byte-by-byte, one character at a time, but it also includes functions that watch for integers or floating-point values. We can use one to control how many times to blink.

~~~
int led = 13;
void setup() {
 pinMode(led, OUTPUT);
 Serial.begin(9600);
}

void loop() {
  int times = 0;
  // This waits until it receives an integer via the serial connection
  times = Serial.parseInt();
  // this loops the number of times entered.
  for (int i=0;i < times; i++) {  
    int pot = analogRead(A5);
    digitalWrite(led, HIGH);
    Serial.print(pot);
    delay(pot);
    Serial.print(",");
    pot = analogRead(A5);
    Serial.println(pot);
    digitalWrite(led, LOW);
    delay(pot);
  }
}
~~~
{: .language-arduino}

> ## Try this:
>
> Can you add code to output an message telling the user to input the number of times to loop?
{: .challenge}

{% include links.md %}
