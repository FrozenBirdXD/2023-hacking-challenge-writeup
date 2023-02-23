# Hidden in plain sight: GIF_me_a_Sign | 50 Points
In this challenge a picture called *pic.png* is provided which looks like this when opened:
<p align="center">
  <img src="https://user-images.githubusercontent.com/118717731/221011124-3596908f-c2e3-4c5c-ad39-babd203b4612.png" alt="original" width="450"/>
</p>

## Solution
Since this appeared to be a normal png there might me something hidden in the picture itself, so I opened the image with an 
online [image analyser](https://29a.ch/photo-forensics/#forensic-magnifier) which provides free online photo forensics tools. If we analyse the noise in the image (process of evaluating the amount and type of noise 
present in a digital image), meaning we analyse the random variation in the brightness or color of pixels, we get this as a result:
<p align="center">
  <img src="https://user-images.githubusercontent.com/118717731/221013372-176c3df2-c9c8-4899-9184-6ae44d428623.png" alt="analysed" width="450"/>
</p>

This openly shows the hidden flag in a place where it appeared that nothing was there. This process of hiding a text in an image is called [steganography](https://en.wikipedia.org/wiki/Steganography). In our case
where the text was hidden within the noise of the image, it's called noise steganography or image-based steganography. 

Flag: **HSAINNOS{GraphicsInterchangeFormat}**.
