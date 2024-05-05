# EFPSE Finite State Machine tutorial {#efpse-finite-state-machine-tutorial}

This is the first tutorial of the EFPSE Finite State Machine.

## Intro {#intro}

### Who is this document for? {#who-is-this-document-for}

Users of EFPSE that are Somewhat familiar with the software. IE: You should know how to navigate efpse, Add textures, Create new maps and do simple tasks.

### What are the assumptions? {#what-are-the-assumptions}

I assume you know what a computer is and that's pretty much it.

### who is the author? {#who-is-the-author}

me

### Structure of document {#structure-of-document}

First half lecture blah blah

Second half implementation and application of blah blah

## First half (lecture blah blah) {#first-half-lecture-blah-blah}

### What is a finite state machine? {#what-is-a-finite-state-machine}

> A state machine \[🤖\] reads a set of \[⏰:🕓\] inputs and changes to a different state\[🚦:🟥,🟨,🟩\] based on those inputs.

~[and an even more technical definition Is available here](https://developer.mozilla.org/en-US/docs/Glossary/State_machine)🤓~

Ok, but what does that quote really mean?

If you've never heard of a finite state machine before you may picture some kind of robot that's... finite? Let's try to see if we can fill in some more details of this finite fuzzy robo we're photoing in our mind. In fact they don't even need to be a robot at all!

Really all we need is a pencil and paper but since this is a computer I'll make a little diagram.

![](simplefm.svg)

So we draw two circles that represent two different `states` and we draw an arrow between them to represent the `input` . The text over the arrow that reads `Go to STATE B`, that's our `input` or our `action`. If we give that `input` or `action` to our machine, then our state machine will transition into `STATE B`.

### Huh? Break it down for me {#huh-break-it-down-for-me}

It can be kind of hard to see what's going on in a diagram like this so let's break it down into three steps.

####  ![](simplefsm0.svg)

![](simplefsm1.svg)

![](simplefsm2.svg)

Let's look at some examples!

### Everyday examples {#everyday-examples}

-   Light switches (☀️:🔛,🌑,📴)
-   Traffic lights (🚦:🟥,🟨,🟩)
-   Brushing teeth (🤔)

### A closer look (👀)

#### At light switches: {#at-light-switches}

#### At traffic lights: {#at-traffic-lights}

![https://medium.com/well-red/state-machines-for-everyone-part-1-introduction-b7ac9aaf482e](traffic.png){fig-alt="Traffic light diagram explaining how as the timer expires the traffic light transitions from green to amber to red and emback the green" fig-align="left"}

[Traffic light state machine simulation using stately](https://stately.ai/registry/editor/f7a50bc1-d70b-4133-823c-4f7370e0ea70?mode=Design&machineId=8757d2cb-9c54-48be-a3f9-651bcd921054)

## Second half (implementation and application of blah blah) {#second-half-implementation-and-application-of-blah-blah}

-   [EFPSE Finite State Machine tutorial {#efpse-finite-state-machine-tutorial}](#efpse-finite-state-machine-tutorial-efpse-finite-state-machine-tutorial)
    -   [Intro {#intro}](#intro-intro)
        -   [Who is this document for? {#who-is-this-document-for}](#who-is-this-document-for-who-is-this-document-for)
        -   [What are the assumptions? {#what-are-the-assumptions}](#what-are-the-assumptions-what-are-the-assumptions)
        -   [who is the author? {#who-is-the-author}](#who-is-the-author-who-is-the-author)
        -   [Structure of document {#structure-of-document}](#structure-of-document-structure-of-document)
    -   [First half (lecture blah blah) {#first-half-lecture-blah-blah}](#first-half-lecture-blah-blah-first-half-lecture-blah-blah)
        -   [What is a finite state machine? {#what-is-a-finite-state-machine}](#what-is-a-finite-state-machine-what-is-a-finite-state-machine)
        -   [Huh? Break it down for me](#huh-break-it-down-for-me)
        -   [Everyday examples {#everyday-examples}](#everyday-examples-everyday-examples)
        -   [A closer look (👀)](#a-closer-look-)
            -   [At light switches: {#at-light-switches}](#at-light-switches-at-light-switches)
            -   [At traffic lights: {#at-traffic-lights}](#at-traffic-lights-at-traffic-lights)
    -   [Second half (implementation and application of blah blah) {#second-half-implementation-and-application-of-blah-blah}](#second-half-implementation-and-application-of-blah-blah-second-half-implementation-and-application-of-blah-blah)