---
phase1: dMC09v6mXK0
---
# Quadcopter
I wanted to learn more about the electronics/protocols used in a flight controller and also learn how we could achieve a stable flight.
I had a long summer ahead of me so I decided to do most of the work from scratch. First, I had to source the parts, and after deciding on the size of the frame I would be using it was a matter of looking online for compatible and suitable parts that would fit my budget. So I ended up using this parts:
- Motors: Racestar 2212 980KV
- ESC's: Racestar RS20A BLHELI OPTO
- Realacc PDB
- the F450 frame itslef
- & propellers, batteries and some extra hardware

And, if you haven't noticed, there's a crucial part missing from this list, the flight controller. To try and learn more about its operation on a quadcopter I decided to build it from scratch, hardware and software.
After some research I used these parts on the FC:
- Brains: Bluepill with an STM32F103
- IMU (gyro and accelerometer): MPU6050
- Barometer: BMP280
- Magnetometer: HMC5883
- Radio receiver: Flysky X6B
- SD card reader
- extras like a voltage regulator and status LED's

This was the result:   
*insert pick here* //self
*insert pick here* //fc on drone

Now we have all of the hardware sorted out, but it still needs the code to run and be able to control itself. This is where the real trouble started, I used C/C++ on top of the Arduino ecosystem, but for the most part I avoided using the already provided Arduino functions and ended up using registers to perform actions more efficiently. It took a little bit to figure it out, but I got the hang of it. In the end, I got a product ready to be tested and ready to have fun with.
[Flight Controller rep](https://github.com/N1etsi/STM32F1_AF_B1)

## Testing
!Warning, looking back at this, I should really have waited and tested this drone in a proper place for it, not in the middle of my living room, fortunately no injuries or major scares occurred from these tests.
After some tuning, this was the result:
[video](https://youtu.be/dMC09v6mXK0)

{% include yt_emb.html id='=page.phase1 %}


## Ground communication and station
To better monitor flight with the drone I developed a small program using Processing to display all the info transmitted from the drone to a receiver connected to a PC (using the NRF24L01 on both sides). It's a little bit unpolished but it kept track of all the user inputs and the state of the drone.
[video](https://youtu.be/KNI_z8phdf0)


## Phase 2
After these initial tests I was running out of program space on the chosen microcontroller (the fact that was programmed using the Arduino framework didn't help). Although I initially was considering upgrading it to a Blackpill (using either an STM32F401 or STM32F411) I decided to purchase an already built flight controller, with the intent of running already made software in the first place and then port my old code to this new much nicer board and continue improving the code.
The chosen flight controller was the Betaflight Omnibus F4 V3s, powered by an STM32F405 MCU.



## Future ideas
- A better ground station with communication both ways
- Include GPS guidance

