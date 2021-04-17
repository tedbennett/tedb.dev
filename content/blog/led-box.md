---
title: "Led Box"
date: 2020-11-16T23:23:44Z
description: Powering an 8x8 LED matrix with a Raspberry Pi
draft: true
---

I've started work on a new project working with [this](https://www.amazon.co.uk/AZDelivery-MAX7219-Matrix-Display-Arduino/dp/B078HYP681/ref=sr_1_4?dchild=1&keywords=led+matrix+8x8&qid=1605569203&quartzVehicle=183-643&replacementKeywords=led+8x8&sr=8-4) 8x8 RGB LED Matrix with a Raspberry Pi. I did some work earlier in getting this working ([here](https://github.com/tedbennett/pi-led-matrix)), including:
  - a simple front-end consisting of a grid and colour picker to allow the user to draw a pattern
  - Firebase backend to receive the pattern from the user and message the Pi
  - Python script running on the Pi to draw the pattern

I'd like to redo this a bit, as this wasn't a very flexible system and wouldn't scale well.

### New Backend

I'm developing a Python Flask backend hosted on Heroku. It'll use websockets to communicate with both the client and the Raspberry Pi. I'd like to save some of the previously used patterns for each user, so that they can scroll through old designs and re-send them. I'll probably use a Postgres database for this; I have very little experience with Postgres but it seems like a common choice with Heroku, and since the amount of data will be so small I don't think the choice here matters.

### New Frontend

I was happy with the front end, it was based on Coding Garden's similar app. I had a couple of bugs with touch devices, but I'd otherwise only like to implement the past designs mentioned before, as well as a dropdown to select which Pi to message. It would be nice if the client would also let the user know if the other person had sent a pattern through.

I'd also like to create an iOS app for this. It'd be very simple but I've never used websockets on iOS which will be interesting. I'd also like to add Notifications when a pattern is received.

### Work for the Pi

I'm quite happy with the script I made for the Pi. It needs to be configured to start on boot, and I'd like to add some visual indicators if it connects to the server successfully or hits some errors. Otherwise I just need to migrate this over from Firebase.
