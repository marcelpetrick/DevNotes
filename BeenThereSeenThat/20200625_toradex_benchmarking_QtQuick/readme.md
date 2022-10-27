20200625 toradex

benchmaring Qt on uC

- company: sequality
- no window managers
- Qt open source edition was used for benchmarking
- would also run with the commercial edition

fullhd graphics with opacity and animations

also on their webpage
automotive off the highway

overdraw analysis
batches
flamegraph
- tools from Qt framework for performance anaylsis?

render graph analysis for qt quick
- overdrawing can be shown: helöpful to find out how clipping can be improved
- 

- effectively set the visible property to false, if not needed!
- analyzing batches: which parts are rendered in one shot? labels and images
- flame graph gives some overview of the execution time of each method (with call stack)

valuable optimizations:
- route simulation took quite long, so they optimized the routing
- QtQuick compiler does just help with startup-performance (surprising)


benchmarking:
even problems with black screen (empty application)
- most were limited to 60 fps (see picture 3)
- adding background picture to mx6 drops performance already to 30!
- first optimization was already: merging the layers with photoshop
- iMx8 faster than RPi4!
- way better than iMx6 (even quad)
--> what impact for user experience?

- if the route is prerendered by some intel nuc, then the graphics performance grows
- imx8, imx6, imx6 quadcore, intel nuc

no code optimiatzions raised fps from 24 to 60 fps (for almost all platforms)
- optimizign qml raised it even higher: even while navigating 40 fps on iMX8
- worse performance for mapboxgl - lower fps; unknoqwn reasons

i.Mx6 Quad better than DL at FullHD

- tool from their: embedded system browser monitor (sequality offers it)
- stefan larndorfer sequality
pasi keränen, senior product owner graphics and UI:
Qt Quick 3d & Benchmark application

!!!!!!!!!!!!!!!!!1
selecting the right hardware is crucial to achieve the goals
!!!!!!!!!!!!!!!!!!

new technology: qt quick 3d

qml language scene graph
efficient rendering of ui elements 

how to figure out hardware platform before selecting it?
Qt Quick 3D Benchmarking Application: can be fo0und at qt.io ... check tora12.png; is also open source

!!!!!!!!!!!!!!!!!!
content is king, in 3d
!!!!!!!!!!!!!!!!!!

try facsimile content out on a platform to get confidence

so for Qt6 they try to introduce a new rendering HW-interface, affecting 2d and 3d
- vulkan is future in embedded systems; less cpu-usage

- how to cache in the qt quick app?
- there is a flag or feature; also mentioned in the officla docu; guy could not name it directly


my own additions:
------------------
https://doc.qt.io/qt-5/qtquick-bestpractices.html
https://doc.qt.io/qt-5/qtquick-performance.html
https://bugreports.qt.io/browse/QTBUG-79485
https://doc.qt.io/QtForDeviceCreation/qtee-custom-embedded-linux-image.html
