## What is this?
This script allows you to easily control the BananaPi's user LED – without
remembering …

* the `/sys/…` path
* available switches
* how to do it


## Installation
Just copy the script to e.g. `/usr/local/bin` on your Banana Pi, and you are
done. Optionally adjust permissions: currently only the owner (root) can
execute it. This is probably fine, as only root should be able to. If a
"normal user" should be enabled, better solve that via `/etc/sudoers`.


## Usage
Simply invoke the script without specifying any argument to it, and it will
list its usage instructions. Some basic examples, assuming you've followed
above installation instructions (or otherwise have the script in your `PATH`
using the name `led` for it):

* show current setting  : `led status`
* blink on cpu0 activity: `led cpu0`
* blink on SDcard writes: `led mmc0`
* steady timer (on-off) : `led timer`
* give heartbeat        : `led heartbeat`
* LED steady on         : `led default-on`
* LED off               : `led none`
