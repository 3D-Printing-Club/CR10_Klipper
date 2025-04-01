# CR10_Klipper
All the config and info for the CR-10 to fix and keep running. 


The CR-10 is currently running off a SKR Mini E3 V3 on klipper. 
It is running a E3D Titan extruder with either a 2.85 or 1.75mm V6 hotend. 
The extrusion system is the Hero ME 7 with some assortment of parts. (https://www.printables.com/model/39322-hero-me-gen7-platform-release4)

This has the Prusa Slicer Profiles, The Klipper configs and some other stuff? The most up to date Klipper configs are under the Klipper branch, not under Main. IDK/ I dont want to fix that right now since it requires me to SSH into the Pi.

---------------

**Explanation of Klipper and the foundation of the software/firmware:**

The foundation of the CR-10 rn is the Raspberry Pi that runs the website and most of the code and then the MCU which is the control board that controls the motors. We have the Raspi 4 with a SKR Mini E3 V3 running klipper. On this GitHub are the config files for the printer that have all the code that is unique to this printer. There are a lot of little things that are a part of this process but you shall eventually learn when you read all of these docs. 

I'll provide links to more in depth stuff and tutorials of where I looked to learn these things because they're the best reference but I'll try to explain them best I can too. Hopefully you know what klipper is, but if not. It's essentially the foundation of the MCU's firmware. It is the base language that the MCU uses to move the motors. You have Marlin, Duet/Reprap, Octoprint, and Prusa's firmware as other examples. On top of klipper, you have Moonraker which is run on the Pi and essentially makes the webserver that hosts the website. Meaning, Moonraker is the software that runs the website we interact with. Finally, we have fluidd which is the last system and is the stuff we look at. It is the front end system and the UI for all of it. That's the main software that you interact with when the printer is working as expected. When it's not working as expected there are a lot more variables and things to deal with. When you're dealing with a klipper printer, things are either super right or super wrong. Not a lot of in between. Teaching that stuff is a whole new story and you have to be very ready to be able to learn and fix those things. 

The back end for setting this stuff up is actually kinda simple when you learn how to do it. To adjust the deeper settings of Moonraker, or Klipper, or flashing the printer's MCU, or getting the IP address of the printer, or downloading additional software for the system or a whole other bunch of things you're gonna need to enter into the Pi. That's gonna be through a monitor and keyboard, or through SSH. I typically prefer hooking the pi up to a monitor since it feels more reliable and you might not need a password. The passwords for everything are also on the Officer Bitwarden in case they're needed. Including the stuff for the pi and whatnot. Once your into the printer, open up the terminal and open up KIAUH( Klipper Installation and Updating Helper) which does a lot of the harder stuff for you. Type: into the terminal. 

Include link to KIAUH
./KIAUH/KIAUH.sh

And this should get you to the parts you want to fix/adjust. But you almost never should need to go here. 

Other than this, the printer is also linked to a Octoeverywhere account which allows me to check into the printer wherever I am. Which is  set up through the Purdue 3DPC account login and running through KIAUH. 

I think that's all the software stuff that you really need to know?? At least the definitions of things.

Actually working klipper isn't too difficult, a YouTube tutorial will explain it better than I can over text. It's rather simple and there's a tool/macro for most of the things you want to do. But sometimes you might have to make it or find it yourself. I tried to have as much set up as I could but idk. 

Link to how to use Klipper here. 

Then we go into the actual code/ config for the printer. This is where things get messy and personal. The deep dark truth of this printer is that all( most) of the code is stolen from my own config of me CR-10 Mini. The second deep dark truth is that that config is stolen of my Voron V0.1. Which is also stolen from the Voron Design team. So it's a little bit of a mess. The references to V0/V0.1 are about another printer and I never cared to remove those comments. It brings the deeper character.

But trust the code and look up something before you change it. There's a lot to learn and not easy to teach, so I won't do it here, but I'll try to find someone on YouTube who can. Or call me up and I'll explain it. 

YouTube link here.

I don't know what else to explain deeper. Make sure you plug in the Pi, give it a minute to boot, then turn on the printer and probably hit firmware restart in fluidd. 


---------------

**Printer Tidbits/ Hardware:**

Hardware wise it should be pretty simple. The HeroME system is a lot and paywalled for a tutorial, so I'll just include the parts that I printed for it and hope you can piece it together. The Titan extruder on this printer can be switched between 1.75 and 2.85 mm filament because the lab has around 20 spools just sitting around that we want to use up. We probably spent more money fixing the printer than the spools but that's not the point. To switch it from 2.85 to 1.75, all you need to do it switch the tube between the extruder and hotend. Switch the hotend out for the one you'd like. And change the software in Klipper, and Prusa Slicer's filament settings. Maybe a little bit of calibration but that's all. 

We have a 4020 Nocuta Fan to cool the hotend and a 5015 Blower fan to cool the parts. With a E3D V6 hotend system currently running a 0.6 Brass nozzle. A BLTouch for the bed leveling system and PEI bed. 

The main issue of the machine right now is the hotend and movement system. I don't think the pritner can print faster than 5 mm^3/s without issues in appearance which is annoying, but can be fixed later on. The motion system is limiting it a little, but right now it seems to be that the 3mm fillament is slowing the machine down a lot. The motion system and E3D v6 should both be able to run faster than 5mm^3. Once we run out we will really see.

- Dev
