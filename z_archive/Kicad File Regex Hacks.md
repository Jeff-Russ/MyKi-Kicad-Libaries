# Kicad File Regex Hacks

## .sch Files

Note that you need to restart Kicad to see any changes made to a .shc file. However, making the changes in a text editor while Kicad is open doesn't seem to be a problem so long as you don't change something afteward in Kicad. Closing and reopening a sheet doesn't seem to grab your external changes; you have to completely close and reopen Kicad.

Here is an example of an entry in .sch `R` resistor:

	$Comp
	L R R100
	U 1 1 59FA8D26
	P 3050 1900
	F 0 "R100" V 3130 1900 50  0000 C CNN
	F 1 "100K" V 3050 1900 50  0000 C CNN
	F 2 "Resistors_THT:Resistor_Horizontal_RM10mm" V 2980 1900 50  0001 C CNN
	F 3 "https://www.vishay.com/docs/31019/ptf.pdf" H 3050 1900 50  0001 C CNN
		1    3050 1900
		1    0    0    -1  
	$EndComp

`R` with spaces around it is the choosen symbol for a Resistor. `F` presumably stands for "Field" with `F 0` being the Reference.  

* `F 0` - Reference  
* `F 1` - Value  
* `F 2` - Footprint Name  
* `F 3` - Datasheet as relative path or URL  

more info here: https://www.compuphase.com/electronics/LibraryFileFormats.pdf  


## Font Sizes

* 1.3 rounds to 1.295 and is seen in .sch as 51  
* 1.27 (Resistor default) is seen in .sch as 50  
* 1.2 rounds to 1.194 and is seen in .sch as 47  
* 1.1 rounds to 1.092 and is seen in .sch as 43  
* 1.0 rounds to 0.991 and is seen in .sch as 39  
* 0.8 rounds to 0.787 and is seen in .sch as 31  
* 0.7 rounds to 0.711 and is seen in .sch as 28  
* 0.6 rounds to 0.610 and is seen in .sch as 24  

An entry in .sch for a resistor with 0.7 entered for value and reference font size would show as something like this:

	$Comp
	L R R7
	U 1 1 59FA9205
	P 4100 1900
	F 0 "R7" V 4180 1900 28  0000 C CNN
	F 1 "100K" V 4100 1900 28  0000 C CNN
	F 2 "" V 4030 1900 50  0001 C CNN
	F 3 "" H 4100 1900 50  0001 C CNN
		1    4100 1900
		1    0    0    -1  
	$EndComp

---

## Reference Font Sizes

__For All Components__  

For changing ALL values font sizes to about 0.8 search:

	(F\s0\s".*"\s\S+\s\d+\s\d+)\s\d+

And replace with:

	$1 31

If `\S` does not work for "non-space" use `[^\s]`. You could probably simplify the search:  

	(F 0 ".*" \S \d+ \d+) \d+

__For All With a Certain Value__  

For this you would just replace `".*"` with the value, so: 

	(F 0 "100K" \S \d+ \d+) \d+


__For All With a Certain Size__  


To limit only change from a particular size to another you would change the ending `\d+` so to change only `43` to `31` the search would be: 

	(F 0 ".*" \S \d+ \d+) 43

__For One Kind of Component__  

To change all `R` resistor values this SHOULD work: 

	(L R .+\nU.+\nP.+\nF 0.+\n ".*" \S \d+ \d+) \d+

---

## Value Font Sizes

__For All Components__  

Here we just need `F 1` instead of `F 0`. For changing ALL values font sizes to about 0.8 search:

	(F\s1\s".*"\s\S+\s\d+\s\d+)\s\d+

And replace with:

	$1 31

Again, you could probably simplify the search to:  

	(F 1 ".*" \S \d+ \d+) \d+


__For All With a Certain Value__  

For this you would just replace `".*"` with the value, so: 

	(F 0 "100K" \S \d+ \d+) \d+


__For All With a Certain Size__  

To limit only change from a particular size to another you would change the ending `\d+` so to change only `43` to `31` the search would be: 

	(F 1 ".*" \S \d+ \d+) 43



__For One Kind of Component__  

To change all `R` resistor values this SHOULD work: 

	(L R .+\nU.+\nP.+\nF 0.+\nF 1 ".*" \S \d+ \d+) \d+




---
---

# Changing Symbols 

Here is a diode chosen as `D_ALT`:

	$Comp
	L D_ALT D_ALT_REF
	U 1 1 59FAA038
	P 4400 1250
	F 0 "D_ALT_REF" H 4400 1350 50  0000 C CNN
	F 1 "D_ALT_VAL" H 4400 1150 50  0000 C CNN
	F 2 "" H 4400 1250 50  0001 C CNN
	F 3 "" H 4400 1250 50  0001 C CNN
		1    4400 1250
		1    0    0    -1  
	$EndComp 

and here is one chosen as `D`

	$EndComp
	$Comp
	L D D1
	U 1 1 59FAA080
	P 4950 1400
	F 0 "D1" H 4950 1500 50  0000 C CNN
	F 1 "D" H 4950 1300 50  0000 C CNN
	F 2 "" H 4950 1400 50  0001 C CNN
	F 3 "" H 4950 1400 50  0001 C CNN
		1    4950 1400
		1    0    0    -1  
	$EndComp
	$Comp

You can swap from `D_ALT` to `D` by searching for 

	(\$Comp\nL\s)D

and replacing with 

	$1D