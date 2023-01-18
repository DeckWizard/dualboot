**Deck Wizard Dual Boot**

On SteamOS Desktop Mode, go to System Settings/User Management and set a password, for a quick install you can use 'passw' or 'deck'.

Open a Konsole Window & enter..

```
git clone https://github.com/DeckWizard/dualboot

cd dualboot

chmod +x SteamDeck_rEFInd_install.sh

./SteamDeck_rEFInd_install.sh
```

Now that the Dual Boot has been installed, **we need** to perform 1 more small task on Windows, to prevent Windows booting over our boot loader when we restart the Steam Deck & also whenever a new SteamOS update occurs which updates the BIOS firmware.

- Boot into Windows & download/extract the file here - shorturl.at/dipv7
- Inside the folder run ```rEFIWindows``` As Administrator
- Confirm the selection with Y in the box that appears
- Click Search on Windows & search for ```Task Scheduler``` & open it
- Select the tasks folder & in the list of tasks, right click ```rEFIndTask-donotdelete``` & choose Properties
- Make sure ```Run whether the user is logged on or not``` is selected & ```Do not store password```
- Click OK, close the window & click run on the ```rEFIndTask-donotdelete``` task
- Inside the C:/ drive a folder called rEFIndtools has been created, inside here access status.txt & you will see the entry for rEFInd written twice.
- Restart the Steam Deck & rEFInd will appear instead of Windows permanently.

```
DISCLAIMER: This script is an alternative rEFInd Script taken from jlobue10's v1.0.9 release with an added theme and config changes.

All Credit goes to jlobue10 for creating this script for multi-booting on the Steam Deck
```

jlobue10 Script - https://github.com/jlobue10/SteamDeck_rEFInd
RyanRudolfoba Windows Script - https://github.com/ryanrudolfoba/SteamDeck-rEFInd-dualboot/tree/main/rEFIndWindows

Theme used for foundation - https://github.com/Yannis4444/Matrix-rEFInd
