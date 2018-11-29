# Cheat Sheets
My cheatsheets

## Add new resolution

```bash
$ cvt 1920 1080 60
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

$ xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
$ xrandr --addmode Virtual1 1920x1080_60.00
```
## Clickjacking Test
[Owasp](https://www.owasp.org/index.php/Testing_for_Clickjacking_(OTG-CLIENT-009))
```html
<html> 

   <head> 

     <title>Clickjack test page</title> 

   </head> 

   <body> 

     <p>Website is vulnerable to clickjacking!</p> 

     <iframe src="URL" width="500" height="500"></iframe> 

   </body> 

</html>
```

## Spawn shell with given user,only for network purpose
Windows
```cmd
runas /netonly /user:domain\user cmd
```

## Get DC, useful in Internal Pentest

```cmd
C:\Users\Kevin> nltest /dclist:DOMAIN
C:\Users\Kevin> echo %LOGONSERVER%
``
