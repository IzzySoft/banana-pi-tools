## What is this?
This script shall make it easier to get/set CPU performance values. It was
inspired by:

* [this article on linux-sunxi.org](http://linux-sunxi.org/Cpufreq)
* [CPU frequency scaling in Linux with cpufreq](https://www.pantz.org/software/cpufreq/usingcpufreqonlinux.html)

and some other pages I consulted while writing it.


## Installation
Just copy the script to e.g. `/usr/local/bin` on your Banana Pi, and you are
done. Optionally adjust permissions: currently only the owner (root) can
execute it. This is probably fine, as only root should be able to. If a
"normal user" should be enabled, better solve that via `/etc/sudoers`.


## Usage
Simply invoke the script without specifying any argument to it, and it will
list its usage instructions. Some basic examples, assuming you've followed
above installation instructions (or otherwise have the script in your `PATH`
using the name `setcpu` for it):

* Check the current settings: `setcpu get`
* Set the governor to ondemand (default): `setcpu gov ondemand` (or `setcpu governor ondemand`)
* Lover the max CPU frequency to 800 MHz: `setcpu max 800000`

Here are some recommended settings from the linux-sunxi.org article, which should
be good to our BananaPi for a responsive, but still power-saving system:

    echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
    echo 1008000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
    echo 408000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq
    echo 25 > /sys/devices/system/cpu/cpufreq/ondemand/up_threshold
    echo 10 > /sys/devices/system/cpu/cpufreq/ondemand/sampling_down_factor
    echo 1 > /sys/devices/system/cpu/cpufreq/ondemand/io_is_busy

io_is_busy=1 is essential if you want to use your sunxi device as file server.

It is recommended to always stay between 144000 and 960000 with the CPU
frequencies. Moreover, quoting the sunxi article:

> adjusting these values works in 48MHz steps [… you] can use any value in
> between min/max but have to keep in mind that the values supplied will be
> rounded down


## Safe-guards
The script has implemented some safe-guards, such as checking you do not set a
higher/lower frequency than supported or making sure io_is_busy gets only set
to 0 or 1. However, use it at your own risk – I take no responsibility for any
damage you might cause (though I'm open for "material thanks" if it helped you :)
