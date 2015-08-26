## What is this?
This script display some basic hardware stats: power usage, CPU status.


## Installation
Just copy the script to e.g. `/usr/local/bin` on your Banana Pi, and you are
done. Optionally adjust permissions: currently only the owner (root) can
execute it. If you want other users to run this, adjust the permissions
accordingly (e.g. `chmod 0755 hwstats` to allow everyone to use it).

As Bash cannot do float calculations, the script uses `awk` for that
(as `awk` was already installed, and `bc` was not). If you want to do
calculation by other means, simply adjust the `calc()` function at the
start of the script.


## Usage
Simply invoke the script without specifying any argument to it, and it will
spit out the stats.


## Example output

    Currently running on 5.2 V with 456.0 mA, eating 2.4 W
    CPUfreqs: 720000 / 912000, governor: ondemand, temperature: 50.6 °C
