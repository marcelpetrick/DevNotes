# 20220614 Qt Dev Con - day 1

## Qt 6.3 and beyond? - Maurice Kalinowski
* oreview on Qt with web assembly
* qt quick compiler ist becoming better in terms of performance
* Qt Speech (text to speech)
* physics/collision
* Multimedia: 3d audio possible again; before problem with codecs
* http server: new in qt 5.12; big feedback; small thin layer as plan; but qt did not know what to do with that?
* qt location: was gone in Qt6, but how to bring it back? in the way of Qt5 or reduced to the basic parts?
* qt vnc (?)
* debian: Qt6 is now inside debian 11, therefore also in ubuntu..; libqt6
* android mobile

* he says "cute" for Qt; 8-10 yers availability for Qt6

* Strengthen embedded, connected first, accelerate design/develop/test, adaptation to new android versions and features faster
* qt language server support (for qt creator): 
* how to make it easier to connect to webservers? REST current, GraphQL (?), protobuf support is coming in Qt6
* Qt learning portal will be imoroved
* conan and vcpackage as package manager: conan has now qt-packages

## questions:
* qt api is stuck in cpp11? qt5 with cpp98 in mind, qt6 with 11: problem with existing projects which can't upgrade the compilers
* analysis what to do with cpp20 is underway: blogpost coming

