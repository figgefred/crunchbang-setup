--------------------------
Crunchbang Waldorf
OPENBOX 
SETUP
--------------------------

The following configurations has worked pretty well with a Sony S15, 2012 edition, laptop and uses Crunchbang Waldorf distribution that uses Openbox as a desktop manager. 

It is assumed that conky is already installed and that most default configurations from a Crunchbang Waldorf installation are set. If not, some steps may not be entirely correct and you must figure out by yourself where to make a replace or change.

This README will guide you throught the setup of:

 - conky configurations
 - powersave script
 - bbswitch
 - keyboardlayout with keybindings



# Conky
-------

1) Login as root or run using sudo the run prepare script.

   Note: Installs acpi and lm-sensors, both used by different scripts that this conky setup is dependent on.
         Also sets all the scripts at CHMOD 755 (owner/group/public rwx/r-x/r-x)

2) Run the "install_conky-start"

3) Copy conky folder to home folder and rename as .conky/

4) Edit openbox autostart at ~/.config/openbox/autostart
Find "conky -q" & and replace with "start-conky"

5) Edit openbox menu.xml at ~/.config/openbox/menu.xml
Replace "geany ~/.conkyrc" with "geany ~/.conky/*"
Replace "conkywonky" with "start_conky"

Note: Or simple replace second with 


5) Reboot computer or restart openbox and you all set.


# Powersave
-----------

The prepare script will run "git clone https://github.com/figgefred/powersave.git"
This will fetch the latest changes made.

It may also be fetched from the original author (from which the latter project is forked) by commenting in 
"git clone https://github.com/unia/powersave.git" (don't forget to comment out old)

Note: In order to use the status field in conky one must use the repository from "figgefred" (default)

Installation:

1) Run as root "make install" in the powersave/ directory.

See powersave/README.md for more details.


# bbswitch
----------
bbswitch is a module from the bumblebee project. It is used in this configuration to turn off a second discrete nvidia graphics card to conserve power. Very effective and noticeable.

If using proprietary drivers one must blacklist these as those will otherwise not allow the card to shut down. Noveau drivers seem fine though.

See bbswitch/README.md for more specifics and howtos.

INSTALLATIONS:
 - See bbswitch/README.md


# Keyboardlayout (and keybindings)
----------------------------------
Keyboardlayout is kind of annyoing in crunchbang. Using this scripts it will hopefully become less painful.

To install: "sudo ./install_keyboardlayout"
There are three layouts preconfigured (swedish, us-english and german) with out any dead keys. It works for other languages too, yet for those there will most likely be dead keys on the keyboard, no altgr for example.

To configure copy one of the case blocks in the keyboardlayoutscript and make a new case for you language and replace the "-variant" argument with a value corresponding to one from this file: "/usr/share/X11/xkb/rules/base.lst".

Usage:
  "keyboardlayout se|de|en" --> You will get a desktop notification :)
  

Key bindings:
1) Open "~/.config/openbox/rc.xml" to edit
2) locate <keyboard> tag and add a keybinding

Use this as a template:
	<!-- COPY BELOW HERE -->
	<keybind key="C-A-S-s">
	  <action name="Execute">
		<startupnotify>
		  <enabled>true</enabled>
		  <name>keyboardlayout_se</name>
		</startupnotify>
		<command>keyboardlayout se</command>
	  </action>
	</keybind>
	<!-- END COPY ABOVE HERE -->
Note: The C-A-S-s is a combination of the buttons CTRL, ALT, SHIFT and "s" key(s)











