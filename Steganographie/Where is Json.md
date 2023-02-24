# A hidden 3D object?: Where is Json | 50 Points
In this challenge, we are provided with a single file called '*where_is_json*'. But it doesn't have a file extension.

## Solution
Since the file type is unknown, we have to analyse it first. We open the file in a hex editor, for example 
[010 editor](https://www.sweetscape.com/010editor/).
There, looking at the first few bytes of the file, also known as the file signature, shows following:
      
    50 4B 03 04 - in hexadecimal ('PK  ' - in text)
    
This is the file signature of a zip file format and formats based on it, such as EPUB or JAR, which means we are working with an archive. 
[Wikipedia](https://en.wikipedia.org/wiki/List_of_file_signatures) has an extensive list of file signatures, which I recommend checking out. 

We can check if the file is a zip archive by renaming the file extension of the *where_is_json* file to ".zip". This works and reveals that the archive 
contains a file named "*where_is_json.json*".

### JSON

After opening "*where_is_json.json*" with a text editor like Notepad, we see a lot of data that cannot be represented by text, and a part containing JSON 
data. Then, after formatting the JSON to make it more readable, the first part of it looks like this:
```JSON
{
  "asset": {
    "generator": "Khronos glTF Blender I/O v3.4.50",
    "version": "2.0"
  },
  "scene": 0,
  "scenes": [
    {
      "name": "Scene",
      "nodes": [
        0
      ]
    }
  ],
  "nodes": [
    {
      "mesh": 0,
      "name": "imagetostl_mesh"
    }
  ],
  "materials": [
    {
      "doubleSided": true,
      "name": "mat0",
      "pbrMetallicRoughness": {
        "baseColorFactor": [
          0.8627451062202454,
          0.8627451062202454,
          0.8627451062202454,
          1
        ],
        "metallicFactor": 0,
        "roughnessFactor": 0.4000000059604645
      }
    }
  ],
  "meshes": [
    {
      "name": "imagetostl_mesh",
      "primitives": [
        {
          "attributes": {
            "POSITION": 0,
            "NORMAL": 1
          },
          "indices": 2,
          "material": 0
        }
      ]
    }
  ]
```

Here there are several indicators that show that the file has something to do with a 3D object and the program [Blender](https://www.blender.org/download/). 

The first
indicator is that a generator called "Khronos glTF Blender" was used. A search on the internet reveals that [Khronos glTF](https://www.khronos.org/gltf/) is an 
open standard 3D file format created for the fast transmission and loading of 3D scenes and models. "Blender ..." means that the 
[Blender glTF 2.0 exporter](https://github.com/KhronosGroup/glTF-Blender-IO) was used to create the file, which means we are working with a 3D object file.

The second indicator is that multiple names are visible, for example "imagetostl_mesh". This shows that something has to do with a 3D object because STL (STereoLithography) is a file format used to represent 3D models.

With a bit of searching on the internet we learn that a glTF (GL Transmission Format) file consists of a JSON (JavaScript Object Notation) file that describes 
the 3D model and one or more binary files (bin) that include the 3D data, such as materials, textures, and other elements. The JSON file
specifies the scene graph and the binary files contain the actual data for these objects and are stored separately.

Applying this knowledge to our problem we can assume that the JSON we found is the JSON file in glTF and the rest of the data that couldn't be displayed by the text
editor is the binary data (bin). This means our file extension can be changed from '*.json*' to '*.glTF*'. 

### Blender
To view the file, we need to import the *.glTF* file into a 3D computer graphics software tool, like the free, popular and open source tool 
called [Blender](https://www.blender.org/download/). When opened in object mode we see this:

![blender](https://user-images.githubusercontent.com/118717731/221148877-503aee0f-57a3-4334-ad2f-a54e9ad1ba48.png)

This is our flag! But to make it more easily readable, we can mirror it by setting the scale in the X direction to -1.00:

![blender new](https://user-images.githubusercontent.com/118717731/221149579-20125751-bb55-47d7-b543-ee27df3afc20.png)

Now the flag can be read.

Flag: **HSAINNOS{YouFoundJson}**.
