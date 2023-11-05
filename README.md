# r2modman

[![Discord](https://img.shields.io/discord/727304496522461185?label=r2modman%20Discord&style=for-the-badge)](https://discord.gg/jE2zWHY)

[![GitHub](https://img.shields.io/github/license/ebkr/r2modmanPlus?color=orange&style=for-the-badge)](https://github.com/ebkr/r2modmanPlus)

| [Features](#features) | [What is a mod manager?](#what-is-a-mod-manager) | [Installing](#installing) | [Help](#help) | [Feedback and suggestions](#feedback-and-suggestions) | [Changelog](#changelog) | [Screenshots](#screenshots) |
|---|---|---|---|---|---|---|

## This fork
> [!NOTE]
>This adaptation was designed for my own ease of use and is in no way production ready. If I eventually find time, I will properly integrate the crossover overrides in the Settings menu of each games.

This fork is a slightly modified version of r2modman. 

It is specifically modified to run on modern MacOS systems with Silicon processors. The automatic directory detection and validation was removed so it can be used with more flexibility. This version also features an optional json that lets you define launchers overrides for easier use with CrossOver (+ Game Porting Toolkit).

## Configuring CrossOver to Mod a Steam Game with r2modman

This comprehensive guide provides detailed instructions for configuring CrossOver to enable modding in a Steam game using r2modman. Our example game is "ROUNDS."

### Step-by-Step Configuration

Follow these steps to successfully configure CrossOver for modding:

1. **Create an r2modman Profile:**
Initiate the process by creating a dedicated r2modman profile for the targeted game.

2. **Get the Appropriate BepInEx Pack:**
Get the BepInEx Pack designed for your game through r2modman.

3. **Establish a New Bottle and Install Steam:**
Within CrossOver, create a new bottle and proceed to install Steam.

   ![Installation Screenshot](https://i.imgur.com/XClGdKE.png)

5. **Game Installation:**
Launch Steam and proceed to install the game of interest (in our case, "ROUNDS").

6. **Configure CrossOver for Optimal Performance:**
Fine-tune CrossOver settings to ensure the game's optimal launch and performance. Detailed configurations can be found in readily available online documentation.

7. **Extraction of required files:**
Within the bottle's `c_drive` directory, navigate to the game folder located in `/drive_c/Program Files (x86)/Steam/steamapps/common/ROUNDS`. Extract the contents of the provided `r2modmanPlus-crossover_bottle.zip` into this directory. This action will create a folder labeled `r2modmanPlus`, which should be located alongside the game's primary executable, "Rounds.exe."

   ![Extraction Screenshot](https://i.imgur.com/nvzULGU.png)

9. **Wine Configuration:**
   - Access the bottle's Wine Configurations.
     
   ![](https://i.imgur.com/llYQyyO.png)
   - Proceed to the Libraries tab and add `winhttp.dll` as a new override library.
   - Navigate to the Drives tab and mount the BepInEx folder from your r2modman profile to the "E:\" drive. For reference, a sample path could resemble: `/Users/USER/Library/Application Support/r2modmanPlus-local/ROUNDS/profiles/Default/BepInEx`.
    <br>
    <img src="https://i.imgur.com/btThXvS.png" width="350">
    <img src="https://i.imgur.com/6LHy6ra.png" width="350">

10. **Creation of the Modded Launcher:**
   - Under the bottle's Run Command settings, browse to the game folder.
    ![](https://i.imgur.com/u0jhP28.png)
   - Select `r2modmanPlus-Modded.bat` as the designated command.
   - Append the Steam game ID and "modded" as command arguments.
   - Save this customized command as a launcher. Example:

     ```
     "/Users/USER/Library/Application Support/CrossOver/Bottles/NEW/drive_c/Program Files (x86)/Steam/steamapps/common/ROUNDS/r2modmanPlus/r2modmanPlus-Modded.bat" 1557740 modded
     ```
     <img src="https://i.imgur.com/V7D7eSN.png" width="500">
   > Tip: The Steam game ID is available within the "games.json" file.

11. **Adjust Launcher Naming:**
   - Navigate to the bottle's folder and proceed to `/Users/tanktheory/Library/Application Support/CrossOver/Bottles/NEW/desktopdata/cxmenu`.
   - Open `cxmenu_macosx.plist` using a text editor.
   - Substitute `<key>r2modmanPlus-Modded</key>` with the chosen game name. For instance, `<key>RoundsModded</key>`.
   - Save this file and restart CrossOver.

11. **Creation of the Vanilla Launcher:**
    - Replicate step 8's procedure but opt for "r2modmanPlus-Vanilla.bat" this time.
    - Use "vanilla" as the second command argument. The following example reflects this adjustment:
    
      ```
      "/Users/USER/Library/Application Support/CrossOver/Bottles/NEW/drive_c/Program Files (x86)/Steam/steamapps/common/ROUNDS/r2modmanPlus/r2modmanPlus-Vanilla.bat" 1557740 vanilla
      ```

12. **Update Vanilla Launcher Name:**
    - Repeat step 9 to implement the modifications to the name of the vanilla launcher.

   > Tip: It is possible to set custom icons for CrossOver launchers within the "cxmenu_macosx.plist" file.

12. **Accessing Newly Created Launchers:**
    The custom launchers are now available within `~/Application/CrossOver/` in the form of .app files.

13. **Optional Configuration for r2modman:**
    Refer to the _Optional JSON_ section to incorporate the created launchers into your r2modman setup.

Your CrossOver environment should now be ready for modding the selected Steam game with r2modman.

## Optional JSON
You can find an optional json in ```r2modman.app/Contents/Frameworks/games.json```
For each games, a launcher override can be defined in this file. Ex:
```
{  
    ...
   "r2modman": { 
        "crossOverLaunchers": {"modded": "/Users/USER/Applications/CrossOver/GAME/MODDEDGAME.app", "vanilla": "/Users/USER/Applications/CrossOver/GAME/GAME.app"},
        ...
    }
    ...
}
```

## Features
- Support for Risk of Rain 2, Dyson Sphere Program, Valheim, GTFO, BONEWORKS, and more
- A clean user interface designed to make modding as simple as possible
- Safer mod installation allowing you to play the game through Steam normally
- Mod profiles to switch between different sets of mods quickly and easily
- Export profiles to easily share both your mods and configs with friends
- Download and install mods directly from the manager
- View and update any outdated mods
- Edit configs directly from the manager
- Auto-updates
- And more!

## What is a mod manager?
It's quite simple really, a mod manager is an application to make it easier to control which mods you have installed.

You can choose to update, enable/disable or even uninstall mods with a simple click, all whilst keeping it available on another profile.

## Installing

### First time installing
#### Windows
1. Click "Manual Download" on Thunderstore.
2. Inside the downloaded **.zip** file. Run the "r2modman Setup X.X.X.exe" (where X.X.X is the current version).
3. Follow the steps in the installer.

#### Linux
1. Click "Manual Download" on Thunderstore.
2. Inside the download **.zip** file there is an AppImage release.

**If you'd prefer to install platform specific builds then you can find them under the latest GitHub release on the ebkr/r2modmanPlus repository**

**Platform builds:**
 - deb
 - rpm
 - pacman
 - tar.gz

 _Problems with Linux builds should be reported in the [r2modman discord](https://discord.gg/jE2zWHY)._

##### Note
- Temporary workaround to force Proton on Linux systems
    - Place a `.forceproton` file in the game directory whilst a solution is in development

### Updating
r2modman will automatically download any available updates whilst you use it.

If an update has been downloaded, it will be installed once you have closed the application.

## Help
### Manager errors:
1. Check the [wiki](https://github.com/ebkr/r2modmanPlus/wiki).
2. If you can't find the solution, join the community modding discord and ask for help in the appropriate channels.

### Mod errors:
1. Join the relevant community modding discord and ask for help in the appropriate channels.

## Feedback and suggestions
It's encouraged to provide as much feedback as you'd like, and fully open to criticism.

Suggestions are welcome and there are already some suggestions that have made it in to the manager!
From small features such as always-expanded cards, all the way to larger features such as code-based profile exports.

The only thing you have to consider when suggesting a feature is the impact it will have on users who don't have a lot of experience with computers.

## Screenshots

Game selection

![](https://i.imgur.com/mmzY9xQ.png)

Installed mod view

![](https://i.imgur.com/d7w4qEl.png)

Downloadable mods

![](https://i.imgur.com/eoIAMMP.png)

Config editor

![](https://i.imgur.com/RT6HsxF.png)

Profiles

![](https://i.imgur.com/nLfNaQJ.png)
