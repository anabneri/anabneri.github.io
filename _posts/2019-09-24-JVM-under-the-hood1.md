---
title: JVM Under The Hoods part1 - What is Java?
tags: [Java, JVM, Advanced]
style: border
color: dark
description: If you want to read that same article in English.
---

* **Well Welcomeeee to the series of articles on Java Virtual Machine!** *

# JVM under the hood - What is Java?
> the goal here is to show it  on the most objective and accessible way for better understanding

## The compiling processes

* It all starts with the history of high-level language computers where the same only understood _micro _instructions
* Know the code you write? Your computer doesn't understand it, it never understood... Yes they're pretty dumb!
* In fact your computer understands the **Executable code**
* Let's take as an example an "old " language, like **Assembly**, see the architecture:

* Basically has a  "Hello World ", which goes through a type of compiler that converts the code into binary 

![](https://i.imgur.com/Ax8hq9a.png)

* **But this is too complex, think well... An operating system will read only what was compiled in it, if you run that same code in a MACOX for example would have to do everything again!!**
* Needed optimization of processes and time 

## Compiling process in C

* Enough people have prejudice with C right, but did you know that Java was based on C?
* Why was the C language revolutionary for the time it became a multiplatform or **has a compiler for each operating system (OS)**
* The process of compiling in C is quite simple, see in Architecture:

![Compiler in C](https://i.imgur.com/mfA4Bhp.png)

* We see that the **Source code** that I program in C it is taken to two processes that will separately transform a **Executable code** For each operating system:D

* It was from this multi-platform idea that the concept of the Java JVM was born...
> Before we leave for history, what we've learned so far:
> **Source code:** is the sequence of commands that I, programming person write.
> **Executable code:** is the sequence of commands that the computer understands.
> * C language is cross-platform.**
> **Java was based on C**

## A brief story about Java

* 1990: Sun Microsystems created a project led by James Gosling based on C++ in order to create a technology where different devices could communicate with each other.
Until then there were no microprocessors so imagine how revolutionary this project would be!
* And so formed the Green Team that created their own language the Green Talk** 
* The language was renamed to OAK**
* And so created the [Star Seven](https://jaxenter.com/java-this-is-your-life-so-far-104122.html)
* 1992: The Star Seven project ended up getting hitted because there was no investment from the companies, *I believe that for being very revolutionary*
* The main core of star Seven was interactivity, so guess who was interested in the language that was programmed the star seven?
* **Tim Berners-Lee**, himself, at the time he was developing the HTML, which had as main function the interactivity with the user in real time (which did not exist yet)
* That's how we joined the Gem and the Clear (bad joke: woman_facepalming:)
* Thus came the **WebRunner** that allowed INTERACTIVITY
* So now it was just changing the name of the language because Oak already existed in the market, it was when Gosling gathered his group and renamed it to JAVA, because it is a term that Americans have when they want very strong coffee,  **Java Coffee**, since we programmers only work the B Coffee, nothing fairer
_*This story of the emergence of the name has other versions, we will never know for sure I think, who knows someday I have the opportunity to talk to someone who was from Sun Microsystems*

> * Okay, let's look at the beautiful story of Java, right?
> * Now we just need to understand why the JVM...

## Compiling code with the JVM

* Observe the architecture below:
![Java compiler](https://i.imgur.com/iLDx4zS.png)

* The code after done goes through the Java Compiler or JavaC ---> After that within the JavaC your source code is converted to Bytecode ---> The JVM reads this Bytecode and converts it to executable code.

* The JVM's balcony is the **BYTECODE**, the JVM language, thus enabling a multiversion for any operating system

* And the coolest of all this is that when you download your Java on your machine The JVM already comes along, do not need to go looking (comes the JVM and more a lot of other features, worth remembering).

> This write concept where Run Anywhere makes it possible for several other languages to roll in the JVM, especially the "hipsters" languages

![Languages that run on the JVM](https://i.imgur.com/UMoSciF.png)

###### And here we finish the first introductory part on JVM! I hope it was of great value, I promise to post part 2 soon


<p class="text-center">
{% include elements/button.html link="https://dev.to/anabneri_8" text="If you want to read that same article in Portuguese" %}
</p>