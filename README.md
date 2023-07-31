# MyKi Kicad Symbols and Footprints

[github.com/Jeff-Russ/MyKi-Kicad-Libaries](https://github.com/Jeff-Russ/MyKi-Kicad-Libaries)  

An ongoing project compiling some add-ons for Kicad in areas I found the Kicad to be lacking.

## Instructions
  
Download or clone this repository. There are many ways to configure KiCad to recognize these libraries but I recommend creating environment variables defining directories in your user directory which can be referenced in forming paths for KiCad to find library items. 

Mac User: I would not place any libary items in `/Applications/KiCad/KiCad.app/Contents/SharedSupport/` subdirectories as updating KiCad will wipe these out. There may be an equivalent situation on Windows and Linux but I can't say for sure. The default environment variables for `KICAD7_SYMBOL_DIR`, `KICAD7_FOOTPRINT_DIR`, `KICAD7_3DMODEL_DIR` are in this location. I also don't recommend changing the value of these variables: instead make new ones that point locations under your control. There are many of the same folders in `/Applications/KiCad/KiCad.app/Contents/SharedSupport/` also in `~/Documents/KiCad/7.0/` and I recommend making environment variables for them. 

Create environment variables from Eeschema via **Preferences** (menu bar) **→ Configure Paths**. I made one called `KICAD_USER_SYMBOL_DIR` that is set to `/Users/<MY_USER_NAME>/Documents/KiCad/7.0/symbols/`, then copied the contents of `Symbols/KiCad7` to this directory and finally imported them from **Preferences → Manage Symbol Libraries**. 

Next open up Pcbnew via **Preferences** (menu bar) **→ Configure Paths** to create an environment variables for footprints. I made one called `KICAD_USER_FOOTPRINT_DIR` that is set to `/Users/<MY_USER_NAME>/Documents/KiCad/7.0/symbols/`, then copied the contents of `Symbols/KiCad7` to this directory and finally imported them from **Preferences → Manage Symbol Libraries**. 

As for the 3D models, just copy the `MyKi/` directory found in `COPYTO-packages3d/` to Kicad's `packages3d/` directory.  

## Updates

For updates you could run `git pull` or re-download the repo but I can't guarantee updates won't break your past project, at least in this early stage while I'm making many changes. Until things stable out you may want to back back up what you've pulled from this repo before making any changes. 
