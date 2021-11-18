# TidalPOD
TidalCycles reamp experiment with Line6 P.O.D. 2.0

Example:

Create a pattern and route the result to the POD.
Used samples: https://github.com/thgrund/samples-ukulele

```haskell
d1 $ superimpose (
      (arp "[up!2 down]") .
      (struct "t*3") .
      (# gain 1.3) .
      (# s "sally:2"))
   $ struct "t*2" $ s "sally:0" <| up "<<c5'maj7 g'maj'4> e'min'4 f'maj'4 f'min'4>"
   # legato "<0.5>" # begin 0.2 # gain 1.2
```

Control the parameters of the POD, i.e.

```haskell
-- Control the P.O.D. parameters:
d8 $ s "pod" <| stack [
     pod_drive 1
     , pod_effect_tweak "<0 1>"
     , pod_effect_select "6"
     , pod_amp_model "<^britblues!4 ^tube!4>"
     , pod_eq_mid "1", pod_eq_bass "0.5", pod_eq_treble "0"
     , pod_dist_switch "<1>" ]
-- Synchronize the pod clock with Tidal
d9 $ s "pod" <| pod_tap_tempo "1*4"
```



## Hardware setup

![reamp_setup](/Users/tgrund/Development/tidalcycles/TidalPOD/concept/reamp_setup.png)

Used hardware: 

- Line6 POD 2.0
- Palmer PAN 01
- Focusrite Scarlett 4i4 

