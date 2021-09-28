盎ˇㄓㄤˊ---
title : 🖥️Digitize Images
date : 2021-09-27_Mon 16:27
aliases : []
---
Source Type :: #📥/📄 <br>
Source Author :: [[@賴祐吉]]<br>
Note Type :: #📝 <br>
Topics :: [[🖥️Computer Graphics MOC]]<br>
Parent Link :: [[]]<br>

---
# 🖥️Digitize Images

## Ideal Images vs Digital Images
### Ideal Images
+ The information stored in images is often **continuous** in nature
+ consider the **ideal photograph**
	- It captures the intensity of light at a **particular set of points** coming from a **particular set of directions** (called irradiance（輻照度）)
	- The intensity of light arriving at the camera can **be any positive real number**, and it **mostly varies smoothly over space**
	- Where so you see spatial（空間上的） discontinuous in a photograph？

### Digital Images
+ Computers works with **discrete（離散）** pieces of information.
+ Digitize a continuous image
	- Break the continuous space into small areas - pixels
	- Use a single value for each pixel - the pixel value (no color, yet)
	- No longer continuous in space or intensity
+ This process is fraught with danger, as we shall see

![[digitize.png]]


## Issues
### Discretization Issues
+ Can only store a **finite number of pixels** -> spatial space
	- Choose your target physical **image size**, choose your **resolution** (pixel per inch, or dots per inch (dpi)), determine **width/height** necessary
	- Storage space goes up with square of resolution
		* 6000dpi has 4x more pixels than 300dpi
+ Can only store a **finite range of intensity values** -> color space
	- Typically referred as **depth** - number od bits per pixel
		* Directly related to the **number of color** available and typically little choice
		* Most common depth is 8, but sometimes see 16 for grey
	- Also concerned with the minimumand maximum intensity - dynamic range

### Perceptual Issues
+ Spatially, human can discriminate about **1/2 a minute of arc**
	- At fovea, so only in center of view, 20/20 vision
	- At 0.5mm about 0.1mm ("Dot pitch" of monitors)
	- Sometimes limits the required number f pixels
+ Humans can discriminate about **8 bits of intensity**
	- "Just Noticeable Difference" experiments
	- Limit the required depth for typical dynamic ranges
	- Actually, it's 9-10 bits, but 8 is far more convenient
+ But, when **manipulating images** much **higher resolution** may be required

### Intensity Perception
+ Humans are actually tuned to the **ratio of intensities**, not their absolute difference
	- So going from a 50 to 100 Watt light bulb looks the same as going from 100 to 200
	- So, if we only have 4 intensities, between 0 and 1, we should choose to use 0, 0.25, 0.5 and 1
+ Most computer graphics ignores this, **giving poorer perceptible（可感知的） intensity resolution at low light levels**, and the better resolution at high light levels
	- It would use 0, 0.33, 0.66, and 1

### Dynamic Range
+ **Image depth** refers to the number of bits available, but not how those bits map onto intensities
+ We can use those bits to represent a **large range at low resolution**, or a **small range at high resolution**
+ **Common display devices** can only show a limited dynamic range, so typically we fix the range at that of the display device and choose high resolution

### More Dynamic Range
+ Real scenes have **very high and very low** intensities
+ Humans can see **contrast（對比）** at very low and very high light levels
	- Can't see all levels all the time - **use adaptation to adjust**
	- Still, high range even at one adaptation level
+ **Film** has **low dynamic range** ~ 100:1
+ **Monitors** are even worse
+ Many ways to deal with the problem

![[High Dynamic Range Imaging.png]]
![[Tone Mapping.png]]

## Display on a Monitor
+ When images are createdm a **linear mapping** between **pixels and intensity** is assumed
+ Monitors, however, do not work that way
	- For **analog monitors**, the pixel value is converted to a voltage
	- The voltage is used to control the **intensity of the monitor pixels**
	- But the voltage to display intensity is **not linear**
	- Similar problem with other monitors, **different causes**
+ The outcome（結果）: A linear intensity scale in memory does not look linear on a monitor
+ Even worse, different monitors do different things

### Gamma Control
+ The mapping from voltage to display is usually an **exponential function**: $$I_{display} \propto I_{to-monitor}^\gamma$$
+ To correct the problem, we pass the pixel values through a **gamma function** before converting them to the monitor $$I_{to-monitor} \propto I_{image}^\frac{1}{\gamma}$$
+ This process is called **gamma correction**
+ The parameter, $\gamma$, is controlled by the user
	- It should be matched to a particular monitor
	- Typical values are **between 2.2 and 2.5**
+ The mapping can be done in hardware or software