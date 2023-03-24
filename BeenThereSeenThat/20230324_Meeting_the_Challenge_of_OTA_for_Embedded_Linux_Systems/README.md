# 20230324 Meeting the Challenge of OTA for Embedded Linux Systems

* hosted by Doulos

## requirements for an OTA system
* security & integrity
* integration
* usability
* fault tolerance and recovery
![](img00.png)

## mechanisms
![](img01.png)
* image based
  * block based - update all the blocks in the current partition - just treat as set of data which has to be written into the device
* file based
  * new app packages or new containers (rather than using single files, the stuff for each particular use case is put into a restricted environment)

## challenges
![](img02.png)
* fualt recovery: per package or per container
![](img03.png)
* partition approach
* or like early android-devices: with an recovery partition
![](img04.png)

## differnt ones: RAUC, mender, SWUpdate, swupd, OSTRee
![](img05.png)

## Toradex part
* torizon Core can be used on several platforms
* Torizon Docker containers
* running on a Toradex module (or something else)
![](img06.png)
* runtime daemon as update client
* functionality is part of the OTA system; has special requirements for power-down
* 


![](img07.png)
