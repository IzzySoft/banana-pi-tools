## What is this?
This is a little "temperature guard", utilizing the BananaPi's user-LED to
signal heat problems.


## Installation
Just copy the `tempguard` script to e.g. `/usr/local/bin` on your Banana Pi, and
also copy the `led` and `hwstats` script there (the latter two must be in your
PATH) – that's all. Permissions are set so only the owner (root) can
execute it. This is usually fine; if you want other users to run this, I
recommend doing so via `/etc/sudoers` and not grant it globally to "all".


## Configuration
In the "configuration" section of the script, you can adjust the values for:

* `WARN`: threshold to issue a "warning signal" (LED blinks)
* `ALERT`: threshold to issue an "alert signal" (LED blinks hectically, aka "heartbeat")
* `INTERVAL`: time between checks

Temperature values have to be specified in milli-°C (e.g. "50000" for 50°C), the
interval is given in seconds. Defaults should be OK – but that depends on how
you use your BananaPi. The script checks for "sane values" (e.g. it makes no
sense to have it warn at 20°C, as temperature will always be more than that),
including "invalid values" (all must be integers) – and exits with error-level 1
if such are violated.


## Usage
You can manually start the script to see whether it works (it doesn't
"background" itself, so you will have to abort it with Ctrl-C then). To have
it run permanently, send it to background directly: `tempguard &`. To make
sure it is automatically run on boot, you can e.g. include it in `/etc/rc.local`.

When running, `tempguard` checks the temperature in the given intervals. If the
WARN threshold is exceeded, it will make the LED blink regularly. If the ALERT
threshold is exceeded, the LED will start to blink hectically, like a heartbeat.
If temperature falls below the WARN threshold, the LED will be turned off again.
