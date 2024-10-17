# strudel+hydra
## Code
````
await initHydra({detectAudio:true})
s0.initCam()
bpm = 160

//Camera
  src(s0)
  //.blend(noise(70))
    .scrollX(0.1, 1)
    .modulateScrollY(osc(6), 0.1, 0.5)
    .rotate(1, -1)
    //.thresh(0.1, 0)
    //.colorama(.1)
    .out(o0)


//Shape
let pattern = "<3 7 4 9 6 24>*22"
shape(H(pattern))
 // .kaleid(2)
  .rotate(-1, -1)
  .scrollY(
    ()=> a.fft[0]*.25)
  .rotate(7, -.52)
  //.modulateRepeat(osc(10), 1, 1, 1, 1)
  //.modulateRotate(o0, -10)
  .colorama(0)
  .brightness(0.09)
  .thresh(0.1, 0)
 // .modulateScrollY(osc(10), 1, 1, 1, 1)
 // .pixelate(100,100)
 // .contrast(100)
 // .saturate(0.3)
  //.modulateRotate(osc(0.1), 1, 1, 1, 1)
.out(o1)

//Colorful Noise
noise(15)
 .colorama(1.05)
  .modulateScale(osc(1000, 0.5, 100))
  .contrast(50)
  .thresh(0.1, 0)
  .colorama(0.5)
  .colorama((noise(0.1),()=>a.fft[0]))
  .diff(o0)
  .add(o1, 0.8)
  .out(o2)



//Dark Colorful Noise
noise(.002, .002).colorama(0)
 .diff(osc(1,0.5,5))
  .modulateScale(osc(112,0.25,140))
  .scrollY(
    ()=> a.fft[0]*.25
  )
  .saturate(1)
  .modulateRepeat(osc(10), 1, 1, 1, 1)
  .modulatePixelate(o0, 20)
  .brightness(0.5)
  .contrast(100)
  .invert()
  .modulateRotate(osc(1), 3, 6, 23, 9)
  .blend(o1, 0.5)
  .blend(o0, 0.3)
  .out(o3)



render(o3)

