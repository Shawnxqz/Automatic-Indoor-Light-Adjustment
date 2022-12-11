# Automatic indoor light adjustment
__Course :__ 12-778 Sensors, Circuits, and Data Infrastructure and Management for Infrastructure (Fall 2022)<br />
__Team Members :__ Luna Kim, Aoran Fu, Xuanqi Zheng, Yide Liu

## Introduction
### Abstract
Living and studying as a CMU student is not easy. There are some students studying in some areas of CMU campus late at night, and the light from the CMU building is never turned off. For the student’s productivity and visual comfort, it is important to provide proper light intensity in the study area. However, most of the lights in the building are too bright or too dimmed and some students feel uncomfortable. In this project, we propose the lighting intensity control system for human visual comfort and productivity improvement based on the occupant’s position. The light intensity sensor was chosen for the key sensor. The smart lighting feature was used for the testing, and 300 lux was chosen for the lighting control threshold. The algorithm was designed based on the distance of the sensor from the lighting source. The result shows that the lighting intensity is successfully adjusted based on the distance. However, it cannot reach the human visual comfort threshold because of the technical issue. 

### Goals
Goals
In this project, the light intensity of the smart lighting feature was controlled based on the occupant’s distance from the light intensity. The project’s goals will be as following bullets

1. Controlling the light intensity based on the sensor position (occupant’s position)
2. Developing the decision-making process that automatically adjusts the light intensity to meet the standard for reading and writing





## Overall progress
Assemble the Raspberry pi pico and the light intensity sensor to react the light intensity
Programming the algorithm that could control the light bulb based on the surrounding light intensity 

To achieve these goals, we design the pico and several experiments as follows.

Part 1.
> - Assemble the Raspberry pi pico and the light intensity sensor for measuring the light intensity around the sensor and the target light feature.
> - Check that the light intensity could be changed based on the surrounding lighting using a small diode.

<div align=center>
<img width="500" alt="5a326d726529b1df2dbc83ff63d7998" src="https://user-images.githubusercontent.com/89351724/205567257-1b542461-da29-4c81-9425-f2beaa0de7b6.png"><br />
<b>Figure 1 &ensp; Assembled hardware system</b>
</div>

Part 2.
> - Connecting the assembled hardware with the bulb and setting up the threshold for human visual comfort for reading and writing.
> - Determine the light intensity could meet the set threshold.

### coding progress
Part 1.
> - Set up the hardware and check the LED can be adjusted based on the surrounding light input from the light intensity sensor.

