# EFPSE <img src="EFPSE_icon.png" width="28px" alt="EFPSE logo" style="margin-bottom:-1px"> Finite State Machine tutorial

Welcome to the first tutorial of the EFPSE <img src="EFPSE_icon.png" width="28px" alt="EFPSE logo" style="margin-bottom:-8px"> finite state machine. Real quick: This document is for users of EFPSE <img src="EFPSE_icon.png" width="28px" alt="EFPSE logo" style="margin-bottom:-8px"> who can Easily do basic engine tasks and want to see what state machines are about. The first half is theory skip this if you know what a state machine is, and then start at How do you create a state machine in EFPSE <img src="EFPSE_icon.png" width="28px" alt="EFPSE logo" style="margin-bottom:-8px">.

Otherwise keep reading and enjoy the rest of the tutorial.:)
## Intro

### Who is this document for?

Users of EFPSE <img src="EFPSE_icon.png" width="28px" alt="EFPSE logo" style="margin-bottom:-8px"> that are Somewhat familiar with the software. IE: You should know how to navigate EFPSE <img src="EFPSE_icon.png" width="28px" alt="EFPSE logo" style="margin-bottom:-8px">, Add textures, Create new maps and do simple tasks.

### What are the assumptions?

I assume you know what a computer is and that's pretty much it.

### In what way will this material be Presented?
> "Wisdom comes from understanding simple things deeply" - Twain maybe

I have no pedagogic background except pretending to tutor in college. 

My aim is to give you the smallest working model of `Finite State Machines` (Theory and implementation) so that you can understand all the moving pieces of EFPSE <img src="EFPSE_icon.png" width="28px" alt="EFPSE logo" style="margin-bottom:-8px">'s state machines.


### who is the author?

me

### Structure of document

#### First half lecture blah blah
This section has some bare bones theory for those who've never even heard of a state machine. It then ends with an explanation of how to create a state machine in EFPSE <img src="EFPSE_icon.png" width="28px" alt="EFPSE logo" style="margin-bottom:-8px">. 

There are some bonus assignment that can be completed in 1ish minutes just to double check and see if you understand. No tricks, nothing that's not from the material.

#### Second half implementation and application of blah blah

## First half (lecture blah blah)

### What is a finite state machine?
Let's first start by answering this question

> A state machine [🤖] reads a set of [⏰:🕓] inputs and changes to a different state[🚦:🟥,🟨,🟩] based on those inputs.

