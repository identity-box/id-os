ID-OS
=====

An *experimental* operating system for decentralized apps.
Based on [balenaOS][1].

Checkout
--------

This repository contains git submodules. Make sure that you clone this repo with
the `--recursive` flag, or invoke `git submodule update --init --recursive`
after cloning.

Installation
------------

ID-OS is currently only tested on a Raspberry Pi 4 with 4Gb. Follow these steps
to install ID-OS:

  1. Download the [balenaOS development image][2] for Raspberry Pi 4.
  2. Flash the image to an SD card for your Pi. You can use [balenaEtcher][3]
      for this.
  3. Install the [balena CLI][4] on the development machine where you checked
      out this repository.
  4. Connect the Pi to the same network as your development machine using an
      ethernet cable. A WiFi connection can be configured later, but for now
      you'll need a fixed connection to the Pi.
  5. Power up the Pi. It should become visible in the network as the
      'balena.local' host.
  6. Invoke `balena push balena.local` in the root of this project. This will
      push the docker configuration from this repository to the Pi.

WiFi Setup
----------

ID-OS includes the [WiFi Connect][5] software from balena. This means that the
Pi exposes an access point called 'WiFi Connect'. You can connect to this access
point using a mobile device, which will pop-up a dialog for configuring the WiFi
connection of ID-OS.

Troubleshooting
---------------

Should you experience interrupted ssb-server builds, then using a faster sd card
may solve the issue.

If this does not solve your issue, please [let us know][6].

[1]: https://balena.io
[2]: https://www.balena.io/os/#download
[3]: https://www.balena.io/etcher/
[4]: https://github.com/balena-io/balena-cli/blob/master/INSTALL.md
[5]: https://github.com/balena-io/wifi-connect
[6]: https://github.com/markspanbroek/id-os/issues
