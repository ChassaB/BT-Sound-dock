# BT-Sound-dock
I've had a lovely original BOSE sound dock for years and still have my iPod to use with it but I wanted to add bluetooth and possibly a line in. I had a BT4 module in my parts box so I watched the various mods on Youtube and quickly found that most of them were very dodgy. Ordered a 24pin ribbon cable breakout board and when it arrived did a bunch of continuity and voltage testing alongside some chatGPT discussions. After a day of tinkering. I got the pinouts sorted and now have a working BT speaker. Clear as a bell, no hum, sense pin switchable on and off. So here are details.

The 24pin ribbon cable is exposed when you remove the iPod dock at the front of the speaker. Looking at the speaker from the front the cable is pin1 to pin 24 left to right. To be sure you are counting from the correct end there will be 16V-18V between pin 24/23 and pin 20/21.
<img width="3024" height="4032" alt="IMG_0952" src="https://github.com/user-attachments/assets/467041d3-05f0-4a63-bb62-6db05acc315a" />


There is no 5V available on any of the 24 pins so the design requires these to be generated. 5V to drive the BT module and 3.3V to operate the sense line (Provided by the iPod usually). Do not use the 3.3V on the Volume pins (9,10) as any press for volume will pull them low and turn off the speaker. I also had some ND4012DA modules in the parts bin. This module can take the 16V and provide a 5V and 3.3V output. Perfect.

<img width="3024" height="4032" alt="IMG_0954" src="https://github.com/user-attachments/assets/a91ad1c0-4f62-4f33-9260-6619e160fb73" />
<img width="3024" height="4032" alt="IMG_0955" src="https://github.com/user-attachments/assets/7f2e06aa-efef-49ee-8692-be73eae348de" />


So the pinout on the 24 pin ribbon cable is as follows.

Firewire GND       -> 23 and 24
Firewire 12V power -> 20 and 21 (actually ~16V when measured on pin 20 without any device connected)
IPod detect        -> 19 (3.3V on this pin will wake up the BOSE)
Left audio         -> 14
Right audio        -> 13
Audio GND          -> 11 and 12
Vol down           -> 10 (The volume down button on the iPod daughter board)
Vol up             -> 9  (Both of these are at 3.3V internally. Pulling to ground activates a vol change)

<img width="3024" height="4032" alt="IMG_0953" src="https://github.com/user-attachments/assets/f459cca3-981e-405d-93c2-f2624c3ccc89" />


Note: be sure to use the audio ground for the audio channels and the firewire and to power things to avoid hum etc.


