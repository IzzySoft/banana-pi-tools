## What is this?
This script display some basic hardware stats: power usage, CPU status.


## Installation
Just copy the script to e.g. `/usr/local/bin` on your Banana Pi, and you are
done. Optionally adjust permissions: currently only the owner (root) can
execute it. If you want other users to run this, adjust the permissions
accordingly (e.g. `chmod 0755 hwstats` to allow everyone to use it).


## Configuration
CPU min/max temperature might not be that useful (as it just shows the range
the sensor covers, and not – as one might have expected – historical low/high:
-144.7 °C resp. 264.8 °C are unlikely values on normal use). So you can decide
whether to include them setting `TEMPMINMAX` to the appropriate value. Default
is `TEMPMINMAX=0`, i.e. not to calculate/display those.

Furthermore, Bash cannot do float calculations, so the script uses `awk` for
that (as `awk` was already installed, and `bc` was not). If you want to do
calculation by other means, simply adjust the `calc()` function at the
start of the script.


## Usage
Simply invoke the script without specifying any argument to it, and it will
tell you how to use it. Basically, you can have the full details spit out in
human-readable format (`hwstats all`), query single values in human-readable
or in raw formats. The latter is useful for scripting, e.g. to be combined
with the user-LED script:

    temp=$(hwstats tempraw)
    if [[ $temp -gt 60000 ]]; then    # > 60°C, have LED flicker hectically
        led heartbeat
    elif [[ $temp -gt 50000 ]]; then  # 50°C < temp < 60°C, have LED blink
        led blink
    else                              # temp ≤ 50°C, shut off LED
        led none
    fi

Put that as script in a cron job to be run e.g. every minute, and you've got a
nice little temperature watchdoc – visually alerting you when things go hot. Of
course, you might prefer different thresholds – fee free to adjust :)


## Example output
Output of `hwstats all` with `TEMPMINMAX=0`:

    Currently running on 5.2 V with 456.0 mA, eating 2.4 W
    CPUfreqs (MHz): 720/912, min/max: 400/912, governor: ondemand, temperature: 50.6 °C

Output with `TEMPMINMAX=1`:

    Currently running on 5.1 V with 725.0 mA, eating 3.7 W
    CPUfreqs: 720/720, min/max: 400/912, governor: ondemand, temperature: 50.6 °C (min/max: -144.7 / 264.8 °C)
