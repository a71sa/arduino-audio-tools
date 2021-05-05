# Digital output via I2S to a external DAC

Sometimes it is quite useful to be able to generate a test tone.
We can use the GeneratedSoundStream class together with a SoundGenerator class. In my example I use a SineWaveGenerator.

To test the I2S output I'm using this generated signal and write it to I2S.

For my tests I am using the 24-bit PCM5102 PCM5102A Stereo DAC Digital-to-analog Converter PLL Voice Module pHAT
![DAC](https://pschatzmann.github.io/arduino-audio-tools/resources/dac.jpeg)

 
### External DAC:

I am just using the default pins defined by the framework. However I could change them with the help of the config object. The mute pin can be defined in the constructor of the I2SStream - by not defining anything we use the default which is GPIO23

 
| DAC     |  ESP32
| --------| ---------------
| VDD     |  5V
| GND     |  GND
| SD      |  OUT (GPIO22)
| L/R     |  GND
| WS      |  WS (GPIO15)
| SCK     |  BCK (GPIO14)
| FMT     |  GND 
| XSMT     | GPIO23 


- DEMP - De-emphasis control for 44.1kHz sampling rate(1): Off (Low) / On (High)
- FLT - Filter select : Normal latency (Low) / Low latency (High)
- SCK - System clock input (probably SCL on your board).
- FMT - Audio format selection : I2S (Low) / Left justified (High)
- XSMT - Soft mute control(1): Soft mute (Low) / soft un-mute (High)

