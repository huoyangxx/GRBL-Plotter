# GRBL-Plotter
[README deutsch](README_de.md)  
A GCode sender for GRBL under windows, using DotNET 4.0 (should also work with Windows XP)  
Written in C# VisualStudio 2015.  
If you like GRBL-Plotter, show it to me with a small donation :-) [![Donate](https://www.paypalobjects.com/en_US/DE/i/btn/btn_donateCC_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=PVBK8U866QNQ6)   
   
### Soon... supporting water color drawing
* Tool table instead of color palette (incl. tool exchange positions (water color pos.))  
* drag tool compensation (to compensate offset when drawing with a brush)   
* automatic subroutine insertion (to refresh brush after drawing a certain distance)  
   
### New in version 1.1.6.x: 
* 1.1.6.4 Add height map manipulation and export to STL, X3D [X3D example](http://svenhb.bplaced.net/?CNC___GRBL-Plotter___Hoehenprofil)  
* 1.1.6.3 Bug fix in surface scan   
* 1.1.6.2 Fixed: After SVG import, first 'pen-up' move was shown as 'pen-down' move   
* 1.1.6.1 Import copied code from [maker.js](https://maker.js.org/demos/)  
  - Just select .DXF or .SVG, press 'Generate', then 'copy the text above'  
  - then paste the code into GRBL-Plotter  
    
* DXF-Text import, check [Font examples](https://www.circuitousroot.com/artifice/drafting/librecad-miscellany/index.html)   
  - Just extend fonts by copying LFF files to subfolder fonts  
  - Information about used fonts [Fonts](https://github.com/svenhb/GRBL-Plotter/blob/master/GRBL-Plotter/fonts/README.md)  

  
### Check [History](https://github.com/svenhb/GRBL-Plotter/blob/master/History.md)  
      
Check the [Wiki](https://github.com/svenhb/GRBL-Plotter/wiki) for further information   

### Program is free and you can use it at your own risk,<br>as you understand there is no warranty of any kind
Zip folder contains ClickOnce application setup. Exe can be found in sub-folder GRBL-Plotter/bin/release.
#### [GRBL-Plotter Vers. 1.1.6.4](https://github.com/svenhb/GRBL-Plotter/releases/latest)  2018-07-08    

### Requirements for compiling
* VisualStudio 2015 
* DotNET 4.0
 
### Feature list:
#### Import/Export:  
* Several options to translate Pen Up/Down
  - controlling a Z axis
  - controlling a servo
  - controlling a laser
  - user defined commands
  - Create GCode absolute or relative (for further use as subroutine)  
* Ruler and import units can be switched between mm or inch
* GCode import via file load, drag & drop or copy & paste
  - Loading GCode with optional replacement of M3 / M4 commands (helpful for 'Laser Mode' $32=1) 
* SVG graphics import via file load, drag & drop (also URL) or copy & paste - tested with [Inkscape](https://inkscape.org/de/) generated SVGs 
  - optional resize to fixed size
  - optional output of nodes only (generating drill holes for string art [Video 'String Art'](https://youtu.be/ymWi15rvTvM)  )
  - optional sorting of paths by used color
  - optional tool change
  - if text needs to be imported, convert text into path first
* DXF graphics import via file load, drag & drop (also URL) - tested with [LibreCAD](http://librecad.org/cms/home.html) generated DXFs 
  - few entities are missing
* Drill file import via file load, drag & drop
* Image import via file load or drag & drop
* GCode can be edited and saved
* Recent File List (Files and URLs)
* Export / import machine specific settings (Joystick, Buttons)
  
#### GCode creation:
* Create Text
  - own created 'Dot Matrix' font [Video 'Dot Matrix'](https://youtu.be/ip_qCQwoufw) 
* Create simple shapes
    
#### GCode manipulation:  
* Transformation of GCodes (scale, rotation, mirror, zero-Offset)  
* Transformation via camera teaching
* Axis Substitution for Rotary Axis
  
#### Machine control:  
* Individual commands via user defined Buttons  
* Joystick like control in user interface  
* support of no-name USB GamePad  
* Optional usage of a WebCam with separate coordinate system: graphics overlay of the current GCode, set zero point, measure angle, zoom, teaching  
  - Shape recognition for easier teach-point (fiducial) assignment  
  - Transforming GCode with camera aid, to match drill file with PCB view [Wiki 'PCB drilling'](https://github.com/svenhb/GRBL-Plotter/wiki/PCB-drilling)   
  
#### Flow control:
* Supporting subroutines M98, M99 Sub-Program Call (P, L)
* Internal variable to support probing, e.g.:
  - G38.3 Z-50		(probe toward tool length sensor, stop on contact - because of deceleration stop-pos. is not trigger-pos.)
  - G43.1 Z@PRBZ	(Offset Tool with value stored on trigger of sensor switch)
  - examine SerialForm.cs for implementation
  
#### GRBL:  
* Automatic reconnect on program start  
* Supporting GRBL 1.1 (and 0.9 also)
* Supporting new GRBL 1.1 features
  - Jogging
  - Feed rate override
  - Spindle speed override
  - real time display GRBL states (in COM CNC window)
* Check limits of GRBL setup - max. STEP frequency and min. FEED rate in COM CNC window  
* Controlling a 2nd GRBL-Hardware
* Supports 4th axis (A, B, C, U, V or W). Status and control (special GRBL version needed)

 
### My test bed
On my german homepage:
[my XYZ platform](http://svenhb.bplaced.net/?CNC___Plotter) 

### GRBL-Plotter in tool change action
[![Import an image](https://img.youtube.com/vi/x5UTHpgsfII/0.jpg)](https://www.youtube.com/watch?v=x5UTHpgsfII) 

### Screenshots
Main GUI
![GRBL-Plotter GUI](doc/GRBLPlotter_GUI.png?raw=true "Main GUI") 

Separate serial COM window(s) - one for the CNC, one for the tool changer (or 4th axis)  
![GRBL-Plotter COM interface](doc/GRBLPlotter_COM2.png?raw=true "Serial connection") ![2nd GRBL control](doc/GRBLPlotter_Control_COM2.png?raw=true "Serial connection")

Setup import / GCode conversion  
![GRBL-Plotter Setup1](doc/GRBLPlotter_Setup1_en.png?raw=true "Setup1") 
  
Setup main configuration  
![GRBL-Plotter Setup2](doc/GRBLPlotter_Setup2_en.png?raw=true "Setup2") 
  
Setup user defined buttons  
![GRBL-Plotter Setup3](doc/GRBLPlotter_Setup3_en.png?raw=true "Setup3") 
  
Setup GamePad  
![GRBL-Plotter Setup4](doc/GRBLPlotter_Setup4_en.png?raw=true "Setup4") 
  
Setup virtual Joystick  
![GRBL-Plotter Setup5](doc/GRBLPlotter_Setup5_en.png?raw=true "Setup5") 
  
Setup shape recogniton for fiducial camera     
![GRBL-Plotter Setup5](doc/GRBLPlotter_Setup6_en.png?raw=true "Setup6") 
  
Text import  
![GRBL-Plotter Text](doc/GRBLPlotter_Text.png?raw=true "Text conversion") 
  
Picture import  
![GRBL-Plotter Image](doc/GRBLPlotter_Image.png?raw=true "Image import") 
  
Different scaling options  
![GRBL-Plotter Scaling](doc/GRBLPlotter_scaling.png?raw=true "GCode scaling") 

Feed rate overrid for Version 0.9 and 1.1  
![GRBL-Plotter Override](doc/GRBLPlotter_override.png?raw=true "GCode override") ![GRBL-Plotter Override](doc/GRBLPlotter_override2.png?raw=true "GCode override")
