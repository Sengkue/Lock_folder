cls
@ECHO OFF

title Folder Locker

if EXIST "Control Panel.{21EC2020-3AEA-1069-A2DD-08002B30309D}" goto UNLOCK

if NOT EXIST secured goto MDLOCKER

:CONFIRM

echo Are you sure u want to Lock the secured(Y/N)

set/p "cho=>"

if %cho%==Y goto LOCK

if %cho%==y goto LOCK

if %cho%==n goto END

if %cho%==N goto END

echo Invalid choice.

goto CONFIRM

:LOCK

ren secured "Control Panel.{21EC2020-3AEA-1069-A2DD-08002B30309D}"

attrib +h +s +r +i "Control Panel.{21EC2020-3AEA-1069-A2DD-08002B30309D}"

echo secured locked

goto End

:UNLOCK

echo put in the key to Unlock the lock

set/p "pass=>password"

if NOT %pass%==123456 goto FAIL

attrib -h -s "Control Panel.{21EC2020-3AEA-1069-A2DD-08002B30309D}"

ren "Control Panel.{21EC2020-3AEA-1069-A2DD-08002B30309D}" secured

echo secured Unlocked

goto End

:FAIL

echo Invalid keyword

goto UNLOCK

:MDLOCKER

md Secured

echo lock unlocked

goto End

:End