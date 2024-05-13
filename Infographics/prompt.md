```
image [EX]cat 0 3
image flea
sound meow
sound bell

state IDLE FLEASCRATCH 0
frame 0 0.5 0 0 0 NONE
frame 0 0.5 0 0 0 SETVAR global.FSM_STATE "IDLE"
frame 0 0.5 0 0 0 SOUND 0
frame 0 0.5 0 0 0 READY

state FLEASCRATCH IDLE 0
frame 1 2 0 0 0 NONE
frame 1 2 0 0 0 SOUND 1
frame 1 2 0 0 0 SETVAR global.FSM_STATE "FLEASCRATCH"
frame 1 2 0 0 0 PARTICLES 4 1,3000,0,64,0 0,64,0
frame 1 2 0 0 0 NONE

state DEATH DEAD 0
frame 2 0.166 0 0 0 NONE
frame 2 0.166 0 0 0 SETVAR global.FSM_STATE "DEATH"
frame 2 0.166 0 0 0 NONE

state DEAD NONE 0
frame 3 0.25 0 0 0 NONE
frame 3 0.25 0 0 0 SETVAR global.FSM_STATE "DEAD"
frame 3 0.25 0 0 0 NONE
```

Consider this script. I want to be able to make an html web application that has a text box that you can paste the script into. The script will be parsed and create images With the text:


NAME {name}
STATE {state} : frame {state_frame}
ACTION: {action}

Where {name} comes from The first line: `image {name} 0 3`  In this case it would be `[EX]cat`
Where {state} comes where the state is: `state IDLE FLEASCRATCH 0` In this case it would be `IDLE`
Where {state_frame} comes where the frame is: `frame 0 0.5 0 0 0 NONE` In this case it would be `frame 0 0.5 0 0 0` 
Where {action} comes where the action is: `frame 0 0.5 0 0 0 SETVAR global.FSM_STATE "IDLE"` In this case it would be `SETVAR global.FSM_STATE "IDLE"`

An image needs to be created for every single frame declaration. On the image their frame numbers count should start from the beginning of their state's declaration. 

```
state IDLE FLEASCRATCH 0
frame 0 0.5 0 0 0 NONE
frame 0 0.5 0 0 0 SETVAR global.FSM_STATE "IDLE"
frame 0 0.5 0 0 0 SOUND 0
frame 0 0.5 0 0 0 READY
```
Would give values:
NAME [EX]cat
STATE IDLE : frame 0 0.5 0 0 0
ACTION: NONE

NAME [EX]cat
STATE IDLE : frame 1 0.5 0 0 0
ACTION: SETVAR global.FSM_STATE "IDLE"

NAME [EX]cat
STATE IDLE : frame 2 0.5 0 0 0
ACTION: SOUND 0

NAME [EX]cat
STATE IDLE : frame 3 0.5 0 0 0
ACTION: READY

But when you save the images you need to number them from zero like so:
[EX]cat0.png
[EX]cat1.png
[EX]cat2.png
[EX]cat3.png

So even though you're counting from zero in the state frames the actual PNG is altogether we'll start from zero.

The user should be ableTo enter the script in a text box, change the resolution of the image and change the font size of the text this should also be able to be downloaded in a zip via some link or button on the page.Please don't make anything just let me know if you're on the same page as me. Please use vanilla javascript and html on a single page to accomplish this Remember parse turn into pictures and let me download a zipped file of them
