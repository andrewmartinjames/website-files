---
title: "IoT Frost Alarm"
date: 2021-07-28T14:13:33-08:00
featured: true
description: "Designed open source frost warning system for gardeners using ESP32 microcontroller, Google Cloud (IoT Core, Pub/Sub, Cloud Functions, and Firebase), and an iOS app written in Swift(UI) using Firebase."
tags: ["Swift","Google Cloud","Firebase","C++","ESP32"]
image: "/img/frostalertimg.png"
link: "https://github.com/andrewmartinjames/FrostAlert"
fact: "Interesting little tidbit shown below image on summary and detail page"
weight: 500
sitemap:
  priority : 0.8
---
A system designed to use internet of things (IoT) technology to enable a small weather station in the home garden to report current climate data and predict frosts, alerting the gardener in time for them to cover their plants.

The system consists of an IoT endpoint, powered by a microcontroller in a watertight housing connected to a weatherproof temperature and humidity sensor, as well as cloud services configured to collect and analyze weather data, and finally an iOS app for gardeners to monitor the conditions in their gardens and receive push notifications about incoming frosts.

To make the system accessible to home gardeners, the design was required to:
- Cost under $200 to construct
- Measure temperature to within half a degree centigrade
- Operate at temperatures down to -20ºC
- Support both ethernet and WiFi connections
- Notify the gardener when a frost is predicted based on the local dew point dropping below freezing
- Allow the gardener to configure a temperature threshold below which they will always be notified, whether or not the dew point indicates an incoming frost.

The final project utilized:
- An **ESP32** microcontroller, coded in **C++**, for the endpoint
- An Adafruit ethernet shield for ethernet functionality
- An SHT31 temperature and humidity sensor
- **Google Cloud** services for the cloud data pipeline
  - **IoT Core** receives data from the endpoint via **MQTT**
  - **Pub/Sub** receives data from IoT Core and verifies schema
  - **Cloud Functions** triggered by Pub/Sub analyze current climate data, update a Firestore database, and trigger push notifications
- **Firebase** as a serverless backend for the iOS app
  - **Cloud Firestore** stores user and endpoint data in a **NoSQL** database
  - **Cloud Messaging** sends push notifications to user's phone
  - **Firebase Auth** for user authentication with the iOS app
- **Swift** for the iOS app
  - **SwiftUI** for GUI
  - **CocoaPods** for dependency management



All design goals were met by the final design except for the low yearly operating cost. This was due to the unexpected requirement of having an Apple Developer account, which costs $99 per year, in order to send push notifications to iOS apps. Due to this unexpectedly high cost, several alternative notification solutions, including an Android app and a secondary physical endpoint with alarm functionality, are proposed at the end of this report, as well as suggestions for potential commercialization.

[**Full design report available here.**](https://drive.google.com/file/d/12IK5U414rHYsYwYDRu3WBsZ4R0oDhcVx/view?usp=sharing)



{{< youtube id="U2NSSIr_3mA" title="Presentation for senior project" >}}
