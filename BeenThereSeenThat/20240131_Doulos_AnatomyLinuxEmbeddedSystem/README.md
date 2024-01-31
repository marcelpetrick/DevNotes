# 20240131 Doulos - Anatomy of an embeded linux system

## agenda
* linux background
* open soruce softwar & licensing
* toolchain
* bootloader
* kernel
* filesytem
* linux distributions

## background
* Torvalds released first version of kernel 1991
* snowball effect mid 90s
* various distributions available
* uptake in servers is high
* much lower on desktop
* 70% mobile market share through android
* incresingly used for mebedded systems
* penguins associated with Linux as mascot
* ported to many architectures: ARM, PowerPC, RISC-V, ..

![](img00)
![](img01)
![](img02)

## pro'/con
* pro: architectures supported and hardware support is vast, choice of compoents
* con: skills needed, licensing
* pro: reduction of software licnesing costs: wide usage of components can improve quality
* easy to evaluate new software
* full control of the source code
* communities (plural): lots of different projects; kernel as project, bootloader is project, libraries are separate, applications, tools ..
![](img03)

## licensing
* GPL applies to the Linux Kernel an other main compnents of a Linux system
  * v2 and v3 version are different; also LGPL
* bookkeeping of used licenses
* consider license terms before using an open-source component
* no GPL, LGPL in proprietar software
* consider who is the end user
* some distribution managemnet systems can helpmanage this

## toolchain
![](img04)


-----
TODO: add notes from the recording due to interruption

## Q & A

