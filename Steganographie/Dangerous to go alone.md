# The game in Steganographie: Dangerous to go alone | 30 Points
For this challenge we are just given a single file called *large_map.gb*. 

## Solution
Since *.gb* isn't a commonly used extension, a quick search on the internet reveals that it might be a Game Boy ROM file. Since the file is called a map it probably is a 
game with a map you can traverse. 

To confirm this hypothesis, download a gameboy emulator like the popular 
[Visual Boy Advance](https://visualboyadvance.org/download/) emulator and open the file with it. After opening, we can move the camera with the keys *'wasd'*. The 
flag is hidden in the middle of the map and is written with some kind of grass. It looks like this:

![flag](https://user-images.githubusercontent.com/118717731/220877078-c7f91578-30de-44ec-b0c5-ac27cedf35b6.png)

## Emulators
But how do emulators enable software that is designed for other devices, to be run on other devices like modern windows computers?

Emulators are programs that imitate the behavior of another computer system. Emulators replicate the behavior of some hardware platform, allowing 
software designed for that platform to be run on the host system. They function by converting the machine code of the emulated system into code that the 
system hosting the software can understand. Emulators often have a software layer that replicates the simulated system's hardware, such as the CPU, memory, and other 
hardware components.

More can be found on the [wiki article](https://en.wikipedia.org/wiki/Emulator) covering emulators.

Flag: **HSAINNOS{CHIPTUNE}**.
