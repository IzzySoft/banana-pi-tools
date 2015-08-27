## What is this?
This repository holds some little helpers to make your life with your Banana Pi
easier. I might add more stuff to it in the future, and I also welcome
contributions from "fellow bananas" – credits will be given, of course.


## What tools are contained?
Just check the sub-directories, where each "helper" should be provided with its
own `README` file. For now, we have:

* **hwstats:** displays some basic hardware stats: power usage, CPU status
* **setcpu:** make it easier to get/set CPU performance values
* **tempguard:** utilizing the BananaPi's user-LED to signal heat problems
* **userLED:** allows you to easily control the BananaPi's user LED


## License
I will keep these little things open source for all to use. Currently I chose
to put it under GPLv2.


## How to contribute?
### If you're familiar with Git and Github
The usual way: Clone this repo, add your contribution, send a pull request.

### If you're not familiar with Git/Github
Multiple choices here:

* make yourself familiar with both. It's worth it :)
* make yourself at least a Github account, then open a new "issue" and attach your contribution
* send me your contribution by mail


## Other interesting BananaPi projects on Github
The following is far from being a complete list – it's just a collection of projects
I thought might be useful even for non-programmers:

### Monitoring
* [zabbix-banana-pi](https://github.com/harryklein/zabbix-banana-pi): Monitor your BPi using
  [Zabbix](http://www.zabbix.com/): CPU speed/temperature, voltage of power supply
* [RPi-Monitor](https://github.com/XavierBerger/RPi-Monitor): another monitor,
  originally written for RasPi, but meanwhile adjusted for Bananas as well (see e.g.
  [RPi-Monitor on sunxi](http://www.lemaker.org/forum.php?mod=redirect&goto=findpost&ptid=8137&pid=83467)
  and [sunxi adjustments for RPi-Monitor](http://forum.armbian.com/index.php/topic/155-testers-wanted-sunxi-adjustments-for-rpi-monitor/))
* [RaspMonitor](https://github.com/DreamedAtlas/RaspMonitor): A web monitor for
  the Raspberry Pi and other similar platform like Cubie Board or Banana Pi (lacks docu)
* [banana-panel](https://github.com/harmon25/banana-panel): Fork of Raspcontrol for the Banana Pi
* [axp209_bananaPI](https://github.com/zoon81/axp209_bananaPI): shell script to
  read some information about power usage on bananaPI. Requires `i2cset` (`apt-get install i2c-tools`),
  see [Hardware-Libre](http://hardware-libre.fr/2014/11/banana-pi-axp209-battery-power-monitoring/)
* [micropc](https://github.com/marines/micropc): another script collection for Pis.
  Currently holding temperature monitoring using RRD.

### Misc collections
* [learning-banana-pi](https://github.com/CMDann/learning-banana-pi): Code
  examples from the book. For non-programmers: includes a shell script to control GPIOs
* [Schnelleinstieg_Banana_Pi](https://github.com/mschlenker/Schnelleinstieg_Banana_Pi): similar
  stuff for Germans: code snippets, additional details, sketched circuit diagrams, etc.
* [bananapi-memo](https://github.com/annbigbig/bananapi-memo): collection of howtos and infos
* [XBananaMC](https://github.com/XBananaMC/XBananaMC): get XBMC (now: Kodi) running on your BPi
