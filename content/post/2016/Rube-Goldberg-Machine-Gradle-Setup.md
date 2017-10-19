---
title: Rube Goldberg Machine - Gradle Setup
author: Sahil Ahuja
categories: [blog]
date: 2016-12-06 02:44:45
tags: [gradle, spock, java, testing, algorithms]
featured: "Rube_Goldberg_Self_Operating_Napkin.gif"
featuredalt: "Rube Goldberg Self Operating Napkin"
featuredpath: "date"
---

A [Rube Goldberg machine](https://en.wikipedia.org/wiki/Rube_Goldberg_machine) is a contraption, invention, device, or apparatus that is deliberately over-engineered to perform a simple task in a complicated fashion, generally including a chain reaction.
<!--more-->
![Self Operating Napkin](/images/2016/Rube_Goldberg_Self_Operating_Napkin.gif)

My Convolution:
===============
To learn algorithms, I started a Coursera course, to run examples of which I needed a Java Project setup locally, in which I needed to input stuff, for which I needed a testing framework, hence I tried to find the best testing framework, and found out about [Spock](https://en.wikipedia.org/wiki/Spock_%28testing_framework%29) and also needed a project dependency manager like Maven/Ant/Gradle, and chose [Gradle](https://en.wikipedia.org/wiki/Gradle) as the dependency manager of choice, and learnt [Groovy](https://en.wikipedia.org/wiki/Groovy_%28programming_language%29) to be able to write Gradle [DSL](https://en.wikipedia.org/wiki/Domain-specific_language).

For a moment I thought Rube Goldberg was sitting next to me. All I wanted was to learn Algorithms.

Gradle
------
To setup Gradle Wrapper: `gradle wrapper` ([Gradle Guide](https://docs.gradle.org/current/userguide/userguide.html))

Now the executable gradlew or gradlew.bat in the current folder will install Gradle if not installed and then delegate to gradle all arguments passed originally to the gradlew command.

Gradle syntax: `gradle[w] taskName[s]`

For help/options simply type: `gradle[w]`
