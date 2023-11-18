# OTA Updates and Fleet Management at Scale

## hosts
* Eric Johnson (Memfault)
* Noah Pendleton (Memfault)
* Philip Johnston (Embedded Artistry)
* David Shoemaker (Tesla)

"Nothing worse than a broken OTA solution."

### When is the right moment to integrate OTA into your workflow?
* PJ: first functionality, then OTA. But this results in delayed shipments
* Should be the first feature to be developed, so maximum number of iteration cycles can be used for that feature
  * Also checks hardware design quite early: if space is sufficient, etc.
  * Especially small teams underestimate the amount of work that needs to be spent; own experience shows that firmware developers usually have no knowledge in the OTA domain
  * Lots of complexity comes in the backend engine
  * What to do with 10k devices, which want to update all at once
* There has to be a way that the bootloader can know that this image is safe and confirmed and won't brick the device
* Security in updates:
  * Integrity of the image (ensuring it's not corrupted or compromised), so another layer like signing is needed (image signed, device checks - either bootloader or cryptographic space), key management therefore becomes something to care about now
* Factory images - to revert everything and go back to a working state
* Fallback mechanisms and strategies: signature verification, rollback (atomic) in case of flash-error, crash-detection (counting)
