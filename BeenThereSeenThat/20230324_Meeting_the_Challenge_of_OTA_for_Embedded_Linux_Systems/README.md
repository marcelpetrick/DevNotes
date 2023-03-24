# 20230324 Meeting the Challenge of OTA for Embedded Linux Systems

## requirements for an OTA system
* security & integrity
* integration
* usability
* fault tolerance and recovery
![](img000.png)

## mechanisms
![](img001.png)
* image based
  * block based - update all the blocks in the current partition - just treat as set of data which has to be written into the device
* file based
  * new app packages or new containers (rather than using single files, the stuff for each particular use case is put into a restricted environment)

## challenges
![](img002.png)

