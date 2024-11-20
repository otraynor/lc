# second tidal cycles patch with documentation
## Code
````
setcps (120/60/4)

d1 $ slow 8 $ note "af1"
  # sound "padlong"
  # attack 2
  # release 10
  # gain 1.7

d2 $ slow 4 $ note "d2 c2"
  # sound "superfork"
  # attack 0.1
  # decay 7
  # release 8
  # fshift 310
  # delaytime "<0.15 0.4>"
  # delay 25
  # delayfb 0.6
  # dry 4
  # room 5
  # size 0.5
  # gain 0.3

d3 $ slow 2 $ note "f6 a5 df4"
  # sound "pad"
  # pan "<0.25 0.75>"
  # vowel "a e i o u"
  # gain "0.3"

d4 $ slow 8 $ note "c0 f0"
  # sound "insect"
  # attack "0.4"
  # release "0.9"
  # dry "4"
  # room "5"
  # size "0.9"
  # gain "0.3"

d5 $ slow 2 $ note "c2"
  # sound "cyclo"
  # hpf 200
  # lpf 4000
  # attack 1
  # decay 2
  # release 1
  # gain 0.9

d6 $ slow 1.5 $ note "c1"
  # sound "supergrind"
  # detune "<5 4 3.5 2 1.7>"
  # voice "<5 6 4 3 2 1>"
  # leslie 10
  # lrate 0.1
  # tsdelay 0.01
  # lpf 200
  # lpq 0.3
  # pan sine
  # gain 0.4

d7 $ slow 4 $ note "~ df0"
  # sound "space:1"
  # attack 1
  # release 10
  # gain 0.9

d8 $ slow 16 $ note "f2 c3"
  # sound "superpiano"
  # octer 1
  # comb 0.5
  # dry 3
  # room 2
  # size 0.9
  # lpf 800
  # gain 0.2
````
## What I Did
I created an eerie drone patch using some of the synthesizers and samples.

## How I Did It
### Tempo
I set the tempo to 120 BPM

### Pads
There are some samples that sounded eerie so I had them loop.

### Superfork
I saw this in the physical modeling section of the documentation and I thought it complemented the vibe well. I set it with a frequency shifter so it would add a tonal quality to the patch.

### Supergrind
Experimenting with another synthesizer. It sounded really harsh but I added a comb filter and filtered out the high end.

### Cyclo
I think this was some sort of shepard's tone synthesizer. It added some movement through the patch while staying in a similar place.

## The Problems I Faced
I spent most of the time on this figuring out the synthesizers. My biggest disappointment is that I couldn't figure out how to get the FM synthesizer to work. I tried to initialize all of the settings like it said to do and it wouldn't work, even after I tried copying and pasting their example into my patch. In addition to this, some parameters for the synthesizers weren't valid when I was programming. I didn't solve any of these problems, but I worked around it. I also feel like tidal cycles is more sensitive than strudel, like when it comes to adjusting gain or the balance of the effects.

## Code That Came From Elsewhere
Everything else in this code was my interpretation and implementation of tidal cycles's documentation.