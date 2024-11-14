# first tidal cycles patch with documentation
## Code
````
setcps (140/60/4)
d1 $ s "clubkick*4"
d2 $ slow 2 $ s "808oh*16? 808oh*12"
d3 $ randslice 16 $ fast 16 $ s "birds" # squiz 2 # comb sine
d4 $ s "dork2" # gain 0.1
d5 $ randslice 32 $ fast 16 $ s "dorkbot" # gain 0.7 # comb sine
d6 $ fast 2 $ s "~ insect"
d8 $ s "techno:1 techno:2 techno:3 techno:4" # comb sine
d9 $ s "space:2 space:1 space:4 space:10" # hbrick 0.1 # gain 0.7
d10 $ palindrome $ note (arp "<converge diverge>" "<a'minor e'minor c'minor>") # s "bass:1 bass:2 bass:3 bass:4" # squiz 1 # comb sine
````
## What I Did
I created an annoying groove with some outdoorsy samples as well as spacy synth samples.

## How I Did It
### Tempo
I set the tempo to 140 BPM

### Drum Machine Percussion
I had a four on the floor kick pattern going as well as a hi hat pattern that would switch between 16th notes and triplet feel.

### Birds, Dorkbot
I spent most of this week checking out the samples and had the bird sample looping initially, until I checked out randslice to spice up the order of chirping. In addition to this, I added squiz and comb filtering so it would be a little more grating. I applied this technique to a vocal sample and it added some subtle chaos to the overall mix. It no longer sounds like a vocal because of how it is sequenced.

### Bass
I was trying out the different arpeggio modes to see how they behaved. I'm still uncertain as to how it works rhythmically based on the chords/scales I specified. Is it triplety because they're triads? Not entirely sure but it works because of how ridiculous the whole thing sounds.

### Everything Else
I was mainly auditioning the built-in samples and keeping it straightfoward with a few effects.

## The Problems I Faced
I'm still getting the hang of this language, and since there isn't a UI where I could easily audition samples, it takes me a little longer to make the sounds and sequences I want to make. I still don't fully grasp the arpeggio modes. I generally prefer specifying what notes I'd like to be played. I think that everything I make with tidal cycles after this patch will be a significant improvement.

## Code That Came From Elsewhere
Everything else in this code was my interpretation and implementation of tidal cycles's documentation in addition to the examples in README.md in 08tidalcyclessamples.