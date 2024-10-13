# r2modman

[![Discord](https://img.shields.io/discord/727304496522461185?label=r2modman%20Discord&style=for-the-badge)](https://discord.gg/jE2zWHY)

[![GitHub](https://img.shields.io/github/license/ebkr/r2modmanPlus?color=orange&style=for-the-badge)](https://github.com/ebkr/r2modmanPlus)

## This fork

> [!NOTE]
> This modification was crafted with a focus on enhancing my own convenience and should not be considered suitable for production.

This fork is a slightly modified version of r2modman. It is specifically modified to run on modern MacOS systems with Silicon processors. The automatic directory detection and validation was removed so it can be used with more flexibility. This version also features a JSON in the .app package contents that lets you define launcher overrides for easier use with CrossOver (+ Game Porting Toolkit).

### Installation on MacOS
To install the mod manager on MacOS, you need to build it from source using NodeJS and Electron.

#### Build from source
1. Clone the repository or download the zip in [Releases](https://github.com/m0dtheory/r2modmanPlus-crossover/releases)
2. Use node v20.18.0 (npm v10.8.2)
4. Make sure you have yarn installed globally `npm install -g yarn`
5. Run `yarn`
6. Run `yarn run run` to test that the application builds
7. Run `yarn run build-osx` to build the application
8. The .app will be located in /dist/electron/Packaged/mac-arm64
9. Move the app to your Applications folder

### Configuring CrossOver to Mod a Steam Game with r2modman

This comprehensive guide provides detailed instructions for configuring CrossOver to enable modding in a Steam game using r2modman. Our example game is "ROUNDS."

You can find all the necessary files in the [Releases](https://github.com/m0dtheory/r2modmanPlus-crossover/releases) page.

#### Step-by-Step Configuration

Follow these steps to successfully configure CrossOver for modding:

1. **Create a New Bottle and Install Steam:**
   Within CrossOver, create a new bottle and proceed to install Steam.

   <img src="https://i.imgur.com/XClGdKE.png" width="700px"/>

2. **Game Installation:**
   Launch Steam and proceed to install the game of interest (in our case, "ROUNDS"). Make sure you are running the right version of the game for the mods to work.

3. **Configure CrossOver for Optimal Performance:**
   Fine-tune CrossOver settings to ensure the game's optimal launch and performance. Detailed configurations can be found in readily available online documentation.

4. **Extraction of required files:**
   Within the bottle's `c_drive` directory, navigate to the game folder located in `/drive_c/Program Files (x86)/Steam/steamapps/common/ROUNDS`. Extract the contents of the provided `r2modmanPlus-crossover_bottle.zip` into this directory. This action will create a folder labeled `r2modmanPlus`, which should be located alongside the game's primary executable, "Rounds.exe."
   <br>
   <img src="https://i.imgur.com/nvzULGU.png" width="350"/>

5. **Wine Configuration:**
   - Access the bottle's Wine Configurations.
       
        <img src="https://i.imgur.com/llYQyyO.png" width="350"/>
   - Proceed to the Libraries tab and add `winhttp.dll` as a new override library.
   - Navigate to the Drives tab and mount the `profiles` folder from your r2modman application to the "E:\" drive. For reference, your path could look like: `/Users/USER/Library/Application Support/r2modmanPlus-local/ROUNDS/profiles`.
   <br>
   <img src="https://i.imgur.com/btThXvS.png" width="350"><img src="https://i.imgur.com/L68NXSh.png" width="350">

6. **Creation of the Modded Launcher:**
   - Under the bottle's Run Command settings, browse to the game folder and to the r2modmanPlus folder.

       <img src="https://i.imgur.com/u0jhP28.png" width="350"/>
       
   - Select `r2modmanPlus-crossover.bat` as the designated command.
   - Save this command as a launcher. Example:

     ```
     "/Users/USER/Library/Application Support/CrossOver/Bottles/NEW/drive_c/Program Files (x86)/Steam/steamapps/common/ROUNDS/r2modmanPlus/r2modmanPlus-crossover.bat"
     ```

       <img src="https://i.imgur.com/7IUwvEE.png" width="500">

7. **Adjust Launcher Name:**
   - Navigate to the bottle's folder and proceed to `/Users/USER/Library/Application Support/CrossOver/Bottles/NEW/desktopdata/cxmenu`.
   - Open `cxmenu_macosx.plist` using a text editor.
   - Substitute `<key>r2modmanPlus-Modded</key>` with the chosen game name. For instance, `<key>RoundsModded</key>`.
   - Save this file and restart CrossOver.
    > Tip: It is possible to set custom icons for CrossOver launchers within the "cxmenu_macosx.plist" file.

8. **Accessing Newly Created Launchers:**
    The custom launchers are now available within your user's Applications folder `~/Application/CrossOver/` in the form of .app files. The launcher will require a command from r2modman before it can launch modded.

Your CrossOver bottle should now be ready for modding the selected Steam game with r2modman. Head over to the next section to see how to setup r2modman to launch the game modded or vanilla.

### Games JSON override

Right-click the r2modman app and click `Show Package Contents` and open the games.json file with a text editor.

Find the object that match your game and add the crossoverLauncher in the r2modman object. For example:

```json
...
"rounds": {
   ...
   "r2modman": {
        "crossOverLauncher": "/Users/USER/Applications/CrossOver/GAME/MODDEDGAME.app",
        "internalFolderName": "ROUNDS",
        "dataFolderName": "Rounds_Data",
        "settingsIdentifier": "ROUNDS",
        "packageIndex": "https://rounds.thunderstore.io/api/v1/package/",
        ...
    }
   ...
}
...
```
> Tip: You can modify this file later to add more bottles for different games without needing to rebuild the app.

### Launching game via r2modman
Create a profile and add mods for the game linked to your bottle. When you’re ready, click the `Start Modded` button. This will execute the launcher you set up in the previous steps, transferring your r2modman profile to the bottle and launching the game with mods enabled.

   >Tip: To play the game without mods afterward, simply relaunch using `Start Vanilla` in r2modman. This will deactivate the mods and send the necessary commands to the bottle.
---

<br>

## Original README

| [Features](#features) | [What is a mod manager?](#what-is-a-mod-manager) | [Installing](#installing) | [Help](#help) | [Feedback and suggestions](#feedback-and-suggestions) | [Changelog](#changelog) | [Screenshots](#screenshots) |
|---|---|---|---|---|---|---|

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