stack(

//909 Hi Hat Pattern

  s("[hh!2 oh ~] *4 ")
  .bank("RolandTR909")
  .decay("150")
  .gain(0.03)
  .hush

,

//808 Snare
s("[~ sd:23] * 2")
  .room("0.4")
  .rsize(0.25)
  .rlp(3000)
  .orbit(1)
  .bank("RolandTR808")
  .gain(0.5)
  .hush

  
, 

//808 Perc
s("<sd:2 sd:22> *16? |rim *16? |<cb:2 sd:22> *16?")
  .rev()
  .speed("2 1.7 1.6 1!6 -3 | 1 1.5 1.2 1.3 | 1.5  | <-2 2 0.7>")
  .penv("0 1 | 1 | 5 | -7 7 | 0 | 10")
  .bank("RolandTR808")
  .pan(rand.range(0, 1))
  //.ir("<ratchet:2 shaker_large:2 numbers:9 numbers:2 numbers:7>")
  //.room(9)
  .delay(1)
  //.dt(0.1)
  .dt(rand.range(0.001, 0.01)*18)
  .dfb(80)
  .compressor("-10:4:40:.03:.02")
  .gain("0.00001 0.2!3 0.00001 0.2!3 0.00001 0.2!3 0.00001 0.2!3")
  .gain(0.15)
  .orbit(2)
  ,

//808 Kick
s("bd:7 *16? | bd:7 *8? | bd:10 *16? | bd:7 *16?")
  .decay(0.4)
  .speed(1)
  .lp(5000)
  .lpq("10")
  .lpd(0.05)
  .bank("RolandTR808")
  .gain("1 0.8!3 0 0.8!3 1 0.8!3 0 0.8!3")
  .gain(0.5)
  .hushawait initHydra({detectAudio:true})
s0.initCam()
bpm = 160

//Camera
  src(s0)
  //.blend(noise(70))
    .scrollX(0.1, 1)
    .modulateScrollY(osc(6), 0.1, 0.5)
    .rotate(1, -1)
    //.thresh(0.1, 0)
    //.colorama(.1)
    .out(o0)


//Shape
let pattern = "<3 7 4 9 6 24>*22"
shape(H(pattern))
 // .kaleid(2)
  .rotate(-1, -1)
  .scrollY(
    ()=> a.fft[0]*.25)
  .rotate(7, -.52)
  //.modulateRepeat(osc(10), 1, 1, 1, 1)
  //.modulateRotate(o0, -10)
  .colorama(0)
  .brightness(0.09)
  .thresh(0.1, 0)
 // .modulateScrollY(osc(10), 1, 1, 1, 1)
 // .pixelate(100,100)
 // .contrast(100)
 // .saturate(0.3)
  //.modulateRotate(osc(0.1), 1, 1, 1, 1)
.out(o1)

//Colorful Noise
noise(15)
 .colorama(1.05)
  .modulateScale(osc(1000, 0.5, 100))
  .contrast(50)
  .thresh(0.1, 0)
  .colorama(0.5)
  .colorama((noise(0.1),()=>a.fft[0]))
  .diff(o0)
  .add(o1, 0.8)
  .out(o2)



//Dark Colorful Noise
noise(.002, .002).colorama(0)
 .diff(osc(1,0.5,5))
  .modulateScale(osc(112,0.25,140))
  .scrollY(
    ()=> a.fft[0]*.25
  )
  .saturate(1)
  .modulateRepeat(osc(10), 1, 1, 1, 1)
  .modulatePixelate(o0, 20)
  .brightness(0.5)
  .contrast(100)
  .invert()
  .modulateRotate(osc(1), 3, 6, 23, 9)
  .blend(o1, 0.5)
  .blend(o0, 0.3)
  .out(o3)



render(o3)

stack(

//909 Hi Hat Pattern

  s("[hh!2 oh ~] *4 ")
  .bank("RolandTR909")
  .decay("150")
  .gain(0.03)
  .hush

,

//808 Snare
s("[~ sd:23] * 2")
  .room("0.4")
  .rsize(0.25)
  .rlp(3000)
  .orbit(1)
  .bank("RolandTR808")
  .gain(0.5)
  .hush

  
, 

//808 Perc
s("<sd:2 sd:22> *16? |rim *16? |<cb:2 sd:22> *16?")
  .rev()
  .speed("2 1.7 1.6 1!6 -3 | 1 1.5 1.2 1.3 | 1.5  | <-2 2 0.7>")
  .penv("0 1 | 1 | 5 | -7 7 | 0 | 10")
  .bank("RolandTR808")
  .pan(rand.range(0, 1))
  //.ir("<ratchet:2 shaker_large:2 numbers:9 numbers:2 numbers:7>")
  //.room(9)
  .delay(1)
  //.dt(0.1)
  .dt(rand.range(0.001, 0.01)*18)
  .dfb(80)
  .compressor("-10:4:40:.03:.02")
  .gain("0.00001 0.2!3 0.00001 0.2!3 0.00001 0.2!3 0.00001 0.2!3")
  .gain(0.15)
  .orbit(2)
  ,

//808 Kick
s("bd:7 *16? | bd:7 *8? | bd:10 *16? | bd:7 *16?")
  .decay(0.4)
  .speed(1)
  .lp(5000)
  .lpq("10")
  .lpd(0.05)
  .bank("RolandTR808")
  .gain("1 0.8!3 0 0.8!3 1 0.8!3 0 0.8!3")
  .gain(0.5)
  .hush

  ,

//FM Bass
note("<[eb1!16] [eb1!2 gb1!2 eb1!2 e2! eb2!2 db2!2 cb2!2 bb1!2]>")
.fm("<[9 4 5 3 9 7 5 8] [4 9 8 5 7 4 2 5]>")
  .fmdecay(".1")
  //.fmattack(rand.range(0, 0.025))
  .fmh("<2 4 3 7>")
  .fmenv("exp")
  .attack(".01")
  .decay("0.15")
  .release("0.05")
  .hpf(60)
  .hpq(5)
  .lp(500)
  .gain(0.5)
  .hush


,

//Square Bass
note("<[eb1!16] [eb1!2 gb1!2 eb1!2 e2! eb2!2 db2!2 cb2!2 bb1!2]>")
  .sound("square")
  .attack("0.1")
  .decay("0.2")
  .release("0.1")
  .lpf(60)
  .gain(0.7)
  .hush



,

//Bell
  note("[eb2]/8")
  .sound("gm_tubular_bells")
  .attack("2")
  .phaser("5")
  .room(10)
  .orbit(2)
  .gain(0.1)
  ,




  
).cpm(160/4)
//rand.range(30, 90)

  ,

//FM Bass
note("<[eb1!16] [eb1!2 gb1!2 eb1!2 e2! eb2!2 db2!2 cb2!2 bb1!2]>")
.fm("<[9 4 5 3 9 7 5 8] [4 9 8 5 7 4 2 5]>")
  .fmdecay(".1")
  //.fmattack(rand.range(0, 0.025))
  .fmh("<2 4 3 7>")
  .fmenv("exp")
  .attack(".01")
  .decay("0.15")
  .release("0.05")
  .hpf(60)
  .hpq(5)
  .lp(500)
  .gain(0.5)
  .hush


,

//Square Bass
note("<[eb1!16] [eb1!2 gb1!2 eb1!2 e2! eb2!2 db2!2 cb2!2 bb1!2]>")
  .sound("square")
  .attack("0.1")
  .decay("0.2")
  .release("0.1")
  .lpf(60)
  .gain(0.7)
  .hush



,

//Bell
  note("[eb2]/8")
  .sound("gm_tubular_bells")
  .attack("2")
  .phaser("5")
  .room(10)
  .orbit(2)
  .gain(0.1)
  ,




  
).cpm(160/4)
//rand.range(30, 90)
````
## What I Did
I created an experimental electro-inspired groove with some visuals revolving around a polygon with changing sides.

