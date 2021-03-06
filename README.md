# Bootstrapping Trust with Buttons

![demo1](Pictures/demoPicture.jpg)

This code was written over summer 2019 as part of a research experience for undergrads (REU) project at Florida International University. The goal of this project was to create a secure button based pairing procedure for two IoT devices. This resulted in the following two files that can be run from two Arduino devices equipped with buttons.

### Getting Started 

This program is written in arduino code for Arduino Uno boards with led lights and buttons wired to it. To run this code download the arduino IDE, plug in each boards to its own computer, and run the code from inside the IDE. Run the D1 code on one board and the D2 code on the other. 

### Explanation 

Once the code is running, start the pairing process by pressing both buttons once at the same time. This will causes a 20 second timer to beign where the user must press both buttons at the same time until the timer ends. They can press the buttons a max of 20 times for a max duration of five seconds per press. Each duration is rounded down to the closest 500 ms interval, then all of these presses are counted to get the frequency of times they appear. Each device's random Nonce is then appended to the end of this vector and the whole thing is turned into a hash. From there D1 sends its hash one byte at a time, D2 does the same. Then D1 and D2 trade nonces. Then D2 appends D1's nonce to its own vector to calculate h3 which must match the hash sent from D1. D2 does the same thing. If both devices match then pairing is complete otherwise it fails. 

Example 
Original button press durations (1285, 2256, 1560, 2015, 3265, 595)
Rounded durations (1000, 2000, 1500, 2000, 3000, 500 )
Frequency of durations going from 500 to 5000 in 500 ms intervals (1, 1, 1, 2, 0, 1, 0, 0, 0, 0 )

### Built With 

* Arduino IDE - IDE
* Arduino Uno - Hardware

### Authors 

* Sanjeev Ramani - sanjeevr93
* Kyle Dennison - KyleDennison
* Juan Buena - jabuena
