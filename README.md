# MyKi Kicad Symbols and Footprints

[github.com/Jeff-Russ/MyKi-Kicad-Libaries](https://github.com/Jeff-Russ/MyKi-Kicad-Libaries)  

An ongoing project compiling some add-ons for Kicad in areas I found the Kicad to be lacking.

## Instructions

Download or clone this repository. There are many ways to configure KiCad to recognize these libraries but I recommend creating environment variables defining directories in your user's home directory which can be referenced in forming paths for KiCad to find library items. 

Mac Users: I would not place any library items in `/Applications/KiCad/KiCad.app/Contents/SharedSupport/` subdirectories as updating KiCad will wipe these out. There may be an equivalent situation on Windows and Linux but I can't say for sure. The default environment variables for `KICAD7_SYMBOL_DIR`, `KICAD7_FOOTPRINT_DIR`, `KICAD7_3DMODEL_DIR` are in this location. I also don't recommend changing the value of these variables. Instead, make new environment variables that point locations on your drive that are under your control. There are many of the same folders in `/Applications/KiCad/KiCad.app/Contents/SharedSupport/` also in `~/Documents/KiCad/7.0/` and I recommend making environment variables that point to these `~/Documents/KiCad/7.0/*` directories, where applicable. 

* **symbols**
  * Create environment variables from Eeschema via **Preferences** (menu bar) **→ Configure Paths**. I made one called `KICAD_USER_SYMBOL_DIR` that is set to `/Users/<MY_USER_NAME>/Documents/KiCad/7.0/symbols/`. Then, copy the contents of `symbols/` to this directory. Finally, import them from **Preferences → Manage Symbol Libraries** by clicking the folder icon.
* **footprints**
  * Next, open up Pcbnew via **Preferences** (menu bar) **→ Configure Paths** to create an environment variable for footprints. I made one called `KICAD_USER_FOOTPRINT_DIR` that is set to `/Users/<MY_USER_NAME>/Documents/KiCad/7.0/footprints/`. Then, copy the contents of `footprints/` to this directory. Finally, import them from **Preferences → Manage Footprint Libraries** by clicking the folder icon.
* **3dmodels**
  * The 3D models are a special case: rather than KiCad having mechanism to import them by location, each footprint optionally has a 3D models associated with it and this association is defined as a path within the definition of the footprint. MyKi footprints identify their footprint location by way of a `KICAD_USER_3DMODEL_DIR` environment variables (set from Pcbnew just as you would with footprints) that I have set to  `/Users/<MY_USER_NAME>/Documents/KiCad/7.0/symbols/`. You can choose the path you want but you must have `KICAD_USER_3DMODEL_DIR`  with the contents of `3dmodels/` copied to it if you want to see the 3D Models on footprints that have them. 



## Updates

For updates you could run `git pull` or re-download the repo but I can't guarantee updates won't break your past project if you have project relying on your local paths for their symbols/footprints. You can, of course, do whatever you want with these symbols/footprints/3dmodels, including copying them to project's folders which use them. This is a good practice to future-proof your archived work. 
