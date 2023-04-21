# 20230421 Anatomy of a Linux Device Driver

* hosted by Doulos
TODO add stuff from the invitation

* explanation about the stability of certain interfaces for each release
![](img00.png)
![](img01.png)
* note: **implement mechanism not policy**
  * no prejudging how the application is using the hardware
  * this makes the driver-implementation quite simple

![](img02.png)
* module license is also needed to be adde

![](img03.png)
![](img04.png)
* kernel offers different frameworks to help: like regmap and pinctrl, gpiod, ..
* manxy types of hardwar are interrupt-driven and will signal if they have something to say
![](img05.png)
* linux driver model
![](img06.png)
* maximize the amount of code, which is used, shared
![](img07.png)
## How to read the driver's source file?
* recommendation: start at the bottom, not top
* initalized, registered with matching framework, then matching to, populates the device
![](img08.png)
* platform devices
![](img09.png)
![](img10.png)
![](img11.png)
![](img12.png)
![](img13.png)
![](img14.png)
![](img15.png)

