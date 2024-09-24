# strudel percussion patch with documentation
## Code
````
samples({ 
  sing1: 'https://cdn.freesound.org/previews/681/681474_13652149-lq.mp3',
  sing2: 'https://cdn.freesound.org/previews/678/678013_13652149-lq.mp3'
})

stack(
  //Soprano Singing Loop
s("sing1")
  .chop(60)
  .attack("0.1")
  .release("0.1")
  .rev()
  .loopAt(10)
  .compressor("-99:20:39:0.0001:0.0001")
  .lp(3000)
  .ftype(2)
  .hp(250)
  .orbit(2)
  .pan("<1 0> * 4")
  .gain(sine.segment("<1 25 50 100 1000>/8").range(0.00000000001, 0.04)),

  //Alto Singing Loop
s("sing2")
  .chop(60)
  .attack("0.3")
  .release("0.1")
  .rev()
  .loopAt(5)
  .compressor("-99:20:39:0.0001:0.0001")
  .lp(7000)
  .ftype(2)
  .hp(250)
  .orbit(2)
  .pan("<0 1> * 4")
  .gain(sine.segment(1).range(0.00000000001, 0.2)),
  
  //Drum Loop
s("bd * 4, ~ sd ~ sd, ~ cp ~ cp")
  .bank("RolandTR909")
  .lpf(700)
  .lpq(0)
  .ftype(2)
  .roomsize(4)
  .room(0.6)
  .orbit(6)
  .gain(0.22),

//Sub Bass
note ("[d1!8 f#1!8 c#1!8 e1!8]/8")
  .attack("0.35")
  .sound("sine")
  .gain(0.3),

//Sub Bass Harmonic
note ("[d2!8 f#2!8 c#2!8 e2!8]/8")
  .attack("0.35")
  .sound("sine")
  .gain(0.3),

//Sub Bass Harmonic 2
note ("[a2!8 c#3!8 g#!8 b2!8]/8")
  .attack("0.35")
  .sound("sine")
  .gain(0.4),

//Choir 1
chord("<F#m7 A^7 C#m7 D^7>/2")
  .layer(x=>x.struct("[x]*4"))
  .voicing()
  .sound("gm_choir_aahs:<4 9>*4")
  .vib(1)
  .vibmod(0.2)
  .attack(0.6)
  .hpf(450)
  .lpf(3000)
  .ftype(2)
  .pan(0)
  .gain(0.017),

//Choir 2
chord("<D^7 F#m7 C#m F#m7>/2")
  .layer(x=>x.struct("[x]*4"))
  .voicing()
  .sound("gm_choir_aahs:<9 4>*4")
  .vib(0.6)
  .vibmod(0.2)
  .attack(0.6)
  .hpf(350)
  .lpf(3000)
  .ftype(2)
  .pan(1)
  .gain(0.017),
  
//Bottle Pad
note ("<[a3 g#3 f#] [a3 b3 g#3 f#]>/7")
  .sound("gm_blown_bottle")
  .vib(sine.segment(7).range(0.1, 5))
  .vibmod("0.1")
  .delay(.7)
  .delaytime(6)
  .lp(500)
  .orbit(2)
  .pan(sine.segment(50).range(0.25, 0.75))
  .gain("0.2"),

//Glass Pad
note("<[c#5 d5 e5 b4] [a4 g#4 b4 a4 e4]>/13")
  .sound("gm_pad_bowed")
  .begin("0.1")
  .vib(sine.segment(16).range(0.1, 5))
  .vibmod("0.25")
  .phaser(0.4)
  .delay(1.2)
  .delaytime(8)
  .dfb(0.6)
  .room("10:10")
  .compressor("-20:8:10:0:60")
  .lp(1000)
  .orbit(3)
  .pan(sine.segment(30).range(0.25, 0.75))
  .gain("0.03"),
  
//Violin
n(rand.range(1,15).segment(sine.segment(1).range(1, 10)))
  .scale("F#:minor")
  .s("gm_violin")
  .begin("0.9")
  .vib(sine.segment(7).range(0.1, 5))
  .vibmod("0.4")
  .pan(rand.range(0, 1))
  .delay(1)
  .dt(5)
  .room(1)
  .rsize(10)
  .phaser(13)
  .lp(3000)
  .ftype(2)
  .orbit(4)
  .gain(0.01),

//Electric Piano
n(rand.range(1,26).segment(sine.segment(0.8).range(1, 7)))
  .scale("F#:minor")
  .s("gm_epiano2")
  .attack("0.1")
  .release(0.3)
  .vib(rand.range(0, 6))
  .vibmod("0.3")
  .pan(rand.range(0, 1))
  .delay(0.1)
  .delaytime(9)
  .phaser(3)
  .phaserdepth(1)
  .phasercenter(700)
  .phasersweep(2000)
  .lp(3000)
  .ftype(1)
  .hp(150)
  .room(saw.segment(90).range(0, 3))
  .orbit(5)
  .gain(sine.segment(0.1).range(0.00000000000001, 0.15)),

  ).compressor("-20:5:30:0.03:0.01")
````
## What I Did
I created an ambient house loop using strudel's samples and some samples from freesound.org.

## How I Did It
### Soprano Singing Loop
I chopped the first singing sample into 60 parts, added some attack and release, then reversed all of the chops. I found the right loop speed for the sample for the pitch to match with some trial and error. It's compressed and filtered to blend in with the overall vibe. It pans hard left and right, and gradually the volume increases and decreases over the course of several cycles.

### Alto Singing Loop
Has most of the same parameters of the Soprano Singing Loop with a different sample and different values for contrast.


### Drum Loop
Made an extremely simple drum loop using TR-909 samples. This patch is more focused on melodic and ambient textures. Was going for a GAS styled groove.

### Sub Bass and Harmonics
Low sine waves that repeats every 8 cycles. Added attack for a pseudo sidechain compression effect.

### Choirs
I was trying to figure out how to use the chords in strudel. I added some vibrato to them and attack for the sidechain effect. Filtered and panned for effect.

## Bottle and Glass Pads
I was initially going for a generative ambient idea for this patch, hence some patterns occuring over odd numbered cycles, but I liked how the drums filled it out. I used some vibrato and delay on these pads, as well as some panning with a sine wave.

### Violin and Electric Piano
I randomized notes to play in the F# minor scale. I have the samples begin a little later on some of them or the attack increased so the transients weren't sticking out. A sine wave modifies the speed of notes being played. Another sine wave modifies the amount of vibrato gradually. And finally, I change the volume with each of these too.

## The Problems I Faced
I couldn't understand how to change the voicings or pitch of the chords. I felt the documentation didn't explain it well. Thankfully it fits well in my patch but I felt frustrated. I wanted to implement ``//n(mousex.segment()`` and ``//n(mousey.segment()``, thinking that I could adjust filter and panning over the entire stack depending on the position of my mouse. However, with everything else going on in my patch, it was too computationally demanding. Sometimes samples wouldn't play or the patch would crash. Besides that, I had a smooth experience with creating this patch.

## Code That Came From Elsewhere
Everything in this code was my interpretation and implementation of strudel's documentation.