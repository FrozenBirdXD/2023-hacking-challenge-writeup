# The third task of Security4Fun!: Compressed | 50 Points
For this challenge only a zip archive called *compressed.zip* is given. But Windows cannot open it, since it is an invalid zip archive.

Again there are multiple ways to find the solution:
1. To figure out what kind of file it is, look at the file header, to do that open it with a hex editor like [010 Editor](https://www.sweetscape.com/010editor/). When
opened, this is the first line: "%PDF-1.3.%ÂµÂ¶ (25 50 44 46 2D 31 2E 33 0A 25 C2 B5 C2 B6 0A)". 
    
    **%PDF-1.3.** is a normal PDF header. This indicates that the file format is PDF and uses PDF specification 1.3. Because the "%" character represents 
a comment in PDF, the first and second lines in the above example are comments, as is true for all PDF documents. After the second "%" there is a comment, 
which are typically used to inform software products that the file includes binary data and should not be interpreted as 7-bit ASCII text. More information about
the PDF file format can be found [here](https://resources.infosecinstitute.com/topic/pdf-file-format-basic-structure/).

    Since the file type is now know, the extension ".zip" can be replaced with ".pdf" and the file can now be opened with a pdf viewer like the popular
[adobe acrobat reader](https://www.adobe.com/de/acrobat/pdf-reader.html). A blank page is displayed with following content, the flag:

>![1](https://user-images.githubusercontent.com/118717731/220561250-fc0994a0-fb3d-420b-9c7a-882ec506e8eb.png)

2. An "easier" way to do this, is to let a program do the work for us. [This](https://filext.com/online-file-viewer.html) online file viewer can analyse a file and
tell us the true file format, in our case PDF. Then it even displays the PDF for us and the same as in the picture above can be seen. 

Flag: **HSAINNOS{PolyglotFilesAreCrazy}**.


