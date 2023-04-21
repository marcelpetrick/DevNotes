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




------------

![](img02.png)

todo: add all the screenshots
