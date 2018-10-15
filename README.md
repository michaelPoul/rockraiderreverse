## Rock Raider Reverse
A WIP C++ reimplementation/reverse engineering of the 1999 video game Lego Rock Raiders.

### Reverse engineering
The reverse engineering is being done in radare2. The radare2 proj file can be found in the repo at "Rock/rc".
Currently, all reverse engineering information (like function names, global variables, struct layouts, etc.) is stored in the project file.

If you have the original game executable, you can open the project file from a cmd line with

`radare2 -p [ABSOLUTE path to Rock/rc file] [path to LegoRR.exe]`

In the more likely case that you don't have the original executable, the project file can be opened with

`radare2 -p [ABSOLUTE path to Rock/rc file] -`

Once opened, all comments/flag names can be examined. Here are some useful commands to examine the data:

```
fs functions
f~!fcn.,sub.
```
prints out all function flags that don't have "sub." or "fcn.". This effectively prints out all manually named functions, since those prefixes are used by radare's analysis when naming.

```
fs globals
f
```
prints out all global variables

```
CC~+hi
```
prints out all comments which have "hi", case insensitive, in them

```
CC. @ flagName/addr
```
prints out any comment at the given flag/address. flagName can be a function or global variable.

### Reimplementation
WIP. The goal is to start the reimplementation once all of the functions used by gameInit and gameUpdate are named.

### Roadmap
❌ = not done or barely done, 〰 = mostly done, ✔ = done
- ❌ reverse engineering
	- 〰 game engine
		- 〰 registry values
		- 〰 ddraw setup
		- ✔ dinput setup
		- ✔ dsound setup
		- ✔ window setup
		- ✔ wad file loading
	- ❌ game logic
		- ❌ game init function
			- 〰 file loading
			- 〰 config parsing
		- ❌ game update function
		- ❌ game end function
- ❌ reimplementation