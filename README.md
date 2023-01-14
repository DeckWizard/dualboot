**Deck Wizard Dual Boot**

On SteamOS Desktop Mode, go to System Settings/User Management and set a password, for a quick install you can use 'passw' or 'deck'.

Open a Konsole Window & enter..

```
git clone https://github.com/DeckWizard/dualboot

cd dualboot

chmod +x SteamDeck_rEFInd_install.sh

./SteamDeck_rEFInd_install.sh
```

Now that the Dual Boot has been installed, **we need** to perform 1 of 2 options to prevent Windows booting over our boot loader when we restart the Steam Deck & also whenever a new SteamOS update occurs which updates the BIOS firmware.

1. Boot into Windows, download EasyUEFI and disable the Windows Boot Manager. If you don't want to use Windows you can boot into the SteamOS Recovery Image, open a Konsole window and type ```sudo efibootmgr -b XXXX -B``` to disable the Windows Boot Manager this way.

2. Boot into Windows, create a folder in the C:/ Drive called ```boot```, download the following file - ```bootsequence-rEFInd-first.ps1``` & place it in the ```boot``` folder.

- Right click on start, search for & open ```Task Scheduler```
- Right click on Task Scheduler Library and create a new folder called ```boot```, click this folder and select ```Create Basic Task```
- Type ```boot``` for the Name & press Next
- Set the task to ```When I log on``` & press Next
- Ensure ```Start a program``` is selected & press Next
- Inside the Program/Script entry field - ```C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe```
- Inside the Arguments field ```-executionpolicy bypass -file C:\boot\bootsequence-rEFInd-first.ps1```
- Make sure to check the box called ```Open the Properties dialog for this task when I click Finish``` & press Finish
- In the Properties window that appears, we want to check ```Run with Highest Privileges``` & ```Hidden``` & set ```Configure for:``` to ```Windows 10```
- Switch to the Conditions tab & ensure ```Start the task only if the computer is on AC power``` is **Unchecked** / **Disabled** & press OK

- To check that what we have just done works correctly, Right click on the ```boot task``` and click ```Run``` where a Powershell window will briefly appear.
- Right click on start, search for ```Windows Powershell``` & ```Run as Administrator```
- Inside Powershell, enter ```bcdedit /enum FIRMWARE``` & press enter
- If all the steps were performed correctly, you should see that a **bootsequence value** for rEFInd has been added, if this is not the case please review the steps above and ensure no typos have been made.

(Step 2 is recommended to avoid having to Disable the Windows Boot Manager whenever there is an major SteamOS firmware update)

With this method you can change branches in SteamOS between Main > Beta > Preview without having to worry about the Dual Boot breaking.

```
DISCLAIMER: This script is an alternative rEFInd Script taken from jlobue10's v1.0.9 release with an added theme and config changes.

jlobue10 Script - https://github.com/jlobue10/SteamDeck_rEFInd

All Credit goes to jlobue10 for creating this script for multi-booting on the Steam Deck
```
