# OTA Updates and Fleet Management at Scale

## hosts
* Eric Johnson (Memfault)
* Noah Pendleton (Memfault)
* PHilip Johnston (Embedded Artistry)
* David Shoemaker (Tesla)

"Nothing worse than a broken OTA solution."

![](img00.png)

### When is the right moment to integrate OTA into your workflow?
* PJ: first functionality, then OTA. But this results in delayed shipments
* should be the first feature to be developed, so maximum of of iteration cycles to use that feature
  * also checks hardware design quite early: if space is sufficient, ..
  * especially small teams underestimate the amount of work which has to be spent; own experience tells that firmware developers have usually no knowledge in the OTA domain
  * lots of complexity comes in the backend engine
  * what to do with 10k devices, which want to update all at once
* there has to be a way thtat the bootloader kan know that this image is safe and confirmed and won't brick the device
* security in updtes:
  * integrity of the image (not corrupted or compromised), so another layer like signing is needed (image signed, device checks - either bootloader or cryptographic space), key management therefore becomes something to care now for
  * 
