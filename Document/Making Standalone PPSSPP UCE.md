# Making Standalone PPSSPP UCE

### Step 1 : Prepare UCE Tool

Download UCETool.tar. Extract tar with following command.

```
tar -xvf UCETool.tar
```

### Step 2 : Prepare Emulator and Game Files

Needed files:
- PPSSPP: PPSSPP program and assets. (Compile by yourself. https://github.com/pac-women/ALP-PPSSPP) 
- Bashlauncher (bash_launcher_libretro.so): A dummy libretro core to run shell script.
- Game rom (GAME.ISO) : PSP game rom. Use ISO or CSO format file for better compatibility.
- Boxart (boxart.png): Boxart shows in UCE menu. PNG format with 222 x 306 resolution.

### Step 3 : Edit Shell Script

Edit RUN.sh as following. Example file can be found in UCE Tool.

```
#!/bin/sh

mkdir -p -m 777 /userdata/saves/psp/

cd ./emu/PPSSPP

LD_PRELOAD=mnt/usr/lib/libstdc++.so.6:mnt/lib/libc.so.6 ./PPSSPP ../GAME.iso

```

### Step 4 : Edit exec.sh

Edit exec.sh as following. Example file can be found in UCE Tool.

```
#!/bin/sh
 
set -x

/emulator/retroplayer ./emu/bash_launcher_libretro.so "./roms/RUN.sh"
```

### Step 5 : Edit cartridge.xml

Edit **<title>GAME</title>** section in cartridge.xml. Replace GAME into the title you want to show in UCE menu. Example file can be found in UCE Tool.

### Step 6 : File Structure

Please adhere the following file structure when preparing your add-on image

- ./AddOn_GAME/          		 <-- name the root directory whatever you want, in the example above
- ./AddOn_GAME/emu/   		 <-- Put PPSSPP main program and assets, bash_launcher_libretro.so, GAME.iso in this folder (with permission 775)
- ./AddOn_GAME/roms/   		 <-- Put RUN.sh in this folder (with permission 755)
- ./AddOn_GAME/boxart/   		 <-- Put boxart.png in this folder (with permission 664)
- ./AddOn_GAME/title.png      	 <-- symbolic link to "boxart/boxart.png" (with permission 664)
- ./AddOn_GAME/cartridge.xml 	 <-- info header for menu display. *in XML format. (with permission 664)
- ./AddOn_GAME/exec.sh       	 <-- the script file to run emulator and game files. (with permission 755)

### Step 7 : Create UCE

Chgane directory into where build_sq_cartridge_pack.sh ism and run following command.

```
./build_sq_cartridge_pack.sh ./AddOn_GAME/ ./AddOn_GAME.UCE
```

### Step 8 : PPSSPP Setting

Connect a Xbox gamepad before lunching UCE. After launch UCE, press Menu button to bring up setting menu.
