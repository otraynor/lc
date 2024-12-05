# Tidal Cycles Solo Final Project
## Tidal Cycles Code

````
setcps (128/60/4)

-- Kick
d1 $ s "clubkick:5*4"
  # lpf 200
  # gain 0.8

-- Bass
d2 $ slow 4 $ note "fs2 as2 cs2 ds2"
  # s "superreese"
  # accelerate 0
  # detune 0
  # legato 1.2
  # hold 4
  # lpf 400
  # hpf 35
  # hpq 0.1
  # gain 0.6

-- Low Pad
d3 $ slow 4 $ note "fs3 as3 cs3 ds3"
  # s "superhoover"
  # accelerate 0
  # detune 0
  # attack 0.001
  # hold 1.4
  # sustain 10
  # release 2
  # lpf 700
  # hpf 125
  # vowel "a e i o"
  # comb 0.3
  # dry 1
  # room 1
  # gain 0.6

-- SID synth
d4 $ n (fast 24 $ fmap (*5) $ run "[4 2 4 3 4 2 4 5]/8")
  # s "superchip"
  # decay 0.01
  # accelerate 0.03
  # voice "[0.8 0.7 0.6 0.5 0.3 0.2 0.1]"
  -- # voice "[0.8|0.7|0.6|0.5|0.3|0.2|0.1]*4"
  # delay 0.4
  # delaytime 0.1
  # delayfb 0.3
  -- # squiz 3
  # lpf 3000
  # fshift 10
  # pan (slow 4 $ sine)
  # gain 0.55

-- Piano (palindrome, rev, iter)
d5 $ iter 5 $ n "5 3 12 13 15 10"
  # s "superpiano"
  # phaserdepth 1
  # phaserrate 5
  # room 0.5
  # sz 0.9
  # gain 0.45

-- Mandolin
d6 $ jux (rev) $ arp "<pinkyup thumbup>" $ slow 2 $ n "fs'major7 as'minor7 cs'major7 ds'minor7"
  # s "supermandolin"
  # legato 3
  # room 0.9
  # sz 0.9
  # delay 0.1
  # delaytime 1
  # delayfb 0.9
  # lpf 9000
  # gain 0.45

-- Metallic Sound
d7 $ s "outdoor:2"
  # room 0.9
  # sz 0.9
  # gain 0.35

````

## Hydra Code
````
await initHydra()
s0.initCam()

//Camera
  src(s0)
    .blend(noise(10)
   .blend(solid(0, 0, 0)))
    .scrollX(0.01, 0.01)
    //.modulateScrollY(osc(1), 0.01, 0.05)
    //.rotate(0.01, -.01)
    //.colorama(.01)
    .pixelate(1000, 50)
    .saturate(10)
    .out(o0)
    
````
## What I Did
I created a chill ambient triplety house beat with the synthesizers in Tidal Cycles. I accompanied my music with visuals from Hydra via Strudel sourced from my webcam.

## How I Did It
### Kick, Bass, Low Pad, and Metallic Sound
These elements remained mostly unchanged throughout the performance. They just provide a consistent groove. I added filters to the melodic elements so they would sound darker. The vowel filter on the low pad has a subtle textural effect on the overall sound.

### SID synth
I wanted to use arpeggios in this patch because I haven't made much melodic material in this course. Before I settled on this sound, I was copying and pasting different examples in the documentation to see what everything did. I was intrigued by fmap, because it increased the note by whatever note increment I set it to. That combined with run to determine how far to repeat fmap (if it went beyond 5, it would go outside of the key) along with changing fast to determine how many notes occur per cycle created some awesome results. I chose the superchip synth to go with this, and I especially liked how it sounded when I set fast to a high number.

## Piano
Most of the sounds used in this patch are simple because I was thinking more about how to combine different variations of arpeggios. I put in some note numbers that were in the correct key and made note of some pattern variations I enjoyed. That with a phaser and reverb, and the piano sound starts to fit in better with the overall vibe.

## Mandolin
The supermandolin synth is strange sounding to me, but I like it because it generates a lot of high frequency content, which helps add a sort of percussion to the patch. juxtoposing the reverse of the arpeggio patterns I selected made a rich sound and cool stereo image. This is filtered and reverbed as well.

## Hydra Code
I kept a very simple visual because I was focused more on the musical aspect of this performance. I am affecting my webcam with pixelation, blends of solid color and noise, and colorama, which does outrageous things to the appearance. I like how it blows out a lot of colors in a bright yet ugly way. I added saturation to make the colors pop out more. The ScrollX, ModulateScrollY, and rotation give some movement so there's visual progression to go along with the musical progression.

# The Problems I Faced
I didn't face any problems besides trying to integrate the visuals using atom-hydra. I decided to use Strudel alongside Tidal Cycles. The only difficulty I have is I'm still getting used to updating musical and visual code. I'm not a visual person so I find it hard to come up with something in Hydra that I find satisfying. My Tidal Cycles patch is pretty simple but I had fun figuring out what the arpeggio variations did.

## Code That Came From Elsewhere
Everything in this code was my interpretation and implementation of Tidal Cycle's documentation and hydra's functions.