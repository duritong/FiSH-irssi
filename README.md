[![Build Status](https://travis-ci.org/falsovsky/FiSH-irssi.svg?branch=master)](https://travis-ci.org/falsovsky/FiSH-irssi)

# Introduction

This is an encryption add-on for irssi, it's based on blowfish. It supports private messages and channel encryption. It also includes a secure key-exchange system.

# Requirements

The requirements for building FiSH-irssi are:

* cmake
* pkg-config
* Glib 2.0
* OpenSSL
* irssi (with includes)

## Debian / Ubuntu

```
# apt-get install build-essential irssi-dev libglib2.0-dev libssl-dev cmake git
```
## OpenBSD

```
# pkg_add glib2 irssi cmake git
```
## Arch Linux

```
# pacman -S cmake pkg-config glib2 openssl irssi
```
## CentOS / Fedora
```
yum install gcc pkgconfig cmake irssi irssi-devel openssl openssl-devel glib2 glib2-devel
```

You can also find packages for CentOS & Fedora in the following [copr](https://copr.fedorainfracloud.org/coprs/duritong/irssi-fish/) repository.

# Building

Just type in the following commands:

```
$ git clone https://github.com/falsovsky/FiSH-irssi.git
$ cd FiSH-irssi
$ cmake .
$ make
```

If you want to install to **/usr** instead of **/usr/local**

```
$ cmake -DCMAKE_INSTALL_PREFIX:PATH=/usr .
$ make
```

Run ``make install`` as a privileged user (if needed) to install it.

# Running

If you installed the module in the default directory, you just need to run the following command inside irssi to load it:

```
/load fish
```

If not, just include the path while loading:

```
/load /home/username/libfish.so
```

## Load automatically at start-up

```
echo "load fish" >> /home/username/.irssi/startup
```

# Configurations

FiSH-irssi has some configurations that can be set via ``/set`` on irssi.

```
process_outgoing
```
FiSH outgoing messages.

Default value is 1

```
process_incoming
```
unFiSH incoming messages.

Default value is 1

```
auto_keyxchange
```
Do an automatic key exchange in private messages.

Default value is 1

```
plain_prefix
```
Prefix needed to send an unFiSHed message. For example:

``+p Hi there in clear text``

Default value is ``+p ``

```
mark_encrypted
```
String used to mark a FiSHed message.

Default value is ``\002>\002 ``

```
mark_position
```
Defines if the mark should be a prefix (1) or a suffix (0).

Default value is 1

```
nicktracker
```
Allows seamless conversations when your chat partner changes his nick. This feature will copy the old key to use with his new nick. It affects nick changes for opened queries!

Default value is 1

```
mark_broken_block
```
Indicates whether a message is incomplete.

Default value is ``\002&\002``

# Commands

```
/topic+ <message>
```
Sets a FiSHed topic in the current channel.

```
/topic+ TAB
```
Allows to edit a FiSHed topic.

```
/notice+ [nick / #channel] <message>
```
Sends a FiSHed notice to the current window or to the specified target.

```
/me+ <message>
```
Send a FiSHed action to the current window.

```
/setkey [servertag] [nick / #channel] <key>
```
Sets the key used to FiSH the messages for the current window or to the specified target.

```
/delkey [servertag] [nick/#channel]
```
Unsets the key used to FiSH the messages for the current window or to the specified target.

```
/key|showkey [servertag] [nick / #channel]
```
Shows the used key to FiSH the messages for the current window or to the specified target. The key will appear in the target window.

```
/keyx
```
Forces a DH key exchange in the current window.

```
/setinipw <password>
```
Sets a custom password used to cipher the contents of blow.ini.

```
/unsetinipw
```
Unset the custom password used to cipher blow.ini.

```
/fishlogin
```
Used to ask again for the blow.ini password if the user inserts an invalid password at start-up.

```
/fishhelp|helpfish
```
Show a little help inside irssi.


# Tested

FiSH-irssi has been tested on various OS and arches:

* Linux/x86
* Linux/sparc
* Linux/arm
* OpenBSD/x86
* OpenBSD/macppc
* OpenBSD/sgi
* FreeBSD/x86
* NetBSD/x86
