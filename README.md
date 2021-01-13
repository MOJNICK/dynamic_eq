Dynamic equalization for pulseaudio aimed at standing wave cancelation (mainly blurry, over ampliffied bass sound)

Consider scenario when you are playing constant sound from speakers:

Fig. 1
![alt text](./audacity_eq_disabled.png)

You of course expects to hear exactly what is playing, but in reality, the sound is distorted by room characteristic.
Rooms have modes - certain frequenicies, at which sound is amplified. In peak it could be as much as 30dB.

Overview of room response characteristic for constant speaker sound:

Fig. 2
![alt text](./room_curve.png)

To fight this effect, sound damping with characteristic reverse to room response can be applied. The functionality is implemented here.

This is oryqinal equalizer gui:

Fig. 3
![alt text](./oryginal_eq.png)

And modified one:

Fig. 4
![alt text](./damping_disabled.png)

Let's create three damping filters and initialize one of them:

Fig. 5
![alt text](./damping_enabled.png)

Test functionality, by playing 120Hz tone (or other in range 108Hz to 132Hz (width parameter)):

Fig. 6
![alt text](./audacity_dynamic_eq.png)

As you can see I played sound from fig. 1 and muted it two times, which gave three 'sound regions': 1-muted-2-muted-3.

Region 1 - starts at full level and then filter attentuates it by ratio 0.88.
Muted - long enough to allow filter to recover.
Region 2 - behaves exactly like region 1.
Muted - short which allows filter to only partially recover (because room still produces sound).
Region 3 - starts at reduced level and then is attentuated.



