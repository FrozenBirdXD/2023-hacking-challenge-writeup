# The QR-Code in Staganographie: White Square | 30 Points
In this challenge we are provided with a single image called *circle.png* which looks like this:

![circle](https://user-images.githubusercontent.com/118717731/220878510-1d064660-245e-4818-9107-ab0aa0b31fd8.png)

A 27x27 white image where all pixels are #FFFFFF. 

## Solution
There has to be something hidden in the file or in the image that isn't currently visible. To see if something is abnormal I opened the picture in a hex 
editor ([010 editor](https://www.sweetscape.com/download/010editor/)). There I noticed that the bit depth was 2 and the color mode was set to indexed. So I tried
different color modes and when it was set to grayscale, a QR-code appeared:

![Screenshot 2023-02-23 125512](https://user-images.githubusercontent.com/118717731/220898799-9e1175b3-6d3b-403d-afa4-ffe1701bb8ac.png)

When the QR-code is scanned. A note with the flag is given. Flag: **HSAINNOS{SquaringTheCircle}**.
