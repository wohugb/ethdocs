Building for Android
====================

We don\'t currently have a working Android build, though that is [on the
roadmap](https://github.com/doublethinkco/webthree-umbrella-cross/issues/35)
for [doublethinkco](http://doublethink.co). Android uses the Linux
kernel, but has a [different
API](http://doublethink.co/2015/12/31/a-tale-of-two-abis/) than the ARM
Linux cross-builds, meaning that specific binaries will be required.

ARM Linux distros use the GLIBC runtime library, where Android uses
bionic.
