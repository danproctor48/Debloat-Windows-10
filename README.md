# Debloat Windows 10

This project collects Powershell scripts which help to *debloat* Windows 10,
tweak common settings and install basic software components.

These scripts are used on my development machine. With a stock OS install, mobile i5 CPU, and 8gb of RAM:
    - ~15% CPU Reduction
    - Additional 1.2gb of usable RAM
    - 15gb more HDD space
    - Faster indexing of local files

**There is no undo**, I recommend only using these scripts on a fresh
installation (including Windows Updates). Test everything after running them
before doing anything else. Also there is no guarantee that everything will
work after future updates since I cannot predict what Microsoft will do next.

## Execution

Enable execution of PowerShell scripts:

    PS> Set-ExecutionPolicy Unrestricted

Unblock PowerShell scripts and modules within this directory:

    PS > ls -Recurse *.ps1 | Unblock-File
    PS > ls -Recurse *.psm1 | Unblock-File

## Usage

1. Install all available updates for your system.
2. Edit the scripts to fit your need.
3. Run the scripts from a PowerShell with administrator priviledges (Explorer `Files > Open Windows PowerShell > Open Windows PowerShell as administrator`)
4. Restart Computer for Changes to Take Effect.

## Disabling Cortana

**THIS WILL BREAK THE NATIVE WINDOWS 10 SEARCH FUNCTIONALITY**

However, you will save a good chunk of resources not having Cortana running in the background. Additionally, the native start menu will still work and if you have your start menu organized, this won't bother you. Want search back? Check the section below.

My reccomendation is using TakeOwn to control ownership of the application files. This will come in handy developing certain system applications down the line. To create this in a context menu check out https://www.howtogeek.com/howto/windows-vista/add-take-ownership-to-explorer-right-click-menu-in-vista/. **Please be extra careful editing the registry!***

    1. add TakeOwn to the context menu or (use takeown from the command line).
    2. Navigate to C:\Windows
    3. Create folder SystemApps.bak
    4. Use Takeown to gain ownership of c:\windows\SystemApps\Microsoft.Windows.Cortana_cw5n1h2txyewy (Gain ownership of anything else you want to move)
    5. Cut/Paste the folder(s) from SystemApps to SystemApps.bak
    6. When the "Permissions" pop-up appears, switch to Task Manager
    7. Kill SearchUI.exe process OR Kill the Cortana/App process 
    8. Switch back and give permission to move the folder (You typically have about 2 seconds to give permission)

The folder is now in SystemsApps.bak - and you can simply move it back if the need arises.


## Startmenu

My reccomendation would be using Start10 by StarDock. It's a $5 start menu replacement that brings back the look and feel of Windows 7 as well as faster local search capabilities. 

https://www.stardock.com/products/start10/

## UWP Slack & Auto Startup
Slack does not come with a start on boot option for Windows when downloaded from the Windows store.

Why should you download from the Windows Store? In short, it is better contained by the OS for performance and battery drain. I reccomend downloading from the store wherever you can (Ex. Spotify). 

    1. Type 'run' in the search box and click Run in the search results.
    2. In the Run dialogue, type 'shell:appsfolder' and click OK. File Explorer will open displaying the Applications folder.
    3. Right click the UWP App you want to run on startup, and select Create Shortcut from the context menu. Click Yes to add shortcut to desktop.
    4. Right click the shortcut on the Desktop, and select Cut form the context menu.
    5. Type run in the search box and click Run in the search results.
    6. In the Run dialogue, type 'shell:startup' and click OK. File Explorer will open displaying the Startup folder.
    7. Right click in the folder window and select Paste from the context menu.

## Liability

**All scripts are provided as is and you use them at your own risk.**

## License

    "THE BEER-WARE LICENSE" (Revision 42):

    As long as you retain this notice you can do whatever you want with this
    stuff. If we meet some day, and you think this stuff is worth it, you can
    buy us a beer in return.

    This project is distributed in the hope that it will be useful, but WITHOUT
    ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or
    FITNESS FOR A PARTICULAR PURPOSE.
