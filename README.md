# MyKi Kicad Symbols and Footprints

[github.com/Jeff-Russ/MyKi-Kicad-Libaries](https://github.com/Jeff-Russ/MyKi-Kicad-Libaries)  

An ongoing project compiling some add-ons for Kicad in areas I found the Kicad to be lacking.

## Instructions
  
Download or clone this repository to somewhere in your on your drive (I found adding it to my local Google Drive or Dropbox directories to be most useful as it's automatically updated on all my machines).  

Kicad is able to access schematic symbols (in `.lib` files) and footprints (`*.pretty/*.kicad_mod` files) anywhere on your drive just fine but it's best to put 3D models within Kicad's `packages3d` directory (more on this later).  

As for schematic symbols, when inside __Eechema__, on the `Preferences` menu click `Component Libraries`. Then click `Add` under `User defined search paths` and locate the `Symbols/` directory inside this repo. I prefer to add the path as relative. Next in this same dialog box click `Add` under `Component library files` and select whatever `Symbols/MyKi_*.lib` you want to add.  

Next open up __Pcbnew__ and under the `Preferences` menu click `Footprint Library Wizard` and with `Files on my Computer` selected click `Next`. Locate the `Footprints/` directory inside this repo and select whatever `MyKi_*.pretty` footprints you want to add and click `Next` and choose whether you want to add them globally or just to this project.  

As for the 3D models, just copy the `MyKi/` directory found in `COPYTO-packages3d/` to Kicad's `packages3d/` directory.  

## Updates

For updates you could run `git pull` or re-download the repo but I can't guarantee updates won't break your past project, at least in this early stage while I'm making many changes. Until things stable out you may want to back back up what you've pulled from this repo before making any changes. 
