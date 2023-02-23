# Scrambled images?: Pixelbrei | 50 Points
For this problem a zip archive is given. When extracted, there are three images called: *channel1.png*, *channel2.png* and *channel3.png*.

They look like this: 
channel1.png             |  channel2.png          |  channel3.png
:-------------------------:|:-------------------------:|:-------------------------:
<img src="https://user-images.githubusercontent.com/118717731/220289624-2ca4b6ea-91d2-43ad-b9f3-508626d1a962.png" alt="channel1" width="320"/>  |  <img src="https://user-images.githubusercontent.com/118717731/220290496-c0526bd2-f2df-497b-9cf3-c08457cf7861.png" alt="channel2" width="320"/> |  <img src="https://user-images.githubusercontent.com/118717731/220290939-8513a6a9-77b9-4147-a9e0-f3300f7e3d7a.png" alt="channel3" width="320"/>

There are several ways to solve this problem:

## Easy way 
You can analyse any of the pictures, e.g. channel1.png, with an online image analyser like [StegOnline](https://stegonline.georgeom.net/image) to see if anything is 
hidden in the colors of the image. When you upload the first image to StegOnline and click "Browse Bit Planes" you, the following is displayed:

<p align="center">
  <img src="https://user-images.githubusercontent.com/118717731/220293419-99115363-b7d5-495b-aefb-3767d70b969e.png" alt="channel1analysed" width="450"/>
</p>

And there you have it. The flag is conveniently written in the middle of the image. Flag: **HSAINNOS{57820d3c}**.

## Intended way
There are 3 images given, but only 1 is needed to find to solution, why? The intended way to solve this problem is to use additive mixing. Additive mixing is used 
in digital graphics, electronics, and other fields. When you encounter the term RGB, for example, in picture editing software, it refers to the three fundamental 
colors red, green and blue.

[Additive mixing](https://en.wikipedia.org/wiki/Additive_color) is performed by combining different colors from the visible light spectrum.

We can apply this procedure to our problem. When we add all the rgb values from the 3 pictures together and combine them to create a new picture, we get the flag as
a result. 
I've written Java code to do this for us:

```Java
import java.awt.image.BufferedImage;
import java.io.File;
import javax.imageio.ImageIO;

public class AdditiveMixing {
    public static void main(String[] args) throws Exception {
        // Load the input images
        BufferedImage image1 = ImageIO.read(new File("channel1.png"));
        BufferedImage image2 = ImageIO.read(new File("channel2.png"));
        BufferedImage image3 = ImageIO.read(new File("channel3.png"));

        // Create the result image
        int width = image1.getWidth();
        int height = image1.getHeight();
        BufferedImage resultImage = new BufferedImage(width, height, BufferedImage.TYPE_INT_ARGB);

        // Loop through each pixel and add the values
        for (int x = 0; x < width; x++) {
            for (int y = 0; y < height; y++) {
                int pixel1 = image1.getRGB(x, y);
                int pixel2 = image2.getRGB(x, y);
                int pixel3 = image3.getRGB(x, y);
                int resultPixel = pixel1 + pixel2 + pixel3;
                resultImage.setRGB(x, y, resultPixel);
            }
        }

        // Save the result image
        ImageIO.write(resultImage, "png", new File("result_image.png"));

    }
}
```

The resulting image is called "result_image.png" and when we view it, it looks like this:
<p align="center">
  <img src="https://user-images.githubusercontent.com/118717731/220298891-2a4b2c58-67d4-4514-8c0b-b4322997dfc0.png" alt="channel1analysed" width="450"/>
</p>

And again the same as before. The flag was hidden in the three images. 

Flag: **HSAINNOS{57820d3c}**.

