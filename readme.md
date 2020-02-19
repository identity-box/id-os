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

The Scuttlebutt Social Network
-------------------------------

ID-OS includes software for the [Scuttlebutt][7] social network. This software
is called a [Scuttlebutt pub][8], and it can keep a copy of all your posts, so
that others can see your posts when you're offline.

In order to connect a Scuttlebutt client such as [Patchwork][9] to the pub
that's running on ID-OS, you need an invite code. Currently, you need to use a
command line to obtain the invite code:

```bash
# login to the pub's container:
balena ssh balena.local ssb-server

# print a new invite code:
node_modules/.bin/ssb-server invite.create 1
```

ID-OS uses the [Tor][10] router for all messages to and from the pub. That's why
the invite code contains a .onion address. Only Scuttlebutt clients that support
Tor can use these invite codes. Patchwork supports Tor; it's usually
[enough][12] to have [Tor Browser][11] open at the same time as Patchwork.

Please note that this does not make you anonymous. Anonymity requires [more][13]
than just the use of Tor.

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
[7]: https://scuttlebutt.nz
[8]: https://handbook.scuttlebutt.nz/faq/basics/pub.html
[9]: https://github.com/ssbc/patchwork/blob/master/README.md
[10]: https://www.torproject.org
[11]: https://www.torproject.org/download/
[12]: https://handbook.scuttlebutt.nz/faq/misc/tor
[13]: https://www.whonix.org/wiki/DoNot
