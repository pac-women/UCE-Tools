# Making DC/PS/PSP/SS UCE with Windows Tool

### Step 1 : Prepare UCE Tool

Download UCETool

```
123
```

### Step 2 : Prepare Emulator and Game Files

Needed files:
- RetroArch (retroarch): RetroArch main program. (Compile by yourself. https://github.com/pac-women/ALP-RetroArch)
- Flycast (reicast.elf): standalone Flycast program. (Compile by yourself https://github.com/pac-women/ALP-flycast)
- PCSX-ReARMed (pcsx_rearmed_libretro.so): PCSX-ReARMed core. (Compile by yourself https://github.com/pac-women/ALP-PCSX-ReARMed)
- PPSSPP: PPSSPP program and assets. (Compile by yourself. https://github.com/pac-women/ALP-PPSSPP) 
- Beetle Saturn (mednafen_saturn_libretro.so): Beetle Saturn core. (Compile by yourself. https://github.com/pac-women/ALP-BeetleSaturn/tree/main) 
- Bashlauncher (bash_launcher_libretro.so): A dummy libretro core to run shell script.
- Game rom (GAME.chd) : SS game rom. Use chd format file for better compatibility.
- BIOS : SS BIOS. Please refer to Beetle Saturn doc for more information.(https://docs.libretro.com/library/beetle_saturn/#bios)
- Boxart (boxart.png): Boxart shows in UCE menu. PNG format with 222 x 306 resolution.

Note: For preparing PPSSPP for Windows, please follow the instruction in https://github.com/pac-women/ALP-PPSSPP.
After you get OUTPUT/PPSSPP folder, use following command to create tar package under Linux enviromant.
```
$ cp -rL OUTPUT/PPSSPP ppsspp_forwin/
$ tar -cvf ppsspp.tar ppsspp_forwin/
```
Copy the tar file to Windows, and enter following command in CMD (Administrator Mode).
```
fsutil.exe file setCaseSensitiveInfo "C:\Users\dorae\AppData\Local\Temp" enable
```
Untar the tar file into Temp folder with 7-zip.

### Step 3 : Create UCE with Windows Tool

