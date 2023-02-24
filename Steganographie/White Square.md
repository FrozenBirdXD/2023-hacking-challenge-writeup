# The QR-Code in Staganographie: White Square | 30 Points
In this challenge we are provided with a single image called *circle.png* which looks like this:

![circle](https://user-images.githubusercontent.com/118717731/220878510-1d064660-245e-4818-9107-ab0aa0b31fd8.png)

A 27x27 white image where all pixels are #FFFFFF. 

## Solution
There has to be something hidden in the file or in the image that isn't currently visible. To see if something is abnormal I opened the picture in a hex 
editor ([010 editor](https://www.sweetscape.com/download/010editor/)). There I noticed that the bit depth was 2 and the color mode was set to indexed. So I tried
different color modes and when it was set to grayscale, a QR-code appeared:

![Screenshot 2023-02-23 125512](https://user-images.githubusercontent.com/118717731/220898799-9e1175b3-6d3b-403d-afa4-ffe1701bb8ac.png)

This can be done by changing the *orange* highlighted number from 03 (which means **indexed** color mode is used) to 00 (which means **grayscale** is used as a color mode):

![hex](https://user-images.githubusercontent.com/118717731/221024747-6a151480-43c9-4282-917e-0aef0e06fe46.png)

The color mode information in a PNG image is recorded in the IHDR (Image Header) chunk. The image's size, bit depth, color type, compression technique, 
filter method, and interlace method are all specified in the IHDR chunk, which is the first chunk in the PNG file. The color mode in a PNG file determines how the
color for each pixel is stored.

The color mode has one of the following values:
- 00 - GrayScale
- 02 - TrueColor
- 03 - Indexed
- 04 - AlphaGrayScale
- 06 - AlphaTrueColor

The [wikipedia article](https://en.wikipedia.org/wiki/PNG) about PNGs explains the file format in great detail.

## Explanation
But why did a QR-code appear when the mode was changed to grayscale?

The picture's color mode was set to indexed in the original picture, which means that each pixel in the image is represented by an index value that corresponds to a 
color in a lookup table or palette. This lookup table is stored as a separate chunk called the "PLTE" chunk. The PLTE chunk contains a list of up to 256 RGB color 
values that are used to represent the pixels in the image. In our picture the PLTE chunk looks like this:

    FF FF FF FF FF FF 00 00 00
    
This means that when the image is decoded/opened the data representing the picture (index values) is used to look up the correct RGB values in the PLTE chunk. In
our case this displays all white pixels. 

The image was transformed from using a lookup table to directly representing each pixel as a shade of gray when the color mode was set to grayscale. This enabled 
for additional grayscale values to be utilized in the picture, revealing the before hidden QR-code. This is a form of [steganography](https://en.wikipedia.org/wiki/Steganography).

When the QR-code is scanned, a note with the flag in plain text is given. 

Flag: **HSAINNOS{SquaringTheCircle}**.
