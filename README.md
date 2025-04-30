# AttilaLinuxForge

A lightweight script for managing mods in Total War: Attila on Linux.

## Features

- Easily load mods from the Steam Workshop.
- Automatically update the preferences script with the selected mods.
- Preserve mod configurations for future use.
- Lightweight, no dependencies required.

## Installation

1. Clone the repository:
   ```sh
   git clone https://github.com/VulcanShot/AttilaLinuxForge.git
   cd AttilaLinuxForge
   ```
2. Make the script executable:
   ```sh
   chmod +x attila-forge.sh
   ```
3. Optionally, move it to a directory in your `$PATH` for global access:
   ```sh
   sudo mv attila-forge.sh /usr/local/bin/attila-forge
   ```

## Usage

### Adding Mods
Run the script with mod filenames:
```sh
./attila-forge.sh mod1 mod2 mod3
```
By default, Total War: Attila overwrites the preferences script on exit. After mod selection, the script prompts you to save the configuration.

### Loading Saved Mod Configurations
```sh
./attila-forge.sh -l saved_config.script.txt
```