```
Q:
    Are there real-time versions of Linux? Also open source?
A:
    Yes, there are options. You can improve Linux real-time behaviour using the RT patch. Another possibility is Xenomai. 
7:12 PM

Webinar staffto everyone

Q:
    How do you find up-to-date introductory documentation about Linux concepts and facilities? With Linux, major subsystems and interfaces come and go, or have gone, but the documentation for those old things lives on. I'd like to know how to learn definitively how things work without reading all 25 million lines of code.
A:
    Depend on what you are looking for. If you want to do application programming, a start is the man page man7. There are good books available too. If you're looking at the kernel programming side of things (driver for instance), the kernel documentation is quite well maintained: https://docs.kernel.org/. I can also suggest books later on.
7:17 PM

Webinar staffto everyone

Q:
    I'm a newbie, but if Linux is truly open-source, then why would you need a license?
A:
    Using Linux, means accepting the license term. This impose certain requirements, if you redistribute your work. What this requirements are depend on the Open Source License. 
7:19 PM

Webinar staffto everyone

Q:
    Why would you prefer Clang over gcc?
A:
    A few years ago, I'd say: clang for user space, gcc for kernel (we had no choice). Now things are not that sharps, as gcc has catched up with the clang extra feature (like the sanitizer), and we can use clang to compile the kernel. I use both, whenever possible :)
7:20 PM

Webinar staffto everyone

Q:
    Why is it not recommended to compile on the target? 
A:
    The target has limited resources/CPU power compare to the host machine... So if you're compiling a big project, it could easily takes hour.
7:21 PM

Webinar staffto everyone

Q:
    Can you run Linux on CPUs without a memory management unit?
A:
    Yes. But that's not common, and you need a lot of patches. It's not use in the industry, as far as I am aware of.
7:22 PM

Webinar staffto everyone

Q:
    Once the RT patch installed are all the sys calls reentrant ?
A:
    In fact, some RT patch functionality are now available in the recent mainline kernel. So it's a matter of kernel configuration ("fully preemptible kernel"). 
7:23 PM

Webinar staffto everyone

Q:
    why is JTAG better than KGDB for debuggers? 
A:
    Because you can put a hardware breakpoint at the very first instruction executed by the kernel. With kgdb, you need a minimum of kernel functionality running (UART...) to work. Also JTAG is less intrusive.
7:24 PM

Webinar staffto everyone

Q:
    Which are the main trace and profile tools available for Linux 
A:
    strace, ltrace, perf, ftrace, sysprof, ebpf and I'm certainly missing a few more :)
7:25 PM

Webinar staffto everyone

Q:
    Not binary compatible with what?
A:
    Sorry, could you please me give the context? 
7:25 PM

Webinar staffto everyone

Q:
    Does debugging through JTag means 3rd party tools running in the host?
A:
    yes. But this tool could also be open source, like openocd
7:26 PM

Webinar staffto everyone

Q:
    how can I verify if the RT patch is installed , say in an Ubuntu distribution?
A:
    RT patch won't likely be installed in an regular ubuntu distro. There might be some "real-time" variant of it. But the way to check is to look at the kernel configuration. 
7:27 PM

Webinar staffto everyone

Q:
    The last of the 3 standard C libraries mentioned (ulibc or something) 
A:
    Yes: I know what you mean now. glicb, uclibc etc. I come back to you on this offline, need to check the slide. Thanks
7:28 PM

Webinar staffto everyone

Q:
    Does U-boot replace Grub or does one of them call the other? 
A:
    Yes, grub is used on x86-based platform; other platforms (like ARM, RISC-V) use U-boot.
7:29 PM

Webinar staffto everyone

Q:
    By introductory documentation, I mean information on how the kernel and device-management subsystems recognize devices, organize the device tree, which operate at multiple levels. In my experience, the kernel documentation assumes the reader already knows those things. How does one find current introductory documentation? 
A:
    I take this question offline, or at the end of the webinar. Thanks.
7:29 PM

Webinar staffto everyone

Q:
    Why would it be expected that musl is slower than glibc? Does a smaller memory image mean slower? 
A:
    smaller do not mean necessarily slower (sometimes, both smaller and faster is possible). glibc is written to be fast, at the expense of the code maintainability. Meaning: it's easier to read musl code, than glibc one!
7:31 PM

Webinar staffto everyone

Q:
    Is U-boot available for x86? If so, why is it not typically used there? Inertia?
A:
    Good question, I don't know that by heart. Need to check offline, sorry.
7:31 PM

Webinar staffto everyone

Q:
    What's a minimum ROM/Flash image size/footprint range of an embedded Linux OS kernal, not including the application?
A:
    That really depends what options you enable. But you are easily in the Mb range. IIRC, our Embedded Linux class has a kernel of ~5 Mb, and ~16 Mb if we include an initramfs. Again, your mileage will vary here.
7:33 PM

Webinar staffto everyone

Q:
    What is the difference between Yocto and Menuconfig for Kernel configuration? 
A:
    Kernel configuration configure what components/feature you want for your kernel image. Yocto is a distribution builder = it builds an entire Linux distribution for you. That is the kernel image, but also the filesystem, uboot and toolchain too!
7:34 PM

Webinar staffto everyone

Q:
    What happens with the drivers in the bootloader stage? 
A:
    Once the bootloader has finished it's job (ie. jump at the first instruction of the linux kernel), then the boot loader is finished. At some point the RAM where the bootloader got loaded will be reused for other purposes.
7:36 PM

Webinar staffto everyone

Q:
    benefits/tradeoffs of compiled-in versus modules? 
A:
    compiled statically = available immediately at boot, increase kernel image size. kernel module = need to be loaded at runtime, reduce image size.
7:38 PM

Webinar staffto everyone

Q:
    So, this RT-patch is not really a "hard real time OS" is it ? It is more like soft real time, which implies all the sys lib call are NOT re-entrant. Is this correct ?
A:
    hard real-time OS means nothing really. What matter is: a) what is my latency requirements and b) what is the consequences of missing the deadline. RT patch improve the latency requirements (and determinism). 
7:39 PM

Webinar staffto everyone

Q:
    Do embedded systems use systemd? 
A:
    yes, more and more these days.
7:39 PM

Webinar staffto everyone

Q:
    can you load a small kernel on top of a larger base kernel?
A:
    not sure what you mean here. It's possible to use containerization technology. The converse is possible: use a smaller kernel (hypervisor) to run one or more kernel. 
7:40 PM

Webinar staffto everyone

Q:
    Why do you want to change the location of the Filesystem 
A:
    This is typical during development. First we're using NFS/TFTP during development, then perhaps SD-card with Hardware proto and when we move closer to production, flash storage.
7:41 PM

Webinar staffto everyone

Q:
    Is it possible to have an ethernet or uart functionality during u-boot? 
A:
    Certainly.
7:41 PM

Webinar staffto everyone

Q:
    Is it possible to use a menu to select what to load as linux kernel image when the u-boot loads? 
A:
    We don't have a menu like grub, but you can interact with Uboot through the interactive shell. And choose to boot other image. You can even create recovery scenarii.
7:42 PM

Webinar staffto everyone

Q:
    Do you need to have some device driver's configurations when you compile u-boot? 
A:
    Uboot come with a "menu config", where you can configure the functionality you want. But your guess is correct. Actually, Uboot is integrating some of the driver coming from Linux.
7:44 PM

Webinar staffto everyone

Q:
    >> hard real-time OS means nothing >>really. Strong disagree with that statement. Talk to folks who develop code for industries such as Avionics....instead of just "opining" about abstract concepts!
A:
    I've been developing safety critical system (airbones and medical). So here you have deadline and consequences. If you mean by "hard real time" that missing the deadline kills people, or causes big damages, I'm with absolutely with you. Unfortunately, hard real time is used often for applications that do not have such stringent requirements
7:47 PM

Webinar staffto everyone

Q:
    How do you load U-Boot on the board? 
A:
    This question is answered by the board manual (each board has different requirements / way to load U-boot in the first place).

```