## How I Did It
### o0
I set up my webcam as a source to modulate the other sources. As you'll see throughout the rest of the code, many modulations are commented out so I could decide in the moment precisely how I'd want to affect a source.

### o1
I got the shape pattern from the hydra functions example and modified it so it would be faster and give an illusion that it'd sync up with the music. There's also a ScrollY modulation that corresponds with the sound, which I also got from a hydra functions example. I used the threshold effect so it would be really bold and sharp looking. This will be what my visuals mostly revolve around.


### o2
I was seeing what happened when I stacked effects on the noise generator. I was winging this but I'm pleased with the results.

### o3
I was trying to emulate the look of lasers and lights with a fog machine. With this, I also felt like I was throwing things at the wall to see what sticked, but I think it makes a cool intro for my set, especially when blended with o1.

### 909 Hi Hat Pattern
Basic TR-909 Hi-Hat Trance Pattern to ground the beat

## 808 Snare
TR-808 Snare Drum to mark 2 and 4. I added a little reverb to give it some stereo space and decay. Also keeps the beat grounded

### 808 Perc
I wanted some chaotic drum machine percussion that didn't poke out too much. There's several variations on the snare drum and I wanted to explore what each one sounded like. I gathered my favorite ones, and randomized them with some rim and cowbell samples. There's also variable speed, pitch envelope, and panning to keep it different every time. I loaded some strange samples for impulse responses to give an unpredictable element to how it would sound. This also causes it to poke out uncomfortably, which creates tension in the overall vibe. I have a randomized delay as well, but it's only noticeable in certain moments.

### 808 Kick
I wanted a kick that was randomized, but also wouldn't be audible during the snare hits, so there's some similar action happening to how I had the 808 Perc set up, in that there are some alternate kick samples within the 808 library. I used gain to make it louder on downbeats, quiet on upbeats, and inaudible during snare hits.

### FM Bass
I love FM synthesis and I haven't explored its implementation in strudel. It's pretty fun to play with overall. I initially wanted to do a 303 type synth with a basic waveform, LP filter, and distortion, but it didn't satisfy me. I'm able to get an alternative to that through this with the modulation adding strange harmonics to the fundamental.

### Square Bass
This has the same notes as the FM Bass. I wanted something that had a consistent low end to layer with the FM, but also have some harmonics so it felt fuller.

### Bell
Ominous bell loop with phaser, reverb, and a slow attack

## The Problems I Faced
Most of the problems I faced revolved around Hydra. I'm not a visual minded person, so I feel a little out of my element using it. I had to plan a lot of effects to comment in and out to keep the visuals interesting, but also set specific numbers because it's a little too easy to create a stroby visual. I think that the more I use it, the more I'll become comfortable with it, but I don't feel like I picked it up as quickly as I picked up strudel.

The other problem I faced was trying to figure out what all I could do in 3-5 minutes. Platforms like this make it easy to just constantly tweak things, which is part of the fun, but also I want to make an interesting performance for other people, not just myself. I'm perceiving it differently because I'm at the helm and have a general idea as to what does what. But again, I'm sure the more I do this, the more I'll find a groove with the performance aspect.

## Code That Came From Elsewhere
Everything in this code was my interpretation and implementation of strudel's documentation and hydra's functions