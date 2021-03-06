﻿# CL3 <sup>v1.2</sup> - clipboard caching AutoHotkey script

CL3 is a lightweight clone of the CLCL clipboard caching utility
which can be found at <http://www.nakka.com/soft/clcl/index_eng.html>
written in AutoHotkey (Source: <https://github.com/hi5/CL3>)

It is not meant to compete with the many clipboard caching utilities
that are (freely) available, but merely as minimal program with some
basic very features.

You can call the clipboard history menu by its default hotkey <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>v</kbd>
If you prefer another hotkey simply change it in the main script, look for the
line "__; show clipboard history menu__" and change **!^v** to something of your preference.
More on they hotkey syntax here <http://ahkscript.org/docs/Hotkeys.htm#Symbols>

CL3 gets its name from CLCL CLone = CL3

**Features**

- Captures text only
- Limited history (18 items+26 items in secondary menu, does remember more entries in XML history file though)
- Search history (v1.2+)
- 10 Slots with options to save/load several sets (v1.2+)
- Remove (yank) entries from history
- No duplicate entries in clipboard (automatically removed)
- Templates: simply text files which are read at start up
- Plugins: AutoHotkey functions (scripts) defined in separate files

## Templates

Any text file placed in the templates\ directory will be read at
start up and added to the Templates sub-menu (<kbd>Alt</kbd>+<kbd>t</kbd>)

File names act as name of the menu entry and are sorted alphabetically
before being added to the menu. You can influence the order of the menu
entries by naming your files in the order you wish them to appear.

**Example**

File name: "templates\01_Boiler plate 1.txt" will be a "menu entry:"
as "&a. Boiler plate 1"

If you add new text files to the templates directory you need to
reload the script in order for them to appear in the templates sub-menu.

## Plugins

Plugins are AutoHotkey functions you will need to #include in the 
script in order for them to work. A plugin acts on the current 
clipboard content and changes it before it is being pasted.

**Adding plugins**

To add a plugin:

1. Create a script and place it in the plugins\ directory
2. edit plugins\plugins.ahk and add the name of script TWICE
   in the "join list" at the top and in the #include section below it as well.
   The order in which they are listed is used for the menu entries

Default plugins included with CL3:

1. Lower Replace Space (convert to lower case, replace any spaces with an underscore)
2. Lower (convert to lower case)
3. Upper (convert to upper case)
4. Title (convert to title case, basic)

### Search plugins

As of v1.2 you can now search the CL3 history, hotkey <kbd>Ctrl</kbd>+<kbd>Win</kbd>+<kbd>h</kbd>
simply start typing, press enter will paste the first result or you can use the <kbd>UP</kbd> & <kbd>DOWN</kbd>
keys to navigate the result list. See [screenshot](#screenshots).

### Slots plugins

Press <kbd>Ctrl</kbd>+<kbd>Win</kbd>+<kbd>F12</kbd> to open the Slots GUI and define your 10 texts
for quick pasting. See [screenshot](#screenshots).

To facility quick pasting of predefined texts you can use the <kbd>RCtrl</kbd>+<kbd>1</kbd> .. <kbd>RCtrl</kbd>+<kbd>0</kbd>
hotkeys. By default the 10 predefined texts are stored in _slots.xml_ but you can save and load as many slot-files
as you like via the buttons available when the Slots gui is open. The last set used is always stored in _slots.xml_

## Yank (delete) entry

If you select the yank option in the menu you will be presented with a 
simple a to r menu to indicate which of the most recent items you wish to
delete.

## Future plans

None really, but feel free to fork and extend the script and send a pull request.

Some ideas for further development you may wish to consider:

- Extending the number of menu entries in the secondary menu ("more history")
- <strike>Allow the user to search the extensive history</strike> _v1.2+_
- Include rich text formats
- Include images
- Exclude certain programs
- Introduce various paste methods, also for specific programs 
  for example send each character individually
- More (default) plugins:
    - Improved title case (various scripts are available which could replace the current basic one)
	- Strip HTML
	- Find, Replace in clipboard
	- Reformat text, for example email reply format, wrap text etc
	- Plain text and/or Markdown to HTML conversion
	- ...

The [WinClip class](http://www.autohotkey.com/board/topic/74670-class-winclip-direct-clipboard-manipulations/)
by Deo may be of interest to develop some of these ideas.

# Screenshots

![CL3 menu](https://raw.github.com/hi5/CL3/master/img/cl3.png)

![CL3 slots](https://raw.github.com/hi5/CL3/master/img/slots.png)

![CL3 search](https://raw.github.com/hi5/CL3/master/img/search.png)

# Credits

- Icons from Iconic <https://github.com/somerandomdude/Iconic>
- [XA Save / Load Arrays to/from XML Functions - trueski](http://www.autohotkey.com/board/topic/85461-ahk-l-saveload-arrays/) - using a 'fixed' version as forum post is messed up

# Changelog

**v1.2**

* Menu: show icons of the program where text was copied from
* New standard Plugins:
	- Search history
	- Slots
