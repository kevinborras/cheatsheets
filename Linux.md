# Linux Cheat Sheet

## Add new resolution

```bash
$ cvt 1920 1080 60
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

$ xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
$ xrandr --addmode Virtual1 1920x1080_60.00
```
## Local port forwarding

```bash
ssh -L 80:127.0.0.1:3306 user@host
```

## Dynamic port forwarding

```bash
$ ssh -D port user@host
```
## BURP SUITE: SSL_ERROR_RX_RECORD_TOO_LONG

There are some problems with the newer versions of Java, we have to use an older version, e.g version 10

```bash
sudo update-alternatives --config java
sudo update-alternatives --config javac
sudo update-alternatives --config javaws
```
