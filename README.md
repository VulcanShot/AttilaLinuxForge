# AttilaLinuxForge

A lightweight script for managing mods in Total War: Attila on Linux.

## Features

- Easily load mods from the Steam Workshop.
- Preserve mod configurations for future use.
- Automatically launch the game after loading mods.
- Lightweight, few dependencies required.

## Dependencies

- `find`
- `basename`
- `steam`

## Installation

1. Clone the repository:
   ```sh
   git clone https://github.com/VulcanShot/AttilaLinuxForge.git
   cd AttilaLinuxForge
   ```
   Make sure that `steam_path` points to your Steam folder!
2. Make the script executable:
   ```sh
   chmod +x attila-forge
   ```
3. Optionally, move it to a directory in your `$PATH` for global access:
   ```sh
   sudo mv attila-forge /usr/local/bin/attila-forge
   ```

## Usage

### 1. Adding Mods
```sh
./attila-forge mod1.pack mod2.pack mod3.pack
./attila-forge mod1 mod2 mod3
```

### 2. Saving Mod Configurations
By default, Total War: Attila overwrites the preferences script on exit. If no save file is provided, the default file name is modded_preferences.script.txt
```sh
./attila-forge -o mk1212.script.txt mk1212base.pack mk1212models.pack ...
./attila-forge --output mk1212base.pack mk1212models.pack ...
```
Note: The script saves the `preferences.script.txt`, so if you change your configurations you would have to copy them over to your saved files.

### 3. Loading Mod Configurations
The specified file (or the default) is copied over to `preferences.script.txt`. The latter is backed up with suffix '~'.
```sh
./attila-forge -l
./attila-forge --load mk1212.script.txt
```

### 4. Running the Game
```sh
./attila-forge -r ...
./attila-forge --run ...
```
