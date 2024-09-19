# strudel percussion patch with documentation
## Code
````
stack(
  //Syncopated Kick Pattern//
  "[RolandCompurhythm1000_bd ~ ~ RolandCompurhythm1000_bd] [RolandCompurhythm1000_bd ~ ~ RolandCompurhythm1000_bd ~ ~ RolandCompurhythm1000_bd ~]",

  //Karplus-Strong Bass
  "[BossDR550_misc | DoepferMS404_oh | EmuModular_perc]*16".delay("0.9").lp("<125 170 360 60> *16").lpq("5").dt("0.016 0.0148 0.03")
  .dfb("0.9").lp("<125 170 260 125 3200 400 300 250 180 130 60> *24").lpq("10")
  .distort("15:0.08").lpf("300").compressor("-50:50:5:0:0")
  .compressor("-130:50:10:0:0").bpf("20").gain("0.1 0 0.0001 0 0.0001 0 0.0001 0.0001"),

  //Snares
  "[~ BossDR110_sd] *2".gain(2),
  "[~ AJKPercusyn_sd] *2".gain(".1"),

  //Ride & Clap
  "[~ BossDR550_rd ~  AlesisHR16_cp]",

  //Randomized Hi-Hats
  ("[RolandTR808_hh | RolandCompurhythm8000_ht | RolandTR909_hh | RolandTR505_hh] * 16")
  .gain(".4!2 1 .4!2 1 .4 1").late(sine.segment(8).range(0, 1)).hpf(14000).gain(0.2),

  //Karplus-Strong Cowbell Experiments with Impulse Responses
  ("[RolandCompurhythm78_cb | RolandTR808_cb | RolandMC303_cb]*16?").gain(0.25).speed(rand.range(-2, 6))
  .delay("0.7").dt("<0.013 0.14 0.4 0.02 0.05> *50").dfb("<0.5>").orbit(2).vowel("<a e i o u>*5").hpf("600")
  .hpq("0").gain(0.2).pan(rand.range(0, 1)).ir("<shaker_large guiro sleighbells dantranh_tremolo>").room("8")
  .rsize("2").compressor("-200:20:40:40:0").gain(0.1)
).cpm(115/4).s().compressor("-200:4:40:.04:.001")
````
## What I Did
I created a distorted off-kilter groove using strudel's samples and manipulated them with delay, reverb, distortion, and compression.

## How I Did It
### Syncopated Kick Pattern
I created a very basic syncopated kick drum pattern with the Roland CR-1000 Kick sample. I decided to keep this element of my patch straightforward so the pattern had a strong foundation.

### Karplus-Strong Bass
I gathered a list of a few samples with higher-frequency content in order to have a harmonically complex drony bass sound that would slightly shift every 16th note. I added a delay with high amplitude and feedback. The delay time changes a few times through the cycle in order to change the fundamental note. I added 2 lowpass filters with sequenced frequency changes to add some different character to the bass as well as some instability in the signal being sent to the delay. After that, I distorted the whole signal and compressed it twice since the distortion would make the bass pop out at different points. I added a bandpass filter in the lower frequencies so the high end wouldn't be so harsh, as well as emphasizing the low end of the bass. And finally, I sequenced the gain level so it sounds like the notes start and stop rhythmically.

### Snares, Ride, and Clap
Samples mixed to taste, since the stack is hitting a gritty master compressor. Rhythmically grounded elements of the patch.

### Randomized Hi-Hats
I made a list of hi-hat samples I liked, implemented a gain sequence from the strudel introduction, had a sine wave delay the signal to shift the timing off at a constantly changing rate, added a high pass filter, and balanced the overall level.

### Karplus-Strong Cowbell Experiments with Impulse Responses
I picked 3 cowbell samples, had them randomly occur in a 16th note sequence. Then I affected the speed so some samples would be reversed or sped up at random intervals. With my karplus-strong bass in mind, I added delay with quick repeat times and high feedback. After this, I added a sequenced formant filter, though it got a little unruly, so I lowered the gain after. I utilized randomized panning with this sound. Then I added an impulse response reverb, and sequenced some samples with interesting "tails" as the impulses, with the final sequence being the longest sample, creating an unsettling, distorted, feedback swell. Then I compressed and balanced it so it wouldn't completely overwhelm the mix.

## The Problems I Faced
When I'm learning some new music technology, my first exercise with it is to push it to its limits. Karplus-Strong, especially with all of the nuance and slight variations I implemented, is not the most computationally efficient synthesis. When I started making this patch, I was trying to figure out the boundaries of the filters and what effect they would have in the synthesis. There was a point where I was trying to use multiple complexly sequenced lowpass filters with high resonance in the bass, and the audio would stutter and crash. I wouldn't say that this was a bug in the way that I had to think hard and patiently troubleshoot to solve my issue. I was trying effects that had, frankly, no noticeable effect in the synthesis, so I eliminated it and this patch ended up being everything I hoped it would be. To test that the patch wouldn't crash, I ran it for an hour, came back, and it still worked.

Another problem I faced with the Karplus-Strong approach was not realizing that delay was a global effect, which definitely factored into the crashing I mentioned earlier, since the delay times are sequenced way differently. I put the cowbell delay on a different orbit and my problem was solved.

Besides that, the problems I faced had to do with figuring out the boundaries of the effects, like the distortion and compression. But with those effects, none of them functioned incorrectly. I just had to consider the consequences of extreme distortion and adjust the post-gain. I wanted a gritty, harsh master compressor on the patch and I was able to dial it in exactly as I wanted it to work.

I had little trouble accomplishing what I was trying to do, which heightens my enthusiasm to learn live coding, but regrettably, I have no debug log.

I plan to look into seeing if there are more efficient ways to do Karplus-Strong synthesis with this coding environment.

## Code That Came From Elsewhere
I implemented some of ``s("hh*8").gain(".4!2 1 .4!2 1 .4 1").fast(2)`` from 01introtostrudel.md in my Hi-Hats

Everything else in this code was my interpretation and implementation of strudel's Effects and Samples documentation.