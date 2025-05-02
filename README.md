# AttilaLinuxForge

A lightweight solution for modding Total War: Attila on Linux.

## Features

- Easily load mods from the Steam Workshop.
- Preserve mod configurations for future use.
- Automatically launch the game after loading mods.
- Lightweight, few dependencies required.

## Dependencies

- `find`
- `basename`
- `steam`

## Variants

There are three variants of **Attila Linux Forge**:

- [attila-forge](./attila-forge): To be used from the terminal.
- [attila-forge-launcher](./attila-forge-launcher): To be automatically launched by Steam.

## Installation

If you wish to install both variants, you could clone the repository instead of downloading them individually.
```sh
   git clone https://github.com/VulcanShot/AttilaLinuxForge.git
   cd AttilaLinuxForge
```

### attila-forge 

1. Download the [script](./attila-forge). Make sure that `steam_path` points to your Steam folder.
2. Make the script executable:
   ```sh
   chmod +x attila-forge
   ```
3. Optionally, move it to a directory in your `$PATH` for global access:
   ```sh
   sudo mv attila-forge /usr/local/bin/attila-forge
   ```

### attila-forge-launcher

1. Download the [script](./attila-forge-launcher).
2. Install `libopenal1`. Honestly, I do not know why this is required to launch the executable.
   ```sh
   sudo apt install libopenal1
   ```
3. Make the script executable:
   ```sh
   chmod +x attila-forge-launcher
   ```
4. Place the script in Attila's folder.
   ```sh
   mv attila-forge-launcher {steam-directory}/steamapps/common/Total\ War\ Attila/
   ```
5. Set the game's launch options to the following (see [usage](##usage)):
```
   ./attila-forge-launcher "%command%" [OPTIONS] [<packfile> ...]
```
The script does not support passing launch options to the game itself since I do not think Attila has any. If you do need to do that then feel free to raise an issue or send a pull request :).

## Usage

Both variants work exactly the same except `attila-forge-launcher` always launches the game, and requieres the "%command%" as its first argument. 

### Adding Mods
```sh
./attila-forge mod1.pack mod2.pack mod3.pack
./attila-forge-launcher "%command%" mod1 mod2 mod3 # Extension is not needed
```

### Saving Mod Configurations
By default, Total War: Attila overwrites the preferences script on exit. If no save file is provided, the default file name is modded_preferences.script.txt
```sh
./attila-forge -o=mk1212.script.txt mk1212base.pack mk1212models.pack ...
./attila-forge-launcher "%command%" --output mk1212base.pack mk1212models.pack ...
```
Note: The script saves the `preferences.script.txt`, so if you change your configurations you would have to copy them over to your saved files.

### Loading Mod Configurations
The specified file (or the default) is copied over to `preferences.script.txt`. The latter is backed up with suffix '~'.
```sh
./attila-forge -l mk1212.script.txt
./attila-forge "%command%" --load 
```

### Running the Game
```sh
./attila-forge -r ...
./attila-forge "%command%" --run ...
```
