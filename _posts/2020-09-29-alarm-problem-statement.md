---
title: House Alarm System with RaspberryPi
---

### Problem Statement
Most of today's real estate properties comes with local alarm system. This means they are equipped at least with
motion, door and window sensors. In the house, there is a main board that powers the sensors,
and receive notifications from them, during detection of motion or doors are open.
Control panel is connected to the main board, through which alarm can be activated or
deactivated by users.
Main output of the alarm panel is buzzer. If alarm is active, and went off,
high volume sound will come from the buzzer to alert on a possible intruder.

This is all fine and nice, but it works only in local. Household members doesn't get notification on the alarm.
If you are not nearby your house or apartment, you are most likely to miss the alarm,
and most likely the intruder will get away without being caught.

In order to get notified when alarm goes on, you have to make a deal with a security company
and pay monthly fees. Monthly fees for this service varies from provider to provider,
and none of them is cheap. Also, security providers will have access to data from the sensors,
hence data will be exposed to the external world, and subject for attackers.

To summarize, main problems that I want to solve here are:
* Avoid expensive security service, and
* Avoid possibility of data exposure

### Objective
Given the problem statement form above, within these articles, I will try to explain
how I managed to set-up home alarm system with RaspberryPi within the local network,
and avoid expensive deals with the security system providers. Since solution will be in the local network,
there will be no data exposure to the outside world.

### Prerequisites
In order to follow the articles you should have some basic understanding of:

* **RaspberryPi**
![https://www.raspberrypi.org/](<../images/rpi.webp>)
The Raspberry Pi is a low cost, **credit-card sized computer**. It is a capable little device that
enables people of all ages to explore computing,
and to learn how to program in languages like Scratch and Python.

  In these articles I will use RaspberryPi as computer for running services for:
  * Scanning sensor status, and
  * Managing and providing visibility into alarm state

* **Alarm Sensors**

  Have a sense how basic alarm sensors works. Most common alarm sensors are a magnetic door and window sensors,
  motion sensors and IP cameras.

* **Programming Skills**
  * **Android**

    One part of my solution is Android application through which users can arm and disarm alarm system.
    Application is fairy simple. It contains login page, buttons for arming and disarming the alarm system and
    panel for sensors status preview. Communication with web service (that is running on RaspberryPi)
    is happening via basic HTTPS protocol. I'm using [Firebase](https://firebase.google.com/docs/cloud-messaging)
    for push notifications when sensors or alarm state changes.
  * **Python**

    I choose Python as programming language to develop services on RaspberryPi. For scanning sensor statuses
    I'm using RaspberryPi GPIO packages. For Web service development I choose
    [flask framework](https://palletsprojects.com/p/flask/). Web service app is keeping track of alarm system state
    and status in [SQLite](https://www.sqlite.org/index.html) database.
  * **Shell Script**

    In order to automate process of deployment and startup of applications, basic knowledge of shell scripting
    is an advantage as well.
* **Basic Electronics**

  Since we are going to deal with wiring (or re-wiring) of sensors and control boards, you also need to be handy
  with electronic devices such as multimeter, jumper wires, insulating tape, soldering iron, etc.
