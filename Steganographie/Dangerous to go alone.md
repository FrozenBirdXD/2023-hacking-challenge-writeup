# The game in Steganographie: Dangerous to go alone | 30 Points
For this challenge we are just given a single file called *large_map.gb*. 

## Solution
Since *.gb* isn't a commonly used extension, a quick search on the internet reveals that it might be a Game Boy ROM file. Since the file is called a map it probably is a 
game with a map you can traverse. 

To confirm this hypothesis, we can download a gameboy emulator like the popular 
[Visual Boy Advance](https://visualboyadvance.org/download/) emulator and open the file with it. After opening we can move the camera with the keys *'wasd'*. The 
flag is hidden in the middle of the map and is written with some kind of grass. It looks like this:

![flag](https://user-images.githubusercontent.com/118717731/220877078-c7f91578-30de-44ec-b0c5-ac27cedf35b6.png)

Flag: **HSAINNOS{CHIPTUNE}**.
