# samsung_notes_launcher
Eng

This exe launches samsung notes on windows even not on galaxy devices. 

Samsung notes must be installed first. You can install it at Microsoft Store.

Windows defender might detected this file as a virus. This can happen to any batch file.

Source code: https://github.com/kellwinr/galaxybook_mask/blob/main/samsungnotes-directlaunch.bat

한국어

이 exe 파일은 삼성 노트를 갤럭시 제품이 아니더라도 윈도우에서 열 수 있게 합니다.

삼성 노트가 먼저 설치되어 있어야 합니다. 마이크로소프트 스토어에서 설치할 수 있습니다.

보안 프로그램에서 이 파일을 바이러스로 감지할 수 있습니다. 이는 모든 배치 파일에서 일어날 수 있습니다.

소스 코드: https://github.com/kellwinr/galaxybook_mask/blob/main/samsungnotes-directlaunch.bat

::Get Admin privileges
set "params=%*" && cd /d "%~dp0" && pushd "%~dp0" && ( if exist "%temp%\getadmin.vbs" del "%temp%\getadmin.vbs" ) && fsutil dirty query %systemdrive% 1>nul 2>nul || (  echo Set UAC = CreateObject^("Shell.Application"^) : UAC.ShellExecute "cmd.exe", "/k cd ""%~sdp0"" && %~s0 %params%", "", "runas", 1 >> "%temp%\getadmin.vbs" && "%temp%\getadmin.vbs" && exit /B )

:: Store the previous system product name and system manufacturer
for /f "tokens=2*" %%a in ('reg query "HKLM\HARDWARE\DESCRIPTION\System\BIOS" /v SystemProductName ^| find "REG_SZ"') do set "prev_product_name=%%b"
for /f "tokens=2*" %%a in ('reg query "HKLM\HARDWARE\DESCRIPTION\System\BIOS" /v SystemManufacturer ^| find "REG_SZ"') do set "prev_manufacturer=%%b"


:: Set the new system product name and system manufacturer
reg add "HKLM\HARDWARE\DESCRIPTION\System\BIOS" /v SystemProductName /t REG_SZ /d "NP960XFG-KC4UK" /f
reg add "HKLM\HARDWARE\DESCRIPTION\System\BIOS" /v SystemManufacturer /t REG_SZ /d "Samsung" /f

:: Start Samsung Notes
start shell:AppsFolder\SAMSUNGELECTRONICSCoLtd.SamsungNotes_wyx1vj98g3asy!App

:: Exit
exit

ANSI encoded
