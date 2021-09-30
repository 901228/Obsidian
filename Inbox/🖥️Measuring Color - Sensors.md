---
title : 🖥️Measuring Color - Sensors
date : 2021-09-30_Thu 20:51
aliases : []
---
Source Type :: #📥/📄 <br>
Source Author :: [[@賴祐吉]]<br>
Note Type :: #📝 <br>
Topics :: [[🖥️Computer Graphics MOC]]<br>
Parent Link :: [[🖥️Color and Light]]<br>

---
# 🖥️Measuring Color - Sensors
+ Expressed as **a graph of sensitivity($\rho$)（sensor對光的靈敏度） vs. wavelength($\lambda$)** => $\rho(\lambda)$
	- For each unit of energy at the given wavelength, how much voltage/impulses/whatever the sensor provides
+ To compute the resonse, take **the integral** $$\int [\ \rho_k(\lambda)\ E(\lambda)]d\lambda$$
	- $E(\lambda)$ is the **incoming energy** at the particular wavelength
	- The integral multiplies **the amount of energy at each wavelength** by **the sensitivity at that wavelength**, and sums them all up

## Example: A "Red" Sensor
### Sensor Sensitivity
![[red_sensor_spectrum.png]]
This sensor will **respond to red light**, but **not to blue light**, and **little to green light**.

### Sensor Respoense
![[red_sensor_response.png]]

| high response                       | low response                         |
| ----------------------------------- | ------------------------------------ |
| ![[big_response_of_red_sensor.png]] | ![[tiny_response_of_red_sensor.png]] |
當sensor的偵測波長範圍與被偵測光的波長範圍接近時，得到的response相對較高；反之，若兩者範圍較遠時，得到response相對較低。

## Changing Response
+ How can we change a **"white"** sensor into a **"red"** sensor ?
	- 套紅色遮罩
+ Can we change a **"red"** sensor into a **"white"** sensor ?
	- 不行
+ Assume for the moment that your eye is a **"white" sensor**. How is it that you can see a **"black light" (UV)** shining on a surface ?
	- Such surfaces are **fluorescent（螢光的）**
	- Your eye isn't really a white sensor - it just approximates one

## Seeing in Color
The eye contains *rods* and *cones*