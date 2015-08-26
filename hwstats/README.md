## What is this?
This script display some basic hardware stats: power usage, CPU status.


## Installation
Just copy the script to e.g. `/usr/local/bin` on your Banana Pi, and you are
done. Optionally adjust permissions: currently only the owner (root) can
execute it. If you want other users to run this, adjust the permissions
accordingly (e.g. `chmod 0755 hwstats` to allow everyone to use it).


## Configuration
CPU min/max temperature values seem to be unreliable, at least on a Banana Pi M1
running Raspian (I doubt the CPU ever was down to -144.7 °C or up to 264.8 °C).
As these values might be better on other Bananas (or with other distributions),
you can decide whether to include them setting `TEMPMINMAX` to the appropriate
value. Default is `TEMPMINMAX=0`, i.e. not to calculate/display those.

Furthermore, Bash cannot do float calculations, so the script uses `awk` for
that (as `awk` was already installed, and `bc` was not). If you want to do
calculation by other means, simply adjust the `calc()` function at the
start of the script.


## Usage
Simply invoke the script without specifying any argument to it, and it will
spit out the stats.


## Example output
Output with `TEMPMINMAX=0`:

    Currently running on 5.2 V with 456.0 mA, eating 2.4 W
    CPUfreqs: 720000 / 912000, governor: ondemand, temperature: 50.6 °C

Output with `TEMPMINMAX=1`:

    Currently running on 5.1 V with 725.0 mA, eating 3.7 W
    CPUfreqs: 720000 / 720000, governor: ondemand, temperature: 50.6 °C(min/max: -144.7 / 264.8 °C)