![bb460e674bc9f9fcb67e830d11b4257](https://user-images.githubusercontent.com/89351724/205567856-e9416adf-767d-4f40-95fe-769122ce1f85.png)

Part 2. 
> - Connecting the hardware to the bulb and testing the bulb can react to the surrounding light intensity.

![f36382bf20ebac22ee5efe95ec4cf05](https://user-images.githubusercontent.com/89351724/205568004-12d7b0fc-9fd0-46e6-bc8f-4f5b8fa1e1a9.png)

### Problems Encountered

In this project, we encountered a lot of questions which are not only theoretical
but also pratical.


__Theoretical__
1. At first, the physical stimulus of our project is luminous intensity.
Therefore, the input signal is the luminous intensity. And then
photodiode transfer it to photocurrent. In this process, we can not
figure out how to quantify this process. We only know it exists a linear
expression, but we cannot find the mathematical function of our
photodiode.
2. In addition, it uses AMP to transfer the current signal to voltage
signal. We also do not know how the voltage signal transfer to the
intensity value shown in our screen.

<div align=center>
<img width="500" alt="205569894-2104cc8a-a4bf-4e8a-9c2c-df5ad308b49b" src="https://user-images.githubusercontent.com/113749822/206890007-8d99f4cc-c1c7-4ed2-b5cb-c7dcc6f6294f.png"><br />
<b>Figure 2 &ensp; Photocurrent vs. illuminance</b>
</div>

__Practical__
1. We find a “huesdk” code file in Pico, which can send the instruction to
hue bridge directly in Pico. Due to its large size, we cannot download
it in Pico. So could we have method to enlarge the storage space of
Pico?

### Future Plan
To overcome difficulties and make the control algorithm more robust, further experiment below is needed.

1. Lighting control algorithm optimization for more effective and sensitive control.
2. Add correlated color temperature as an input variable for human visual comfort by providing a better lighting environment for working and studying.
3. Improve the algorithm to detect the exact distance between each light feature to the sensor for adjusting each lighting feature's light intensity independently. 

## Methodology
### Phenomena of Interest
We want to measure the light intensity in order to control the light
intensity within a specific range at different position by adjusting the
brightness of the light source. Therefore, we need to describe the
characteristics of visible light.


__Visible Light__

The physical stimulus of our project is artificial light source. Since
light is a type of electromagnetic radiation, it has the features of
electromagnetic waveform which is a kind of periodic function. 
Light with different color has different wave length, which determines
the period of light waveform (Figure 3). The artificial light source of
our project is LED white light, which contains the primary colors -
red, green, and blue. The wavelength interval of visible light is shown
below (Figure 4).

<div align=center>
<img width="500" alt="waveform" src="https://user-images.githubusercontent.com/113749822/206889399-210704ae-51ae-4276-94a1-d83b048e214a.png"><br />
<b>Figure 3 &ensp; Waveform of electromagnetic radiation</b>
</div>
<br />

<div align=center>
<img width="500" alt="wavelength" src="https://user-images.githubusercontent.com/113749822/206889408-e4c66617-40d1-49e5-9fc7-450ab811b339.png"><br />
<b>Figure 4 &ensp; Wavelength interval of visible light</b>
</div>

From the specification of our light intensity sensor, we learn that the
upper limit of wave length that the sensor can detect is 560 nm, which
means that red light cannot be detected, and only green and blue light can
be measured. During the experiment in our project, we need to adjust the
light intensity. Increasing the amplitude will increase the intensity of light
while decreasing the amplitude will get the opposite effect. However, the
wavelength of the light will not change because we do not plan to change
the color of light.


### Measurement
(1)Light intensity:

We plan to use BH1750 light intensity sensor to measure the light
intensity at the position of our testing object. The goal of our project is
to control the light intensity measured by the sensor within a range
that makes human’s eyes comfortable for studying, reading, etc. We
will adjust the brightness of light source by coding to control the light
intensity measured by sensor within the specific range at different position. The light intensity is recorded using the unit of lx (lux). Lux
is the unit of illuminance (luminous flux per unit area). It is equal to
one lumen per square meter.
Illuminance can be expressed as：
<div align=center>
<img width="72" alt="intensity1" src="https://user-images.githubusercontent.com/113749822/206890957-fb5b9c71-9aeb-4997-ac12-84e6b3dede68.png">
</div>
  
E: light intensity - illuminance  
Φ: luminous flux - the quantity of light emitted by a light source  
A: area
  
The intensity of light measured by the light sensor can be defined by
the equation below:
<div align=center>
<img width="85" alt="intensity2" src="https://user-images.githubusercontent.com/113749822/206890971-534ba8ab-966e-4b22-91b6-88e2a14b331e.png">
</div>
  
A: amplitude  
d: distance between sensor and light source  
  
From the equation, we can see that the intensity of light will increase
if we increase A or decrease d.

(2)Human visual comfort:

control threshold, what is it, etc.
Light Level or Illuminance is the total luminous flux incident on a
surface per unit area. The outdoor light level is approximately 10000
lx on a clear day. In a building in the area closest to the windows the
light level may be reduced to approximately 1000 lx. In the middle
area it may be as low as 25 - 50 lx. Additional lighting is often
necessary to compensate low levels.
According the information on the internet, the minimum illuminance
is 50 lx for walls and 30 lx for ceilings. Earlier it was common with
light levels in the range 100 - 300 lx for normal activities. Today the
light level is more common in the range 500 - 1000 lx - depending on
activity. For precision and detailed works the light level may even
approach 1500 - 2000 lx. The optimal illuminance for focused
activity (e.g., reading, studying or working) would be 300 - 500 lx.
Therefore, we need to control the light intensity measured by the
sensor within the range of 300 – 500 lx by adjusting the brightness of
light source through programming.

(3)Distance:

We will change the sensor to different position in order to simulate the
real condition that people sit at different place. Changing position will
also change the distance between the sensor and the light source. We
can use a tape measure to measure the distance. Then, we can find the relation between distance and the
brightness of light source.

### Sensor(s) Used
Illuminance measurement with BH1750 digital Ambient Light Sensor model

The aim of this project is to measure the environment luminous intensity.
For measuring luminous intensity, this module use photodiode, which can
produce photocurrent when this diode exposes to the light. Photodiode
can produce more photocurrent with the increase of light intensity. This
sensor is possible to detect min. 0.11 lx, max. 100000 lx.

#### Sensor characteristics 

<div align=center>
<img width="350" alt="sensor" src="https://user-images.githubusercontent.com/113749822/206890183-4189a7d0-3514-44ca-8eb0-00b8e7c80932.png"><br />
<b>Figure 5 &ensp; BH1750 digital Ambient Light Sensor</b>
</div>
<br />



> - 2.4 ～ 3.6 v Vcc voltage(typically 3.3v)
> - Operating temperature -40～85 ℃
> - Peak Wave Length 560 nm 
> - Detection range 1 - 65535 lx (actually min. 0.11 lx, max. 100000 lx)
> - H-Resolution Mode Measurement Time 120 ms 
> - Measurement Accuracy 1.2 times
> - Body size 3.0mm * 1.6mm * 0.75mm

Hue bridge:
It is controller to control two LED lights, which can control their light
remotely.

### Physical Principle

Light intensity:

There are several measures of light known as intensity. In our project, we
concentrate on luminous intensity (unit lux). In photometry, luminous
intensity is a measure of wavelength-weighted power emitted by a light
source in a particular direction, per unit solid angle. It is also a
standardized model of sensitivity of human eye. In different working
environment, human perception to acceptable luminous intensity is
different. For an instance, the range of home lighting is 30 to 300
lux(human eye comfort range is 100-150 lux based on different people).
However, the office desk lighting range is 100-1000 lux and the most
comfortable range is 500-600 lux.(eye sensitivity)


### Signal Conditioning and Processing

We want to control the light to be able to responsible to the lower or
higher environmental luminous intensity, which can adjust its intensity to
influence the environment intensity. To achieve this goal, we set a
threshold for the light intensity, which would trigger the lights. If the
luminous intensity is smaller than 35, then the light will increase its light
intensity until reach the lower bound. If the luminous intensity exceeds
55, then the light will decrease its light intensity until reach the upper
bound. 

To do this, we first use Pico to read the measure data in sensor and then
send it to the Adafruit website. Then we use another laptop to subscribe
this data and use them to compare with the threshold. Each time, we will
decrease or increase the light source intensity 20 lux under different
condition. Then we send istructions to the hue bridge and set the light
intensity to each led light.





## Experiments and Results

After the BH1750 sensor was installed, we performed simple test by
using flashing light or blinding it by a coverage. It performs very well and
response instantaneously. 
Then we test whether the hue bridge can control the Led lights normally
by using official app to change the light intensity. The test is good. Then,
we find the ip address of the hue bridge(http://10.0.0.78/debug/clip.html)
and use this website to visit hue bridge directly to send istructions to
lights. 
After that, we build connection between Pico with BH1750 sensor and
Adafruit website. Then we use another laptop to receive this data and
then send instructions based on this data to change light source intensity.
Due to the limitation of uploading rate of data (1 time / second) and the
limitation of downloading rate of data (1 time / second), so LED lights
cannot adjust their intensity quickly. However, the whole trend is correct
and the result of experiment is acceptable. The light does increase its light
intensity automatically under dark environment and will decrease its light
intensity under bright experiment.

### Demo Video


https://user-images.githubusercontent.com/89351724/206880433-324394b1-912e-4b32-96e6-a1842dab914a.mp4

## Evaluation of light system 
<div align=center>
<img width="800" alt="923372e8a6e9532922094e319679cef" src="https://user-images.githubusercontent.com/120152014/206883469-5eb7d769-3373-4575-a3d6-c70cb85308d6.png">
</div>

In this project, the light does can change its light automatically in proper distance. However, it takes 10 seconds to adjust its intensity from the minimum intensity (0) to the maximum intensity (254). During this period, it doesn't reach the threshold (human eye comfort range). We define the system score 0% when it takes 10 seconds to reach the threshold. In our system, it always take 5 seconds to reach the equilibrium, so it score 50%. There are two limitations here. The first solution is improving the efficiency of our algorithm. At first, when the light intensity detected by the sensor is higher (lower) than the threshold range, our light will increase (decrease) its intensity a certain number. However, now we will compare the detected data to the threshold. If the difference is too big (50 or 100), we let the light decrease (increase) more. When the difference is small, it will decrease (increase) less. Now, we only need three seconds to reach threshold, which means its score is 70%. The second solution is increasing the uploading and downloading speed of Adafruit. The mechanism is when our computer receive one data, it will send one instructions to light and adjust its intensity. Now our computer can receive one data per second, so we need ten seconds to adjust intensity. If the speed can increase 10 data/second, it need one second to adjust. So, we need to buy the VIP of Adafruit.

## Discussion

In this project, we are trying to adjust the brightness of the smart bulb based on the surrounding light intensity. Raspberry pi pico with the light intensity sensor was used for the hardware to achieve this goal. The result shows that we can control the brightness of the smart light feature successfully. 
However, there are several limitations in this project. First, we had a technical issue. we had to adjust the threshold much lower than our goal because of the range of the available light intensity of the bulbs. In addition, the developed algorithm cannot control the single light bulb's light intensity by its distance from the bulb. We presume that we programmed the algorithm to react to the overall surrounding light intensity, so the sensor only measures average or the total light intensity of two bulbs around the sensor. To overcome these issues, the further experiment is needed.

For the future goal, we can optimize the control algorithm to sensitively react to the surrounding light intensity for better human visual comfort for working. In this optimization process, we can use not only the light intensity, but also the color temperature as an input variable for better human visual comfort. Also, we need to code the algorithm that could control multiple light bulbs individually. To achieve this goal, the possible solution is to use separate light intensity sensor per each light bulb, or we need a sensor that could visually detect the distance between the light bulb and occupant (e.g. camera) and control the light based on the measured distance and measured light intensity. Elaborating this process, we need further research on this methodology.

## Referrence
Measuring Units Light Level - Illuminance: https://www.engineeringtoolbox.com/light-level-rooms-d_708.html<br />
Recommended Lighting Levels in Buildings: https://www.archtoolbox.com/recommended-lighting-levels/<br />
Characteristics and use of photo IC diodes: https://www.hamamatsu.com/content/dam/hamamatsu-photonics/sites/documents/99_SALES_LIBRARY/ssd/photo_ic_diode_kpic9007e.pdf<br />
Human eye sensitivity and photometric quantities: https://sites.ecse.rpi.edu/~schubert/Light-Emitting-Diodes-dot-org/Sample-Chapter.pdf
