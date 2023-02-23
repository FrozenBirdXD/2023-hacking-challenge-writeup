# The hidden flag on a PCB: CrunchyPCB | 30 Points
Here we're given a text file called "*board.txt*" with the following content:
```txt
The basic pcb files for KiCad were provided by the https://github.com/OLIMEX/OLINUXINO/tree/master/HARDWARE/A64-OLinuXino
Project. DO NOT PRINT OR USE THIS PCB, IT IS BROKEN!!!

(kicad_pcb (version 20211014) (generator pcbnew)

  (general
    (thickness 1.6)
  )

  (paper "A4")
  (layers
    (0 "F.Cu" mixed)
    (1 "In1.Cu" power)
    (2 "In2.Cu" signal)
    ...
    ...
```
## Solution
The file already shows us that it's intended to be viewed with KiCad and is supposed to be a pcb, with the flag probably hidden on it. 
[KiCad](https://www.kicad.org/download/) is an open-source software suite used for electronic design automation (EDA) that allows users to create schematic 
diagrams and printed circuit board (PCB) layouts. Then open KiCad and create a new project. There we see that the correct file extension for our 
pcb is "*.kicad_pcb*". 

But when we try to open the file with the correct extension and the pcb editor, this error is shown: "**Error loading PCB. Expecting '(' in ...**". This shows us that
the first comment in the given file needs to be removed for it to open correctly. That is because this comment does not follow the correct syntax for KiCad files 
and causes an error. After doing that, it works and the pcb can now be seen:

![pcb](https://user-images.githubusercontent.com/118717731/220567652-5d880e35-4a34-4b83-b95e-611fb52e9a9f.png)

This is very cluttered and the flag is not visible. So, remove most of the layers except the second and third one.

![pcb](https://user-images.githubusercontent.com/118717731/220568731-c83cf9fc-1e61-490f-9b84-e2e4a575f0fe.png)

Then we see that the flag is written on the PCB. 

Flag: **HSAINNOS{PCB-FLAG}**.
