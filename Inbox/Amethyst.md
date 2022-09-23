---
tags:
- tools/amethyst 
---
## Config

- Modifiers
	- `mod1` => `option + shift + command`
	- `mod2` => `ctrl + option + shift + command`
- Actions
	- Layout
		- `mod1 + t` Select Tall-right layout
		- `mod1 + s` Select Row layout
		- `mod1 + r` Select Fullscreen layout
	- Windows
		- Focus
			- `mod1 + m` Move focus to main window
			- `mod1 + j` Move focus counter clockwise
			- `mod1 + k` Move focus clockwise 
		- Swap
			- `mod1 + enter` Swap focused window with main window
			- `mod2 + j` Swap focused window counter clockwise
			-  `mod2 + k` Swap focused window clockwise
		- Throw
			- `mod2 + w` Throw focused window to screen 1
			- `mod2 + e` Throw focused window to screen 2
		- Toggle float
			- `mod1 + a` 
	- Screen
		- Focus
			- `mod1 + w` Focus Screen 1
			- `mod1 + e` Focus Screen 2
	- Misc
		- `mod1 + z` Force windows to be reevaluated
		- `mod2 + x` Relaunch Amethyst
		- `mod1 + i` Display current layout

## Needs
- Allow to switch to specific layout
	- Already implemented https://github.com/ianyh/Amethyst#keyboard-shortcuts
- Allow per screen layout config (eg Screen 1 : Full screen+row ; Screen 2 Full screen+Tall)
	- Choose a default layout for each display https://github.com/ianyh/Amethyst/issues/1098 
	- Add option to specify initial layout for each virtual desktop https://github.com/ianyh/Amethyst/issues/302
	- Persistent Application State https://github.com/ianyh/Amethyst/issues/151
	- Configure default layout based on screen dimensions https://github.com/ianyh/Amethyst/issues/293
	- Assign a default layout to a space https://github.com/ianyh/Amethyst/issues/150
- Allow Nord/East/West/South window focus instead of cycle only
	- Directional focus https://github.com/ianyh/Amethyst/issues/521
- Allow Nord/East/West/South window swap instead of main only
	- Directional swap https://github.com/ianyh/Amethyst/issues/1305