~[and an even more technical definition Is available here](https://developer.mozilla.org/en-US/docs/Glossary/State_machine)🤓~

Ok, but what does that quote really mean?

If you've never heard of a finite state machine before you may picture some kind of robot that's... finite? Let's try to see if we can fill in some more details of this finite fuzzy robo we're photoing in our mind. In fact they don't even need to be a robot at all!

Really all we need is a pencil and paper but since this is a computer I'll make a little diagram.

![](simplefm.svg)

So we draw two circles that represent two different `states` and we draw an arrow between them to represent the `input` . The text over the arrow that reads `Go to STATE B`, that's our `input` or our `action`. If we give that `input` or `action` to our machine, then our state machine will transition into `STATE B`.

### Huh? Break it down for me

It can be kind of hard to see what's going on in a diagram like this so let's break it down into three steps.

In the very zeroth step we have our machine represented by this little box in `STATE A`

#### ![](simplefsm0.svg)

Now we give our machine the signal to go to `STATE B`

![](simplefsm1.svg)

And upon receiving this signal the machine will change the `STATE B` and that's where it will stay

![](simplefsm2.svg)

OK admittedly that was kind of abstract, so let's look at some real world examples that we've already interacted with.

### Everyday examples

That's right, you've interacted with state machines plenty of time and probably even multiple times today!

-   Light switches (🔛:💡,📴:⬛)
-   Traffic lights (🚦:🟥,🟨,🟩)
-   Brushing teeth (🤔)

### A closer look (👀)

#### At light switches:




![](lightswitchfsm.svg){width="350"}

A light switch is a perfect example of a state machine. Two states off and on. The signal is the light switch. Only send the on signal when the switch is off and you can only send the off signal when the switch is on. This simple state machine has two states and has two actions. Nothing unknown can happen you could say it's very...finite.
<video width="426" height="240" controls>
  <source src="lightswitch.mp4" type="video/mp4">
</video>
Video by Kapaw from Pexels 

<a href="https://www.pexels.com/video/a-big-lightbulb-turning-on-4735258/">Link to video source</a>


#### At traffic lights:

![https://medium.com/well-red/state-machines-for-everyone-part-1-introduction-b7ac9aaf482e](traffic.png){fig-alt="Traffic light diagram explaining how as the timer expires the traffic light transitions from green to amber to red and emback the green" fig-align="left"}

Traffic lights are another perfect example of state machines that we interact with every day. Instead of two states like the light switch there's three. And instead of a switch you use with your finger, The traffic lights Use timers pressure sensors and other signals to determine when to switch to the next state.

##### Traffic lights simulation (🚦:🟥,🟨,🟩)
Let's take a look at a simulation below(Because I made it 🤓). If you click on <span style="background-color:#2E2F3C !important;color:white;padding:12px;padding-left:10px;padding-right:16px; border-radius: 3px;">▶️  Simulate</span>
**in the bottom right of the embedded window**, You will enter into simulation mode. From here you can click on <span style="background-color:#2949A5 !important;color:white;padding:6px;padding-left:10px;padding-right:10px; border-radius: 14px;">20s</span> to simulate 20 seconds going off and moving to the next state: <span style="background-color:#4D4F5F !important;color:white;padding:6px;padding-left:10px;padding-right:10px; border-radius: 3px;">RED</span>, <span style="background-color:#4D4F5F !important;color:white;padding:6px;padding-left:10px;padding-right:10px; border-radius: 3px;">GREEN</span>, or <span style="background-color:#4D4F5F !important;color:white;padding:6px;padding-left:10px;padding-right:10px; border-radius: 3px;">YELLOW</span>
.
<iframe src="https://stately.ai/registry/editor/embed/f7a50bc1-d70b-4133-823c-4f7370e0ea70?machineId=8757d2cb-9c54-48be-a3f9-651bcd921054" width="90%" height="400px" frameborder="0">
https://stately.ai/registry/editor/&mode=design
</iframe>

<span style="color:grey">NOTE: The embedded window behaves kind of funny with the scroll wheel so if you end up losing the traffic light state machine you can use the middle click to drag the content back into center. Sorry.😅</span>



#### Brushing Teeth <span style="color:grey">... (🤔)?</span>

![](brushteethfsm.svg){width="500"}

Yes even brushing your teeth can be conceptualized as a state machine!

Why anyone would do that <span style="color:grey">(For the tutorial! 🤓)</span> is any other one's guess but the point is that **_Finite state machines_ don't have to just be _mechanical_ or _electronic_ things**. **As long as you have a set of** <span style="background-color:#4D4F5F !important;color:white;padding:6px;padding-left:10px;padding-right:10px; border-radius: 3px;">STATES</span> **and a set of** <span style="background-color:#2949A5 !important;color:white;padding:6px;padding-left:10px;padding-right:10px; border-radius: 14px;">inputs</span>**(signals) that are known, _you can conceptualize these states and inputs as a state machine_.**

That's the intrinsic power of the state machine. You can boil down sophisticated decision making Processes or Respond to specific events in consistent reliable ways using logic.

So as you continue with this tutorial <span style="color:grey">(And after 🙏)</span> try to think about everyday objects That could be broken down into a series of <span style="background-color:#4D4F5F !important;color:white;padding:6px;padding-left:10px;padding-right:10px; border-radius: 3px;">STATES</span> and <span style="background-color:#2949A5 !important;color:white;padding:6px;padding-left:10px;padding-right:10px; border-radius: 14px;">inputs</span>.(Radios, TV's, washing machines...)

### Summary of part one <span style="color:grey">(condensed blah blah )</span>
In summary state machines are conceptual tools used to model Systems. These systems are comprised of known states and known actions Actions and inputs. The systems can only ever be in the predefined states it can only ever take predefined actions and respond to predefined signals.

That is a lot of boring text thanks for bearing with all the prerequisite stuff now we can start using what we know to make state machines inside EFPSE <img src="EFPSE_icon.png" width="28px" alt="EFPSE logo" style="margin-bottom:-8px">!

<details class="bonus-assignment">
  <summary><span style="color:grey">Bonus assignment</span></summary>
  
  <p>On a piece of paper draw out your own state machine!</p>
  <p>Try to think about something you've interacted with recently that you could break down into a state machine. (States and inputs)</p>
  <p>I made a bunch already but here's one last one</p>
  <img src="wolf.png">
  <img src="dummy.png">
  <details class="bonus-assignment">
    <summary><span style="color:grey">answer</span></summary>
    <p>This is the answer</p>
    </details>
</details>


### How do you create a state machine (In EFPSE 1.10.4)?
<div style="max-width: 250px; padding: 10px; background-color: #DCF8C6; border-radius: 15px; position: relative; margin: 20px;">
    <img src="wolf.png" alt="Avatar" style="width: 32px; height: 32px; border-radius: 50%; position: absolute; top: 50%; left: -42px; transform: translate(-50%, -50%);">
    <div style="display: flex; align-items: center; margin-left: 22px;">
        <span style="font-size: 14px;">OK finally we're here! Let's make a state machine in EFPSE <img src="EFPSE_icon.png" width="28px" alt="EFPSE logo" style="margin-bottom:-8px">!
        <br>...<br>...<br>
        But how do we do that?  </span>
    </div>
    <div style="position: absolute; top: 50%; left: -15px; border-style: solid; border-width: 8px 15px 8px 0; border-color: transparent #DCF8C6 transparent transparent; content: '';"></div>
</div>

<div style="max-width: 250px; padding: 10px; background-color: #DCF8C6; border-radius: 15px; position: relative; margin: 20px;">
    <div style="display: flex; align-items: center;">
        <span style="font-size: 14px;">Thankfully the <a href="https://pixelwolf.net/efpse/wiki/index.php?title=Main_Page">wiki</a>  has an example of a <a href="https://pixelwolf.net/efpse/wiki/index.php?title=FSM#Basic_FSM_for_decorations:">simple state machine for a decoration</a>. So we'll build an example based off that with some of our own twists! And we'll do it step by step and analyze every single component starting with how to describe our state machine in EFPSE <img src="EFPSE_icon.png" width="28px" alt="EFPSE logo" style="margin-bottom:-8px">.</span>
    </div>
    <div style="position: absolute; top: 50%; right: -15px; border-style: solid; border-width: 8px 0 8px 15px; border-color: transparent transparent transparent #DCF8C6; content: '';"></div>
    <img src="quokka_new.png" alt="Avatar" style="width: 32px; height: 32px; border-radius: 50%; position: absolute; top: 50%; right: -42px; transform: translate(50%, -50%);">
</div>










#### Overview
Within the EFPSC game engine state machines are used for three different components. 
<!-- These really should be diagrams in a table -->
Weapons, decorations, and enemies. 

With these state machines we can display frames of animation,Play sounds,emit two different types of particles,Set and read variables, do simple calculations, and jump to different states Conditionaly or otherwise.(And probably a whole bunch of stuff I've never even thought of)

But in this specific tutorial we'll just take a look at basic functionality for the basic decoration state machine..

EFPSE <img src="EFPSE_icon.png" width="28px" alt="EFPSE logo" style="margin-bottom:-8px"> State machines are described declaratively in a script-like language saved in a text file with the ext `.states`. These state scripts should be located in the <span style="color:#0070C1;cursor:help" title="📁C:\Users\<user>\OneDrive\Desktop\Projects\Project\States">📂Project/States</span> folder.



<details class="bonus-assignment">
  <summary><span style="color:grey">Can't find the folder?</span></summary>
  <p>The    folder is Is wherever EFPSE saves its projects. I'm pretty sure by default that Located in the same directory as the EFPSE  executable `.exe`. I run mine on my desktop so on my desktop there is a folder called 📁projects that contains examples of the folder's namesakes. Here's the full path:</p>
  <p>📂C:\Users\User\OneDrive\Desktop\Projects\FSMTUT01</p>
  <p>and an image of the inside of the 📂Project/ folder</p>
  <img src="ss_states.png" alt="ss_states.png">
</details>

##### EXAMPLE
Let's take a look at the example script:


<span style="color:#0070C1;cursor:help" title="📁C:\Users\<user>\OneDrive\Desktop\Projects\Project\States\Decoration.states">📂Project/States/Decoration.states</span>

``` states
image Decoration 0 4

state IDLE NONE 0
frame 0 0.25 0 0 0 NONE
frame 0 0.25 0 0 0 READY

state DEATH DEAD 0
frame 1 0.166 0 0 0 NONE
frame 2 0.166 0 0 0 NONE
frame 3 0.166 0 0 0 NONE

state DEAD NONE 0
frame 4 0.25 0 0 0 NONE
frame 4 0.25 0 0 0 NONE
```



#### Syntax

Let's break this down by taking a look at each line and identify what's going on.

##### Resource declarations

`image Decoration 0 4`

All resource declarations need to be done at The top of the file. This can include `image`s using the `image` keyword or `sound`s using the `sound` keyword (Which will be covered later). 

##### State declarations

`state IDLE NONE 0`

Each `state` definition is preceded by the keyword `state` then followed by the `NAME` of the `state` you would like to define followed by the `NAME` of the `state` you would like to come after. The end of this line it needs a zero and this is an interpolation flag for 3D models.

~That is correct you can use 3D models but we will not be covering that in this tutorial.~

##### Frame declarations

``` state
state IDLE NONE 0
frame 0 0.25 0 0 0 NONE
frame 0 0.25 0 0 0 READY
```

Each line of the `state` begins with the keyword `frame` followed by the frame number (`0`) followed by duration the frame will be displayed (`0.25`), followed by XYZ offsets for weapons (`0 0 0`), followed by an action where default is the keyword `NONE`

Let's take an even closer look at one of these `frame` declarations.

| <span style="background-color: rgb(102, 102, 102);">**Frame keyword**</span> | <span style="background-color: aqua;">**Frame index**</span> | <span style="background-color:orange;">**Duration on screen**</span> | <span style="background-color:salmon;">**XYZ offsets (only for weapons)**</span> | <span style="background-color:yellowgreen;">**Action to take**</span> |
| ---------------------------------------------------------------------------- | ------------------------------------------------------------ | -------------------------------------------------------------------- | -------------------------------------------------------------------------------- | --------------------------------------------------------------------- |
| `frame`                                                                      | `0`                                                          | `0.25`                                                               | `0 0 0`                                                                          | `READY`                                                               |

<span style="background-color: rgb(102, 102, 102);">**Frame keyword**</span> - Frame keyword used on every line of a frame in a state's definition

<span style="background-color: aqua;">**Frame index**</span> - The index of the list of images that have been loaded to display

<span style="background-color:orange;">**Duration on screen**</span> - Duration on screen This is the length in seconds of how long to display the image for

<span style="background-color:salmon;">**XYZ offsets (only for weapons)**</span> - This is an XYZ offset used for weapons, Allows for on screen position adjustment

<span style="background-color:yellowgreen;">**Action to take**</span> - The action to perform on this frame. Default is none and will make the frame loop.\*\*

> \*\*Here we're Performing the ready action. This action is only necessary to be called before a weapon or enemy can attack. In this case we're using only a decoration and the decoration entity does not support the attack state so essentially this does nothing

#### Whoa that's a lot! 😱
Absolutely! No worries if it doesn't sink in the first time. Let's back It way back up. Let's look at the original code but let's remove all those messy frame declarations and let's just look at the state declaration syntax:


📂Project/States/Decoration.states
<span  style="color:grey;">`frame` declarations omitted</span>

``` states
image Decoration 0 4

state IDLE NONE 0

state DEATH DEAD 0

state DEAD NONE 0
```
Now let's compare that to a diagram of what's going on;

🤖`Decoration` state machine diagram
![](02_2_FSM_HOW_EFPSE_diagram.svg){width="650"}

As we can see both the script and the diagram have three states which are idle death and dead, But what's not included in the script is a <span style="color: transparent; background-image: linear-gradient(to right, black, #f0f0f0); -webkit-background-clip: text; background-clip: text; text-fill-color: transparent;">hidden signal...🥷</span>

In EFPSE Things that have HP <img src="../HUD/HP.png"> like breakable decorations, enemies ,and the player are hard coded to do certain things and one of them is to always check if their hp is above 0. 

If this happens the state machine stops what it's doing immediately and it goes to the death state.
>This happens no matter what state the entity is in. This includes any custom states that you have defined as well. 

From here we can control what it does but most commonly we transition to the dead state where... Nothing happens.

<!-- To do put the picture of the decoration option -->
I'm pretty sure the state doesn't even loop. And inside the decoration options if you click the check box destroy on death the entity will be removed.


##### back 2 a bit deeper
Now let's dive back in just a little bit deeper and look at the simulation that I have prepared. It works just like the stoplight simulation but this time I've made it so that it mirrors our decoration state machine.

Inside the states there are mockups of what happens inside EFPSE's state machine. They are only for demonstration purposes. The intention here is to convey that when the state machine is in a specific state it executes each frame while in that state until it goes to another state.
<iframe src="https://stately.ai/registry/editor/embed/f7a50bc1-d70b-4133-823c-4f7370e0ea70?machineId=94fa47ad-0e4b-461c-8865-4e04f15a520d" width="90%" height="400px" frameborder="0">
https://stately.ai/registry/editor/&mode=design
</iframe>

It might be a little bit hard to see this time around because when the if statement is true it looks like nothing happens. You can click on the view in Stately studio button and run the simulation there and you'll get more feedback or if you're lazy I put a video below that shows me doing that so you don't have to do it yourself. 🙏

<video controls width="720">
  <source src="DecorationSim.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>


#### Translating it into English
If you're still I'm not sure exactly what's going on in the Script or you enjoy things being talked about until they're no longer interesting, let's translate the script into English below. Otherwise, feel free to skip this and move on directly to the implementation.


<div style="font-family: Arial, sans-serif; background-color: #f2f2f2; color: #333; margin: 0; padding: 0;">
    <div class="chat-container" style="max-width: 100%; margin: 20px auto; border-radius: 8px; overflow: hidden; box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);">
        <ul class="chat" style="list-style: none; margin: 0; padding: 0;">
            <li class="bot-message" style="padding: 8px 16px; border-bottom: 1px solid #ccc;">
                <span class="sender-name" style="font-weight: bold; color: #555;">🤖EFPSE GPT:</span>
                <p class="message" style="margin-top: 4px; font-size: 16px;">Hello, how can I help you?</p>
            </li>
            <li class="user-message" style="padding: 8px 16px; border-bottom: 1px solid #ccc;">
                <span class="sender-name" style="font-weight: bold; color: #555;">🐖Cleverhog:</span>
                <p class="message" style="margin-top: 4px; font-size: 16px;"><code>image Decoration 0 4</code>
                 <p>What does this line say?</p>
                </p>
            </li>
            <li class="bot-message" style="padding: 8px 16px; border-bottom: 1px solid #ccc;">
                <span class="sender-name" style="font-weight: bold; color: #555;">🤖EFPSE GPT:</span>
                <p class="message" style="margin-top: 4px; font-size: 16px;">This script says to load an <code>image</code> called <code>Decoration</code> frames <code>0</code> through <code>4</code>.</p>
            </li>
            <li class="user-message" style="padding: 8px 16px; border-bottom: 1px solid #ccc;">
                <span class="sender-name" style="font-weight: bold; color: #555;">🐖Cleverhog:</span>
                <p class="message" style="margin-top: 4px; font-size: 16px;">
                <code>state IDLE NONE 0<br>
                    frame 0 0.25 0 0 0 NONE<br>
                    frame 0 0.25 0 0 0 READY</code> 
                    <br>
                    <p>-</p>
                    <p>What does this line say? </p>
                    </p>
            </li>
            <li class="bot-message" style="padding: 8px 16px; border-bottom: 1px solid #ccc;">
                <span class="sender-name" style="font-weight: bold; color: #555;">🤖EFPSE GPT:</span>
                <p class="message" style="margin-top: 4px; font-size: 16px;">Make a state called <code>IDLE</code> that repeats with two <code>frame</code>s where they're both the <code>0th</code> image from the <code>Decoration</code> <code>image</code> list and they both last <code>0.25</code> seconds; set the last <code>frame</code>'s action to be <code>READY</code>. Because <code>NONE</code> is set as the <em>transition state</em>, loop <u>indefinitely</u>♾️</p>
            </li>
            <li class="user-message" style="padding: 8px 16px; border-bottom: 1px solid #ccc;">
                <span class="sender-name" style="font-weight: bold; color: #555;">🐖Cleverhog:</span>
                <p class="message" style="margin-top: 4px; font-size: 16px;">
                <code>
                    <br>
                    state DEATH DEAD 0<br  >
                    frame 1 0.166 0 0 0 NONE<br>
                    frame 2 0.166 0 0 0 NONE<br>
                    frame 3 0.166 0 0 0 NONE<br>
                </code>
                <p>What about all this garbage?</p>
                </p>
            </li>
            <li class="bot-message" style="padding: 8px 16px; border-bottom: 1px solid #ccc;">
                <span class="sender-name" style="font-weight: bold; color: #555;">🤖EFPSE GPT:</span>
                <p class="message" style="margin-top: 4px; font-size: 16px;">
                Make a state called DEATH that transitions into the DEAD state. Make the state have three frames starting at 1 ending at 3, and make each of them last for  .166 seconds. Do not invoke any actions in this state.
                </p>
            </li>
            <!-- Add more messages here -->
        </ul>
    </div>
    <div style="width: 100%; padding: 16px; background-color: #fff; border-top: 1px solid #ccc;">
        <input type="text" style="width: calc(100% - 32px); padding: 8px; border: 1px solid #ccc; border-radius: 4px; box-sizing: border-box;" placeholder="Type your message here...(This doesn't actually work 😅)">
    </div>
</div>






#### Say it in English!!!
## Second half (implementation and application of blah blah)