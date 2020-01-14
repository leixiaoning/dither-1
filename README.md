This is a command line interface for dithering images using the hitherdither library.

# Setup:
1. Install python3
2. cd into the folder which this file is stored and create a folder called output
3. Use pip to install the requirements from requirements.txt, the command `pip install -r requirements.txt` should work, but if it doesn't, you may want to try `pip3 install -r requirements.txt` or `python -m pip install -r requirements.txt`
4. Now run `python dither.py --help` to show all the options available

Inside dither.py I have some code that assumes when writing paths you will be using forwards slashes (/) but if you are on windows this may not be the case, if you need to use backslashes (\\), simply edit the line:
`split_path = image_path.split("/")`
to say:
`split_path = image_path.split("\\")`
(the two backslashes are needed to escape the backslash so it's a valid string)

# Arguments

## Image
**-i** or **--image** </br>
Path to the image you wish to dither. If you do not give the absolute path, it must be either within the same folder as this script or a subfolder. This command is the only one that is always required.

Example:
`python dither.py -i myimage.png`

## Dither
**-d** or **--dither**\n
The name of the dithering algorithm you wish to use.
Available choices:
1. **bayer** or **b**
2. **yliluoma** or **y**
3. **cluster-dot** or **cd**
4. **floyd-steinberg** or **fs**
5. **jarvis-judice-ninke** or **jjn**

Example:
`python dither.py --image input/mycoolimage.png -d yliluoma`

## Palette
**-p** or **--palette**\n
Name of the palette you wish to dither with. If you want to add more palettes, add them to the palettes.py file as a list of rgb tuples, and then go into dither.py and edit the choices of this arg to include the name that you give to your list.
Available choices:
1. **geo32**
2. **dawnbringer16**
3. **pixelcanvas**
4. **pixelzone**
5. **pxlsspace**

Example:
`python dither.py -i /home/username/Pictures/myverycoolimage.jpg -p geo32`

# TODO: document order and threshold better lol
  -t {2,4,8,16,32,64,128,256,512}, --threshold {2,4,8,16,32,64,128,256,512}
                        The threshold value you want to use for dithering.
  -o {2,4,8,16,32}, --order {2,4,8,16,32}
                        The order value you want to use for dithering.

